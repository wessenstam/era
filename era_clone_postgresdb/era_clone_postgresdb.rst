.. _era_clone_postgresdb:

----------------------
Era: Clone Postgres DB
----------------------

Overview
++++++++

.. note::

  Estimated time to complete: **30 MINUTES**

This lab will show you how to clone, connect, and view a Postgres Database. It will also show you how to modify and refresh the clone.

Cloning Your PostgreSQL Source
++++++++++++++++++++++++++++++

So we have created and connected to our database, now lets make a clone.

In **Era > Time Machines**, and select the Time Machine instance for your Source DB.

.. figure:: images/16.png

Click **Snapshot**, and name it **First_Snapshot**

.. figure:: images/17.png

Click **Create**

Monitor the Create Snapshot job from under the **Operations menu**.

.. figure:: images/18.png

After the snapshot creation completes, from the Time Machine select **Clone**

**Time**

- **Snapshot** - First_Snapshot

.. figure:: images/19.png

Click **Next**

**Server**

- **Database Server** - Create New Server
- **VM Name** - DBServer-*Initials*-Clone
- **Compute Profile** - Take Default
- **Network Profile** - Take Default

Create a new SSH Key following the Instructions in the SSH Key Creation Lab :ref:'sshkey_creation'

Copy and paste the public key into the SSH public key “text” option for the database server

.. figure:: images/20.png

Click **Next**

**Database**

- **Name** - LabDB-*Initials*-Clone
- **Description** - (Optional) Description
- **Password** - techX2019!
- **Database Parameter Profile** - Take Default

.. figure:: images/21.png

Click **Clone**

The clone process will take roughly the same amount of time as provisioning your original source.

You can monitor this process through the **Operations menu**.

While waiting for the clone to compete you can explore other areas of the Era GUI.

For example, view the settings that represent the Software, Compute, Network and DB Parameters from under the Profiles menu.

.. figure:: images/22.png

Following the completion of the clone operation, you can connect to the clone instance as described in the previous section, **Viewing and Connecting to PostgreSQL**.

.. figure:: images/23.png

Refreshing Your Clone Copy
++++++++++++++++++++++++++

In **Era > Databases**, and select your Cloned DB instance.

Select the radio button next to your instance and click **Refresh**

.. figure:: images/24.png

Choose the previous snapshot you created and click **Refresh**

Follow the job to completion under **Operations**

Modify source database and refresh your clone (10 min)
++++++++++++++++++++++++++++++++++++++++++++++++++++++

Lets modify the source database and refresh the clone.

Start pgAdmin, select your source database instance, go to the Tools menu and select Query Tool

.. figure:: images/25.png

From the **Query Tool**, paste the following SQL command into the editor:

.. code-block:: bash
  :name: inline-code-example

  CREATE TABLE products (
  product_no integer,
  name text,
  price numeric
  );

Choose Execute/Refresh

.. figure:: images/26.png

View the newly created table from under the Schemas tree view

.. figure:: images/27.png

From **Era > Time Machines**, and select the Time Machine instance for your Source DB.

Create a **Snapshot**, and name it **Second_Snapshot**

.. note::

  Follow the same process as the **Cloning Your PostgreSQL Source** section for creating the snapshot.

Refresh your clone copy using this new snapshot as outlined in the previous section **Refreshing your clone copy**.

Once the clone refresh operation is complete, refresh your view for the clone copy in pgAdmin to see the table from the source

.. figure:: images/28.png

View the environment using the REST API Explorer (5 min)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Now view the environment using the REST API Explorer

From the top right drop down menu choose **REST API Explorer**.

.. figure:: images/29.png

Expand the various categories to view the possible operations.

To execute a given operation, like GET /databases for example, select the operation and choose **“try it out”**

.. figure:: images/30.png

After selecting **“try it out”** choose **Execute**

.. figure:: images/31.png

You should see a response like the following

.. figure:: images/32.png

Takeaways
++++++++++

-
