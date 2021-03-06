---
node_id: 4798
title: Prevent issues with Windows Server reboots
type: article
created_date: '2015-08-18'
created_by: Rose Contreras
last_modified_date: '2016-01-13'
last_modified_by: Rose Coste
product: Cloud Servers
body_format: full_html
---



This article describes the procedures that are necessary to restore your
Windows server to a working state automatically after a reboot. After
you have completed the procedures in this article, you should not need
to manually launch applications or apply firewall rules after your
Windows server has rebooted.

### Contents

1.  [Verify that your server is fully patched](#verify)
2.  [Automatically start all critical services](#crit)
3.  [Perform a test reboot](#test)



Verify that your server is fully patched
----------------------------------------

If your Windows server is not fully patched, install all pending
updates. Use the following instructions appropriate for your Windows
server version.

### Before you begin

If you are running Windows Server 2008 R2, verify that Service Pack 1 is
installed on the server. This service pack is not pushed through the
Windows Update Service.

1.  Open the Control Panel and select **System**.

2.  In the Windows Edition section, you should see Service Pack 1
    listed.


### Windows Server 2008 and 2008 R2

1.  Log in to your Windows server.

2.  Click **Start &gt; Control Panel**.

3.  Click **Windows Update** to view the information about the updates
    that are ready to be installed.


If there is a green shield on the Windows Update page, then the server
has all patches applied. Otherwise, proceed with the installation of any
pending updates.

### Windows Server 2012 and 2012 R2

1.  Move the cursor to the bottom-right corner of the screen and
    activate the **Charms** menu.
2.  Click **Search**.

3.  Type **Control Panel** for the search term.

4.  On the ribbon under the search field, click **Control Panel**.

5.  Click **System and Security**.

6.  Click **Windows Update** to see if there are pending updates
    to install. If so, install the updates at a convenient time.


[back to top](#top)




Automatically start all critical services
-----------------------------------------

Review and confirm that all of the services critical to your processes
are set to start automatically. Run the following PowerShell script to
grab all services that have an automatic startup:

    Get-WmiObject Win32Service | Select-Object Name, State, StartMode | Where-Object {$.StartMode -eq 'Auto'} | Format-Table

### Windows Server 2008 and 2008 R2

1.  Click the **Start** menu.

2.  In the search field, type `services.msc` in the search field.

3.  Press **Enter**.

4.  In the Services Management window, double-click a service that you
    want to configure for automatic startup.

5.  Set the startup type to **Automatic**.

### Windows Server 2012 and 2012 R2

1.  Move the cursor to the bottom right corner of the screen and
    activate the **Charms** menu.

2.  Click **Search**.

3.  Type `services.msc`.

4.  On the ribbon under the search field, click `services.msc`.

5.  In the Services Management window opens, double-click a service that
    you want to configure for automatic startup.

6.  Set the startup type to **Automatic**.

[back to top](#top)




Perform a test reboot
---------------------

After performing the procedures in this article, schedule a maintenance
window during your application's off-peak hours and test your work by
issuing a reboot. You can reboot your server by performing a soft reboot
through the server's **Action** menu in the Cloud Control Panel, or by
running the `reboot` command on the server.

When you perform a test reboot, allocate sufficient time in your
maintenance window to troubleshoot any issues that arise.



