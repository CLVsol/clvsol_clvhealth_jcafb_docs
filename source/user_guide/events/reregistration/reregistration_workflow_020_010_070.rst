.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: [Pessoa já cadastrada] A Pessoa mudou-se para um Endereço fora da comunidade atendida pela JCAFB, permanecendo na mesma Família

===================================================================================================================================
[Pessoa já cadastrada] A Pessoa mudou-se para um Endereço **fora da comunidade** atendida pela JCAFB, permanecendo na mesma Família
===================================================================================================================================

.. _Cadastro Auxiliar (7):

Cadastro Auxiliar
-----------------

    O **Cadastro Auxiliar** criado poderá ser composto pelas seguintes **Entidades (Aux)**:

        * :bi:`Person (Aux)`:
        * :bi:`Address (Aux)`:
        * :bi:`Family (Aux)`:

    O relacionamento entre os diversos registros dos Cadastros será o seguinte:

        * :bi:`Person (Aux)`: 

            * :bi:`(Reference) Address` » **vazio**
            * :bi:`Family` » :bi:`Family`
            * :bi:`(Reference) Address (Aux)` » :bi:`Address (Aux)`
            * :bi:`Family (Aux)` » :bi:`Family (Aux)`
            * :bi:`Related Person` » :bi:`Person`
            * :bi:`Contact Information` = Dados do registro :bi:`Address (Aux)`
            * Outros Dados = Outros Dados do registro :bi:`Person`

        * :bi:`Address (Aux)`:

            * :bi:`Related Address` » **vazio**
            * :bi:`Contact Information` = Dados com informações que indiquem o novo Endereço fora da comunidade
            * Outros Dados = **sem informações**

        * :bi:`Family (Aux)`:

            * :bi:`Related Family` » :bi:`Family`
            * :bi:`(Reference) Address` » :bi:`Address`
            * :bi:`(Reference) Address (Aux)` » :bi:`Address (Aux)`
            * :bi:`Contact Information` = Dados do registro :bi:`Address (Aux)`
            * Outros Dados = Outros Dados do registro :bi:`Family`

.. Fluxo de Trabalho (*Workflow*) (7):

Fluxo de Trabalho (*Workflow*)
------------------------------

    #. *View* **Contatos** ou *View* :bi:`Persons`:

        #. Procurar pelo registro :bi:`Person` associado à Pessoa utilizando um dos métodos:

            * :doc:`reregistration_workflow_010_010`
            * :doc:`reregistration_workflow_010_020`

        #. O **Cadastro Auxiliar** relacionado à Pessoa deve ser criado a partir do registro :bi:`Person`, executando a Ação ":bi:`Person (Aux) Associate to Family (Aux)`":

                * A criação de :bi:`Person (Aux)`, deve ser **habilitada**.
                * A criação de :bi:`Address (Aux)`, deve ser **desabilitada**.
                * A criação de :bi:`Family (Aux)`, deve ser **desabilitada**.

    #. Registro :bi:`Address (Aux)`:

        #. Um registro :bi:`Address (Aux)` deverá ser **criado manualmente** com informações que que indiquem o novo Endereço fora da comunidade.

        #. Não será necessário qualquer outra ação de atualização do registro :bi:`Address (Aux)` relacionado à Pessoa.

    #. Registro :bi:`Person (Aux)`:

        #. O :bi:`(Reference) Address` do registro :bi:`Person (Aux)` deve ser manualmente removido.

        #. O :bi:`(Reference) Address (Aux)` do registro :bi:`Person (Aux)` deve ser manualmente associado ao registro :bi:`Address (Aux)` criado.

        #. As informações de :bi:`Address` do :bi:`Contact Information` do registro :bi:`Person (Aux)` devem ser substituídas pelas informações de :bi:`Address` do :bi:`Contact Information` de :bi:`(Reference) Address (Aux)`.

        #. Um registro :bi:`Family (Aux)` deve ser criado a partir do registro :bi:`Person (Aux)`, executando a Ação ":bi:`Person (Aux) Associate to Family (Aux)`":

                * A criação de :bi:`Family (Aux)`, deve ser **habilitada**.

    #. Registro :bi:`Family (Aux)`:

        #. Não será necessário qualquer ação de atualização do registro :bi:`Family (Aux)`.

    #. Registro :bi:`Person (Aux)`:

        #. Não será necessário qualquer ação de atualização adicional do registro :bi:`Person (Aux)`.

.. toctree::
   :maxdepth: 2
   :caption: Procedimentos:
