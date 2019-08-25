.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: Todos os dados da Pessoa serão mantidos

=======================================
Todos os dados da Pessoa serão mantidos
=======================================

Cadastro
--------

    O **Cadastro** identificado poderá ser composto pelos seguintes registros:

        * :bi:`Person`: registro :bi:`Person` associado à Pessoa
        * :bi:`Address`: registro :bi:`Address` associado ao Endereço da Pessoa
        * :green:`(Opcional)` :bi:`Family`: registro :bi:`Family` associado à Família da Pessoa

Cadastro Auxiliar
-----------------

    O **Cadastro Auxiliar** criado automáticamente poderá ser composto pelos seguintes registros:

        * :bi:`Person (Aux)`
        * :bi:`Address (Aux)`
        * :green:`(Opcional)` :bi:`Family (Aux)``

    O relacionamento entre os registros dos Cadastros será o seguinte:

        * Registro :bi:`Address (Aux)`:

            * :bi:`Related Address` » registro :bi:`Address`
            * :bi:`Contact Information` = Dados de Endereço do :bi:`Contact Information` do registro :bi:`Address`
            * Outros Dados = Outros Dados do registro :bi:`Address`

        * :green:`(Opcional)` Registro :bi:`Family (Aux)`:

            * :bi:`Address` » registro:bi:`Address`
            * :bi:`Address (Aux)` » registro :bi:`Address (Aux)`
            * :bi:`Related Family` » registro :bi:`Family`
            * :bi:`Contact Information` = Dados de Endereço do :bi:`Contact Information` do registro :bi:`Address`
            * Outros Dados = Outros Dados do registro :bi:`Family`

        * Registro :bi:`Person (Aux)`: 

            * :bi:`Address` » registro :bi:`Address`
            * :bi:`Address (Aux)` » registro :bi:`Address (Aux)`
            * :bi:`Family` » registro :bi:`Family`
            * :bi:`Family (Aux)` » registro :bi:`Family (Aux)`
            * :bi:`Related Person` » registro :bi:`Person`
            * :bi:`Contact Information` = Dados de Endereço do :bi:`Contact Information` do registro :bi:`Address`
            * Outros Dados = Outros Dados do registro :bi:`Person`

.. Fluxo de Trabalho (*Workflow*) (1):

Fluxo de Trabalho (*Workflow*)
------------------------------

    #. **Cadastro Auxiliar**:

        #. Procurar pelo registro :bi:`Person` associado à Pessoa utilizando um dos métodos:

            * :doc:`reregistration_workflow_010_010`
            * :doc:`reregistration_workflow_010_020`

        #. O **Cadastro Auxiliar** relacionado à Pessoa deve ser criado a partir do registro :bi:`Person`, executando a Ação ":BI:`Person (Aux) Associate to Family (Aux)`":

                * A criação de :bi:`Person (Aux)`, deve ser **habilitada**.
                * A criação de :bi:`Address (Aux)`, deve ser **habilitada**.
                * A criação de :bi:`Family (Aux)`, deve ser **habilitada**.

    #. :bi:`Address (Aux)`:

        #. Não será necessário qualquer ação de atualização do registro :bi:`Address (Aux)`.

    #. :bi:`Family (Aux)`:

        #. Não será necessário qualquer ação de atualização do registro :bi:`Family (Aux)`.

    #. :bi:`Person (Aux)`:

        #. Não será necessário qualquer ação de atualização do registro :bi:`Person (Aux)`.

    O processamento deste *Workflow* é executado utilizando o procedimento ":doc:`reregistration_procedure_020_010_010`".

.. toctree::
   :maxdepth: 2
   :caption: Procedimentos:
