.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

=================
:bi:`OCA` Modules
=================

* `OCA - Odoo Community Association <https://github.com/OCA>`_
	
	The GitHub repos for all Open Source work around Odoo.

* `Colorize field in tree views <https://github.com/OCA/web/tree/12.0/web_tree_dynamic_colored_field>`_
	
	This module aims to add support for dynamically coloring fields in tree view according to data in the record.

	It provides attributes on fields with the similar syntax as the ``colors`` attribute
	in tree tags.

	Further, it provides a ``color_field`` attribute on tree tags's ``colors`` to use
	a field's value as color.

* `Custom shortcut icon <https://github.com/OCA/web/tree/12.0/web_favicon>`_
	
	This module was written to allow you to customize your Odoo instance's shortcut
	icon (aka favicon). This is useful for branding purposes, but also for
	integrators who have many different Odoo instances running and need to see at a
	glance which browser tab does what.

	The icon is shown also for portal users when the website modules are not
	installed.

	More info about favicon: https://en.wikipedia.org/wiki/Favicon

* `OdooRPC <https://github.com/OCA/odoorpc>`_
	
	**OdooRPC** is a Python package providing an easy way to
	pilot your **Odoo** servers through `RPC`.

	Features supported:
	    - access to all data model methods (even ``browse``) with an API similar
	      to the server-side API,
	    - use named parameters with model methods,
	    - user context automatically sent providing support for
	      internationalization,
	    - browse records,
	    - execute workflows,
	    - manage databases,
	    - reports downloading,
	    - JSON-RPC protocol (SSL supported),

.. toctree::
   :maxdepth: 2
   :caption: Contents:
