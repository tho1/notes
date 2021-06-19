##Powershell cmdlets that are useful to look things up.

Windows operating system comes with powershell to look things up.  It is like a Windows version of Unix shell, with its set of cmdlet. 
The great thing is it comes with windows.  No installation required.
Windows also had the PowerShell ISE to try out new cmdlet.  Think of like a scratchpad to try out cmdlet. Good tool to help learn the powershell.


This checks the powershell version installed.
```$PSVersionTable```

Check the network connections and check is it open
```
Test-NetConnection -ComputerName localhost -Port 9080
```

Check the security certificate available.
```Get-TlsCipherSuite | ft name, certificate, cipherlength```


compare two files.  It is an alias to the following command. compare-object (get-content one.txt) (get-content two.txt)
```diff (cat file1) (file2)```

Reference: https://serverfault.com/questions/5598/how-do-i-diff-two-text-files-in-windows-powershell?newreg=c02d8c5e112b40e99352b6ee00b26170


I'm trying to find differences in the content of two folder structures using Windows Powershell. I have used the following method to ensure that the file names are the same, but this method does not tell me if the contents of the files are the same:


```
$firstFolder = Get-ChildItem -Recurse folder1
$secondFolder = Get-ChildItem -Recurse folder2
Compare-Object -ReferenceObject $firstFolder -DifferenceObject $secondFolder
```
The technique described in this ServerFault question works for diffing a single file, but these folders contain hundreds of files at a variety of depths.

The solution does not necessarily need to tell me what specifically in the files is different - just that they are. I am not interested in differences in metadata such as date, which I already know to be different.


If you want to wrap the compare into a loop I would take the following approach:
```
$folder1 = "C:\Users\jscott"
$folder2 = "C:\Users\public"

# Get all files under $folder1, filter out directories
$firstFolder = Get-ChildItem -Recurse $folder1 | Where-Object { -not $_.PsIsContainer }

$firstFolder | ForEach-Object {

    # Check if the file, from $folder1, exists with the same path under $folder2
    If ( Test-Path ( $_.FullName.Replace($folder1, $folder2) ) ) {

        # Compare the contents of the two files...
        If ( Compare-Object (Get-Content $_.FullName) (Get-Content $_.FullName.Replace($folder1, $folder2) ) ) {

            # List the paths of the files containing diffs
            $_.FullName
            $_.FullName.Replace($folder1, $folder2)

        }
    }   
}
```
Note that this will ignore files which do not exist in both $folder1 and $folder2.

I have taken jscott's answer an expanded it to output the files that are present in one but not the other for those who are insterest in that type of functionality. Please note it also shows progress made since it was hard for me to see that given the huge folders with not very many differences. It looked like the script was hung to me. Here is the 
powershell code for that:

```
$folder1 = "C:\Folder1"
$folder2 = "C:\Folder2"

# Get all files under $folder1, filter out directories
$firstFolder = Get-ChildItem -Recurse $folder1 | Where-Object { -not $_.PsIsContainer }

$failedCount = 0
$i = 0
$totalCount = $firstFolder.Count
$firstFolder | ForEach-Object {
    $i = $i + 1
    Write-Progress -Activity "Searching Files" -status "Searching File  $i of     $totalCount" -percentComplete ($i / $firstFolder.Count * 100)
    # Check if the file, from $folder1, exists with the same path under $folder2
    If ( Test-Path ( $_.FullName.Replace($folder1, $folder2) ) ) {
        # Compare the contents of the two files...
        If ( Compare-Object (Get-Content $_.FullName) (Get-Content $_.FullName.Replace($folder1, $folder2) ) ) {
            # List the paths of the files containing diffs
            $fileSuffix = $_.FullName.TrimStart($folder1)
            $failedCount = $failedCount + 1
            Write-Host "$fileSuffix is on each server, but does not match"
        }
    }
    else
    {
        $fileSuffix = $_.FullName.TrimStart($folder1)
        $failedCount = $failedCount + 1
        Write-Host "$fileSuffix is only in folder 1"
    }
}

# Rename multiple files extension in a directory

Get-ChildItem -Path C:\temp\bsarWork\checkCode  -Filter *.inc | Rename-Item -NewName {[System.IO.Path]::ChangeExtension($_.Name, ".dev")}

$secondFolder = Get-ChildItem -Recurse $folder2 | Where-Object { -not $_.PsIsContainer }

$i = 0
$totalCount = $secondFolder.Count
$secondFolder | ForEach-Object {
    $i = $i + 1
    Write-Progress -Activity "Searching for files only on second folder" -status "Searching File  $i of $totalCount" -percentComplete ($i / $secondFolder.Count * 100)
    # Check if the file, from $folder2, exists with the same path under $folder1
    If (!(Test-Path($_.FullName.Replace($folder2, $folder1))))
    {
        $fileSuffix = $_.FullName.TrimStart($folder2)
        $failedCount = $failedCount + 1
        Write-Host "$fileSuffix is only in folder 2"
    }
}
```

* [User Page: Richard Mueller
](https://social.technet.microsoft.com/wiki/contents/articles/31616.user-page-richard-mueller.aspx)

* [powershell](https://gallery.technet.microsoft.com/PowerShell-Script-to-b7c247db)    sample to call winform from powershell
* [GUI for powershell](https://theitbros.com/powershell-gui-for-scripts/)
* [powershell winform](https://adamtheautomator.com/powershell-form/)
* [sqlcmd](https://www.sqlshack.com/working-with-powershells-invoke-sqlcmd/)
