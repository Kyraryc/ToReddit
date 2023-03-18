# Kyr's bot to scan a respect Thread, download Streamables/Gfycats, upload them to Reddit, and spit out a new rt

How to make this work:

1.) Download SQL Server https://learn.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-ver16

2.) Download Visual Studio https://visualstudio.microsoft.com/downloads/

3.) Download the zip file, extract it, and open SQLStreamable.sln in Visual Studio

4.) Use Ctrl F to find "downloadDirectory" on line 708. There are several filepaths that you'll need to change. https://i.imgur.com/Ekz3yFC.png

  A.) downloadDirectory -> This is a folder where the bot can download the streamables/gfycats to.
  
  B.) threadsDirectory -> This is a folder where the bot will save the finished respect threads.
  
  C.) rtLinksDoc -> The direct filepath to a text document with links to all the threads you want to scan.
  
  D.) redditUsername -> Your reddit username
  
  E.) redditPassword -> Your reddit password.
  
  F.) sqlConnection -> This string is used to connect to the SQL database. You'll need to replace the "KyrarycPC" part of it with the name of your computer.
  
5.) Click the green arrow to start it up. https://i.imgur.com/uG71rSt.png

6.) The bot should automatically automatically log into Reddit and start downloading.

7.) When the bot uploads the video to reddit, it will stop after opening the file browser. You'll need to actually select the video to upload.

8.) Once its done uploading videos, it will save the new respect thread as a text document. You can review it and upload it.

9.) The bot will move onto the new thread and start the whole thing all over again.
