##Powershell cmdlets that are useful to look things up.

Windows operating system comes with powershell to look things up.  It is like a Windows version of Unix shell, with its set of cmdlet. 
The great thing is it comes with windows.

Windows also had the PowerShell ISE to try out new cmdlet.  Think of like a scratchpad to try out cmdlet.

Useful one.


$PSVersionTable
This checks the powershell version installed.

Test-NetConnection -ComputerName localhost -Port 9080
Check the network connections and check is it open

Get-TlsCipherSuite | ft name, certificate, cipherlength
Check the security certificate available.

diff (cat file1) (file2)
compare two files.  It is an alias to the following command. compare-object (get-content one.txt) (get-content two.txt)

Reference: https://serverfault.com/questions/5598/how-do-i-diff-two-text-files-in-windows-powershell?newreg=c02d8c5e112b40e99352b6ee00b26170

diff two directories.

Viewed 24k times

Report this ad

11


3
I'm trying to find differences in the content of two folder structures using Windows Powershell. I have used the following method to ensure that the file names are the same, but this method does not tell me if the contents of the files are the same:

$firstFolder = Get-ChildItem -Recurse folder1
$secondFolder = Get-ChildItem -Recurse folder2
Compare-Object -ReferenceObject $firstFolder -DifferenceObject $secondFolder
The technique described in this ServerFault question works for diffing a single file, but these folders contain hundreds of files at a variety of depths.

The solution does not necessarily need to tell me what specifically in the files is different - just that they are. I am not interested in differences in metadata such as date, which I already know to be different.

powershell diff
share  improve this question  follow 
edited Apr 13 '17 at 12:14

Community♦
1
asked Aug 19 '13 at 16:01

David Smith
21911 gold badge22 silver badges77 bronze badges
add a comment
4 Answers
Active
Oldest
Votes

15

If you want to wrap the compare into a loop I would take the following approach:

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
Note that this will ignore files which do not exist in both $folder1 and $folder2.

share  improve this answer  follow 
edited Aug 19 '13 at 17:24
answered Aug 19 '13 at 17:18

jscott
22.8k66 gold badges6464 silver badges9393 bronze badges
add a comment

5

I have taken jscott's answer an expanded it to output the files that are present in one but not the other for those who are insterest in that type of functionality. Please note it also shows progress made since it was hard for me to see that given the huge folders with not very many differences. It looked like the script was hung to me. Here is the powershell code for that:

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

