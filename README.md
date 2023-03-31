# Kyr's bot to scan a respect Thread, download Streamables/Gfycats, upload them to Reddit, and spit out a new rt

***
How to make it work
***
Latest Version: 3/30/2023
***

1.) Download and install Visual Studio. This one may take awhile.
  
  https://visualstudio.microsoft.com/downloads/
  
  https://i.imgur.com/DFRrgm7.png
  
      A.) Once Visual Studio has been installed, download this framework https://aka.ms/dotnet-core-applaunch?framework=Microsoft.NETCore.App&framework_version=3.1.0&arch=x64&rid=win10-x64

2.) Download and install SQL Server Express. Once it's downloaded, click "Connect." If the command prompt says something like "1 row affected" and doesn't give an error message, you can close the command prompt. Grab the connection string it provides. Copy and store the server name, which will be be between the "=" and the ";" in the connection string. So if the string is something like "Server=localhost\SQLEXPRESS;Database=master...", then the server name is localhost\SQLExpress.

  https://www.microsoft.com/en-us/sql-server/sql-server-downloads?rtc=1
  
  https://imgur.com/a/R8JRRFq
  
3.) Download and install SQL Server Management Studio. You may need to restart your computer. Once its downloaded, open it up. If the connection popup has a server name by default, great. If not, paste in the server name you copied. Don't worry if SQLExpress gave something like "localhost" and Management studio gives something like "YourPC'sName", either will work. Click "Connect". If it returns an error, check that you have admin privledge, google the error, and try to fix it.

  https://learn.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-ver16

  https://i.imgur.com/DK5aIbl.png

4.) Download SQLStreamable.zip, extract it, and open SQLStreamable.sln in Visual Studio.  Double click on "Program.cs" in the solution explorer. You should see code.

5.) Download the Chromedriver that matches your Chrome's version
  
  https://chromedriver.chromium.org/downloads

  https://imgur.com/a/JOMI5G6

6.) In Visual Studio's Solution Explorer, expand SQLStreamable -> Dependencies -> Packages. If you don't see that, double click Right click on Selenium.Chrome.WebDriver (85.0.0) and select "Open folder in file explorer". If you don't have that option, copy the path and open it up in a file explorer. Navigate into the Driver folder and replace the Chromedriver in it with the one you just downloaded.

  https://imgur.com/a/87oiTGF

7.) Go to line 716: public static string sqlConnection = "Data Source=KyrarycPC;Integrated Security=SSPI;";  Replace the "KyrarycPC" part of that string with the server name you copied earlier. Everything else should remain the same.

  https://imgur.com/a/G2D5P2Y

8.) Change the filepaths on the lines 711, 712, and 713. Make sure the directories end with a \
  
  A.) downloadDirectory -> This is a folder where the bot can download the streamables/gfycats to.
  
  B.) threadsDirectory -> This is a folder where the bot will save the finished respect threads.
  
  C.) rtLinksDoc -> The direct filepath to a text document with links to all the threads you want to scan, seperated by new lines (ENTER). Only use threads that you created. The bot needs to be able to click the edit button to 
  
9.) Enter your reddit Username and password into the variables on lines 714 and 715. I promise it won't send that info to me in any way. If you have two-factor authentication set up, you'll need to disable it.

10.) On the Visual Studio, click Build -> Clean Solution. Once that succeeds, click Build -> Rebuild Solution. 

11.) Click the green arrow to start it up. If it says you need to download additional files, follow the instructions, close the chromedriver it opened, and click the green arrow again.

12.) The bot will start scanning the threads and downloading gfycats/streamables.

13.) When it comes to uploading, you'll have to navigate to the folder and actually upload the video. If for whatever reason it fails, simply reupload it. If you have to reload the page entirely, make sure the title is the same one the bot entered. It usees that to find the video url.

14.) Once its done uploading videos, it will save the new respect thread as a text document. You can review it and upload it yourself.

15.) The bot will move onto the next thread and start the whole thing all over again.

16.) Once its completely done, it will report details on everything, from what files it looked at, any broken links, any videos that were too short to upload, and any video it had a problem uploading. All results will also be stored in the sql database for future runs.

***********

Troubleshooting

************

A.) If Visual Studio fails to run, make sure to close any opened Chromedrivers.

B.) If Chrome fails to open, download and replace chromedriver again.

C.) If its opening RTVideos but immediately moving onto the next feat without trying to upload, go to your Reddit User Settings and opted out of the redesign. This bot needs old reddit to work properly.

D.) If Visual Studio errors out on the SQL Connection string and gives the message "Unrecognized escape sequence", then add an extra slash. So if it errors out on localHost\SQLExpress, change it to localHost\\SQLExpress
https://i.imgur.com/hIyzwJ1.png
