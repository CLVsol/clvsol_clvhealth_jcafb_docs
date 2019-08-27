.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: Atualização de dados Address do Contact Information da Pessoa, não caracterizando uma mudança de Endereço

====================================================================================================================================
:red:`(Revisar)` Atualização de dados *Address* do *Contact Information* da Pessoa, não caracterizando uma mudança de Endereço
====================================================================================================================================

Os dados :bi:`Address` do :bi:`Contact Information` são compartilhados por todas as Entidades do **Cadastro** (:bi:`Person`, :bi:`Address` e :bi:`Family`) e do **Cadastro Auxiliar** (:bi:`Person (Aux)`, :bi:`Address (Aux)` e :bi:`Family (Aux)`), descrevendo o Endereço dessas Entidades.

Atualizações não caracterizando uma mudança de Endereço são aquelas que corrigem e/ou complementam a descrição do Endereço sem alterá-lo.

No contexto do Recadastramento, essas atualizações devem ser aplicadas manualmente no regitro :bi:`Address (Aux)` e posteriormente replicadas nos registros :bi:`Family (Aux)` e :bi:`Person (Aux)`.

.. _Cadastro Auxiliar (3):

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

.. Fluxo de Trabalho (*Workflow*) (3):

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

        #. As atualizações dos dados :bi:`Address` do :bi:`Contact Information` da Pessoa devem ser aplicadas manualmente nos campos :bi:`Address` do :bi:`Contact Information` do registro :bi:`Address (Aux)`.

    #. :bi:`Family (Aux)`:

        #. Os dados :bi:`Address` do :bi:`Contact Information` do registro :bi:`Family (Aux)` devem ser replicados dos dados :bi:`Address` do :bi:`Contact Information` do :bi:`(Reference) Address (Aux)`.

    #. :bi:`Person (Aux)`:

        #. Os dados :bi:`Address` do :bi:`Contact Information` do registro :bi:`Person (Aux)` devem ser replicados dos dados :bi:`Address` do :bi:`Contact Information` do :bi:`(Reference) Address (Aux)`.

.. toctree::
   :maxdepth: 2
   :caption: Procedimentos:
