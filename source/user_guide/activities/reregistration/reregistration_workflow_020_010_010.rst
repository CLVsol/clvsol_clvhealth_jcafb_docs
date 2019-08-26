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

    O **Cadastro** identificado contém os seguintes registros:

        * :bi:`Person`: relativo à Pessoa
        * :bi:`Address`: relativo ao Endereço da Pessoa
        * :green:`(Opcional)` :bi:`Family`: relativo à Família da Pessoa

Cadastro Auxiliar
-----------------

    O **Cadastro Auxiliar** criado contém os seguintes registros:

        * :bi:`Person (Aux)`
        * :bi:`Address (Aux)`
        * :green:`(Opcional)` :bi:`Family (Aux)``

Relacionamento entre os registros dos Cadastros
-----------------------------------------------

    * :green:`(Opcional)` :bi:`Family`:

        * *Address* » :bi:`Address`
        * *Contact Information* = Dados de Endereço de :bi:`Address` (:bi:`Contact Information`)

    * :bi:`Person`:

        * *Address* » :bi:`Address`
        * *Family* » :bi:`Family`
        * *Contact Information* = Dados de Endereço de :bi:`Address` (:bi:`Contact Information`)

    * :bi:`Address (Aux)`:

        * *Related Address* » :bi:`Address`
        * *Contact Information* = Dados de Endereço de :bi:`Address` (:bi:`Contact Information`)
        * Outros Dados = Outros Dados de :bi:`Address`

    * :green:`(Opcional)` :bi:`Family (Aux)`:

        * *Address* » :bi:`Address`
        * *Address (Aux)* » :bi:`Address (Aux)`
        * *Related Family* » :bi:`Family`
        * *Contact Information* = Dados de Endereço de :bi:`Address` (:bi:`Contact Information`)
        * Outros Dados = Outros Dados de :bi:`Family`

    * :bi:`Person (Aux)`:

        * *Address* » :bi:`Address`
        * *Address (Aux)* » :bi:`Address (Aux)`
        * *Family* » :bi:`Family`
        * *Family (Aux)* » :bi:`Family (Aux)`
        * *Related Person* » :bi:`Person`
        * *Contact Information* = Dados de Endereço de :bi:`Address` (:bi:`Contact Information`)
        * Outros Dados = Outros Dados de :bi:`Person`

Fluxo de Trabalho (*Workflow*)
------------------------------

    #. **Cadastro Auxiliar**:

        #. Procurar pelo registro :bi:`Person` associado à Pessoa utilizando um dos métodos:

            * :doc:`reregistration_workflow_010_010`
            * :doc:`reregistration_workflow_010_020`

        #. Confirmar que todos os dados dos registros :bi:`Person`, :bi:`Address` e :bi:`Family`, relacionados à Pessoa, serão mantidos.

        #. O **Cadastro Auxiliar** relacionado à Pessoa deve ser criado a partir do registro :bi:`Person`, executando a Ação ":BI:`Person (Aux) Associate to Family (Aux)`":

                * A criação de :bi:`Person (Aux)`, deve ser **habilitada**.
                * A criação de :bi:`Address (Aux)`, deve ser **habilitada**.
                * A criação de :bi:`Family (Aux)`, deve ser **habilitada**.

    #. Registro :bi:`Address (Aux)`:

        #. Não será necessário qualquer ação de atualização do registro :bi:`Address (Aux)`.

    #. Registro :bi:`Family (Aux)`:

        #. Não será necessário qualquer ação de atualização do registro :bi:`Family (Aux)`.

    #. Registro :bi:`Person (Aux)`:

        #. Não será necessário qualquer ação de atualização do registro :bi:`Person (Aux)`.

    O processamento deste *Workflow* é executado utilizando o procedimento ":doc:`reregistration_procedure_020_010_010`".

.. toctree::
   :maxdepth: 2
   :caption: Procedimentos:
