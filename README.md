# Kyr's bot to scan a respect Thread, download Streamables/Gfycats, upload them to Reddit, and spit out a new rt

***
How to make it work
***

1.) Download and install both SQL Server Management Studio and Visual Studio.
https://learn.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-ver16
https://i.imgur.com/DK5aIbl.png
https://visualstudio.microsoft.com/downloads/
https://i.imgur.com/DFRrgm7.png

2.) Download SQLStreamable.zip, extract it, and open SQLStreamable.sln in Visual Studio.

3.) Download the Chromedriver that matches your Chrome's version - https://chromedriver.chromium.org/downloads
https://imgur.com/a/JOMI5G6

4.) In Visual Studio's Solution Explorer, expand SQLStreamable -> Dependencies -> Packages. Right click on Selenium.Chrome.WebDriver (85.0.0) and select properties. Copy the path and open it up in a file explorer. Navigate into the Driver folder and replace the Chromedriver in it with the one you just downloaded
https://imgur.com/a/87oiTGF

5.) Open SQL Server Management Studio. Copy the Server name and hit connect. If it fails to connect, make sure you have admin privileges. This bot will not work if you can't connect to SQL. If it succeeds, go to Visual Studio and go to line 716 public static string sqlConnection = "Data Source=KyrarycPC;Integrated Security=SSPI;";  Replace the "KyrarycPC" part of that string with the server name you just copied. Everything else should remain the same.
https://imgur.com/a/G2D5P2Y

6.) Change the filepaths on the lines 711, 712, and 713. Make sure the directories end with a \
  A.) downloadDirectory -> This is a folder where the bot can download the streamables/gfycats to.
  
  B.) threadsDirectory -> This is a folder where the bot will save the finished respect threads.
  
  C.) rtLinksDoc -> The direct filepath to a text document with links to all the threads you want to scan, seperated by new lines (ENTER). Only use threads that you created. The bot needs to be able to click the edit button to 
  
7.) Enter your reddit Username and password into the variables on lines 714 and 715. I promise it won't send that info to me in any way. If you have two-factor authentication set up, you'll need to disable it.

8.) Click the green arrow to start it up. If it says you need to download additional files, follow the instructions, close the chromedriver it opened, and click the green arrow again.

9.) The bot will start scanning the threads and downloading gfycats/streamables.

10.) When it comes to uploading, you'll have to navigate to the folder and actually upload the video. If for whatever reason it fails, simply reupload it. If you have to reload the page entirely, make sure the title is the same one the bot entered. It usees that to find the video url.

11.) Once its done uploading videos, it will save the new respect thread as a text document. You can review it and upload it yourself.

12.) The bot will move onto the next thread and start the whole thing all over again.

13.) Once its completely done, it will report details on everything, from what files it looked at, any broken links, any videos that were too short to upload, and any video it had a problem uploading. All results will also be stored in the sql database for future runs.

***********

Troubleshooting

************

A.) If Visual Studio fails to run, make sure to close any opened Chromedrivers.

B.) If Chrome fails to open, download and replace chromedriver again.
