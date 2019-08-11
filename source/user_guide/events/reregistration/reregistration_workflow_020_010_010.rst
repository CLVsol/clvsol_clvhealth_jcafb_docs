.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: [Pessoa já cadastrada] Todos os dados da Pessoa serão mantidos

======================================================================================
:red:`(Não Verificado)` [Pessoa já cadastrada] Todos os dados da Pessoa serão mantidos
======================================================================================

.. _Cadastro Auxiliar (1):

Cadastro Auxiliar
-----------------

    O **Cadastro Auxiliar** criado automáticamente poderá ser composto pelas seguintes **Entidades (Aux)**:

        * :bi:`Person (Aux)`:

            * A criação de :bi:`Person (Aux)`, **deve ser habilitada**.

        * :bi:`Address (Aux)`:

            * A criação de :bi:`Address (Aux)`, **deve ser habilitada**.

        * :bi:`Family (Aux)`:

            * A criação de :bi:`Family (Aux)`, **deve ser habilitada**.

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

.. Fluxo de Trabalho (*Workflow*) (1):

Fluxo de Trabalho (*Workflow*)
------------------------------

    #. **Cadastro Auxiliar**:

        #. Procurar pelo registro :bi:`Person` associado à Pessoa utilizando um dos métodos:

            * :doc:`reregistration_workflow_010_010`
            * :doc:`reregistration_workflow_010_020`

        #. O **Cadastro Auxiliar** relacionado à Pessoa deve ser criado a partir do registro :bi:`Person`, executando a Ação ":BI:`Person (Aux) Associate to Family (Aux)`":

                * A criação de :bi:`Person (Aux)`, **deve ser habilitada**.
                * A criação de :bi:`Address (Aux)`, **deve ser habilitada**.
                * A criação de :bi:`Family (Aux)`, **deve ser habilitada**.

    #. :bi:`Address (Aux)`:

        #. Não será necessário qualquer ação de atualização do registro :bi:`Address (Aux)`.

    #. :bi:`Family (Aux)`:

        #. Não será necessário qualquer ação de atualização do registro :bi:`Family (Aux)`.

    #. :bi:`Person (Aux)`:

        #. Não será necessário qualquer ação de atualização do registro :bi:`Person (Aux)`.

.. toctree::
   :maxdepth: 2
   :caption: Procedimentos:
