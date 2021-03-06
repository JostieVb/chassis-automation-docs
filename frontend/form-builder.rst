.. _FormBuilder:

Form builder
============

.. _FormBuilderIntroduction:

Introduction
------------

The form builder enables end-users to create their own forms that can be linked to a process that
is created with the :ref:`Modeler`. The form builder is accessible via the 'Form builder' page.
This chapter will explain the features that are currently implemented in the form builder and
how to extend them.

.. _FormBuilderFeatures:

Code location
-------------

The form builder's front-end code can be found in ``chassis-automation/src/app/forms/pages/form-builder``.

.. _FormBuilderExtending:

Extending the form builder
--------------------------

All the form fields that can be used for making a form are registered in the ``FORM_BUILDER_ITEMS`` constant which can be
found in ``chassis-automation/src/app/forms/form-builder-items.ts``. To add a new draggable field to the form builder's
available items, you simple have to add a new object to the array. An preview of the array is shown below.

.. code-block:: javascript

    export const FORM_BUILDER_ITEMS = [
        {type: 'Title', description: 'A bigger title', icon: 'fa-font', data: 'title'},
        {type: 'Sub-title', description: 'Provide more information with a sub-title', icon: 'fa-comment', data: 'subtitle'},
        {type: 'Text', description: 'A normal text input field', icon: 'fa-text-width', data: 'text'},
        {type: 'Textarea', description: 'A large text input field that can be resized', icon: 'fa-align-justify', data: 'textarea'},
        {type: 'WYSIWYG', description: 'A WYSIWYG textarea input field', icon: 'fa-align-left', data: 'wysiwyg'},
        {type: 'Numeric', description: 'A numeric input field', icon: 'fa-sort', data: 'numeric'}
    ];

When that is done, you can add a new preview field in the form builder's template. This preview field will be shown when
the user drags a new field into the drag-and-drop field. Every preview field must have a type check with the ``*ngIf`` directive to
determine when the field must be shown. An example of this is shown below.

.. code-block:: text

    <input *ngIf="fields[id].type === 'text'" type="{{fields[id].type}}" class="form-control" name="{{id}}" placeholder="{{fields[id].description}}" disabled />