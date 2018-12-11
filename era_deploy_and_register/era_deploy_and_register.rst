.. _era_deploy_and_register:

------------------------
Era: Deploy and Register
------------------------

Overview
++++++++

.. note::

  Estimated time to complete: **15 MINUTES**

In this exercise you will deploy Nutanix Era and register your Nutanix cluster.

Pre-requirements
++++++++++++++++

To be able to run the workshops you need to have the following available or installed

A public ssh key of your machine by using :ref:'sshkey_creation'

pgAdmin 4 (This can be downloaded and installed for your OS from https://www.pgadmin.org/download/).

.. note::

  The screenshots in this Workshop are created using a Windows 7 machine. For the Mac OS/X it may be different. An example is the way to create a ssh key pair. Differences will be in writing and may contain a screenshot for clarification where possible.

Deploy ERA VM
+++++++++++++

Deploy Era VM from Prism Central.

In **Prism Central > VMs > List**, click **Create VM**.

Fill out the following fields and click **Save**:

- **Name** - Era-*Initials*
- **Description** - (Optional) Description for your VM.
- **vCPU(s)** - 4
- **Number of Cores per vCPU** - 1
- **Memory** - 16 GiB

- Select **+ Add New Disk**
    - **Type** - DISK
    - **Operation** - Clone from Image Service
    - **Image** - **“Era-Server-build…”**.qcow2
    - Select **Add**

- Select **Add New NIC**
    - **VLAN Name** - Primary
    - Select **Add**

Click **Save** to create the VM.

Select the Nutanix Era VM you created and click **Power On**.

.. figure:: images/2.png

Register Cluster with Nutanix ERA
+++++++++++++++++++++++++++++++++

In **Prism Central > VMs > List**, indentify the IP Address assigned to the Era VM you just deployed (“IP Addresses” column).

.. note::

  If the IP address does not populate, log into the console of the VM and Run “ifconfig” to see the assigned IP address'
  - **Username - Era
  - **Password - Nutanix.1

In a new browser tab, log on to Era https://ERA-IP:8443/ using these credentials:

.. note::

  It may take a **couple minutes** for the Era interface to initialize after booting the VM.

  Check off “I have read and agree to terms and conditions.” And select **Continue**

- **Username** - admin
- **Password** - Set new admin password **techX2019!**

.. figure:: images/3.png

At the "Welcome to Era" screen, fill in the following information and click **Next**:

- **Name** - HPOC Cluster Name
- **Description** - (Optional) Description
- **IP address of Prism Element** - *HPOC Cluster IP*
- **Prism Element Administrator** - admin
- **Password** - techX2019!

.. figure:: images/4.png

Click **Next**

Select the container named **“default…”** and click **Next**.

For the Network Profile choose **Primary** and leave Manage IP Address Pool in Era unchecked.

Click **Next**.

Setup of Era will proceed automatically and takes a couple minutes.

Once complete select **Get Started**.

Takeaways
++++++++++
