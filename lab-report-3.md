# Lab Report 3

Source: [Find Manual](https://man7.org/linux/man-pages/man1/find.1.html)

## `-type`
```
$ find technical -name "*ov*" -type "d"
technical/government
```

```
$ find technical -name "*ov*" -type "f"
technical/government/Env_Prot_Agen/nov1.txt
technical/government/Gen_Account_Office/GovernmentAuditingStandards_yb2002ed.txt
technical/government/Media/Poverty_Lawyers.txt
technical/government/Media/Providing_Legal_Aid.txt
```
This flag is used to match files based on its type. If you are looking for a directory, use `d`. If you are looking for a file, use `f`.

## `-printf`
```
$ find technical -name "ar1*" -printf "%P %s %t \n" # print file path (excluding the starting folder), then size in bytes, then the date of file's creation
biomed/ar104.txt 37874 Wed May 10 20:31:53.9562655000 2023 
biomed/ar118.txt 36954 Wed May 10 20:31:53.9577802000 2023
biomed/ar120.txt 32968 Wed May 10 20:31:53.9618004000 2023
biomed/ar130.txt 47382 Wed May 10 20:31:53.9637294000 2023
biomed/ar140.txt 38888 Wed May 10 20:31:53.9662463000 2023
biomed/ar149.txt 25721 Wed May 10 20:31:53.9662463000 2023
```

```
$ find technical -name "*sion*" -printf "%p\t %a\n" # print file's full path, tab, and then the time it was last accessed
technical/government/About_LSC/commission_report.txt     Wed May 10 21:03:38.7072646000 2023
technical/government/About_LSC/ODonnell_et_al_v_LSCdecision.txt  Wed May 10 21:03:38.7115275000 2023
technical/government/Alcohol_Problems/Session2-PDF.txt   Wed May 10 21:03:38.7151015000 2023
technical/government/Alcohol_Problems/Session3-PDF.txt   Wed May 10 21:03:38.7151015000 2023
technical/government/Alcohol_Problems/Session4-PDF.txt   Wed May 10 21:03:38.7151015000 2023
```
This flag is used to customize the data that the command prints. You can specify what format the output will be printed much like Java's `System.out.printf()` function.

## `-mmin`
```
$ find technical -name "LegalServCorp*" -mmin "-1" -printf "%p %t\n" # match files that were modified within the last minute and print the file path and the time it was last modified
technical/government/About_LSC/LegalServCorp_v_VelazquezDissent.txt Wed May 10 21:38:34.1913717000 2023
```

```
$ find technical -name "LegalServCorp*" -mmin "+1" -printf "%p %t\n" # match files that were modified more than a minute ago and print the file path and the time it was last modified
technical/government/About_LSC/LegalServCorp_v_VelazquezOpinion.txt Wed May 10 20:31:54.4119748000 2023
technical/government/About_LSC/LegalServCorp_v_VelazquezSyllabus.txt Wed May 10 20:31:54.4129921000 2023
```
This flag is used to match based on how many minutes the file was last modified. Useful for when you want to look for files that have been or been not recently changed.

## `-size`
```
$ find technical -size +300k -printf "%p %s \n" # match files whose sizes are greater than 300kb and print their paths and size in bytes
technical/government/Gen_Account_Office/d01591sp.txt 307735 
technical/government/Gen_Account_Office/Statements_Feb28-1997_volume.txt 312125
```

```
$ find technical -size 1k -printf "%p %s \n" # match files whose sizes are equal to 1kb (rounded up) and print their paths and size in bytes
technical/plos/pmed.0020191.txt 893 
technical/plos/pmed.0020226.txt 937
```
This flag matches files whose size matches the given criteria. This is useful for if you want to find which files are taking up the most space.

