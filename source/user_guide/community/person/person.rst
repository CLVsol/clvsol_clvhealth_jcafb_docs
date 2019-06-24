.. raw:: html

    <style> .red {color:red} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: bi

.. index:: Person

============
:bi:`Person`
============

	#. Atualização de :bi:`Contact Information`:

		* Para atualizar as informações de :bi:`Contact Information` da Pessoa, a partir dos dados do **Endereço** (*Reference* :doc:`/user_guide/community/address/address`) atual, utilizar o botão :bi:`Get Reference Address Data`.

			* Os campos de *Address* de :bi:`Contact Information` da Pessoa serão atualizados com os respectivos campos de :bi:`Contact Information` do **Endereço** (*Reference* :doc:`/user_guide/community/address/address`) atual da Pessoa.

		* Como alternativa, executar a ação ":doc:`/user_guide/community/person/person_contact_info_updt`".

			* Os campos de *Address* de :bi:`Contact Information` da Pessoa serão atualizados com os respectivos campos de :bi:`Contact Information` do **Endereço** (*Reference* :doc:`/user_guide/community/address/address`) atual da Pessoa.

			* Opcionalmente alguns campos de informações pessoais, tais como telefones, email, etc., de :bi:`Contact Information` da Pessoa serão atualizados com os respectivos campos de :bi:`Contact Information` do **Endereço** (*Reference* :doc:`/user_guide/community/address/address`) atual da Pessoa.

	#. Associação a uma :bi:`Family`:

		* Para associar a Pessoa a uma ":doc:`/user_guide/community/family/family`" que tenha o mesmo **Endereço** (*Reference* :doc:`/user_guide/community/address/address`) atual da Pessoa, utilizar o botão :bi:`Associate to Family with Reference Address`.

			* A Pessoa será associada à Família já existente no **Endereço** (*Reference* :doc:`/user_guide/community/address/address`) atual da Pessoa.

		* Como alternativa, executar a ação ":doc:`/user_guide/community/person/person_associate_to_family`".

			* A Pessoa será associada à Família já existente no **Endereço** (*Reference* :doc:`/user_guide/community/address/address`) atual da Pessoa.

			* Opcionalmente. quando não existir uma Família no **Endereço** (*Reference* :doc:`/user_guide/community/address/address`) atual da Pessoa, uma nova Família será criada para permitir a associação. Neste caso, opcionalmente, todas as demais Pessoas com o mesmo **Endereço** (*Reference* :doc:`/user_guide/community/address/address`) serão associadas à nova Família criada.


.. index:: Contact Information
.. index:: Get Reference Address Data
.. index:: Get Reference Address Family

.. toctree::
   :maxdepth: 2
   :caption: Ações:

   person_mass_edit
   person_contact_info_updt
   person_associate_to_family
   person_associate_to_person_off
   person_associate_to_set
