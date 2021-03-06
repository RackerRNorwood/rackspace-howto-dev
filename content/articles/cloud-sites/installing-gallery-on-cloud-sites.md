---
node_id: 550
title: Installing Gallery on Cloud Sites
type: article
created_date: '2011-03-16'
created_by: Rackspace Support
last_modified_date: '2016-01-15'
last_modified_by: Nate Archer
product: Cloud Sites
body_format: full_html
---

**NOTE:** This article refers to the [Cloud Sites Control
Panel](https://manage.rackspacecloud.com/). You can access this
interface from the [Cloud Control Panel](https://mycloud.rackspace.com/)
by clicking your username in the upper-right corner of the control panel
and selecting Cloud Sites Control Panel.

This article will lead you through prepping your Cloud Sites domain to
host a php based photo gallery using "Gallery", an open source and
readily available site application.

Contents
--------

-   [<span class="tocnumber">1</span> <span class="toctext">Getting
    Started</span>](#Getting_Started)
-   [<span class="tocnumber">2</span> <span class="toctext">Setting up
    the Sites</span>](#Setting_up_the_Sites)
-   [<span class="tocnumber">3</span> <span class="toctext">Prepare your
    data</span>](#Prepare_your_data)
-   [<span class="tocnumber">4</span> <span class="toctext">Configure
    the Site</span>](#Configure_the_Site)
-   [<span class="tocnumber">5</span> <span
    class="toctext">Success</span>](#Success)



<span class="mw-headline">Getting Started </span>
-------------------------------------------------

If you have not already done so, goto <http://gallery.menalto.com/> and
download the latest stable release of Gallery.

Here is the link that was current at the time of this article:

    http://sourceforge.net/project/downloading.php?group_id=7130&filename=gallery-2.3-typical-en.zip

    or

    http://codex.gallery2.org/Downloads



<span class="mw-headline">Setting up the Sites </span>
------------------------------------------------------

1.  Create your new domain from the Cloud Sites Control Panel with
    minimum requirements being PHP 4, and MySQL 4 or 5.
2.  Once the domain has finished creating, create your database. To do
    this, click on the &lsquo;Features&rsquo; tab from the top menu. Click &lsquo;Add&rsquo;,
    and then select &lsquo;MySQL 4 or 5&rsquo;. Type in whatever name you would like
    to call the DB, type in a username and password of your choice.
    Follow prompts to finish creation. (You may want to write down the
    information provided, the hostname, database name, database username
    and, database password.)



<span class="mw-headline">Prepare your data </span>
---------------------------------------------------

1.  Extract the content of the Gallery file you downloaded earlier to
    your local computer.
2.  Open up your FTP client software and login to your new domain. If
    you are not familiar with uploading content, go here: [What FTP
    software should I
    use?](/how-to/getting-started-with-cloud-sites-ftpsshfsftp-clients "What FTP software should I use?")
    and use the information to connect provided here: [Getting Started
    With Cloud Sites, FTP/SSHFS/FTP
    Clients](/how-to/getting-started-with-cloud-sites-ftpsshfsftp-clients) .
    Your best bet will be to upload everything inside the &lsquo;gallery&rsquo;
    folder contained within the .zip file you downloaded to your
    web/content folder.
3.  Once the files have finished uploading, you are ready to get started
    with the installation of the Gallery and its settings.



<span class="mw-headline">Configure the Site</span>
---------------------------------------------------

1.  The information needed here is provided when you created your
    Database, if did you not already write them down, you can view this
    by logging into your Cloud Sites Control Panel and select your
    domain from the list. Click on the features tab and select the
    database from the list. After you click it, you will see all the
    info you need, except for the password. This is only known to you.
2.  Fill in the DB Hostname: with the hostname you now have. DB
    Username: with the database username you created, Fill in DB
    Password: with the password you created, Fill in DB Name: with the
    database name you created as well. Once you have filled in those
    fields, click Continue to Step 6.
3.  The admin account username and password for Gallery will be
    auto generated. Make sure to write this down because you will need
    it.
4.  Click Start Using Gallery.



<span class="mw-headline">Success </span>
-----------------------------------------

You have now successfully installed Gallery. Please keep in mind that
this is a very much used and known PHP application, just like any well
used software it is susceptible to exploit. The best way to protect
yourself and your data is to update your software regularly, I recommend
joining their mailing list, this will keep you up to date on releases
and security problems, so you can react accordingly.

