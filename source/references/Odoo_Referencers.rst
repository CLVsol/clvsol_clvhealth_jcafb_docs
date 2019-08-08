.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

=====================
:bi:`Odoo` References
=====================

* `Odoo <https://www.odoo.com/>`_
	
* `Odoo - Git - Commit message structure <https://www.odoo.com/documentation/12.0/reference/guidelines.html#git>`_
	
	**Commit message structure**

	Commit message has four parts: tag, module, short description and full
	description. Try to follow the preferred structure for your commit messages

	.. code-block:: text

	  [TAG] module: describe your change in a short sentence (ideally < 50 chars)

	  Long version of the change description, including the rationale for the change,
	  or a summary of the feature being introduced.

	  Please spend a lot more time describing WHY the change is being done rather
	  than WHAT is being changed. This is usually easy to grasp by actually reading
	  the diff. WHAT should be explained only if there are technical choices
	  or decision involved. In that case explain WHY this decision was taken.

	  End the message with references, such as task or bug numbers, PR numbers, and
	  OPW tickets, following the suggested format:
	  task-123 (related to task)
	  Fixes #123  (close related issue on Github)
	  Closes #123  (close related PR on Github)
	  opw-123 (related to ticket)

	**Tag and module name**

	Tags are used to prefix your commit. They should be one of the following

	- **[FIX]** for bug fixes: mostly used in stable version but also valid if you
	  are fixing a recent bug in development version;
	- **[REF]** for refactoring: when a feature is heavily rewritten;
	- **[ADD]** for adding new modules;
	- **[REM]** for removing resources: removing dead code, removing views,
	  removing modules, ...;
	- **[REV]** for reverting commits: if a commit causes issues or is not wanted
	  reverting it is done using this tag;
	- **[MOV]** for moving files: use git move and do not change content of moved file
	  otherwise Git may loose track and history of the file; also used when moving
	  code from one file to another;
	- **[REL]** for release commits: new major or minor stable versions;
	- **[IMP]** for improvements: most of the changes done in development version
	  are incremental improvements not related to another tag;
	- **[MERGE]** for merge commits: used in forward port of bug fixes but also as
	  main commit for feature involving several separated commits;
	- **[CLA]** for signing the Odoo Individual Contributor License;
	- **[I18N]** for changes in translation files;

	After tag comes the modified module name. Use the technical name as functional
	name may change with time. If several modules are modified, list them or use
	various to tell it is cross-modules. Unless really required or easier avoid
	modifying code across several modules in the same commit. Understanding module
	history may become difficult.

* `Odoo Guidelines <https://www.odoo.com/documentation/12.0/reference/guidelines.html>`_

	This page introduces the Odoo Coding Guidelines. Those aim to improve the quality of Odoo Apps code. Indeed proper code improves readability, eases maintenance, helps debugging, lowers complexity and promotes reliability. These guidelines should be applied to every new module and to all new development.
	
* `Widgets in Odoo <https://www.cybrosys.com/blog/widgets-in-odoo>`_

	There are many widgets present in Odoo user interface to perform different functionalities. Status bar, Checkboxes, Radio button etc. make the operations in Odoo simpler. In this blog, I will be explaining about different default widgets in Odoo, its purpose, and implementation syntax.
	
* `Widgets in Odoo 2 <https://odooforbeginnersblog.wordpress.com/2017/03/09/widgets-in-odoo/#more-839>`_

	These are the widget list used in odoo “V8.0, V9.0, V10.0” that can make our development more easy, flexible and usable. Here we have the widgets and their descriptions.
	
* `Odoo - Smart buttons <https://www.slideshare.net/openobject/odoo-smart-buttons>`_

* `Odoo icon smart buttons <https://pt.slideshare.net/TaiebKristou/odoo-icon-smart-buttons>`_

* `Mixing Pandas with Odoo <https://blog.agayon.be/tag/xml-rpc.html>`_

	This article describes the use of XML-RPC API provided by Odoo, a well-known ERP system. Upgrading to version 11.0 is the occasion to update my python scripts to reduce considerably the number of requests. The improvements were done with the help of pandas, the famous data structures and data analysis library.

.. toctree::
   :maxdepth: 2
   :caption: Contents:
