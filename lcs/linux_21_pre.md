# Linux Important cmd

## Basic Cmd

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

## File Display CMD / Viewing Files

1. cat
2. more
3. less
4. head
5. tail

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

## Permissions

Types of Permissions:

1.  r - read
2.  w - write
3.  x - running a program (executable)

rwx

Types of permission group

1.  u - user
2.  g- group
3.  o - other

Command to change permisson

    	chmod

    	chmod ugo+r FILE

change Permission

		chmod g+w sales.txt (change sales.txt to write permission)

		chmod g-w sales.txt (remove permission)

		chmod g+wx sales.txt (multiple permissions)

		chmod u+rwx,g-x sales.txt

		chmod a=r sales.txt

		chmod u=rwx,g=rw o= sales.txt (after o= no value means no permission to other)

		chmod a-r file.txt (remove read permission for everyone)

5.  Numeric Based Permissions

		chmod ugo+ FILE

or

		chmod 444 FILE

## Permission list

![chmod-Notation-1](https://user-images.githubusercontent.com/85335954/133926158-8380423e-ac36-4213-ac4f-5cfdfe08cf03.png)

If type

    chmod 644 files.txt

![chmod-octal-format-explained](https://user-images.githubusercontent.com/85335954/133926227-b8743324-6b8e-4a89-94c5-d4d558c2f900.jpg)

        chmod 400 my-cat (dr--------)

        chmod 500 my-cat (dr-x------)

## File Ownership

1.  chown
2.  chgrp

		chown root lisa

		chgrp root lisa

## Access Control List(ACL) : Provides an additional,more flexible permission mechanism for file systems

user is not a member of group created by you but still you want to give some read or write access,how can you do it without making user a member of group.

Add permission to the user

		setfacl -m u:user:rwx /path/to/file

Add permission to the group

		setfacl -m g:group:rw /path/to/file

To remove specific entry

		setfacl -x u:user /path/to/file

To remove all entries

		setfacl -b path/to/file

Show the file permission of a file

		getfacl filename

# Not Complete--------------------------X X X

## Help CMD

    	whatis

    	help

    	man

    	whatis ls

    	whatis cd

    	whatis pwd

## Adding Text to files

3 way to add text to a file

1.  vi
2.  Redirect command output
3.  echo > or >>

Create file and write line >

        echo "it is raining outside" > rain.txt

Append line in the second line >>

        echo "it is raining again second line" >> rain.txt

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

## Read and write files

		cat file1.txt > file2.txt ---> read file1 and write data file2

		cat file1.txt file2.txt --> read multiple files

		cat file1.txt file2.txt > combined.txt ---> read two file and write into 1

		echo hello file1.txt

		ls -l /etc > files.txt

		cat files.txt

## Filters/ Text Processors Commands

1. cut
2. awk
3. greap and egrep
4. sort
5. uniq
6. wc

## Cut - Text Processors commands

		cut filename

		cut --version

		cut -c1 filename    = List one character

		cut -c1,2,4 filename = pick and chose character

		cut -c1-3,6-8 filename = list range of character
		
		cut -b1-3 filename    = byte size file
		
		cut -d: -f 6 /etc/passwd =  6th column separated by

		ls -l | cut -c2-4 = Only print user permissions of files/dir


## AWK : utility/language designed for data extraction.Most of the time it is used to extract fields from a file of=r from an output.














