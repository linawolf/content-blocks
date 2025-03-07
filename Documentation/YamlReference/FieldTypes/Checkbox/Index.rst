.. include:: /Includes.rst.txt
.. _field_type_checkbox:

========
Checkbox
========

The :yaml:`Checkbox` type generates one or more checkbox fields.

Settings
========

..  confval-menu::
    :name: confval-checkbox-options
    :display: table
    :type:
    :default:
    :required:

.. confval:: default
   :name: checkbox-default
   :required: false
   :type: integer (bit value)
   :default: "0"

   The default value corresponds to a bit value. If you only have one checkbox
   having 1 or 0 will work to turn it on or off by default. For more than one
   checkbox you need to calculate the bit representation.

.. confval:: items
   :name: checkbox-items
   :required: false
   :type: array

   Only necessary if more than one checkbox is desired. Contains the checkbox
   elements as separate array items. The `label` can also be defined as a
   LLL-reference.

   Example:

   .. code-block:: yaml

      items:
        - label: 'The first'
        - label: 'The second'
        - label: 'The third'

   XLF translation keys for items have the following convention:

   .. code-block:: xml

        <body>
            <trans-unit id="FIELD_IDENTIFIER.items.0.label">
                <source>Label for first Checkbox item</source>
            </trans-unit>
            <trans-unit id="FIELD_IDENTIFIER.items.1.label">
                <source>Label for second Checkbox item</source>
            </trans-unit>
            <trans-unit id="FIELD_IDENTIFIER.items.n.label">
                <source>Label for nth Checkbox item</source>
            </trans-unit>
        </body>

.. confval:: renderType
   :name: checkbox-renderType
   :required: false
   :type: string
   :default: check

   *  :yaml:`checkboxToggle`
   *  :yaml:`checkboxLabeledToggle`

.. confval:: allowedCustomProperties
   :name: checkbox-allowedCustomProperties
   :required: false
   :type: array
   :default: ["itemsProcConfig"]

   Sometimes it is needed to provide custom configuration for the :ref:`itemsProcFunc <t3tca:tca_property_itemsProcFunc>`
   functionality. These extra properties need to be explicitly allowed via this
   option. This option receives an array of those strings. By default, the
   custom option :yaml:`itemsProcConfig` is allowed.


Examples
========

Minimal
-------

.. code-block:: yaml

    name: example/checkbox
    fields:
      - identifier: checkbox
        type: Checkbox

Advanced / use case
-------------------

Multiple checkboxes:

.. code-block:: yaml

    name: example/checkbox
    fields:
      - identifier: checkbox
        type: Checkbox
        items:
          - label: 'The first'
          - label: 'The second'
          - label: 'The third'
        default: 2
        cols: 3

Toggle checkbox:

.. code-block:: yaml

    name: example/checkbox
    fields:
      - identifier: toggle
        type: Checkbox
        renderType: checkboxToggle
        default: 1

Labeled toggle checkbox:

.. code-block:: yaml

    name: example/checkbox
    fields:
      - identifier: toggle
        type: Checkbox
        renderType: checkboxLabeledToggle
        items:
          - label: 'Your label'
            labelChecked: 'Label checked'
            labelUnchecked: 'Label unchecked'
            invertStateDisplay: true
