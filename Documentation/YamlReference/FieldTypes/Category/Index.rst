.. include:: /Includes.rst.txt
.. _field_type_category:

========
Category
========

The :yaml:`Category` type can handle relations to categories. The categories are
taken from the system table :sql:`sys_categories`.

Settings
========

..  confval-menu::
    :name: confval-category-options
    :display: table
    :type:
    :default:
    :required:

.. confval:: relationship
   :name: category-relationship
   :required: false
   :type: string

   Depending on the relationship, the category relations is stored (internally)
   in a different way. Possible keywords are `oneToOne`, `oneToMany` or
   `manyToMany` (default).

.. confval:: maxitems
   :name: category-maxitems
   :required: false
   :type: integer
   :default: "0"

   Maximum number of items. Defaults to a high value. JavaScript record
   validation prevents the record from being saved if the limit is not satisfied.

.. confval:: minitems
   :name: category-minitems
   :required: false
   :type: integer
   :default: "0"

   Minimum number of items. Defaults to 0. JavaScript record validation
   prevents the record from being saved if the limit is not satisfied.
   The field can be set as required by setting `minitems` to at least 1.

.. confval:: treeConfig.startingPoints
   :name: category-treeConfig.startingPoints
   :required: false
   :type: string

   Allows to set one or more roots (category uids), from which the categories
   should be taken from.

Examples
========

Minimal
-------

.. code-block:: yaml

    name: example/category
    fields:
      - identifier: categories
        type: Category

Advanced / use case
-------------------

.. code-block:: yaml

    name: example/category
    fields:
      - identifier: categories
        type: Category
        minitems: 1
        treeConfig:
          startingPoints: 7
        relationship: oneToOne
