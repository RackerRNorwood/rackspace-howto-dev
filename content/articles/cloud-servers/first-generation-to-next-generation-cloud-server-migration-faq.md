---
node_id: 4473
title: First Generation to Next Generation cloud server migration FAQ
type: article
created_date: '2015-01-08'
created_by: Trey Hoehne
last_modified_date: '2016-01-07'
last_modified_by: Renee Rendon
product: Cloud Servers
body_format: tinymce
---

This article provides answers to frequently asked questions about
the migration from First Generation Cloud Servers to Next Generation
Cloud Servers. If you have additional questions about the migration, see
the [migration thread in our community
forum](https://community.rackspace.com/products/f/25/t/4787).

-   [Why is there a migration?](#1)
-   [What is the Next Generation Cloud Server platform?](#2)
-   [How will I be notified about the migration of my servers?](#3)
-   [How can I migrate my server now?](#4)
-   [How will the migration work?](#5)
-   [What is the benefit of taking advantage of the self-migration
    window?](#6)
-   [What happens if I wait for Rackspace to perform the migration?](#7)
-   [What will happen to my backups and snapshots?](#8)
-   [Will my backups and snapshots stay in the same Cloud Files
    container?](#9)
-   [What about my scheduled images or Backup Schedule?](#10)
-   [What can I do to ensure a smooth transition?](#11)
-   [Will the flavor (size) of my server remain the same?](#12)
-   [There are less expensive flavors in Next Generation. How can I get
    those rates?](#13)
-   [How will I be billed in Next Generation?](#14)
-   [Does the API change?](#15)
-   [Where are the external customer resources?](#externalresources)

------------------------------------------------------------------------

#### Why is there a migration?

<span class="s1">First Generation Cloud Servers is moving to an End of
Life status.</span>

[&lt;back to top&gt;](#top)

#### What is the Next Generation Cloud Servers platform?

Next Generation is the Cloud Servers environment powered by OpenStack.
For more information about the details and features of this change, see
[Next Generation Cloud Servers migration considerations and
options](/how-to/next-generation-cloud-servers-migration-considerations-and-options).

[&lt;back to top&gt;](#top)

#### How will I be notified about the migration of my servers?

Rackspace will create a migration ticket that includes a scheduled
migration date for your server. During the time *before* a server's
scheduled migration date, instructions on how to schedule your own
migration will be sent to you. On your scheduled date listed in your
migration ticket, we will begin migrating servers to the Next Generation
platform. The time period in which you can schedule your own migration
will also be visible in the Cloud Control Panel and in the server's
metadata. At the end of this time period, your server will be migrated
by Rackspace to the Next Generation platform.

[&lt;back to top&gt;](#top)

#### How can I migrate my server now?

Migration batch schedules are based on the virtual server, not on the
customer. As a customer, you might have servers in various states of
migration availability depending on the number of virtual servers and
the age of those virtual servers. Because of this, you can migrate a
server only when that server's migration window is open.

[&lt;back to top&gt;](#top)

#### How will the migration work?

The public, private, and shared IP addresses of your server will remain
the same if you schedule the migration during the migration window or if
Rackspace migrates the server for you.

The memory state of your server will be preserved whenever possible,
avoiding system restarts as often as possible. In some cases, because of
the operating system or age of the server, a restart will be necessary.
These exceptions will be outlined in your migration notification.

You will receive an automated notification when your server's migration
starts and ends.

[&lt;back to top&gt;](#top)

#### What is the benefit of taking advantage of the self-migration window?

The self-migration was designed to allow a server to be migrated at a
time of your choosing within the given time period. This level of
control is for customers who require the ability to specify the exact
time that a server is taken offline. For example, if a database was
scheduled for migration, taking the application offline would ensure the
integrity of the data being moved rather than risk having the migration
start mid update.

[&lt;back to top&gt;](#top)

#### What happens if I wait for Rackspace to perform the migration?

At the end of the self-migration window, all customers within a batch
will be placed into a queue. There will be a degree of variability when
a migration will start at the end of a window as Rackspace controls the
number of simultaneous migrations to ensure overall quality.

[&lt;back to top&gt;](#top)

#### What will happen to my backups and snapshots?

Because of the large number of snapshots and backups, we will migrate
snapshots and backups that are one year and under in age. We will
migrate one half of your automated snapshots and backups that are one
year and under.

If you have a particular snapshot that contains valuable data, Support
can help you migrate it.

Snapshots and backups will not be migrated at the same time as the
server they belong to. There will be some delay in the time it takes for
them to appear in Next Generation. The exact time depends on the number
and size being migrated, but in most cases this should not be longer
than 72 hours after the server has been migrated.

[&lt;back to top&gt;](#top)

#### Will my backups and snapshots stay in the same Cloud Files container?

No. In the Next Generation platform, backups and snapshots are located
in a common container owned by Rackspace. This change was made because
of the way that the OpenStack Glance service manages server images,
snapshots, and backups. You still have full visibility of these items
and control to delete them via the API or Cloud Control Panel.
Snapshots, backups, and images will still be charged at the current
Cloud Files rate.

[&lt;back to top&gt;](#top)

#### What about my current scheduled images or Backup Schedule?

<span class="author-a-bjz122zpkrz76zevz87zz81zz84zz65zz86zkz79z">Backup
schedules for First Generation servers *will not* be carried over to
Next Generation servers. The Next Generation cloud offers several data
backup options, including [Rackspace Cloud
Backup](/how-to/cloud-backup) and [Rackspace
Cloud Block
Storage](/how-to/cloud-block-storage) volume
snapshots. You can schedule images, but image scheduling works
differently than backup schedules, and may not be appropriate for all
use cases. </span>For instance, with Scheduled Backups in the Next
Generation Cloud:

<div id="magicdomid14">

-   <span class="author-a-bjz122zpkrz76zevz87zz81zz84zz65zz86zkz79z">You
    don't get to choose the time that your server image is created; we
    schedule this for you, and the time is subject to change.  (We
    reserve the right to reschedule if necessary in order to keep the
    load balanced throughout the cloud.)</span>
-   <span
    class="author-a-bjz122zpkrz76zevz87zz81zz84zz65zz86zkz79z">Some Next
    Generation flavors have separate system disks and data disks. You
    can create an image only of your server's system disk.</span>
-   <span class="author-a-bjz122zpkrz76zevz87zz81zz84zz65zz86zkz79z">To
    increase processing speed, some applications buffer data in memory
    and write to disk only when the buffer is full.  If such an
    application is running on your server when an image is created, when
    you boot a new server from that image, the application might resume
    operation in an inconsistent state or refuse to start at all.</span>
-   <span class="author-a-bjz122zpkrz76zevz87zz81zz84zz65zz86zkz79z">To
    retrieve files from an image, you must first boot a server from the
    image and then go into the file system. You cannot just pull files
    out of an image.</span>

</div>

<span class="author-a-bjz122zpkrz76zevz87zz81zz84zz65zz86zkz79z">We
recommend that you take this opportunity to review your data backup
needs and select the option that will best safeguard your data.</span>

[&lt;back to top&gt;](#top)

#### What can I do to ensure a smooth transition?

The migration involves transferring data, so anything that you can do to
ensure a healthy file system will make the move smoother. This includes
performing routine maintenance and trimming log and temporary files from
the server. The following article provides steps that you can take
before your migration: [Preparing for a Cloud Server
Migration](/how-to/prepare-to-migrate-a-linux-server).

[&lt;back to top&gt;](#top)

#### Will the flavor (size) of my server remain the same?

A flavor refers to the RAM, vCPU, and disk that a server is provisioned
with. A new flavor class called Classic will be created to mirror the
resources in First Generation. When your server is migrated into Next
Generation, it will use a Classic flavor that has the same amount of
RAM, vCPU, and disk as the original server flavor. The only difference
will be that the server is now running on the Next Generation platform.

[&lt;back to top&gt;](#top)

#### There are less expensive flavors in Next Generation. How can I get those rates?

The Next Generation environment has multiple flavor classes that are
built around specific ratios of resources and features, and they are
priced accordingly. Migrating a server to a new flavor class to take
advantage of those features is your choice and responsibility. The
migration to the Next Generation environment is simply about taking your
server out of one environment and placing it in another.

[&lt;back to top&gt;](#top)

#### How will I be billed in Next Generation?

You will be billed at the same usage rate as you are in First
Generation. When the migration of a server starts, the billing usage
stops for that server. After the server is in an active state in Next
Generation, usage starts. As a result, there be will two separate
invoice items for a migrated server. One will represent the First
Generation usage from the billing cycle's start until the start of the
server's migration. The second will represent the time that a server
became active in Next Generation until the end of the billing cycle.
There is a distinct break in billable usage during the migration of a
server, so a server will never accrue billable usage in both
environments.

[&lt;back to top&gt;](#top)

#### Does the API change?

Yes. The Next Generation platform has a different API. Information about
getting starting with the Next Generation API is located at
[https://developer.rackspace.com/docs](https://developer.rackspace.com/docs/).
Any third-party tools or SDKs that you are currently using will need to
be updated.

[&lt;back to top&gt;](#top)

#### Where are the external customer resources?

-   Official External Thread on the Rackspace Community:
    [https://community.rackspace.com/products/f/25/t/4787 ](https://community.rackspace.com/products/f/25/t/4787)
-   Google Hangout customer Q&A sessions
    -   Date/Time: Wednesday 2014-01-14 at 10am CST.
        Link: <https://plus.google.com/events/cdnijo5alfbic3r06phjm0qltro>

[&lt;back to top&gt;](#top)

