.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: A Pessoa faleceu

================
A Pessoa faleceu
================

    Caso **exista uma Família** associada ao Endereço da Pessoa, os itens indicados como ":green:`(Opcional)`" deverão ser considerados.

    Caso **não exista uma Família** associada ao Endereço da Pessoa, os itens indicados como ":green:`(Opcional)`" deverão ser desconsiderados.

Cadastro
--------

    O **Cadastro** identificado poderá conter os seguintes registros:

        * :bi:`Person`: relativo à Pessoa
        * :bi:`Address`: relativo ao Endereço da Pessoa
        * :green:`(Opcional)` :bi:`Family`: relativo à Família da Pessoa

Cadastro Auxiliar
-----------------

    O **Cadastro Auxiliar** criado poderá conter os seguintes registros:

        * :bi:`Person (Aux)`

Relacionamento entre os registros dos Cadastros
-----------------------------------------------

    * :green:`(Opcional)` :bi:`Family`:

        * *Address* » :bi:`Address`
        * *Contact Information* = Dados de Endereço de :bi:`Address`

    * :bi:`Person`:

        * *Address* » :bi:`Address`
        * :green:`(Opcional)` *Family* » :bi:`Family`
        * *Contact Information* = Dados de Endereço de :bi:`Address`

    * :bi:`Person (Aux)`:

        * *Address* » **vazio**
        * *Address (Aux)* » **vazio**
        * :green:`(Opcional)` *Family* » **vazio**
        * :green:`(Opcional)` *Family (Aux)* » **vazio**
        * *Related Person* » :bi:`Person`
        * *Contact Information* = **vazio**
        * Outros Dados = Outros Dados de :bi:`Person`

Fluxo de Trabalho (*Workflow*)
------------------------------

    #. **Cadastro**:

        #. Procurar pelo registro :bi:`Person` associado à Pessoa utilizando um dos métodos:

            * :doc:`reregistration_workflow_010_010`
            * :doc:`reregistration_workflow_010_020`

        #. Confirmar que todos os dados do registro :bi:`Person`, relacionados à Pessoa, serão mantidos.

        #. Confirmar que todos os dados do registro :bi:`Address`, relacionados ao Endereço da Pessoa, serão mantidos.

        #. :green:`(Opcional)` Confirmar que todos os dados do registro :bi:`Family`, relacionados à Família da Pessoa, serão mantidos.

    #. **Cadastro Auxiliar**:

        #. Os registros do  **Cadastro Auxiliar** relacionados à Pessoa devem ser criados a partir do registro :bi:`Person`, executando a Ação ":BI:`Person (Aux) Associate to Family (Aux)`":

                * A criação de :bi:`Person (Aux)`, deve ser **habilitada**.
                * A criação de :bi:`Address (Aux)`, deve ser **desabilitada**.
                * A criação de :bi:`Family (Aux)`, deve ser **desabilitada**.

    #. Registro :bi:`Person (Aux)`:

        #. Remover do campo *Address* a associação ao registro :bi:`Address`.

        #. Excluir as informações de *Contact Information*.

        #. :green:`(Opcional)` Remover do campo *Family* a associação ao registro :bi:`Family`.

        #. Indicar de alguma forma que a Pessoa faleceu.

    O processamento deste *Workflow* é executado utilizando o procedimento ":doc:`reregistration_procedure_020_010_090`".

.. toctree::
   :maxdepth: 2
   :caption: Procedimentos:
