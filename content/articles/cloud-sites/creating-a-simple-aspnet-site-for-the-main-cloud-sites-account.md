---
node_id: 533
title: Creating a Simple ASP.NET site for the main Cloud Sites account
type: article
created_date: '2011-03-16 21:57:40'
created_by: RackKCAdmin
last_modified_date: '2015-12-29 18:2720'
last_modified_by: stephanie.fillmon
product: Cloud Sites
body_format: tinymce
---

**Note**: This article refers to the [Cloud Sites Control
Panel](https://manage.rackspacecloud.com/). You can access this
interface from the [Cloud Control Panel](https://mycloud.rackspace.com/)
by clicking the **Cloud Control Panel** menu at the top of the window
and selecting **Cloud Sites**.

**Prerequisites**

-   Administrative access to the website

**To create the ASP.NET web page**

1.  Log in to the [Cloud Sites Control
    Panel](http://manage.rackspacecloud.com/pages/Login.jsp|).

    If you are new to the Rackspace Cloud an have not yet create a
    website, see [How to add a new
    website](http://www.rackspace.com/knowledge_center/article/getting-started-with-cloud-sites-how-to-add-a-new-website).

    **Note**: The domain must have .Net and Asp technology Feature
    enabled. If necessary, this can be verified and changed in the
    **Features**tab of the domain as shown below.

2.  Navigate to **Hosting \> Cloud Sites**.
3.  In the list of all the websites owned by the account, click the
    website that you want to update.
4.  Create the following two files:
    -   **First\_asp\_page.asp** - This is a simple ASP page:

            <html>
             <head>

             <title>My First ASP Page</title>
             </head>
             <body bgcolor="white" text="black">
             <%
               'Dimension variables
               Dim strMessage           
               strMessage = "Hello World"
               Response.Write (strMessage)
               Response.Write (" ")
               Response.Write ("The time on the server is: " & Time())
             %>

             </body>
             </html>

    -   **web.config** This is the configuration file. Enter your
        username and password to allow impersonation. For more
        information, see [ASP.NET
        Impersonation](https://msdn.microsoft.com/en-us/library/xh507fc5.aspx)
        on MSDN.

             <?xml version="1.0" encoding="utf-8" ?>

             <configuration>
               <system.web>
                <identity impersonate="true" userName="dfw\YOURNAME" password="YOURPASSWORD" />
               </system.web>
             </configuration>

5.  Verify that logging is turned on. For instructions, see [Enable raw
    logging for a Cloud Sites
    website](http://www.rackspace.com/knowledge_center/article/enabling-raw-logging-for-a-cloud-sites-website "/knowledge_center/index.php/Enabling_logging_for_a_website").
6.  Upload the two files created to the main directory of the website
    using FTP: For instructions, see [Uploading your
    content](http://www.rackspace.com/knowledge_center/article/getting-started-with-cloud-sites-uploading-your-content "/knowledge_center/index.php/Uploading_content_to_a_website_using_FTP").
7.  Navigate to the **First\_asp\_page.asp** file by using the Testing
    URL if necessary. For instrutions, see [Use a staging
    URL](http://www.rackspace.com/knowledge_center/article/using-a-staging-url "/knowledge_center/index.php/Using_a_staging_URL").


