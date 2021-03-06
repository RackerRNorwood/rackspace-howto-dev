---
node_id: 3773
title: Deploy WordPress packages by using Rackspace Cloud Orchestration
type: article
created_date: '2013-11-12'
created_by: Rackspace Support
last_modified_date: '2016-01-11'
last_modified_by: Rose Coste
product: Cloud Orchestration
body_format: markdown_w_tinymce
---

Rackspace Cloud Orchestration for Cloud Servers simplifies the process of creating a WordPress environment, either as a stand-alone server or in a multiple-server cluster.

This guide covers the process of deploying your servers and preparing them for use with WordPress, using these steps:

- [Deploy the servers](#1)
- [Access the servers](#2)
- [Set up DNS](#3)

<a name="1"></a>
###Deploy the servers

1. Log in to the [Cloud Control Panel](http://mycloud.rackspace.com).

2. In the top navigation bar, click **Orchestration**, and under Create Resources, click **Stack**.

     <img src="https://8026b2e3760e2433679c-fffceaebb8c6ee053c935e8915a3fbe7.ssl.cf2.rackcdn.com/field/image/1560-3549-newimage_1.png" width="481" height="134" border="1" alt=""  />

3. Specify a name and region for your stack.

4. In the **Application Name** list, select **WordPress** and then choose the flavor, either **Single Linux server** or **Multiple Linux servers**.

5. Click **Next Step**.

6. On the next page, specify server and WordPress settings.

7. Under Advanced Options, enter the database name.

8. Click **Create Stack**.

On the stack details page you will see Up in the status field when the stack is complete.

<img src="https://8026b2e3760e2433679c-fffceaebb8c6ee053c935e8915a3fbe7.ssl.cf2.rackcdn.com/field/image/3773Wordpressscreen.png" width="782" height="608" alt=""  border="1"/>

<a name="2"></a>
### Access the servers

When your stack is up, go to the Stack Details page and click **View *n* Credentials** to access the login information for your new servers.

<img src="https://8026b2e3760e2433679c-fffceaebb8c6ee053c935e8915a3fbe7.ssl.cf2.rackcdn.com/field/image/3773Wordpressscreen_0.png" width="220" height="26" border="1" alt=""  />

In the Stack Credentials window, you will see an SSH Private Key that you can use to access the servers in your stack as the root user, the root password for the database, and the WordPress password.

For more information about using the provided SSH key to access your servers, see [Logging in with a SSH Private Key on Windows](/how-to/logging-in-with-an-ssh-private-key-on-windows) or [Logging in with a SSH Private Key on Linux and Mac](/how-to/logging-in-with-an-ssh-private-key-on-linuxmac).
<a name="3"></a>

###  Set up DNS

If you host your DNS with Rackspace DNS, you can now add a DNS record for your new WordPress stack. For information about adding a DNS record, see [Creating DNS Records for Cloud Servers](/how-to/create-dns-records-for-cloud-servers-with-the-control-panel). Point your domain to the public IP address of the load balancer that was created for you.

If you are not ready to use public DNS with WordPress, modify your desktop's Hosts file to point your domain to your new stack. For information about modifying your Hosts file, see [How do I Modify My Hosts File](/how-to/modify-your-hosts-file). Be sure to use the load balancer public IP address.

After you are finished, you can start using WordPress by navigating to the URL that you entered during the stack configuration.
