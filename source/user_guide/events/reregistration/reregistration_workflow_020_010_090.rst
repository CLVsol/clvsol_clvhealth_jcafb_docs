.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: [Pessoa já cadastrada] A Pessoa faleceu

=======================================
[Pessoa já cadastrada] A Pessoa faleceu
=======================================

.. _Cadastro Auxiliar (9):

Cadastro Auxiliar
-----------------

    O **Cadastro Auxiliar** criado poderá ser composto pelas seguintes **Entidades (Aux)**:

        * :bi:`Person (Aux)`:

            * A criação de :bi:`Person (Aux)`, **deve ser habilitada**.

        * :bi:`Address (Aux)`:

            * A criação de :bi:`Address (Aux)`, **deve ser desabilitada**.

        * :bi:`Family (Aux)`:

            * A criação de :bi:`Family (Aux)`, **deve ser desabilitada**.

    O relacionamento entre os diversos registros dos Cadastros será o seguinte:

        * :bi:`Person (Aux)`: 

            * :bi:`Related Person` » :bi:`Person`
            * :bi:`(Reference) Address` » :bi:`Address`
            * :bi:`(Reference) Address (Aux)` » "**vazio**"
            * :bi:`Family` » :bi:`Family`
            * :bi:`Family (Aux)` » :bi:`Family (Aux)`
            * :bi:`Contact Information` = **vazio**
            * Outros Dados = Outros Dados do registro :bi:`Person`

        * :bi:`Address (Aux)`:

            * Registro **não disponível**

        * :bi:`Family (Aux)`:

            * Registro **não disponível**

Criações/Atualizações
---------------------

    * **Cadastro Auxiliar**:

        #. O **Cadastro Auxiliar** relacionado à Pessoa deve ser criado automaticamente conforme as condições descritas em ":ref:`Cadastro Auxiliar (9)`".

    * :bi:`Address (Aux)`:

        * Registro **não disponível**

    * :bi:`Family (Aux)`:

        * Registro **não disponível**

    * :bi:`Person (Aux)`:

        #. As informações de :bi:`Contact Information` do registro :bi:`Person (Aux)` devem ser **excluídas**.

        #. :red:`(Precisa ser Modificado)` Indicar de alguma forma que a Pessoa faleceu.

.. toctree::
   :maxdepth: 2
   :caption: Procedimentos:
