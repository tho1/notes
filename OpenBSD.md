### Installing openbsd

https://sohcahtoa.org.uk/openbsd.html

https://news.ycombinator.com/item?id=20344766 some thoughts on using openbsd as a workstation.


### Make openbsd a desktop system with GUI
https://framagit.org/3hg/isotop/-/blob/master/README.md


### Conversion between Unix and Dos format

#### DOS to UNIX

```
tr -d '\r' < input.file > output.file
perl -pi -e 's/\r\n/\n/g' input.file
```

#### UNIX to DOS
```
sed 's/$'"/`echo \\\r`/" input.txt > output.txt
```
