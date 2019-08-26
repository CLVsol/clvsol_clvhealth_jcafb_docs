.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: Atualização de dados relativos à Pessoa não relacionados ao Endereço, à Família ou às Relações Familiares

=========================================================================================================
Atualização de dados relativos à Pessoa não relacionados ao Endereço, à Família ou às Relações Familiares
=========================================================================================================

Os dados não relacionados ao Endereço, à Família ou às Relações Familiares englobam todos os dados do registro :bi:`Person` relacionado à Pessoa, **exceto**:

    * :bi:`Address`

    * :bi:`Family`

    * **Relações Familiares**:

        * :bi:`Spouse`
        * :bi:`Father`
        * :bi:`Mother`
        * :bi:`Responsible`
        * :bi:`Caregiver`

No contexto do Recadastramento, essas atualizações devem ser aplicadas manualmente no regitro :bi:`Person (Aux)`.

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
        * Outros Dados = Outros Dados de :bi:`Person`, acrescidos das atualizações de dados relativas à Pessoa

Fluxo de Trabalho (*Workflow*)
------------------------------

    #. **Cadastro Auxiliar**:

        #. Procurar pelo registro :bi:`Person` associado à Pessoa utilizando um dos métodos:

            * :doc:`reregistration_workflow_010_010`
            * :doc:`reregistration_workflow_010_020`

        #. Confirmar a necessidade de atualização de dados do registro :bi:`Person` relacionado à Pessoa não relacionados ao Endereço, à Família ou às Relações Familiares.

        #. Confirmar também que todos os dados dos registros :bi:`Address` e :bi:`Family`, relacionados à Pessoa, serão mantidos.

        #. O **Cadastro Auxiliar** relacionado à Pessoa deve ser criado a partir do registro :bi:`Person`, executando a Ação ":BI:`Person (Aux) Associate to Family (Aux)`":

                * A criação de :bi:`Person (Aux)`, deve ser **habilitada**.
                * A criação de :bi:`Address (Aux)`, deve ser **habilitada**.
                * A criação de :bi:`Family (Aux)`, deve ser **habilitada**.

    #. :bi:`Address (Aux)`:

        #. Não será necessário qualquer ação de atualização do registro :bi:`Address (Aux)`.

    #. :bi:`Family (Aux)`:

        #. Não será necessário qualquer ação de atualização do registro :bi:`Family (Aux)`.

    #. :bi:`Person (Aux)`:

        #. As atualizações necessárias devem ser aplicadas diretamente no registro :bi:`Person (Aux)`.

    O processamento deste *Workflow* é executado utilizando o procedimento ":doc:`reregistration_procedure_020_010_020`".

.. toctree::
   :maxdepth: 2
   :caption: Procedimentos:
