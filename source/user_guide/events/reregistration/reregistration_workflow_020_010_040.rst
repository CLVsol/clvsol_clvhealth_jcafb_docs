.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: [Pessoa já cadastrada] A Pessoa mudou-se para um Endereço **já cadastrado**

===========================================================================
[Pessoa já cadastrada] A Pessoa mudou-se para um Endereço **já cadastrado**
===========================================================================

.. _Cadastro Auxiliar (4):

Cadastro Auxiliar
-----------------

    O **Cadastro Auxiliar** criado automáticamente poderá ser composto pelas seguintes **Entidades (Aux)**:

        * :bi:`Person (Aux)`:

            * A criação de :bi:`Person (Aux)`, **deve ser habilitada**.

        * :bi:`Address (Aux)`:

            * A criação de :bi:`Address (Aux)`, **deve ser desabilitada**.

                * Um registro :bi:`Address (Aux)` deverá ser **criado automaticamente** a partir do registro :bi:`Address` relacionado ao Endereço informado para a Pessoa.

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

        #. O **Cadastro Auxiliar** relacionado à Pessoa deve ser criado automaticamente conforme as condições descritas em ":ref:`Cadastro Auxiliar (4)`".

    #. :bi:`Address (Aux)`:

        #. Um registro :bi:`Address (Aux)` deverá ser **criado automaticamente** a partir do registro :bi:`Address` relacionado ao Endereço informado para a Pessoa.

        #. Não será necessário qualquer ação de atualização do registro :bi:`Address (Aux)` relacionado à Pessoa.

    #. :bi:`Family (Aux)`:

        #. O :bi:`(Reference) Address (Aux)` do registro :bi:`Family (Aux)` deve ser manualmente substituido pelo :bi:`Address (Aux)` do Endereço para o qual a Pessoa se mudou.

        #. O :bi:`(Reference) Address` do registro :bi:`Family (Aux)` deve ser mantido.

        #. As informações de :bi:`Contact Information` devem ser subistituídas pelas informações de :bi:`Contact Information` do :bi:`(Reference) Address (Aux)`.

    #. :bi:`Person (Aux)`:

        #. O :bi:`(Reference) Address (Aux)` do registro :bi:`Person (Aux)` deve ser manualmente substituido pelo :bi:`Address (Aux)` do Endereço para o qual a Pessoa se mudou.

        #. O :bi:`(Reference) Address` do registro :bi:`Person (Aux)` deve ser mantido.

        #. As informações de :bi:`Contact Information` devem ser subistituídas pelas informações de :bi:`Contact Information` do :bi:`(Reference) Address (Aux)`.

.. toctree::
   :maxdepth: 2
   :caption: Procedimentos:
