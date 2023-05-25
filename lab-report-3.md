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
The command only returns either files or directories. If you are looking for a directory, use `d` (top). If you are looking for a file, use `f` (bottom). This is useful for when you only are looking for a file or only a directory and using `find` normally returns both.

## `-printf`
```
$ find technical -name "ar1*" -printf "%P %s %t \n" 
biomed/ar104.txt 37874 Wed May 10 20:31:53.9562655000 2023 
biomed/ar118.txt 36954 Wed May 10 20:31:53.9577802000 2023
biomed/ar120.txt 32968 Wed May 10 20:31:53.9618004000 2023
biomed/ar130.txt 47382 Wed May 10 20:31:53.9637294000 2023
biomed/ar140.txt 38888 Wed May 10 20:31:53.9662463000 2023
biomed/ar149.txt 25721 Wed May 10 20:31:53.9662463000 2023
```

```
$ find technical -name "*sion*" -printf "%p\t %a\n" 
technical/government/About_LSC/commission_report.txt     Wed May 10 21:03:38.7072646000 2023
technical/government/About_LSC/ODonnell_et_al_v_LSCdecision.txt  Wed May 10 21:03:38.7115275000 2023
technical/government/Alcohol_Problems/Session2-PDF.txt   Wed May 10 21:03:38.7151015000 2023
technical/government/Alcohol_Problems/Session3-PDF.txt   Wed May 10 21:03:38.7151015000 2023
technical/government/Alcohol_Problems/Session4-PDF.txt   Wed May 10 21:03:38.7151015000 2023
```
This flag is used to customize the data that the command prints, such as path, size (top), or when it was last accessed (bottom), in a format similar to Java's `System.out.printf()` function. This is useful if you want to display certain information about the files you are looking for. 

## `-mmin`
```
$ find technical -name "LegalServCorp*" -mmin "-1" -printf "%p %t\n" 
technical/government/About_LSC/LegalServCorp_v_VelazquezDissent.txt Wed May 10 21:38:34.1913717000 2023
```

```
$ find technical -name "LegalServCorp*" -mmin "+1" -printf "%p %t\n"
technical/government/About_LSC/LegalServCorp_v_VelazquezOpinion.txt Wed May 10 20:31:54.4119748000 2023
technical/government/About_LSC/LegalServCorp_v_VelazquezSyllabus.txt Wed May 10 20:31:54.4129921000 2023
```
This flag is used to match based on if the file was last modified more than (bottom), less than (top), or equal to the specified number of minutes. This is useful for when you want to search for files that have been recently edited within a specific time frame.

## `-size`
```
$ find technical -size +300k -printf "%p %s \n" 
technical/government/Gen_Account_Office/d01591sp.txt 307735 
technical/government/Gen_Account_Office/Statements_Feb28-1997_volume.txt 312125
```

```
$ find technical -size 1k -printf "%p %s \n" 
technical/plos/pmed.0020191.txt 893 
technical/plos/pmed.0020226.txt 937
```
This flag matches files whose size is larger (top), smaller, or around the same size (bottom) as given in the command. This is useful for if you want to find files that take up a certain amount of space.

