---
node_id: 4702
title: Detailed Permissions Matrix for Cloud Big Data v2
type: article
created_date: '2015-06-01 18:56:07'
created_by: catherine.richardson
last_modified_date: '2016-01-11 20:4218'
last_modified_by: stephanie.fillmon
product: Cloud Big Data
body_format: tinymce
---

The following permissions matrix displays specific permissions for the
roles in Cloud Big Data v2. The matrix displays the method names, their
corresponding RESTful API commands, and the roles that are supported.  

**[API Documentation](http://docs.rackspace.com/)**

**[Cloud Big Data Terminology](#bigdata)**

### As of June 30, 2015    

CAPABILITY

ROLE

Description

Method name

API call

Observer

Creator

Admin

 

### CREDENTIALS

List all credentials

GET /credentials

 ![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

Lists all user credentials.

 

List credentials by type

GET /credentials/{type}

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

Lists all user credentials of the specified type.

 

Create a credential

POST /credentials/{type}

 

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

Creates a new credential of the specified type.

 

Update a credential

PUT /credentials/{type}/{name}

 

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

Updates the specified credential.

 

Delete a credential

DELETE /credentials/{type}/{name}

 

 

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

Deletes the specified credential.

 

### DISTROS

List available distros

GET /distros

 ![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

List all available distros.

 

Show distro details

GET /distros/{distroId}

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

For the specified distro, lists all of the supported services and their
corresponding components and modes of operation.

 

### STACKS

Create a stack

POST /stacks

 

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

Creates a new stack.

**Note:** This functionality is not yet implemented.

 

List all stacks

GET /stacks

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

Lists all stacks, including global stacks and user-created stacks.

 

Show stack details

GET /stacks/{stackId}

 
![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

Lists details for the specified stack.

 

Delete a stack

DELETE /stacks/{type}/{stackId}

 

 

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

Deletes the specified stack.

**Note:** This functionality is not yet implemented.

 

### CLUSTERS

Create a cluster

POST /clusters

 

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

Creates a new cluster.

 

Delete a cluster

DELETE /clusters/{clusterId}

 

 

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

Deletes the specified cluster.  

 

List all clusters

GET /clusters

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

Lists all clusters for your account.  

 

Show cluster details

GET /clusters/{clusterId}

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

Lists details for the specified cluster.  

 

Resize a cluster

PUT /clusters/{clusterId}

 

 ![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

 Resizes the specified cluster.

 

### NODES

List cluster nodes

GET /clusters/{clusterId}/nodes

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

Lists all nodes for the specified cluster. 

 

### SCRIPTS

Create a script

POST /scripts

 

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

Creates a new script.

 

List all scripts

GET /scripts

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

Lists all scripts, including global, product-provided scripts and
user-created scripts.

 

Update a script

PUT /scripts/{scriptId}

 

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

Updates the specified script.

 

Delete a script

DELETE /scripts/{scriptId}

 

 

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

Deletes the specified script.

 

### FLAVORS

List available flavors 

GET /flavors 

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

Lists all available flavors. 

 

### RESOURCE LIMITS

List resource limits

GET /limits

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

![](/knowledge_center/sites/default/files/field/image/green%20checkmark_7.png)

Lists the resource limits for the user, including the remaining node
count, available RAM, and remaining disk space.

 

 
-

Cloud Big Data terminology
--------------------------

### Credentials

Credentials allow you to set up SSH keys and other connector credentials
for use with clusters.

### Distros

Distros provide a list of supported distributions and their
corresponding versions, as well as a list of supported services and
components per distribution.

### Stacks

Stacks are high-level building blocks of software that compose a Big
Data architecture. Stacks are composed of services, which in turn are
composed of components. A stack is specific to a distribution because of
to the differences in services that are supported across distributions.

### Clusters

A cluster is a group of servers (nodes). In Cloud Big Data, the servers
are virtual.

### Node

In a network, a node (or server) is a connection point&mdash;either a
redistribution point or an end point for data transmissions. In general,
a node has programmed or engineered capability to recognize and process
or forward transmissions to other nodes. A node is a member of a
cluster.

### Scripts

You can create a custom script that runs during various phases of the
cluster's life cycle. The script is invoked on all nodes of the cluster.
The script type currently supported is POST\_INIT, which runs after the
cluster is completely set up. The script must be executable. Preferably,
the script should be a bash script, but it could be a Python script or a
self-contained executable that works with the base libraries of the
installed OS.

### Flavor

A flavor is an available configuration for Cloud Big Data. Each flavor
has a unique combination of memory capacity and priority for CPU time.

### Resource limits

Resource limits include items such as remaining node count, available
RAM, and remaining disk space for the user.

[ **\< Permissions Matrices for RBAC**](http://www.rackspace.com/knowledge_center/article/permissions-matrix-for-role-based-access-control-rbac)
------------------------------------------------------------------------------------------------------------------------------------------------

###  

** **

