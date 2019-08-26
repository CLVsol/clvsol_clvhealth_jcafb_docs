.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: A Pessoa reside em um Endereço não cadastrado

=============================================
A Pessoa reside em um Endereço não cadastrado
=============================================

    Caso se opte por associar ao Endereço da Pessoa a uma Família, a Pessoa será associada a essa Família e os itens indicados como ":green:`(Opcional)`" deverão ser considerados.

    Caso se opte por não associar ao Endereço da Pessoa a uma Família, os itens indicados como ":green:`(Opcional)`" deverão ser desconsiderados.

Cadastro
--------

    Nenhum registro será identificado no **Cadastro**.

Cadastro Auxiliar
-----------------

    O **Cadastro Auxiliar** criado poderá conter os seguintes registros:

        * :bi:`Person (Aux)`
        * :bi:`Address (Aux)`
        * :green:`(Opcional)` :bi:`Family (Aux)`

Relacionamento entre os registros dos Cadastros
-----------------------------------------------

    * :bi:`Address (Aux)`:

        * *Related Address* » **vazio**
        * *Contact Information* = Dados informados para o Endereço da Pessoa
        * Outros Dados = Outros Dados informados para o Endereço da Pessoa

    * :green:`(Opcional)` :bi:`Family (Aux)`:

        * *Address* » **vazio**
        * *Address (Aux)* » :bi:`Address (Aux)`
        * *Related Family* » **vazio**
        * *Contact Information* = Dados de Endereço de :bi:`Address (Aux)`
        * Outros Dados = Outros Dados de :bi:`Family`

    * :bi:`Person (Aux)`:

        * *Address* » **vazio**
        * *Address (Aux)* » :bi:`Address (Aux)`
        * *Family* » **vazio**
        * :green:`(Opcional)` *Family (Aux)* » :bi:`Family (Aux)`
        * *Related Person* » **vazio**
        * *Contact Information* = Dados de Endereço de :bi:`Address (Aux)`
        * Outros Dados = Outros Dados informados para a Pessoa

Fluxo de Trabalho (*Workflow*)
------------------------------

    #. **Cadastro**:

        #. Procurar pelo(s) registro(s) :bi:`Person` e/ou :bi:`Person (Aux)` associado(s) à Pessoa utilizando o método:

            * :doc:`reregistration_workflow_010_010`

        **Observação 1**: Nenhum registro :bi:`Person` deverá ser encontrado.

        **Observação 2**: Nenhum registro :bi:`Person (Aux)` deverá ser encontrado, a menos que a nova Pessoa já esteja em processo de recadastramento.

    #. **Cadastro**:

        #. Procurar pelo registro :bi:`Address` associado ao Endereço informado para a Pessoa utilizando um dos métodos:

            * :doc:`reregistration_workflow_010_050`

        **Observação 1**: Nenhum registro :bi:`Address` deverá ser encontrado.

        **Observação 2**: Nenhum registro :bi:`Address (Aux)` deverá ser encontrado, a menos que o novo Endereço já esteja em processo de recadastramento.

    #. *View* :bi:`Address (Aux)`:

        #. Criar manualmente um novo registro :bi:`Address (Aux)`, preenchido com as informações apresentadas para o Endereço da Pessoa.

    #. Registro :bi:`Address (Aux)`:

        #. Não será necessário qualquer outra ação de atualização do registro :bi:`Address (Aux)`.

    #. *View* :bi:`Person (Aux)`:

        #. Criar manualmente um novo registro :bi:`Person (Aux)`, preenchido com as informações apresentadas para a Pessoa, exceto as informaçôes do Endereço.

    #. Registro :bi:`Person (Aux)`:

        #. Associar o registro :bi:`Address (Aux)` criado ao campo *Address (Aux)*.

        #. Preencher os campos de *Contact Information* com os dados de Endereço do registro :bi:`Address (Aux)`.

    #. :green:`(Opcional)` Registro :bi:`Person (Aux)`:

        #. Criar um novo registro :bi:`Family (Aux)`, executando a Ação ":bi:`Person (Aux) Associate to Family (Aux)`":

                * A criação de um registro :bi:`Family (Aux)`, deve ser **habilitada**.

    #. :green:`(Opcional)` Registro :bi:`Family (Aux)`:

        #. Não será necessário qualquer ação de atualização do registro :bi:`Family (Aux)`.

    O processamento deste *Workflow* é executado utilizando o procedimento ":doc:`reregistration_procedure_020_020_020`".

.. toctree::
   :maxdepth: 2
   :caption: Itens Relacionados:
