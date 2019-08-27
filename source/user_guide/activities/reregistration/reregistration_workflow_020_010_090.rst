.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: A Pessoa faleceu

=======================================
:red:`(Revisar)` A Pessoa faleceu
=======================================

.. _Cadastro Auxiliar (9):

Cadastro Auxiliar
-----------------

    O **Cadastro Auxiliar** criado poderá ser composto pelas seguintes **Entidades (Aux)**:

        * :bi:`Person (Aux)`:

    O relacionamento entre os diversos registros dos Cadastros será o seguinte:

        * :bi:`Person (Aux)`: 

            * :bi:`(Reference) Address` » **vazio**
            * :bi:`Family` » **vazio**
            * :bi:`(Reference) Address (Aux)` » **vazio**
            * :bi:`Family (Aux)` » **vazio**
            * :bi:`Related Person` » :bi:`Person`
            * :bi:`Contact Information` = **vazio**
            * Outros Dados = Outros Dados do registro :bi:`Person`

        * :bi:`Address (Aux)`:

            * Registro **não disponível**

        * :bi:`Family (Aux)`:

            * Registro **não disponível**

.. Fluxo de Trabalho (*Workflow*) (9):

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

    #. Registro :bi:`Person (Aux)`:

        #. O :bi:`(Reference) Address` do registro :bi:`Person (Aux)` deve ser manualmente removido.

        #. As informações de :bi:`Contact Information` do registro :bi:`Person (Aux)` devem ser **excluídas**.

        #. O :bi:`Family` do registro :bi:`Person (Aux)` deve ser manualmente removido.

        #. :red:`(Precisa ser Modificado)` Indicar de alguma forma que a Pessoa faleceu.

.. toctree::
   :maxdepth: 2
   :caption: Procedimentos:
