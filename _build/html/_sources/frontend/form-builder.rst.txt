.. _FormBuilder:

Form builder
============

.. _FormBuilderIntroduction:

Introduction
------------

The form builder enables end-users to create their own forms that can be linked to a process that
is created with the :ref:`Modeler`. The form builder is accessible via the 'Forms' page when creating a new form or editing an
existing form. This chapter will explain the features that are currently implemented in the form builder and
how to extend it.

.. _FormBuilderFeatures:

Form builder features
---------------------

The form builder's front-end code can be found in ``chassis-automation/src/app/forms/pages/form-builder``.

.. _FormBuilderExtending:

Extending the form builder
--------------------------

To extend the form builder, you have to add a new property to the form builder's class that is bound
to the desired input field in the form builder. When that is done, you have to add this property
as a new parameter to the ``pushField(params)`` method. This method makes sure that a new field will be pushed
to the form's structure. The last step is to add a new property to the ``structure`` object for the property
you just created in the form builder's class. A quick example is shown below.

.. code-block:: javascript

    this.structure[index][{property_name}] = {class property name};