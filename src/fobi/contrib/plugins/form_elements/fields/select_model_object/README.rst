=============================================================
fobi.contrib.plugins.form_elements.fields.select_model_object
=============================================================
A ``Fobi`` Select Model Object form field plugin. Makes use of the
``django.forms.models.ModelChoiceField`` and ``django.forms.widgets.Select``.

Installation
============
1. Add ``fobi.contrib.plugins.form_elements.fields.select_model_object`` to the
   ``INSTALLED_APPS`` in your ``settings.py``.

.. code-block:: python

    INSTALLED_APPS = (
        # ...
        'fobi.contrib.plugins.form_elements.fields.select_model_object',
        # ...
    )

2. In the terminal type:

.. code-block:: sh

    ./manage.py fobi_sync_plugins

3. Assign appropriate permissions to the target users/groups to be using
   the plugin if ``FOBI_RESTRICT_PLUGIN_ACCESS`` is set to True.

4. Make sure to take a look at
   ``fobi.contrib.plugins.form_elements.fields.select_model_object.defaults.IGNORED_MODELS``.
   If necessary, override it in your `settings` as shown in the example below:

.. code-block:: python

    FOBI_FORM_ELEMENT_SELECT_MODEL_OBJECT_IGNORED_MODELS = [
        'auth.User',
        'auth.Group',
    ]

5. By default, the submitted form value of `select_model_object` elements is
   `app_label.model_name.object_pk.object_repr`. However, that part of the
   behaviour has been made configurable. You can choose between the following
   options:

   .. code-block:: text

       - "val": `app_label.model_name.object_pk.object_repr`.
       - "repr": `object_repr` (uses the ``__unicode__`` method of the model).
       - "mix" (default): `app_label.model_name.object_pk.object_repr`.

   Simply set the ``FOBI_FORM_ELEMENT_SELECT_MODEL_OBJECT_SUBMIT_VALUE_AS``
   assign one of the following values: "val", "repr" or "mix" to get the
   desired behaviour.
