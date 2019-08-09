.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: [Pessoa já cadastrada] A Pessoa mudou-se para um Endereço **desconhecido**

==========================================================================
[Pessoa já cadastrada] A Pessoa mudou-se para um Endereço **desconhecido**
==========================================================================

.. _Cadastro Auxiliar (6):

Cadastro Auxiliar
-----------------

    O **Cadastro Auxiliar** criado automáticamente poderá ser composto pelas seguintes **Entidades (Aux)**:

        * :bi:`Person (Aux)`:

            * A criação de :bi:`Person (Aux)`, **deve ser habilitada**.

        * :bi:`Address (Aux)`:

            * A criação de :bi:`Address (Aux)`, **deve ser desabilitada**.

        * :bi:`Family (Aux)`:

            * A criação de :bi:`Family (Aux)`, **deve ser habilitada**.

    O relacionamento entre os diversos registros dos Cadastros será o seguinte (quando existirem os registros, como indicado anteriormente):

        * :bi:`Person (Aux)`: 

            * :bi:`Related Person` » :bi:`Person`
            * :bi:`(Reference) Address` » :bi:`Address`
            * :bi:`(Reference) Address (Aux)` » "**vazio**"
            * :bi:`Family` » :bi:`Family`
            * :bi:`Family (Aux)` » :bi:`Family (Aux)`
            * :bi:`Contact Information` = "informações que indiquem o desconhecimento do novo Endereço"
            * Outros Dados = Outros Dados do registro :bi:`Person`

        * :bi:`Address (Aux)`:

            * Registro **não disponível**

        * :bi:`Family (Aux)`:

            * :bi:`Related Family` » :bi:`Family`
            * :bi:`(Reference) Address` » :bi:`Address`
            * :bi:`(Reference) Address (Aux)` » "**vazio**"
            * :bi:`Contact Information` = "informações que indiquem o desconhecimento do novo Endereço"
            * Outros Dados = Outros Dados do registro :bi:`Family`

Criações/Atualizações
---------------------

    #. **Cadastro Auxiliar**:

        #. O **Cadastro Auxiliar** relacionado à Pessoa deve ser criado automaticamente conforme as condições descritas em ":ref:`Cadastro Auxiliar (6)`".

    #. :bi:`Address (Aux)`:

        * Registro **não disponível**

    #. :bi:`Family (Aux)`:

        #. O :bi:`(Reference) Address (Aux)` do registro :bi:`Family (Aux)` deve ser manualmente **excluído**.

        #. O :bi:`(Reference) Address` do registro :bi:`Family (Aux)` deve ser mantido.

        #. As informações de :bi:`Contact Information`  do registro :bi:`Family (Aux)` devem ser subistituídas por informações que indiquem o desconhecimento do novo Endereço.

    #. :bi:`Person (Aux)`:

        #. O :bi:`(Reference) Address (Aux)` do registro :bi:`Person (Aux)` deve ser manualmente **excluído**.

        #. O :bi:`(Reference) Address` do registro :bi:`Person (Aux)` deve ser mantido.

        #. As informações de :bi:`Contact Information`  do registro :bi:`Person (Aux)` devem ser subistituídas por informações que indiquem o desconhecimento do novo Endereço.

.. toctree::
   :maxdepth: 2
   :caption: Procedimentos:
