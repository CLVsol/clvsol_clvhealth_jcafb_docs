.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: [Pessoa já cadastrada] A Pessoa mudou-se para Endereço já cadastrado, juntamente com a Família

======================================================================================================================
:red:`(Não Verificado)` [Pessoa já cadastrada] A Pessoa mudou-se para Endereço já cadastrado, juntamente com a Família
======================================================================================================================

.. _Cadastro Auxiliar (4):

Cadastro Auxiliar
-----------------

    O **Cadastro Auxiliar** criado poderá ser composto pelas seguintes **Entidades (Aux)**:

        * :bi:`Person (Aux)`:

            * A criação de :bi:`Person (Aux)`, **deve ser habilitada**.

        * :bi:`Address (Aux)`:

            * A criação de :bi:`Address (Aux)`, **deve ser desabilitada**.

                * Um registro :bi:`Address (Aux)` deverá ser criado a partir do registro :bi:`Address` relacionado ao Endereço informado para a Pessoa.

        * :bi:`Family (Aux)`:

            * A criação de :bi:`Family (Aux)`, **deve ser desabilitada**.

                * Um registro :bi:`Family (Aux)` deverá ser criado a partir do registro :bi:`Family` relacionado à Pessoa.

    O relacionamento entre os diversos registros dos Cadastros será o seguinte:

        * :bi:`Person (Aux)`: 

            * :bi:`(Reference) Address` » :bi:`Address`
            * :bi:`Family` » :bi:`Family`
            * :bi:`(Reference) Address (Aux)` » :bi:`Address (Aux)`
            * :bi:`Family (Aux)` » :bi:`Family (Aux)`
            * :bi:`Related Person` » :bi:`Person`
            * :bi:`Contact Information` = Dados do registro :bi:`Address`
            * Outros Dados = Outros Dados do registro :bi:`Person`

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

.. Fluxo de Trabalho (*Workflow*) (4):

Fluxo de Trabalho (*Workflow*)
------------------------------

    #. **Cadastro Auxiliar**:

        #. Procurar pelo registro :bi:`Person` associado à Pessoa utilizando um dos métodos:

            * :doc:`reregistration_workflow_010_010`
            * :doc:`reregistration_workflow_010_020`

        #. O **Cadastro Auxiliar** relacionado à Pessoa deve ser criado a partir do registro :bi:`Person`, executando a Ação ":BI:`Person (Aux) Associate to Family (Aux)`":

                * A criação de :bi:`Person (Aux)`, **deve ser habilitada**.
                * A criação de :bi:`Address (Aux)`, **deve ser desabilitada**.
                * A criação de :bi:`Family (Aux)`, **deve ser habilitada**.

    #. :bi:`Address (Aux)`:

        #. Procurar pelo registro :bi:`Address` associado ao novo Endereço informado para a Pessoa utilizando um dos métodos:

            * :doc:`reregistration_workflow_010_050`
            * :doc:`reregistration_workflow_010_060`

        #. Um registro :bi:`Address (Aux)` deve ser criado a partir do registro :bi:`Address`, executando a Ação ":BI:`Address Associate to Address (Aux)`":

                * A criação de :bi:`Address (Aux)`, **deve ser habilitada**.

        #. Não será necessário qualquer ação de atualização do registro :bi:`Address (Aux)`.

    #. :bi:`Family (Aux)`:

        #. Abrir o registro :bi:`Family` associado ao registro :bi:`Person (Aux)`.

        #. Um registro :bi:`Family (Aux)` deve ser criado a partir do registro :bi:`Family`, executando a Ação ":BI:`Family Associate to Family (Aux)`":

                * A criação de :bi:`Family (Aux)`, **deve ser habilitada**.
                * A criação de :bi:`Address (Aux)`, **deve ser desabilitada**.

        #. O :bi:`(Reference) Address (Aux)` do registro :bi:`Family (Aux)` deve ser manualmente associado ao :bi:`Address (Aux)`.

        #. As informações de :bi:`Contact Information` devem ser subistituídas pelas informações de :bi:`Contact Information` do :bi:`(Reference) Address (Aux)`.

    #. :bi:`Person (Aux)`:

        #. O :bi:`(Reference) Address (Aux)` do registro :bi:`Person (Aux)` deve ser manualmente associado ao :bi:`Address (Aux)` do Endereço para o qual a Pessoa se mudou.

        #. As informações de :bi:`Contact Information` devem ser subistituídas pelas informações de :bi:`Contact Information` do :bi:`(Reference) Address (Aux)`.

        #. A :bi:`Family (Aux)` do registro :bi:`Person (Aux)` deve ser manualmente associado ao :bi:`Address (Aux)`.

.. toctree::
   :maxdepth: 2
   :caption: Procedimentos:
