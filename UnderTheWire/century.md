## My answers to UnderTheWire --- https[:]//underthewire[.]tech/century

### Century 1: 
	Challenge: The password for Century2 is the build version of the instance of PowerShell installed on this system.
	Username: century1
	Password: century1
	Solution Description: $psversion table varible holds the answer. Use Get-Variable or gv to list all variables
	Answer: 10.0.14393.6343

### Century 2: 
	Challenge: The password for Century3 is the name of the built-in cmdlet that performs the wget like function within PowerShell PLUS the name of the file on the desktop.
	Username: century2
	Password: 10.0.14393.6343
	Solution Description: help wget > invoke-webrequest and ls desktop > file 443
	Answer: invoke-webrequest443

### Century 3: 
	Challenge: The password for Century4 is the number of files on the desktop.	
	Username: century3
	Password: invoke-webrequest443
	Solution Description: (ls).count > to get the number of items in the output
	Answer: 123

### Century 4: 
	Challenge: The password for Century5 is the name of the file within a directory on the desktop that has spaces in its name.
	Username: century4
	Password: 123
	Solution Description: Just cd into the directory. cd '.\<Dir Name Here>'
	Answer: 34182

### Century 5: 
	Challenge: The password for Century6 is the short name of the domain in which this system resides in PLUS the name of the file on the desktop.
	Username: century 5
	Password: 34182
	Solution Description: Use the evironment variable USERDOMAIN. $env:USERDOMAIN + file name in desktop dir
	Answer: underthewire3347

### Century 6: 
	Challenge: The password for Century7 is the number of folders on the desktop.	
	Username: century6	
	Password: underthewire3347
	Solution Description: Same thing as century3 except we will use the -Directory flag to only select directories. (ls -Dir).count
	Answer: 197

### Century 7: 
	Challenge: The password for Century8 is in a readme file somewhere within the contacts, desktop, documents, downloads, favorites, music, or videos folder in the user’s profile.
	Username: century7
	Password: 197
	Solution Description: Get-ChildItem -Recurse | Where-Object {$_.Name -like 'readme*'}. 
			      Recursivly list directories and use the where-object to sort through the names.
	Answer: 7points

### Century 8:
	Challenge: The password for Century9 is the number of unique entries within the file on the desktop.
	Username: century8
	Password: 7points
	Solution Description: (get-unique -inputobject (gc .\unique.txt)).count
			      Use the get-unique command and pipe the output of uniqure.txt. Count the list that is outputted by get-unique
	Answer: 696

### Century 9:
	Challenge: The password for Century10 is the 161st word within the file on the desktop.
	Username: century9
	Password: 696
	Solution Description: $words = ((gc .\Word_File.txt).split(" "))
			      $words[160]
			      Split file by spaces, load into array, print out 161st element of array == 160th
	Answer: pierid

### Century 10:
	Challenge: The password for Century11 is the 10th and 8th word of the Windows Update service description combined
		   PLUS the name of the file on the desktop.
	Username: century10
	Password: pierid
	Solution Description: I tried to make this a one liner but was unable to figure out a way to convert the out put of the following command
			      to an array in one line. 
			      Get-WmiObject win32_service | ?{$_.Name -like 'wuauserv'} | select Description
			      Gets a wmi object, looks for services using the property name, and then only shows the description of that service
			      Took the 10th word, 8th word, and file name and appended them all together.
	Answer: windowsupdates110

### Century 11:
	Challenge: The password for Century12 is the name of the hidden file within the
		   contacts, desktop, documents, downloads, favorites, music, or videos folder in the user’s profile.

	Username: century11
	Password: windowsupdates110
	Solution Description: Get-ChildItem -Recurse -hidden -ErrorAction SilentlyContinue
			      Recursively list each directory and only show the hidden files. Sift through the results and found the only hidden file 
			      in the names directories 
	Answer: secret_sauce

### Century 12:
	Challenge: The password for Century13 is the description of the computer designated
		   as a Domain Controller within this domain PLUS the name of the file on the desktop.
	Username: century12
	Password: secrete_sauce
	Solution Description: Get-ADComputer -filter * -Properties description
			      GetAD can show all information about a computer. In this case I wanted to see every 
			      computer on the network since I had no other information to go off of. And I specified 
			      that I wanted the "description" property to show in the output as well. ("i_authenticate")
			      Also append to it the name of the file on the desktop. ("30_things")
	Answer: i_authenticate_things

### Century 13:
	Challenge: The password for Century14 is the number of words within the file on the desktop.	
	Username: century13
	Password: i_authenticate_things
	Solution Description:  $words = (gc .\countmywords).split(" ")
			       $words.Length == 755
			       Same thing as century9, take the txt file, split it by spaces (split(" ")), get the length of the output
			       Found this out after the fact, but you can also use "Measure-Object" to count chars, words, lines, ect in a file
	Answer: 755

### Century 14:
	Challenge: The password for Century15 is the number of times the word “polo” appears within the file on the desktop.
	Username: century14
	Password: 755
	Solution Description: (Select-String -InputObject .\countpolos  -Pattern "polo " -AllMatches).Matches.Count
			      This one was bit odd. It asks me to find the "WHOLE WORD" so in the command I made it look for " polo ". 
 			      The word polo is trailing and being followed by a space here. And that gave me the answer 152 which was wrong. I tried
			      out all of the combinations and the 3 totals I was given was 158, 152, and 153... 153 worked 
	Answer: 153

### Century 15:
	Challenge: Congratulations!
	Username: century15
	Password: 153
	Solution Description: gg
	Answer: gg
