
.. _bonuslab:

-------------
ERA Bonus Lab
-------------

Overview
++++++++

This bonus lab will show how ERA can be used to:

#. Modify a source database and fresh the clone
#. View the environment using the REST API Explorer

Modify source database and refresh your clone (10 min)
++++++++++++++++++++++++++++++++++++++++++++++++++++++

1.	Start pgAdmin, select your source database instance, go to the Tools menu and select Query Tool

.. figure:: images/25.png

2.	From the **Query Tool**, paste the following SQL command into the editor

.. code-block:: bash
  :name: inline-code-example

  CREATE TABLE products (
  product_no integer,
  name text,
  price numeric
  );

3.	Choose Execute/Refresh

.. figure:: images/26.png

4.	View the newly created table from under the Schemas tree view

.. figure:: images/27.png

5.	From the Time Machine of your source database create a new snapshot.  Follow the same process as the “Cloning Your PostgreSQL Source” section for creating the snapshot.
6.	Refresh your clone copy using this new snapshot as outlined in the previous section “Refreshing your clone copy.”
7.	Once the clone refresh operation is complete, refresh your view for the clone copy in pgAdmin to see the table from the source

.. figure:: images/28.png



View the environment using the REST API Explorer (5 min)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

1.	From the top right drop down menu choose **REST API Explorer**.

.. figure:: images/29.png

2.	Expand the various categories to view the possible operations.
3.	To execute a given operation, like GET /databases for example, select the operation and choose **“try it out”**

.. figure:: images/30.png

4.	After selecting **“try it out”** choose **Execute**

.. figure:: images/31.png

5.	You should see a response like the following

.. figure:: images/32.png

_________

Take Aways
++++++++++

- ERA is a powerful tool that is easy to set and maintain.
- Using ERA provide a means of refreshing existing clones without being a PostgreSQL DBA.
- ERA supports a full API interface.
