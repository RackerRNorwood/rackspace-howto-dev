---
node_id: 1120
title: Setup Automatic MySQL Server Backups to Cloud Files from Windows
permalink: article/setup-automatic-mysql-server-backups-to-cloud-files-from-windows
type: article
created_date: '2011-06-07 21:31:05'
created_by: RackKCAdmin
last_modified_date: '2015-01-06 00:3301'
last_modified_by: jered.heeschen
products: 'Cloud Servers,Cloud Files'
body_format: tinymce
---

+--------------------------------------------------------------------------+
| Contents                                                                 |
| --------                                                                 |
|                                                                          |
| -   [1 Setup automatic MySQL Server Backups to Cloud Files in            |
|     Windows](#Setup_automatic_MySQL_Server_Backups_to_Cloud_Files_in_Win |
| dows)                                                                    |
|     -   [1.1 1. Download and build the upload                            |
|         software](#1._Download_and_build_the_upload_software)            |
|     -   [1.2 2. Create a .bat file for taking                            |
|         backups](#2._Create_a_.bat_file_for_taking_backups)              |
|     -   [1.3 3. Fully automate, scheduled                                |
|         task](#3._Fully_automate.2C_scheduled_task)                      |
+--------------------------------------------------------------------------+

Setup automatic MySQL Server Backups to Cloud Files in Windows
--------------------------------------------------------------

This article is about setting up automatic MySQL server backups from
your Windows Cloud Server to your Rackspace Cloud Files container.
Follow these three steps to perform this task.

1.  Download and build a small piece of software to upload a file to
    Cloud Files.
2.  Create a .bat file to take the backup of your MySQL server database
    and upload it to Cloud Files using the software created in the
    previous step.
3.  Create a scheduled task in Windows to run the above .bat file from
    step 2 at a scheduled date and time.

### 1. Download and build the upload software

First you will need to download a small piece of C\# software and
compile it on Windows Cloud Server. Use the following easy steps to
build the Cloud Files upload software.

-   Download the software from this
    [link](http://c16281.r81.cf2.rackcdn.com/chmouel-upload-to-cf-cs-0.1-0-g79abd66.zip "http://c16281.r81.cf2.rackcdn.com/chmouel-upload-to-cf-cs-0.1-0-g79abd66.zip").

-   After downloading, extract the software into your C: drive, e.g.
    c:/upload-to-cf-cs-0.1/

-   Now download and install nant, a free .Net Build tool, from
    [http://nant.sourceforge.net/](http://nant.sourceforge.net/ "http://nant.sourceforge.net/").

-   Once you have successfully installed nant, then open a command
    prompt and navigate to the directory **c:/upload-to-cf-cs-0.1** and
    run **nant.exe** command as shown in the following screenshot.

![mysqlbackuptoCF1.png](http://c602889.r89.cf2.rackcdn.com/mysqlbackuptoCF1.png)

 

-   The above command will compile the binary file upload-to-cf.exe. We
    will be using this binary file to upload our backup files to Cloud
    Files. You can test this command using the following syntax:

<!-- -->

     
    upload-to-cf.exe [cloud username] [cloud api_key] [container name] [file path]

### 2. Create a .bat file for taking backups

-   Next, we need to create a .bat file to automate the MySQL database
    backup procedure. We want to backup the MySQL database backup file
    to a date-stamped file. There are several ways to do this, but the
    easiest way is through a batch file. The command we'll be using is
    as follows:

<!-- -->

     
    c:\<path-to-mysql>\bin\mysqldump -u[user] -p[password] --result-file="c:\<path>\backup.%DATE:~0,3%.sql" [database name]

-   Replace the values for username, password, and database name with
    your MySQL information. You can try this command from the normal
    command prompt to make sure that it works without any problems
    before actually including it in a .bat file. The above command
    should end up with a .sql file containing a full dump of the MySQL
    database, with the name you provided at the end of the above
    command.

-   Once you are satisfied that the above command works without any
    problem, you can go ahead and create a .bat backup file (e.g.,
    mysql-backup.bat). It can look like this...

*Note: You need to replace the values in [] brackets with actual values
for your system.*

     
    @echo off 
    echo &ldquo;Running dump... &ldquo;
    c:\<path-to-mysql>\bin\mysqldump -u[user] -p[password] --result-file="c:\<path>\backup.%DATE:~0,3%.sql" [database name] 
    echo &ldquo;MySQL dump done!&rdquo;
    echo &ldquo;Uploading to cloud files&rdquo;
    upload-to-cf.exe [cloud username] [cloud api_key] [container name] &ldquo;c:\<path>\backup.%DATE:~0,3%.sql&rdquo;
    echo &ldquo;backup file uploaded to cloud files!&rdquo;

-   Now you should be able to run **mysql-backup.bat** from a command
    prompt. If it works, you should see a success message, and a file
    should be generated in the directory you specified. If not, make
    sure you have the correct username, password, and database values
    specified and then try it again.

### 3. Fully automate, scheduled task

-   So now we should have our mysql-backup.bat file that creates the
    backup of our MySQL database and uploads the file to Rackspace Cloud
    Files using the upload-to-cf.exe program. The next step is to create
    a Windows Scheduled Task so that all the above steps run
    automatically at a scheduled date and time. Follow the steps below
    to setup a scheduled task in Windows.

-   Click Start, click Run, type cmd, and then click OK.

-   At the command prompt, type **net start**, and then press ENTER to
    display a list of currently running services. If Task Scheduler is
    not displayed in the list, type net start "task scheduler", and then
    press ENTER.

![mysqlbackuptoCF2.png](http://c602889.r89.cf2.rackcdn.com/mysqlbackuptoCF2.png)

-   At the command prompt, type the following command and then press
    ENTER:

<!-- -->

    schtasks /create /tn "MySQL_Backup" /tr c:\apps\mysql-backup.bat /sc Value /st HH:MM:SS /ed MM/DD/YYYY

-   Note that you may have to change the parameters for your situation.
    For example, you might type ***schtasks /create /tn "MySQL\_backup"
    /tr c:\\apps\\mysql-backup.bat /sc daily /st 08:00:00 /ed
    12/31/2014***

![MySQLbackuptoCF3.png](http://c602889.r89.cf2.rackcdn.com/MySQLbackuptoCF3.png)

-   This example schedules the MySQL\_Backup program to run once a day,
    every day, at 8:00 A.M. until December 31, 2014. Because it omits
    the **/mo** parameter, the default interval of 1 is used to run the
    command every day.

-   During the task creation you will be asked your currently logged in
    user&rsquo;s password. Once you enter the password, a new task will be
    created for you. You can view the newly created task with the
    **schtasks** command.


