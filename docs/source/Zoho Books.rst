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

.. image:: img/cost_items.png
     :alt: Alternative text
    
#.  Create a Map of custom fields to compare with estimate custom fields. Also add project id into Map.
#.  Fetch Estimate custom fields and compare it with above created Map of Sales Order custom fields.
#.  Check if salesperson is not empty field.
#.  Check if contact persons is not empty field.
#.  Check discount type. If type is entity_level and a discount at entity level or if its on item level add it on item level.
#.  Get all line items detials from estimate and create a JSON map for Sales Order creation. 
#.  Also add Project id into Line Items.
#.  Get all line items detials from 
#.  In this function we are creating Sales Order when estimate is accepted.

Sales Orders
------------

- **Convert Sales Order to Purchase Order**

  +------------------------+---------------+-----------+-------------+----------------+---------+
  |        Zoho App        |  Module Name  | On Button | On Workflow |  On Scheduler  |  Status |
  +========================+===============+===========+=============+================+=========+
  | Zoho Books             |  Sales Order  |    Yes    |      No     |       No       |   Live  |
  +------------------------+---------------+-----------+-------------+----------------+---------+

- **Update SO Details on Zoho Project**

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
