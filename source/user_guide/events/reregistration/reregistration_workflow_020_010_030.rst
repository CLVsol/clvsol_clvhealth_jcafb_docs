.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: [Pessoa já cadastrada] Atualização de dados de Contato da Pessoa exceto mudança de Endereço

===========================================================================================
[Pessoa já cadastrada] Atualização de dados de Contato da Pessoa exceto mudança de Endereço
===========================================================================================

.. _Cadastro Auxiliar (3):

Cadastro Auxiliar
-----------------

    O **Cadastro Auxiliar** criado automáticamente poderá ser composto pelas seguintes **Entidades (Aux)**:

        * :bi:`Person (Aux)`:

            * A criação de :bi:`Person (Aux)`, **deve ser habilitada**.

        * :bi:`Address (Aux)`:

            * A criação de :bi:`Address (Aux)`, **deve ser habilitada**.

        * :bi:`Family (Aux)`:

            * A criação de :bi:`Family (Aux)`, **deve ser habilitada**.

    O relacionamento entre os diversos registros dos Cadastros será o seguinte (quando existirem os registros, como indicado anteriormente):

        * :bi:`Person (Aux)`: 

            * :bi:`Related Person` » :bi:`Person`
            * :bi:`(Reference) Address` » :bi:`Address`
            * :bi:`(Reference) Address (Aux)` » :bi:`Address (Aux)`
            * :bi:`Family` » :bi:`Family`
            * :bi:`Family (Aux)` » :bi:`Family (Aux)`
            * :bi:`Contact Information` = Dados do registro :bi:`Address`
            * Outros Dados = Outros Dados do registro :bi:`Person`

        * :bi:`Address (Aux)`:

            * :bi:`Related Address` » :bi:`Address`
            * :bi:`Contact Information` = Dados do registro :bi:`Address`
            * Outros Dados = Outros Dados do registro :bi:`Address`

        * :bi:`Family (Aux)`:

            * :bi:`Related Family` » :bi:`Family`
            * :bi:`(Reference) Address` » :bi:`Address`
            * :bi:`(Reference) Address (Aux)` » :bi:`Address (Aux)`
            * :bi:`Contact Information` = Dados do registro :bi:`Address`
            * Outros Dados = Outros Dados do registro :bi:`Family`

Atualizações
------------

    #. **Cadastro Auxiliar**:

        #. O **Cadastro Auxiliar** relacionado à Pessoa deve ser criado automaticamente conforme as condições descritas em ":ref:`Cadastro Auxiliar (3)`".

    #. :bi:`Address (Aux)`:

        #. As atualizações de dados de :bi:`Contact Information` da Pessoa devem ser aplicadas manualmente no :bi:`Contact Information`do registro :bi:`Address (Aux)`.

    #. :bi:`Family (Aux)`:

        #. As informações de :bi:`Contact Information` do registro :bi:`Family (Aux)` devem ser subistituídas pelas informações de :bi:`Contact Information` do :bi:`(Reference) Address (Aux)`.

    #. :bi:`Person (Aux)`:

        #. As informações de :bi:`Contact Information` do registro :bi:`Person (Aux)` devem ser subistituídas pelas informações de :bi:`Contact Information` do :bi:`(Reference) Address (Aux)`.

.. toctree::
   :maxdepth: 2
   :caption: Procedimentos:
