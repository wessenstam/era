.. _lab:

-------------
ERA Lab
-------------

Overview
++++++++

This lab will show how ERA can be used to:

#. What are the requirements for this Workshop
#. Create the ERA VM
#. Log into the ERA VM and register the cluster
#. Deploy a PostgreSQL environment
#. Connect and view the PostgreSQL environment
#. Clone the PostgreSQL environment source
#. Refresh the Clone

Pre-requirements
++++++++++++++++

To be able to run the workshops you need to have the following available or installed

1. A public ssh key of your machine by using PuttyGen (https://the.earth.li/~sgtatham/putty/latest/w64/puttygen.exe) or by copying the content of the id_rsa.pub file from a Mac OS/X machine (https://secure.vexxhost.com/billing/knowledgebase/171/How-can-I-generate-SSH-keys-on-Mac-OS-X.html)
2. pgAdmin 4. This can be downloaded and installed for your OS from https://www.pgadmin.org/download/.
3. The ERA VM available in the to be used Nutanix Cluster. If not available, you can download it at https://portal.nutanix.com/#/page/releases/eraDetails (Nutanix Support Portal Login details required)


.. note::

  The screenshots in this Workshop are created using a Windows 7 machine. For the Mac OS/X it may be different. An example is the way to create a ssh key pair. Differences will be in writing and may contain a screenshot for clarification where possible.

.. note::

  Make sure the ERA VM disk image has been uploaded in the AHV cluster. If not do that now **before** you start the following lab.

Create ERA VM (AHV) (5 min.)
++++++++++++++++++++++++++++

1. Log into the PRISM Element interface of your cluster


.. figure:: images/1.png


2. Go to the VM dashboard, click Create VM. Do the following in the indicated fields.

  a. **Name:**  Enter a name for the VM.
  b. **(Optional) Description:**  Enter a description for the VM.
  c. **vCPU(s):**  Enter 4 as the number of virtual CPUs to allocate to this VM.
  d. **Number of Cores per vCPU:**  Enter 1 as the number of cores assigned to each virtual CPU.
  e. **Memory:**  Enter 16 GB as the amount of memory (in GB) to allocate to this VM.
  f. To attach a disk to the VM, click **Add New Disk**.  Do the following in the indicated fields.

    i.	**Type:**  Select Disk as the type of storage device from the drop-down list.
    ii.	**Operation:**  Select Clone from Image Service to copy the Nutanix Era image that you have.
    iii.	**Bus** Type:  Select SCSI as the bus type from the pull-down list.
    iv.	**Image:**  Select the Nutanix Era image (**“Era-Server-build…”**)
    v.	**Size:** Will populate with the size of the image you select
    vi.	Click **Add** to attach the disk to the VM and return to the Create VM dialog box

  g.	Create a network interface for the VM, click Add New NIC

    i.	Select VLAN Name **“Primary”** An IP will be assigned over DHCP
    ii.	Click Add

  h.	Click the **Save** button to create the VM

  i. In the Table view of the VM dashboard, select the Nutanix Era VM and click **Power On**.


  .. figure:: images/2.png

Log into the Nutanix ERA and register the Cluster (5 min.)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

1.	From the VM dashboard, look for the IP Address assigned to your Era VM (“IP Addresses” column).

  a.	If the IP address does not populate, log into the console of the VM (Select “Launch Console”)
  b.	Log into the VM with user “Era” and password “Nutanix.1”
  c.	Run “ifconfig” to see the assigned IP address

2.	Open your Chrome browser and go to https://<era_vm_ip>:8443

.. note::

  It may take a **couple minutes** for the Era interface to initialize after booting the VM.

3.	Check off “I have read and agree to terms and conditions.” And select **Continue**
4.	Set the new admin password matching complexity requirements *(eg. Nutanix.1)*
5.	Log into the cluster with user “admin” and your new password

.. figure:: images/3.png

6.	At the Welcome to Era page

  a.	Enter the IP address for accessing Prism Element for your assigned Nutanix cluster
  b.	Enter your admin credentials and choose **Next**.
  c.	Select the container named **“default…”** and choose Next
  d.	For the Network Profile choose **“Primary”** and leave Manage IP Address Pool in Era unchecked.  Choose **Next**.
  e.	Step 4, Setup Era, will proceed automatically and takes a couple minutes.  Once complete select **Get Started**.


Getting started: Deploy PostgreSQL (15 min.)
++++++++++++++++++++++++++++++++++++++++++++

1. On the **Getting Started** page click on PostgreSQL

.. figure:: images/4.png

2.	In the Provision a PostgreSQL database, select the bottom link, “2. Provision a Database”
3.	In the Provision a Database menu

  a.	For step 1: Engine, select PostgreSQL and choose Next
  b.	For step 2: Database Server


    i.	Choose Create New Server
    ii.	Enter a unique Database Server Name
    iii.	Select the existing Software Profile
    iv.	Select the Default Compute Profile
    v.	Select the Default Network Profile
    vi.	Create a new public key using puttygen. For the Mac OS/X use this article that describes how to create a use the public part of the ssh pair. https://secure.vexxhost.com/billing/knowledgebase/171/How-can-I-generate-SSH-keys-on-Mac-OS-X.html

      1. From the Putty Key Generator ensure “RSA” is selected.

      .. figure:: images/6.png
        :align: center


      2.	Click Generate and move your mouse over the blank area of the Putty Key Generator window.

    vii.	Copy and paste the public key into the SSH public key “text” option for the database server

    .. figure:: images/7.png
      :align: center

    viii.	Click Next

c.	For step 3: Database

  i.	Enter a database name of your choice
  ii.	Enter a password of your choice as the POSTGRES Password
  iii.	Choose the default Database Parameter Profile
  iv.	Keep the default Listener Port and Size (GiB)

  .. figure:: images/8.png
    :align: center

  v.	Click Next

d.	For step 4: Time Machine

  i.	Accept the existing populated Name, SLA (Gold) and Schedule defaults

  .. figure:: images/9.png
    :align: center

  ii.	Click Provision

e.	Monitor the Provision Database task from under the Operations menu, should take around 5 minutes.  While you wait, you can explore other areas of the Era GUI, such as viewing the dashboard or administration pages.

.. figure:: images/10.png
  :align: center

Viewing and Connecting to PostgreSQL (2 Min)
++++++++++++++++++++++++++++++++++++++++++++

1.	In the Era UI go to “Databases”

.. figure:: images/11.png


2.	Select your PostgreSQL Source DB
3.	On the Summary page take note of your Database Server IP address

.. figure:: images/12.png


4.	Start pgAdmin.

  a.	Right click Servers in the Browser menu and select Create, then Server
  b.	For Connection information, enter in the IP address of your PostgreSQL instance with the password you specified on creation

  .. figure:: images/14.png
    :align: center

  c.	Also enter a name of your choice under the General tab.
  d.	Choose Save.

5.	You should now be able to browse your database instance

.. figure:: images/15.png


Cloning Your PostgreSQL Source (10 min.)
++++++++++++++++++++++++++++++++++++++++

1.	Go to the Time Machines drop down menu in Era and select the *ime machine instance for your source

.. figure:: images/16.png

2.	Create an on-demand snapshot by choosing the **Snapshot** option and giving it a friendly name.

.. figure:: images/17.png

3.	Click **Create**
4.	Monitor the Create Snapshot job from under the **Operations menu**.

.. figure:: images/18.png

5.	After the snapshot creation completes, from the Time Machine select **Clone** and choose the snapshot you created.

.. figure:: images/19.png

6.	Choose **Create New Server**, select the Default Compute and Network profiles, and create a new public key as in the previous steps.

.. figure:: images/20.png

7.	Choose **Next**.
8.	For the Database, enter a name and password of your choice and the default Database Parameter Profile.

.. figure:: images/21.png

9.	Select **Clone**.
10.	The clone process will take roughly the same amount of time as provisioning your original source.  You can monitor this process through the **Operations menu**.
11.	While waiting for the clone to compete you can explore other areas of the Era GUI.  For example, view the settings that represent the Software, Compute, Network and DB Parameters from under the Profiles menu.

.. figure:: images/22.png

12.	 Following the completion of the clone operation, you can connect to the clone instance as described in the previous section, *Viewing and Connecting* to PostgreSQL.

.. figure:: images/23.png


Refreshing Your Clone Copy (3 min)
++++++++++++++++++++++++++++++++++

1.	From the Era GUI go to Databases and select your Cloned DB instance
2.	Select the radio button next to your instance and click Refresh

.. figure:: images/24.png

3.	Choose the previous snapshot you created and click Refresh
4.	Follow the job to completion under Operations


_________

Take Aways
++++++++++

- ERA is a powerful tool that is easy to set and maintain.
- Using ERA provide a means of deploying PostgreSQL database environments, cloning databases and refreshing existing clones without being a PostgreSQL DBA
- All actions are run via an easy to understand webinterface.
