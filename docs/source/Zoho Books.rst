Zoho Books
==========

.. _estimates:

Estimates
---------

- **Convert Estimate to Sales Order**  (11 Jan 2023)

  +------------------------+---------------+-----------+-------------+----------------+----------+
  |        Zoho App        |  Module Name  | On Button | On Workflow |  On Scheduler  |  Status  |
  +========================+===============+===========+=============+================+==========+
  | Zoho Books             |    Estimate   |    Yes    |      No     |       No       |   Live   |
  +------------------------+---------------+-----------+-------------+----------------+----------+

**Steps:**

#.  Check if estimate contains the Zoho Project.

.. image:: img/estimate_img.png
     :alt: Alternative text
    
2.  Create a Map(JSON) of all custom fields to compare it with Sales Order custom fields in next step. Also add project id into Map.
#.  Fetch Sales Order custom fields to compare it with above created Map of Estimate custom fields against following conditions.

    * Check if both fields are active.
    * Data type of fields are same.
    * Label of both fields are same.

#.  If project id was not null add it into the custom fields Map.
#.  Add Discount by checking discount type. It may be on item level or entity level.
#.  Add sales person into Sales Order.
#.  Add contact persons into Sales Order.
#.  Add all custom fields in Sales Order which were campared in step 3 along with Project id.
#.  Create a Sales Order.

#.  Submit Sales Order for approval.

..  code-block:: php
 
	  url :"https://books.zoho.com/api/v3/salesorders/" + salesorder_id + "/submit"

11. Approve the Sales Order.

..  code-block:: php
  
	  url :"https://books.zoho.com/api/v3/salesorders/" + salesorder_id + "/approve"

12.  Mark Sales Order as Confiremd/Open.

..  code-block:: php
  
	  url :"https://books.zoho.com/api/v3/salesorders/" + salesorder_id + "//status/open"

13.  Update the following fields on Zoho Project.

     * Update Sales Order Number on Zoho Project.
     * Status of Salesorder will be updated as Zoho Project Status & Substatus.

Sales Orders
------------

- **Update SO Data on Zoho Project (Status & Installation Date)**

  +------------------------+---------------+-----------+-------------+----------------+---------+
  |        Zoho App        |  Module Name  | On Button | On Workflow |  On Scheduler  |  Status |
  +========================+===============+===========+=============+================+=========+
  | Zoho Books             |  Sales Order  |     No    |     Yes     |       No       |   Live  |
  +------------------------+---------------+-----------+-------------+----------------+---------+
**Steps:**

#.  Check if Sales Order contains the Zoho Project.

.. image:: img/Salesorder.png
     :alt: Alternative text
    
2.  Push the following fields on Zoho Project.

    * Expected Install Date.
    * Project Managers.
    * Production Managers.

3.  Update Sales Order Number on Zoho Project.
#.  Update the status on Zoho Project as it is on Sales Order.

  +---------------------------------+------------------------+---------------------------+
  |        Sales Order Status       |  Zoho Project Status   |  Zoho Project Sub Status  |                
  +=================================+========================+===========================+
  |               Open              |        Approved        |          Approved         |
  +---------------------------------+------------------------+---------------------------+
  |               Void              |        Declined        |          Declined         |
  +---------------------------------+------------------------+---------------------------+
  |            Production           |        Production      |          Production       |
  +---------------------------------+------------------------+---------------------------+
  |          Order Material         |        Production      |          Production       |
  +---------------------------------+------------------------+---------------------------+
  |             Permitting          |         Permit         |          Permit           |
  +---------------------------------+------------------------+---------------------------+
  |             Installing          |      Installation      |        Installation       |
  +---------------------------------+------------------------+---------------------------+
  |      Waiting for Fulfilment     |       Order Setup      |         Order Setup       |
  +---------------------------------+------------------------+---------------------------+
  |          Being Fulfiled         |       Order Setup      |         Order Setup       |
  +---------------------------------+------------------------+---------------------------+
  |              Service            |         Service        |          Service          |
  +---------------------------------+------------------------+---------------------------+

#.  Add sales person into Sales Order.
#.  Add contact persons into Sales Order.
#.  Add all custom fields in Sales Order which were campared in step 3 along with Project id.
#.  Create a Sales Order.

#.  Submit Sales Order for approval.

..  code-block:: php
 
	  url :"https://books.zoho.com/api/v3/salesorders/" + salesorder_id + "/submit"

11. Approve the Sales Order.

..  code-block:: php
  
	  url :"https://books.zoho.com/api/v3/salesorders/" + salesorder_id + "/approve"

12.  Mark Sales Order as Confiremd/Open.

..  code-block:: php
  
	  url :"https://books.zoho.com/api/v3/salesorders/" + salesorder_id + "//status/open"

13.  Update the following fields on Zoho Project.

     * Update Sales Order Number on Zoho Project.
     * Status of Salesorder will be updated as Zoho Project Status & Substatus.

- **Update Sales Order to Purchase Order**

  +------------------------+---------------+-----------+-------------+----------------+---------+
  |        Zoho App        |  Module Name  | On Button | On Workflow |  On Scheduler  |  Status |
  +========================+===============+===========+=============+================+=========+
  | Zoho Books             |  Sales Order  |     No    |     Yes     |       No       |   Live  |
  +------------------------+---------------+-----------+-------------+----------------+---------+

  **Steps:**
  
  #.  Search all ``cost items(custom module)`` by using estimate line items.
  
.. image:: img/cost_items.png
     :alt: Alternative text
     :width: 200
     :height: 200
     :align: left
  
  
2.  List the vendors from cost items and remove duplicates s.
3.  Get all cost items against vendors and create a PO.
4.  Create a PO.
5.  Update PO number on Estimate
  
To retrieve a list of random ingredients,
you can use the ``lumache.get_random_ingredients()`` function:

.. autofunction:: lumache.get_random_ingredients

The ``kind`` parameter should be either ``"meat"``, ``"fish"``,
or ``"veggies"``. Otherwise, :py:func:`lumache.get_random_ingredients`
will raise an exception.

.. autoexception:: lumache.InvalidKindError

For example:

>>> import lumache
>>> lumache.get_random_ingredients()
['shells', 'gorgonzola', 'parsley']
