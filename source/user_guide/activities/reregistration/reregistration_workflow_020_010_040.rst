.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: A Pessoa mudou-se para Endereço já cadastrado, juntamente com a Família

=======================================================================
A Pessoa mudou-se para Endereço já cadastrado, juntamente com a Família
=======================================================================

Cadastro
--------

    O **Cadastro** identificado deverá conter os seguintes registros:

        * :bi:`Person`: relativo à Pessoa
        * :bi:`Address` :green:`(antigo)`: relativo ao antigo Endereço da Pessoa
        * :bi:`Address` :green:`(novo)`: relativo ao novo Endereço da Pessoa
        * :bi:`Family`: relativo à Família da Pessoa

Cadastro Auxiliar
-----------------

    O **Cadastro Auxiliar** criado deverá conter os seguintes registros:

        * :bi:`Person (Aux)`
        * :bi:`Address (Aux)`
        * :bi:`Family (Aux)``

Relacionamento entre os registros dos Cadastros
-----------------------------------------------

    * :bi:`Family`:

        * *Address* » :bi:`Address` :green:`(antigo)`
        * *Contact Information* = Dados de Endereço de :bi:`Address` :green:`(antigo)`

    * :bi:`Person`:

        * *Address* » :bi:`Address` :green:`(antigo)`
        * *Family* » :bi:`Family`
        * *Contact Information* = Dados de Endereço de :bi:`Address` :green:`(antigo)`

    * :bi:`Address (Aux)`:

        * *Related Address* » :bi:`Address` :green:`(novo)`
        * *Contact Information* = Dados de Endereço de :bi:`Address` :green:`(novo)`
        * Outros Dados = Outros Dados de :bi:`Address` :green:`(novo)`

    * :bi:`Family (Aux)`:

        * *Address* » :bi:`Address` :green:`(novo)`
        * *Address (Aux)* » :bi:`Address (Aux)`
        * *Related Family* » :bi:`Family`
        * *Contact Information* = Dados de Endereço de :bi:`Address` :green:`(novo)`
        * Outros Dados = Outros Dados de :bi:`Family`

    * :bi:`Person (Aux)`:

        * *Address* » :bi:`Address` :green:`(novo)`
        * *Address (Aux)* » :bi:`Address (Aux)`
        * *Family* » :bi:`Family`
        * *Family (Aux)* » :bi:`Family (Aux)`
        * *Related Person* » :bi:`Person`
        * *Contact Information* = Dados de Endereço de :bi:`Address` :green:`(novo)`
        * Outros Dados = Outros Dados de :bi:`Person`

Fluxo de Trabalho (*Workflow*)
------------------------------

    #. **Cadastro**:

        #. Procurar pelo registro :bi:`Person` associado à Pessoa utilizando um dos métodos:

            * :doc:`reregistration_workflow_010_010`
            * :doc:`reregistration_workflow_010_020`

        #. Confirmar que todos os dados do registro :bi:`Person`, relacionados à Pessoa, serão mantidos.

        #. Confirmar que todos os dados do registro :bi:`Family`, relacionados à Família da Pessoa, serão mantidos.

    #. **Cadastro**:

        #. Procurar pelo registro :bi:`Address` :green:`(novo)` associado ao novo Endereço informado para a Pessoa utilizando um dos métodos:

            * :doc:`reregistration_workflow_010_050`
            * :doc:`reregistration_workflow_010_060`

        #. Confirmar que todos os dados do registro :bi:`Address` :green:`(novo)` serão mantidos.

    #. **Cadastro Auxiliar**:

        #. Os registros do  **Cadastro Auxiliar** relacionados à Pessoa devem ser criados a partir do registro :bi:`Person`, executando a Ação ":BI:`Person Associate to Person (Aux)`":

                * A criação de :bi:`Person (Aux)`, deve ser **habilitada**.
                * A criação de :bi:`Address (Aux)`, deve ser **desabilitada**.
                * A criação de :bi:`Family (Aux)`, deve ser **desabilitada**.

    #. Registro :bi:`Person (Aux)`:

        #. Remover do campo *Address* a associação ao registro :bi:`Address` :green:`(antigo)`.

        #. Associar o registro :bi:`Address` :green:`(novo)` ao campo *Address*.

    #. Registro :bi:`Person (Aux)`:

        #. Criar um novo registro :bi:`Address (Aux)`, executando a Ação ":bi:`Person (Aux) Associate to Address (Aux)`":

            * A criação de um registro :bi:`Address (Aux)`, deve ser **habilitada**.

    #. Registro :bi:`Address (Aux)`:

        #. Não será necessário qualquer ação de atualização do registro :bi:`Address (Aux)`.

    #. Registro :bi:`Person (Aux)`:

        #. Criar um novo registro :bi:`Family (Aux)`, executando a Ação ":bi:`Person (Aux) Associate to Family (Aux)`":

                * A criação de :bi:`Family (Aux)`, deve ser **habilitada**.

    #. Registro :bi:`Family (Aux)`:

        #. Não será necessário qualquer ação de atualização do registro :bi:`Family (Aux)`.

    #. Registro :bi:`Person (Aux)`:

        #. Não será necessário qualquer ação de atualização adicional do registro :bi:`Person (Aux)`.

    O processamento deste *Workflow* é executado utilizando o procedimento ":doc:`reregistration_procedure_020_010_040`".

.. toctree::
   :maxdepth: 2
   :caption: Procedimentos:
