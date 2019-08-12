.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: [Pessoa não cadastrada] A Pessoa reside em um Endereço fora da comunidade atendida pela JCAFB

=============================================================================================
[Pessoa não cadastrada] A Pessoa reside em um Endereço fora da comunidade atendida pela JCAFB
=============================================================================================

.. _Cadastro Auxiliar (13):

Cadastro Auxiliar
-----------------

    O **Cadastro Auxiliar** criado poderá ser composto pelas seguintes **Entidades (Aux)**:

        * :bi:`Person (Aux)`:
        * :bi:`Address (Aux)`:
        * :bi:`Family (Aux)`:

    O relacionamento entre os diversos registros dos Cadastros será o seguinte:

        * :bi:`Person (Aux)`: 

            * :bi:`(Reference) Address` » **vazio**
            * :bi:`(Reference) Address (Aux)` » :bi:`Address (Aux)`
            * :bi:`Family` » **vazio**
            * :bi:`Family (Aux)` » **vazio**
            * :bi:`Related Person` » **vazio**
            * :bi:`Contact Information` = Dados do registro :bi:`Address (Aux)`
            * Outros Dados = Outros Dados coletadas para a Pessoa

        * :bi:`Address (Aux)`:

            * :bi:`Related Address` » **vazio**
            * :bi:`Contact Information` = Dados informados para o Endereço da Pessoa
            * Outros Dados = Outros Dados informados para o Endereço da Pessoa

        * :bi:`Family (Aux)`:

            * Registro **não disponível**

.. Fluxo de Trabalho (*Workflow*) (13):

Fluxo de Trabalho (*Workflow*)
------------------------------

    * **Cadastro Auxiliar**:

    #. *View* **Contatos** ou *View* :bi:`Persons`:

        #. Procurar pelo registro :bi:`Person` associado à Pessoa utilizando um dos métodos:

            * :doc:`reregistration_workflow_010_010`
            * :doc:`reregistration_workflow_010_020`

            **Observação**: Nenhum registro :bi:`Person` deverá ser encontrado, a menos que a nova Pessoa já esteja em processo de recadastramento.

    #. *View* :bi:`Address (Aux)`:

        #. Um registro :bi:`Address (Aux)` deverá ser **criado manualmente** a partir dos dados do Endereço informado para a Pessoa.

    #. Registro :bi:`Address (Aux)`:

        #. Não será necessário qualquer outra ação de atualização do registro :bi:`Address (Aux)`.

    #. *View* :bi:`Person (Aux)`:

        #. Um registro :bi:`Person (Aux)` deverá ser **criado manualmente** e preenchido com as informações informadas para a Pessoa, exceto as informaçôes de Endereço.

    #. Registro :bi:`Person (Aux)`:

        #. O :bi:`(Reference) Address (Aux)` do registro :bi:`Person (Aux)` deve ser manualmente associado ao :bi:`Address (Aux)` do Endereço informado para a Pessoa.

        #. As informações de :bi:`Contact Information` devem ser subistituídas pelas informações de :bi:`Contact Information` do :bi:`(Reference) Address (Aux)`.

.. toctree::
   :maxdepth: 2
   :caption: Itens Relacionados:
