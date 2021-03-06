---
node_id: 68
title: Connecting to Linux from Windows by using PuTTY
type: article
created_date: '2011-03-08'
created_by: Rackspace Support
last_modified_date: '2016-01-14'
last_modified_by: Stephanie Fillmon
product: Cloud Servers
body_format: tinymce
---

### Previous section

[Getting Started with Cloud
Servers](/how-to/getting-started-with-cloud-servers-0)

After you have [created a new cloud
server](/how-to/getting-started-with-cloud-servers-0)
with the control panel, your next step is to make a secure remote
connection from your local computer to your cloud server.  This article
describes how to use a client called PuTTY to form an Secure Shell (SSH)
connection from a computer running a Microsoft Windows OS to a Linux
server.

**Notes**:

-   For an OnMetal Server, see the [Create OnMetal Cloud
    Servers](/how-to/create-onmetal-cloud-servers)
    article for applicable OnMetal steps.
-   This procedure requires you to install PuTTY or another SSH client
    which you do at your own risk.  PuTTY is not affiliated with
    Rackspace in any way, but their software is simple to use, is freely
    available, and reputable.
-   If you are a Mac OS X user, you can [connect to a Linux server by
    using
    Terminal](/how-to/connecting-to-linux-from-mac-os-x-by-using-terminal), a
    console program included with the operating system.



Windows versions
----------------

The procedure and examples in this article use  Windows XP, Service Pack
2.  Different versions of Windows may have slightly different
interfaces.

Download PuTTY
--------------

Download PuTTY from the
[website](http://www.chiark.greenend.org.uk/~sgtatham/putty/ "http://www.chiark.greenend.org.uk/~sgtatham/putty/").
Be sure to comply with the license requirements.

After you download PuTTY, launch the application.

Configure you connection
------------------------

In the PuTTY Configuration window, enter the following values and then
click **Open**:

-   In the Host Name enter the IP address of your Cloud Server.
-   Ensure the Connection Type is set to SSH.
-   (*Optional*) In the Saved Sessions field, you can assign a name for
    this connection.  Feel free to save it to whatever name you want: it
    simply saves time next time you use Putty.  You can have a different
    name for each of your Cloud Servers.

![](http://c768825.r25.cf2.rackcdn.com/1_Connect.png)



Accept the key
--------------


If this is the first time that you have used PuTTY to log in to your
server with SSH, a warning similar to the following one is displayed:

![](http://c768825.r25.cf2.rackcdn.com/2_AcceptKey.png)

If you are sure that you have entered the correct information, click
**Yes**.
Subsequent connections will not show this warning because the host key
is now cached in the registry of your local computer.  You can expect to
see that warning, however, if you connect to your server from a
different computer.





Enter your username and password
--------------------------------

After you accept the warning, the terminal prompts you for your username
and password.

If this is the first time that you are logging in to the server, you
must log in as the root user.

When you are prompted for the password for the root user**,** enter the
current root password for this server. When you enter this password at
the prompt, it is not echoed to the screen.  Then, press **Enter**.

If you have entered the correct root password, the prompt responds with
a shell prompt:

`[root@yourservername ~]#`

![](http://c768825.r25.cf2.rackcdn.com/3_login.png)

Now you can work on your server with all permissions.

Change your root passwords

FWe recommend that you change the root password to something personal.
 You can easily do this by using the passwd command.

1.  From the shell prompt, enter the passwd command.
2.  Enter the new password that you want to set for your server.  The
    password does not echo to the screen.
3.  Reenter the new password and press **Enter**.

Reenter the new password and press **Enter**.

![](http://c768825.r25.cf2.rackcdn.com/4_passwd.png)

You will now use this password with the root user whenever you connect
to your server.

### Next section

[Remote Connection from Mac to a Linux
Server](/how-to/connecting-to-linux-from-mac-os-x-by-using-terminal)

