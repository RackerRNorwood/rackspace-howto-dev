---
node_id: 4928
title: Install End Point Operations Management Agents on VMs and Verify Data Collection
type: article
created_date: '2015-11-17 21:21:52'
created_by: erik.wilson
last_modified_date: '2016-01-06 13:4657'
last_modified_by: Nate.Archer
product: Managed VMware Services
body_format: tinymce
---

To get the new functionality from VMware&reg; vRealize&reg; Operations&reg; (vROps)
6.1 with End Point Operations (EP Ops) Management, you will need to
install EP Ops agents on the VMs that you want to monitor. All VMs in
your cluster are currently monitored by vROps; however, by installing
the EP Ops agents you get customer-managed guest OS monitoring that you
may need for critical workloads. 

This document includes the steps to install agents and verify data
collection, or remove agents if they are no longer needed. Also there
are steps to view which additional metrics and alerts are included in
End Point Operations Management.

The following sections include steps and information about:

-   [Locate EP Ops Agents files](#Locating%20EP%20Ops%20Agent's%20files)
-   [Install EP Ops Agent on
    Linux](#Installing%20EP%20Ops%20Agent%20on%20Linux)
-   [Install EP Ops Agent on
    Windows](#Installing%20EP%20Ops%20Agent%20on%20Windows)
-   [Remove EP Ops Agent on
    Linux](#Uninstalling%20EP%20Ops%20Agent%20on%20Linux)
-   [Remove EP Ops Agent on
    Windows](#Uninstall%20EP%20Ops%20Agent%20on%20Windows)
-   [Verify EP Ops Agent is collecting
    data](#Verify%20that%20EP%20Ops%20Agent%20is%20collecting%20data)
-   [View EP Ops specific
    metrics](#View%20EP%20Ops%20specific%20metrics)
-   [EP Ops specifc alerts](#View%20EP%20Ops%20specific%20alerts)

Locate EP Ops Agent files
-------------------------

The EP Ops agent files will be located in the *vROps End Point
Agents*folder the local VMFS datastore on the first ESXi host in your
inventory. There will be zip or tar files for Microsoft&reg; Windows&reg; or
Linux in both x32 and x64 formats. From the vSphere Client or vSphere
Web Client, you can select the first ESXi host in the inventory, browse
its local datastore, and download the files to your desktop or a central
location. You can then copy these to your VMs and extract them as
needed.

**Note: **The EP Ops Agents installation files that include Java will
overwrite your current Java version. If you need to configure the EP Ops
Agent to use a different version of Java than what you have installed on
the Virtual Machine, please refer to the vRealize Operation Manager
Installation and Configuration Guide for instructions.
[http://pubs.vmware.com/vrealizeoperationsmanager-61/topic/com.vmware.ICbase/PDF/vrealize-operations-manager-61-linux-windows-install-guide.pdf](http://pubs.vmware.com/vrealizeoperationsmanager-61/topic/com.vmware.ICbase/PDF/vrealize-operations-manager-61-linux-windows-install-guide.pdf)
{Page 56}

Install EP Ops Agent on Linux
-----------------------------

1.  Locate the Linux (tar) EP Ops agent installation files in both the
    x32 and x64-bit formats, as described in the [Locate EP Ops Agent
    files](#Locating%20EP%20Ops%20Agent's%20files) section.<br>
      
2.  Copy the installation file to the VM where you want to install the
    agent:

        # tar -zxvf epops-agent-x86-64-linux-xxx.tar.gz

3.  Change directory to the EP Ops agent bin directory:

        # cd /epops-agent/bin

4.  Run **ep-agent.sh**with start parameter and enter the correct
    information when prompted:

        # ./ep-agent.sh start

        Enter the server hostname or IP address: Enter IP of the vROps Server

        Enter the server SSL port [default=443]: Press Enter to accept the default

        Are you sure you want to trust this certificate (yes/no/more)? Yes

        Enter your server username: vCenter Login

        Enter your server password: vCenter Password
               

Install EP Ops Agent on Windows
-------------------------------

1.  Locate the Windows (zip) EP Ops agent installation files in both the
    x32 and x64-bit formats, as described in the [Locate EP Ops Agent
    files](#Locating%20EP%20Ops%20Agent's%20files) section.<br>
      
2.  Copy the installation file to the VM where you want to install the
    agent.<br>
      
3.  Extract the EP Ops agent zip file located on the VM to the
    **C:\\epops-agent** directory locally.<br>
      
4.  Open the command prompt and change directory to the EP Ops agent bin
    directory:

        cd c:\epops-agent\bin

5.  Install the EP Ops agent service:

        c:\epops-agent\bin> ep-agent.bat install

6.  Run ep-agent.bat with start parameter and enter the correct
    information when prompted:

        c:\epops-agent\bin> ep-agent.bat start

        Enter the server hostname or IP address: Enter IP of vROps Server

        Enter the server SSL port [default=443]: Press Enter to accept the default

        Are you sure you want to trust this certificate (yes/no/more)? Yes 
         
        Enter your server username: vCenter Login

        Enter your server password: vCenter Password
             

****Remove EP Ops Agent on Linux 
---------------------------------

If you no longer want to monitor a guest OS on a particular VM, you must
remove the EP Ops agent from the VM.  Alternatively, if you want to
reinstall the agent on a particular VM, we reccommend that you remove
the agent first. Deleting the directory will not allow a new
installation of the EP Ops agent to successfully re-register.

1.  Change directory to the EP Ops agent bin directory:

        # cd /epops-agent/bin

2.  Stop the EP Ops agent:

        # ./ep-agent.sh stop 

3.  Delete the data directory:

        # rm -rf /opt/epops-agent/data

4.  Delete the epops-token file:

        # rm /etc/vmware/epops-token

****Remove EP Ops Agent on Windows
----------------------------------

1.  Open the command prompt and change directory to the EP Ops agent bin
    directory:

        cd c:\epops-agent\bin

2.  Stop the EP Ops agent:

        c:\epops-agent\bin>ep-agent.bat  stop

3.  Remove the EP Ops agent service:

        c:\epops-agent\bin>ep-agent.bat  remove

4.  Delete the data directory using the command line or Windows
    Explorer:

        c:\epops-agent>rd /s data

        Are you sure (Y/N)? Y

5.  Delete the epops-token file using the command line or Windows
    Explorer:

        c:\epops-agent>del "C:\ProgramData\VMware\EP Ops Agent\epops-token"

**Note:** Enable **Show hidden files, folder, and drives**in **Folder
Options** if using Windows Explorer.

Verify that EP Ops Agent is collecting data
-------------------------------------------

After installing the agent on a VM, verify that the agent is collecting
data properly.

1.  Log in to vROps and click **Administration.**<br>
      
2.  Click **Inventory Explorer** on the left navigation bar.<br>
      
3.  In the **Inventory Explorer** window, click **Adapter Instances.**<br>
      
4.  Under **Adapter Instances** click **EP Ops Adapter Instance.**<br>
      
5.  Under **EP Ops Adapter Instance**, click **EP Ops Adapter**.<br>
     You will see your reporting VMs in the format of **EP Ops Agent &ndash;
    {*VM Name*}.**<br>
      
6.  Select an EPO Ops adapter to see the status of the agents. <br>
     In the following image, two VMs are listed as **Lab-Win12** and
    **LabUbuntu**.<br>
     <br>
     ![](/knowledge_center/sites/default/files/field/image/twoVMs.png)<br>
     <br>
     In the following figure, **EP Ops Agent &ndash; Lab-Win12** is receiving
    (green) for both **Collection State** and **Collection Status**.<br>
     <br>
     ![](/knowledge_center/sites/default/files/field/image/collections.png)

 

View EP Ops specific metrics
----------------------------

vROps 6.1 with End Point Operations Management adds specific OS metrics
to get a granular view of what is happening inside your VMs. To view a
list of these metrics complete the following steps:

1.  Log in to vROps and click **Environment.**<br>
      
2.  Click **Operating Systems** in the right pane.<br>
      
3.  Under **Operating Systems World**, expand the folders and select a
    VM.<br>
      
4.  Click the **Troubleshooting** tab in the right pane.<br>
      
5.  In the **Troubleshooting** tab, click the **All Metrics** tab to
    list the EP Ops specific metrics.<br>
      
6.  Double-click a metric to see a bar graph representation of the
    data. <br>
     <br>
     ![](/knowledge_center/sites/default/files/field/image/bargraph.png)<br>
     <br>
     You can double click on the images in the map view to see specific
    info on those objects.

View EP Ops specific alerts
---------------------------

vROps 6.1 with End Point Operations Management adds alerts specific to
operating systems to get a broader view of what is happening inside your
VMs. To view a list of these alerts complete the following steps:

1.  Log in to vROps and click **Content**.<br>
      
2.  Click **Alert Definitions**.<br>
      
3.  In the right pane, filter the list by clicking **All Filters** and
    choosing **Adapter Type**.<br>
      
4.  In the pop-up box, enter **EP Ops** and press **OK**to see all the
    active alerts related to EP Ops.<br>
     <br>
     ![](/knowledge_center/sites/default/files/field/image/adaptertypes.png)

