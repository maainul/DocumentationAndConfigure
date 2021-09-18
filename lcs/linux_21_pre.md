# Linux Important cmd

## Basic Cmd

## File Display CMD

1. cat
2. more
3. less
4. head
5. tail
	
 List directory
	
		ls
		
 Change dirctory
	
		cd
		
 Display current working dirctory
	
		pwd
		
 display files data

		cat filename
		
 Display argument to the screen
	
		echo filename
		
 Display online manual
	
		man commandname
		
 Exit current session
	
		exit
		
 Clear the screen
	
		clear
		
 Make directory 
	
		mkdir filename
	
 Making Multiple directory

		mkdir -p dir1/dir2/dir3

 Remove dirctory
	
		rmdir dir1

 Remove multiple directory

		rm -rf dir1

 Go the the previous directory
	
		cd -
		
## List Directory CMD

 list directory 
	
		ls -l
		
 list directory with all files

		ls -l -a (ls -la)

 list directory with filetype
	
		ls -laF (F = FileType)

 list files with time		
		ls -t (list files by time)
		
 list files with files and reverse order

		ls -r (Reverse order)

 list long with files reverse sort time
		
		ls -latr (long listing,all files,reverse, sort by time)

 list with directory
	
		ls -d

 list files with color
		
		ls --color

 list Music files name

		ls -l Music

 list Music directory Music
	
		ls -ld Music
		
 Tree command to list of files
	
		tree -d

 Tree command with color
		
		tree -c


## Finding Files
	
		find .
		
		find

		find -iname anyname

		find /sbin -name makedif


## Find files 10 days old but less than 30 than pwd

		find . -mtime +10 -mtime -13
		
		find . -name s* -ls
		
		find . -size +1kb

		find . -type d -newer file.txt

		
## Viewing Files

 Show file info

		cat App.js

 See first 10 line
	
		head App.js

 See first 2 line

		head -2 App.js
	
 See last 10 line
	
		tail App.js

 See last 2 line

		tail -2 App.js

 See page wise
	
		more App.js
	
 see line by line	
	
		less App.js


## Copy files

		cp src dest

		cp src_fil1 src_file2 dest_dir

		cp - i file1 file2

		cp -r dir1 dir2


## Moving and rename files

		mv src dest (rename dirctory src to dest)

		mv -i src dst
## Sorting Data

		sort more.txt

		sort -u more.txt


## Create Directory and Files

		cp
		
		touch

		vi		
## CMDS

		
		mv test newfilename
		
		touch hello.txt
		
		touch hello1.txt hello2.txt
		
		rm -r docker/
		
		vi file1.txt

## WildCards 

		* - zero or more character

		? - a single character

		[] - a range of characters

## create files using wildcards

		touch 

		rm abc*

		touch abcd{1..9}-xyz
		
		ls -l abc*

		rm abcd*

		ls -l ?bcd*

		ls -l ?[cd]*
				
## Linux file types

		- --> regular file
		
		l --> link
		
		c --> special file
		
		s --> socket
		
		p --> named pipe
		
		b--> block device
	
## Read and write files

		cat file1.txt > file2.txt ---> read file1 and write data file2

		cat file1.txt file2.txt --> read multiple files

		cat file1.txt file2.txt > combined.txt ---> read two file and write into 1

		echo hello file1.txt

		ls -l /etc > files.txt

		cat files.txt		

## Standard Output with tee

Read data
		
		echo "mainul hasan"

Create File with some text

		echo "mainul" > file.txt

Create file and write data and show lines
	
		echo "this is me" | tee file2.txt

append line in the existing file

		echo "This is second line" | tee -a file2.txt

		cat file2.txt

Check how many character in a file

		wc -c file2.txt


## Pipes : Connects two or many commands

		cd /etc
		
show files and one page at a time

		ls -ltr | more

Show last lines of output

		ls -ltr | tail -1
		
		
		

























	
