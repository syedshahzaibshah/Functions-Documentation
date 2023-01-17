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

..  code-block:: php
    :caption: EXT:site_package/Configuration/TCA/Overrides/sys_template.php
    :linenos:
    :emphasize-lines: 4, 7

    /**
     * Add default TypoScript (constants and setup)
     */
    \TYPO3\CMS\Core\Utility\ExtensionManagementUtility::addStaticFile(
         'site_package',
         'Configuration/TypoScript',
         'Site Package'
    );

#.  Submit Sales Order for approval.
#.  Approve the Sales Order.
#.  Mark Sales Order as Confiremd/Open.
#.  Update the following fields on Zoho Project.

    * Update Sales Order Number on Zoho Project.
    * Status of Salesorder will be updated as Zoho Project Status & Substatus.

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
