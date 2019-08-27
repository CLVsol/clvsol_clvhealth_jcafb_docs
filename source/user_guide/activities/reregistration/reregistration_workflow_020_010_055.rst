.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: A Pessoa mudou-se para um Endereço não cadastrado, sem a Família

================================================================
A Pessoa mudou-se para um Endereço não cadastrado, sem a Família
================================================================

Cadastro
--------

    O **Cadastro** identificado deverá conter os seguintes registros:

        * :bi:`Person`: relativo à Pessoa
        * :bi:`Address` :green:`(antigo)`: relativo ao antigo Endereço da Pessoa
        * :bi:`Family` :green:`(antiga)`: relativo à antiga Família da Pessoa

Cadastro Auxiliar
-----------------

    O **Cadastro Auxiliar** criado deverá conter os seguintes registros:

        * :bi:`Person (Aux)`
        * :bi:`Address (Aux)`
        * :bi:`Family (Aux)``

Relacionamento entre os registros dos Cadastros
-----------------------------------------------

    * :bi:`Family` :green:`(antiga)`:

        * *Address* » :bi:`Address` :green:`(antigo)`
        * *Contact Information* = Dados de Endereço de :bi:`Address` :green:`(antigo)`

    * :bi:`Person`:

        * *Address* » :bi:`Address` :green:`(antigo)`
        * *Family* » :bi:`Family` :green:`(antiga)`
        * *Contact Information* = Dados de Endereço de :bi:`Address` :green:`(antigo)`

    * :bi:`Address (Aux)`:

        * *Related Address* » **vazio**
        * *Contact Information* = Dados informados para o Endereço da Pessoa
        * Outros Dados = Outros Dados informados para o Endereço da Pessoa

    * :bi:`Family (Aux)`:

        * *Address* » **vazio**
        * *Address (Aux)* » :bi:`Address (Aux)`
        * *Related Family* » **vazio**
        * *Contact Information* = Dados de Endereço de :bi:`Address (Aux)`
        * Outros Dados = Outros Dados informados para a Família da Pessoa`

    * :bi:`Person (Aux)`:

        * *Address* » **vazio**
        * *Address (Aux)* » :bi:`Address (Aux)`
        * *Family* » **vazio**
        * *Family (Aux)* » :bi:`Family (Aux)`
        * *Related Person* » :bi:`Person`
        * *Contact Information* = Dados de Endereço de :bi:`Address (Aux)`
        * Outros Dados = Outros Dados de :bi:`Person`

Fluxo de Trabalho (*Workflow*)
------------------------------

    #. **Cadastro**:

        #. Procurar pelo registro :bi:`Person` associado à Pessoa utilizando um dos métodos:

            * :doc:`reregistration_workflow_010_010`
            * :doc:`reregistration_workflow_010_020`

        #. Confirmar que todos os dados do registro :bi:`Person`, relacionados à Pessoa, serão mantidos.

        #. Confirmar a mudança de Endereço da Pessoa.

        #. Confirmar a mudança de Família da Pessoa.

    #. **Cadastro**:

        #. Procurar pelo registro :bi:`Address` associado ao novo Endereço informado para a Pessoa utilizando um dos métodos:

            * :doc:`reregistration_workflow_010_050`

        **Observação 1**: Nenhum registro :bi:`Address` deverá ser encontrado.

        **Observação 2**: Nenhum registro :bi:`Address (Aux)` deverá ser encontrado, a menos que o novo Endereço já esteja em processo de recadastramento.

    #. *View* :bi:`Address (Aux)`:

        #. Criar manualmente um novo registro :bi:`Address (Aux)`, preenchido com as informações apresentadas para o novo Endereço da Pessoa.

    #. Registro :bi:`Address (Aux)`:

        #. Não será necessário qualquer outra ação de atualização do registro :bi:`Address (Aux)`.

    #. **Cadastro Auxiliar**:

        #. Os registros do  **Cadastro Auxiliar** relacionados à Pessoa devem ser criados a partir do registro :bi:`Person`, executando a Ação ":BI:`Person Associate to Person (Aux)`":

                * A criação de :bi:`Person (Aux)`, deve ser **habilitada**.
                * A criação de :bi:`Address (Aux)`, deve ser **desabilitada**.
                * A criação de :bi:`Family (Aux)`, deve ser **desabilitada**.

    #. Registro :bi:`Person (Aux)`:

        #. Remover do campo *Address* a associação ao registro :bi:`Address` :green:`(antigo)`.

        #. Associar o registro :bi:`Address (Aux)` ao campo *Address (Aux)*.

        #. Preencher os campos de *Contact Information* com os dados de Endereço do registro :bi:`Address (Aux)`.

    #. Registro :bi:`Person (Aux)`:

        #. Remover do campo *Family* a associação ao registro :bi:`Family` :green:`(antiga)`.

        #. Criar um novo registro :bi:`Family (Aux)`, executando a Ação ":bi:`Person (Aux) Associate to Family (Aux)`":

                * A criação de um registro :bi:`Family (Aux)`, deve ser **habilitada**.

    #. Registro :bi:`Family (Aux)`:

        #. Não será necessário qualquer ação de atualização do registro :bi:`Family (Aux)`.

    #. Registro :bi:`Person (Aux)`:

        #. Não será necessário qualquer ação de atualização adicional do registro :bi:`Person (Aux)`.

    O processamento deste *Workflow* é executado utilizando o procedimento ":doc:`reregistration_procedure_020_010_055`".

.. toctree::
   :maxdepth: 2
   :caption: Procedimentos:
