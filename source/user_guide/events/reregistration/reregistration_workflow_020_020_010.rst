.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: [Pessoa não cadastrada] A Pessoa reside em um Endereço já cadastrado, pertencendo à Família já cadastrada

=========================================================================================================
[Pessoa não cadastrada] A Pessoa reside em um Endereço já cadastrado, pertencendo à Família já cadastrada
=========================================================================================================

.. _Cadastro Auxiliar (10):

Cadastro Auxiliar
-----------------

    O **Cadastro Auxiliar** criado poderá ser composto pelas seguintes **Entidades (Aux)**:

        * :bi:`Person (Aux)`:
        * :bi:`Address (Aux)`:
        * :bi:`Family (Aux)`:

    O relacionamento entre os diversos registros dos Cadastros será o seguinte:

        * :bi:`Person (Aux)`: 

            * :bi:`(Reference) Address` » :bi:`Address`
            * :bi:`Family` » :bi:`Family`
            * :bi:`(Reference) Address (Aux)` » :bi:`Address (Aux)`
            * :bi:`Family (Aux)` » :bi:`Family (Aux)`
            * :bi:`Related Person` » **vazio**
            * :bi:`Contact Information` = Dados do registro :bi:`Address`
            * Outros Dados = Outros Dados coletadas para a Pessoa

        * :bi:`Address (Aux)`:

            * :bi:`Related Address` » :bi:`Address`
            * :bi:`Contact Information` = Dados do registro :bi:`Address`
            * Outros Dados = Outros Dados do registro :bi:`Address`

        * :bi:`Family (Aux)`:

            * :bi:`(Reference) Address` » :bi:`Address`
            * :bi:`(Reference) Address (Aux)` » :bi:`Address (Aux)`
            * :bi:`Related Family` » :bi:`Family`
            * :bi:`Contact Information` = Dados do registro :bi:`Address`
            * Outros Dados = Outros Dados do registro :bi:`Family`

.. Fluxo de Trabalho (*Workflow*) (10):

Fluxo de Trabalho (*Workflow*)
------------------------------

    #. *View* **Contatos** ou *View* :bi:`Persons`:

        #. Procurar pelo registro :bi:`Person` associado à Pessoa utilizando um dos métodos:

            * :doc:`reregistration_workflow_010_010`
            * :doc:`reregistration_workflow_010_020`

            **Observação**: Nenhum registro :bi:`Person` deverá ser encontrado, a menos que a nova Pessoa já esteja em processo de recadastramento.

    #. *View* **Contatos** ou *View* :bi:`Addresses`:

        #. Procurar pelo registro :bi:`Address` associado ao Endereço informado para a Pessoa utilizando um dos métodos:

            * :doc:`reregistration_workflow_010_050`
            * :doc:`reregistration_workflow_010_060`

    #. *View* :bi:`Contatos`:

        #. Procurar pelo registro :bi:`Person (Aux)` associado à Pessoa utilizando um dos métodos:

            * :doc:`reregistration_workflow_010_010`

            **Observação**: Nenhum registro :bi:`Person (Aux)` deverá ser encontrado, a menos que a nova Pessoa já esteja em processo de recadastramento.

    #. *View* :bi:`Person (Aux)`:

        #. Um registro :bi:`Person (Aux)` deverá ser **criado manualmente** e preenchido com as informações informadas para a Pessoa, exceto as informaçôes de Endereço.

    #. Registro :bi:`Person (Aux)`:

        #. O :bi:`(Reference) Address` do registro :bi:`Person (Aux)` deve ser manualmente associado ao registro :bi:`Address` encontrado.

        #. Um registro :bi:`Address (Aux)` deve ser criado a partir do registro :bi:`Person (Aux)`, executando a Ação ":bi:`Person (Aux) Associate to Address (Aux)`":

            * A criação de :bi:`Address (Aux)`, deve ser **habilitada**.

    #. Registro :bi:`Address (Aux)`:

        #. Não será necessário qualquer ação de atualização do registro :bi:`Address (Aux)`.

    #. Registro :bi:`Person (Aux)`:

        #. Procurar pelo registro :bi:`Family` associado ao :bi:`(Reference) Address` do registro :bi:`Person (Aux)`.

        #. O :bi:`Family` do registro :bi:`Person (Aux)` deve ser manualmente associado ao registro :bi:`Family` encontrado.

        #. Um registro :bi:`Family (Aux)` deve ser criado a partir do registro :bi:`Person (Aux)`, executando a Ação ":bi:`Person (Aux) Associate to Family (Aux)`":

                * A criação de :bi:`Family (Aux)`, deve ser **habilitada**.

    #. Registro :bi:`Family (Aux)`:

        #. Não será necessário qualquer ação de atualização do registro :bi:`Family (Aux)`.

.. toctree::
   :maxdepth: 2
   :caption: Itens Relacionados:
