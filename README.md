<h1>File Integrity Monitoring</h1>

<h2>Description</h2>
Project consists of writing a script that will create and check the hashes for an Apache server.
<br />


<h2>Utilities Used</h2>

- <b>VirtualBox</b>
- <b>Debian Environment</b>
- <b>Terminal</b>
- <b>Apache</b>

<h2>Writing a Script to Check File Integrity:</h2>
A scheduled task will run daily to check file integrity in the www/html folder. 
<br />
<br />
In Debian, the html directory is navigated to under the root user. Touch is used to create 3 html files that will be used in the script:<br/>
<img src="https://imagizer.imageshack.com/img924/1198/RG0vWq.png"
<br />
<br />
Changing back to the root user's home directory, a file named WebsiteIntegrity.sh is created:<br/>
<img src="https://imagizer.imageshack.com/img922/1255/Uahe2x.png"
<br />
<br />
The script is started with the hashbang interpreter. A variable is created that points to all files in the html directory:<br/>
<img src="https://imagizer.imageshack.com/img923/3569/nfffuT.png"
<br />
<br />
A variable is created that points to the wwwHash directory. This directory will contain the new hashes:<br/>
<img src="https://imagizer.imageshack.com/img924/6663/cQhSH3.png"
<br />
<br />
A variable is created pointing to the same wwwHash directory that will contain the older hashes:<br/>
<img src="https://imagizer.imageshack.com/img923/5452/5WTphU.png"
<br />
<br />
An if-then statement is written that uses the created variables to copy previously-checked hashes from /var/log/wwwHash to /tmp/wwwHash, storing them for later comparison:<br/>
<img src="https://imagizer.imageshack.com/img923/3259/unlBG7.png"
<br />
<br />
A line is written that creates the file /var/log/wwwHash the first time the script is run:<br/>
<img src="https://imagizer.imageshack.com/img922/3717/9LZdTD.png"
<br />
<br />
An if-then statement is written if a for loop that will make new hashes for files in the HTML/* directory, and append them to the wwwHash directory:<br/>
<img src="https://imagizer.imageshack.com/img924/8735/1CcxgR.png"
<br />
<br />
An if-then statement is written that compares the hashes located in the /var/log/wwwHash and /tmp/wwwHash files. If a change is made, the if-then will report whether or not the file changed, and which files were changed:<br/>
<img src="https://imagizer.imageshack.com/img923/8497/15eNs9.png"
<br />
<br />
The changes are saved and the script is is exited:<br/>
<img src="https://imagizer.imageshack.com/img922/8653/pGOQhb.png"
<br />
<br />
The script is executed for the first time. It should only generate a baseline for further checking:<br/>
<img src="https://imagizer.imageshack.com/img922/9885/ZJC4tc.png"
<br />
<br />
File2.html is changed to verify the script's functionality:<br/>
<img src="https://imagizer.imageshack.com/img924/7692/2ijlu6.png"
<br />
<br />
The script recognizes that file2.html was changed, and reports it to the user:<br/>
<img src="https://imagizer.imageshack.com/img922/313/M9lm4z.png"
<br />
<br />


<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
