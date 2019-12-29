.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: A Pessoa mudou-se para Endereço desconhecido

============================================
A Pessoa mudou-se para Endereço desconhecido
============================================

Cadastro
--------

    O **Cadastro** identificado deverá conter os seguintes registros:

        * :bi:`Person`: relativo à Pessoa
        * :bi:`Address` :green:`(antigo)`: relativo ao antigo Endereço da Pessoa
        * :bi:`Family`: relativo à Família da Pessoa

Cadastro Auxiliar
-----------------

    O **Cadastro Auxiliar** criado deverá conter os seguintes registros:

        * :bi:`Person (Aux)`

Relacionamento entre os registros dos Cadastros
-----------------------------------------------

    * :bi:`Family`:

        * *Address* » :bi:`Address` :green:`(antigo)`
        * *Contact Information* = Dados de Endereço de :bi:`Address` :green:`(antigo)`

    * :bi:`Person`:

        * *Address* » :bi:`Address` :green:`(antigo)`
        * *Family* » :bi:`Family`
        * *Contact Information* = Dados de Endereço de :bi:`Address` :green:`(antigo)`

    * :bi:`Person (Aux)`:

        * *Address* » **vazio**
        * *Address (Aux)* » **vazio**
        * *Family* » :bi:`Family`
        * *Related Person* » :bi:`Person`
        * *Contact Information* = Dados com informações que indiquem o desconhecimento do novo Endereço da Pessoa
        * Outros Dados = Outros Dados de :bi:`Person`

Fluxo de Trabalho (*Workflow*)
------------------------------

    #. **Cadastro**:

        #. Procurar pelo registro :bi:`Person` associado à Pessoa utilizando um dos métodos:

            * :doc:`reregistration_workflow_010_010`
            * :doc:`reregistration_workflow_010_020`

        #. Confirmar que todos os dados do registro :bi:`Person`, relacionados à Pessoa, serão mantidos.

        #. Confirmar que todos os dados do registro :bi:`Family`, relacionados à Família da Pessoa, serão mantidos.

    #. **Cadastro Auxiliar**:

        #. Os registros do  **Cadastro Auxiliar** relacionados à Pessoa devem ser criados a partir do registro :bi:`Person`, executando a Ação ":BI:`Person Associate to Person (Aux)`":

                * A criação de :bi:`Person (Aux)`, deve ser **habilitada**.
                * A criação de :bi:`Address (Aux)`, deve ser **desabilitada**.

    #. Registro :bi:`Person (Aux)`:

        #. Remover do campo *Address* a associação ao registro :bi:`Address` :green:`(antigo)`.

        #. Preencher os campos de *Contact Information* com informações que indiquem o desconhecimento do novo Endereço da Pessoa.

    #. Registro :bi:`Person (Aux)`:

        #. Não será necessário qualquer ação de atualização adicional do registro :bi:`Person (Aux)`.

    O processamento deste *Workflow* é executado utilizando o procedimento ":doc:`reregistration_procedure_020_010_060`".

.. toctree::
   :maxdepth: 2
   :caption: Procedimentos:
