.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: [Pessoa não cadastrada] A Pessoa reside em um Endereço não cadastrado

=================================================================================================
:red:`(Não Verificado)` [Pessoa não cadastrada] A Pessoa reside em um Endereço **não cadastrado**
=================================================================================================

.. _Cadastro Auxiliar (11):

Cadastro Auxiliar
-----------------

    O **Cadastro Auxiliar** criado poderá ser composto pelas seguintes **Entidades (Aux)**:

        * :bi:`Person (Aux)`:

            * Um registro :bi:`Person (Aux)` deverá ser **criado manualmente** e preenchido com as informações coletadas para a Pessoa.

        * :bi:`Address (Aux)`:

            * Um registro :bi:`Address (Aux)` deverá ser **criado manualmente** a partir dos dados do Endereço informado para a Pessoa.

        * :bi:`Family (Aux)`:

            * Nenhum :bi:`Family (Aux)` será associado à Pessoa.

    O relacionamento entre os diversos registros dos Cadastros será o seguinte:

        * :bi:`Person (Aux)`: 

            * :bi:`Related Person` » **vazio**
            * :bi:`(Reference) Address` **vazio**
            * :bi:`(Reference) Address (Aux)` » :bi:`Address (Aux)`
            * :bi:`Family` » **vazio**
            * :bi:`Family (Aux)` » **vazio**
            * :bi:`Contact Information` = Dados do registro :bi:`Address`
            * Outros Dados = Outros Dados coletadas para a Pessoa

        * :bi:`Address (Aux)`:

            * :bi:`Related Address` » :bi:`Address`
            * :bi:`Contact Information` = Dados do registro :bi:`Address`
            * Outros Dados = Outros Dados informados para o Endereço da Pessoa

        * :bi:`Family (Aux)`:

            * Nenhum :bi:`Family (Aux)` será associado à Pessoa.

Atualizações
------------

    * **Cadastro Auxiliar**:

        #. O **Cadastro Auxiliar** relacionado à Pessoa deve ser criado manualmente conforme as condições descritas em ":ref:`Cadastro Auxiliar (11)`".

    * :bi:`Address (Aux)`:

        #. Um registro :bi:`Address (Aux)` deverá ser **criado manualmente** a partir dos dados do Endereço informado para a Pessoa.

        #. Não será necessário qualquer outra ação de atualização do registro :bi:`Address (Aux)` relacionado à Pessoa.

    * :bi:`Person (Aux)`:

        #. O :bi:`(Reference) Address (Aux)` do registro :bi:`Person (Aux)` deve ser manualmente associado ao :bi:`Address (Aux)` do Endereço informado para a Pessoa.

        #. As informações de :bi:`Contact Information` devem ser subistituídas pelas informações de :bi:`Contact Information` do :bi:`(Reference) Address (Aux)`.

.. toctree::
   :maxdepth: 2
   :caption: Itens Relacionados:
