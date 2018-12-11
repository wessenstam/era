.. _era_provision_postgresdb:

--------------------------
Era: Provision Postgres DB
--------------------------

Overview
++++++++

.. note::

  Estimated time to complete: **30 MINUTES**

This lab will show you how to provision, connect, and view a Postgres Database.

Deploy PostgreSQL
+++++++++++++++++

On the **Getting Started** page click on PostgreSQL.

.. figure:: images/4.png

In the Provision a PostgreSQL database, select **Provision a Database**.

**Provision a Database**

- **Database Engine** - PostgreSQL

**Database Server**

- **Database Server** - Create New Server
- **Database Server Name** - DBServer-*Initials*
- **Description** - (Optional) Description
- **Software Profile** - Take Default
- **Compute Profile** - Take Default
- **Network Profile** - Take Default

Create a new SSH Key following the Instructions in the SSH Key Creation Lab :ref:'sshkey_creation'

Copy and paste the public key into the SSH public key “text” option for the database server

.. figure:: images/7.png

Click **Next**

**Database**

- **Database Name** - LabDB-*Initials*
- **Description** - (Optional) Description
- **Password** - techX2019!
- **Database Parameter Profile** - Take Default
- **Listener Port** - Take Default
- **Size (GiB)** - Take Default

.. figure:: images/8.png

Click **Next**

**Time Machine**

- **Name** - LabDB-*Initials*-TM
- **Description** - (Optional) Description
- **SLA** - Gold
- **Schedule** - Take Defaults

.. figure:: images/9.png

Click **Provision**

Monitor the Provision Database task from under the Operations menu, should take around 5 minutes.

While you wait, you can explore other areas of the Era GUI, such as viewing the Dashboard or Administration pages.

.. figure:: images/10.png

Viewing and Connecting to PostgreSQL
++++++++++++++++++++++++++++++++++++

Lets connect to our Database.

In **Era > Databases**, and select your PostgreSQL Source DB.

.. figure:: images/11.png

On the Summary page take note of your Database Server IP address

.. figure:: images/12.png

Start **pgAdmin**.

Right click Servers in the Browser menu and select **Create**, then **Server**

**General**

- **Name** - Era-Lab-*Intials*

**Connection Information**

- **Hostname/IP Address - IP for DBServer-*Initials*
- **Port** - 5432
- **Maintenance Database** - postgres
- **Username** - postgres
- **Password** - techX2019!

.. figure:: images/14.png

Click **Save**

You should now be able to browse your database instance.

.. figure:: images/15.png

Take Aways
++++++++++

- 
