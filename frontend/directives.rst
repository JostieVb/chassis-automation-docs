Directives
==========

.. _DirectivesIntroduction:

Introduction
------------

Angular let's you extend html elements with new attributes called **directives**.
Angular has some built-in directives, like ``ngFor``, ``ngIf`` and ``ngSwitch``.
You can also define your own directives. Chassis Automation uses two custom directives:

* ``form``
* ``caller``

These directives can be found in ``chassis-automation-client/src/app/bpmn/directives/``.
More information about these directives will be given below.

.. _DirectivesFormDirective:

Form directive
--------------

The ``form`` directive makes sure that a form built with the form builder will be rendered on the location where
the directive is set. The directive requires as input the identifier of the desired form.
The example below shows how the ``form`` directive should be used.

.. code-block:: text

    <form [form]="'form-new-product'"></form>

.. danger::

    The form identifier should be given to the directive as a ``string``, so single quotations are required.

.. danger::

    In the current version of the prototype, the form directive doesn't render a submit button and form meta-data such as
    a form title and a subtitle, because this isn't supported by the form builder yet. You should add a submit button
    manually just below the ``<form>`` element where the directive is set.

To handle the submit event, the ``caller`` directive comes in. More information about the ``caller`` directive will be
given in the next sub-chapter.

.. _DirectivesCallerDirective:

Caller directive
----------------

The ``caller`` directive makes sure that a form is submitted and that a call is made to the back-end to check if a
workflow is linked to the submitted form. This directive should only be set on a submit button for a form.
The example below shows how the ``caller`` directive should be used.

.. code-block:: text

    <button [caller]="'form-new-product'">Add product</button>

.. danger::

    The form identifier should be given to the directive as a ``string``, so single quotations are required.

.. _DirectivesUsingBothDirectives:

Using both directives
---------------------

In order to render a form and check for a linked workflow, both directives must be used.
A full example is shown below.

.. code-block:: text

    <div class="form-container">
        <h5>New product</h5>
        <p>Please, add a new product.</p>
        <form [form]="'form-new-product'"></form>
        <button [caller]="'form-new-product'">Add product</button>
    </div>