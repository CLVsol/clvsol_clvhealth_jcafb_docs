.. raw:: html

    <style> .red {color:red} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: bi

.. index:: Criação do Cadastro Auxiliar da Pessoa

======================================
Criação do Cadastro Auxiliar da Pessoa
======================================

    Se, após a execução da :doc:`/user_guide/community/person_off/person_off_reregistration_010` não for identificado um registro associado à Pessoa pesquisada no **Cadastro Auxiliar**, independentemente da Pessoa ter sido declarada "**já cadastrada**" ou "**não cadastrada**", essa Pessoa deve ser cadastrada no **Cadastro Auxiliar**.

    #. :ref:`Criação do Cadastro Off de uma Pessoa já cadastrada`

        Este procedimento pode ser utilizado somente quando **for identificado** um registro :bi:`Person` para a Pessoa a ser recadastrada, utilizando-se um dos métodos: :ref:`Procura pela Pessoa a ser recadastrada (via view Contatos)` ou :ref:`Procura pela Pessoa a ser recadastrada (via view Persons)`.

        Por esse método, quando não existir ainda um Cadastro *Off* para a Pessoa, o mesmo será automaticamente criado como uma cópia do Cadastro dessa Pessoa.

        O Cadastro *Off* criado será composto por um registro de :bi:`Person (Off)`, um registro de :bi:`Address (Off)` (quando existir um registro de :bi:`Address` associado à Pessoa), e um registro de :bi:`Family (Off)` (quando existir um registro de :bi:`Family` associado à Pessoa).

        O relacionamento entre os diversos registros dos Cadastros será o seguinte (quando existirem os registros, como indicado anteriormente):

            * :bi:`Person (Off)`: 

                * :bi:`(Reference) Address` » :bi:`Address`
                * :bi:`(Reference) Address (Off)` » :bi:`Address (Off)`
                * :bi:`Family` » :bi:`Family`
                * :bi:`Family (Off)` » :bi:`Family (Off)`
                * :bi:`Related Person` » :bi:`Person`
                * :bi:`Contact Information` = Dados do registro :bi:`Address`
                * Outros Dados = Outros Dados do registro :bi:`Person`

            * :bi:`Address (Off)`:

                * :bi:`Related Address` » :bi:`Address`
                * :bi:`Contact Information` = Dados do registro :bi:`Address`

            * :bi:`Family (Off)`:

                * :bi:`(Reference) Address` » :bi:`Address`
                * :bi:`(Reference) Address (Off)` » :bi:`Address (Off)`
                * :bi:`Related Family` » :bi:`Family`
                * :bi:`Contact Information` = Dados do registro :bi:`Address`

    #. :ref:`Criação do Cadastro Off de uma Pessoa não cadastrada`

        Este procedimento pode ser utilizado somente quando **não for identificado** um registro :bi:`Person` para a Pessoa a ser recadastrada, utilizando-se um dos métodos: :ref:`Procura pela Pessoa a ser recadastrada (via view Contatos)` ou :ref:`Procura pela Pessoa a ser recadastrada (via view Persons)`.

        Por esse método, quando não existir ainda um Cadastro *Off* para a Pessoa, o mesmo deverá ser manualmente criado para conter as informações coletadas para a Pessoa. Essas informações coletadas serão manualmente inseridas nos registros pertinentes.

        O Cadastro *Off* criado será composto por um registro de :bi:`Person (Off)`, um registro de :bi:`Address (Off)` (quando necessário), e um registro de :bi:`Family (Off)` (quando necessário).

        O relacionamento entre os diversos registros dos Cadastros será o seguinte (quando existirem os registros, como indicado anteriormente):

            * :bi:`Person (Off)`: 

                * :bi:`(Reference) Address` » **vazio**
                * :bi:`(Reference) Address (Off)` » :bi:`Address (Off)`
                * :bi:`Family` » **vazio**
                * :bi:`Family (Off)` » :bi:`Family (Off)`
                * :bi:`Related Person` » **vazio**
                * :bi:`Contact Information` = Dados do Endereço da Pessoa
                * Outros Dados = Outros Dados coletados da Pessoa

            * :bi:`Address (Off)`:

                * :bi:`Related Address` » **vazio**
                * :bi:`Contact Information` = Dados do Endereço da Pessoa

            * :bi:`Family (Off)`:

                * :bi:`(Reference) Address` » **vazio**
                * :bi:`(Reference) Address (Off)` » :bi:`Address (Off)`
                * :bi:`Related Family` » **vazio**
                * :bi:`Contact Information` = Dados do Endereço da Pessoa

.. _Criação do Cadastro Off de uma Pessoa já cadastrada:

Criação do Cadastro *Off* de uma Pessoa já cadastrada
-----------------------------------------------------

.. _Criação do Cadastro Off de uma Pessoa não cadastrada:

Criação do Cadastro *Off* de uma Pessoa não cadastrada
------------------------------------------------------

.. toctree::
   :maxdepth: 2
   :caption: Índice:
