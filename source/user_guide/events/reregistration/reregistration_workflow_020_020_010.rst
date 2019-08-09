.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: [Pessoa não cadastrada] A Pessoa reside em um Endereço já cadastrado

========================================================================
[Pessoa não cadastrada] A Pessoa reside em um Endereço **já cadastrado**
========================================================================

.. _Cadastro Auxiliar (10):

Cadastro Auxiliar
-----------------

    O **Cadastro Auxiliar** criado poderá ser composto pelas seguintes **Entidades (Aux)**:

        * :bi:`Person (Aux)`:

            * Um registro :bi:`Person (Aux)` deverá ser **criado manualmente** e preenchido com as informações coletadas para a Pessoa.

        * :bi:`Address (Aux)`:

            * Um registro :bi:`Address (Aux)` deverá ser **criado automaticamente** a partir do registro :bi:`Address` relacionado ao Endereço informado para a Pessoa.

        * :bi:`Family (Aux)`:

            * Um registro :bi:`Family (Aux)` deverá ser **criado automaticamente** a partir do registro :bi:`Family` relacionada ao Endereço informado para a Pessoa.

    O relacionamento entre os diversos registros dos Cadastros será o seguinte:

        * :bi:`Person (Aux)`: 

            * :bi:`Related Person` » **vazio**
            * :bi:`(Reference) Address` **vazio**
            * :bi:`(Reference) Address (Aux)` » :bi:`Address (Aux)`
            * :bi:`Family` » **vazio**
            * :bi:`Family (Aux)` » :bi:`Family (Aux)`
            * :bi:`Contact Information` = Dados do registro :bi:`Address`
            * Outros Dados = Outros Dados coletadas para a Pessoa

        * :bi:`Address (Aux)`:

            * :bi:`Related Address` » :bi:`Address`
            * :bi:`Contact Information` = Dados do registro :bi:`Address`
            * Outros Dados = Outros Dados do registro :bi:`Address`

        * :bi:`Family (Aux)`:

            * :bi:`Related Family` » **vazio**
            * :bi:`(Reference) Address` » :bi:`Address`
            * :bi:`(Reference) Address (Aux)` » :bi:`Address (Aux)`
            * :bi:`Contact Information` = Dados do registro :bi:`Address`
            * Outros Dados = Outros Dados do registro :bi:`Family`

Atualizações
------------

    * **Cadastro Auxiliar**:

        #. O **Cadastro Auxiliar** relacionado à Pessoa deve ser criado manualmente conforme as condições descritas em ":ref:`Cadastro Auxiliar (10)`".

    * :bi:`Address (Aux)`:

        #. Um registro :bi:`Address (Aux)` deverá ser **criado automaticamente** a partir do registro :bi:`Address` relacionado ao Endereço informado para a Pessoa.

        #. Não será necessário qualquer ação de atualização do registro :bi:`Address (Aux)` relacionado à Pessoa.

    * :bi:`Family (Aux)`:

        #. Não será necessário qualquer ação de atualização do registro :bi:`Family (Aux)` relacionado à Pessoa.

    * :bi:`Person (Aux)`:

        #. O :bi:`(Reference) Address (Aux)` do registro :bi:`Person (Aux)` deve ser manualmente associado ao :bi:`Address (Aux)` do Endereço informado para a Pessoa.

        #. As informações de :bi:`Contact Information` devem ser subistituídas pelas informações de :bi:`Contact Information` do :bi:`(Reference) Address (Aux)`.

.. toctree::
   :maxdepth: 2
   :caption: Itens Relacionados:
