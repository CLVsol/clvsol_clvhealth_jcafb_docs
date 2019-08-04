.. raw:: html

    <style> .red {color:red} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: bi

.. index:: Criação do Cadastro Auxiliar de uma Pessoa

==========================================
Criação do Cadastro Auxiliar de uma Pessoa
==========================================

    Se, após a execução da :doc:`/user_guide/events/reregistration/reregistration_010` não for identificado um registro associado à Pessoa pesquisada no **Cadastro Auxiliar**, independentemente da Pessoa ter sido declarada "**já cadastrada**" ou "**não cadastrada**", essa Pessoa deve ser cadastrada inicialmente no **Cadastro Auxiliar**.

    #. :doc:`/user_guide/events/reregistration/reregistration_020_010`

        Este procedimento pode ser utilizado somente quando **for identificado** um registro :bi:`Person` para a Pessoa, utilizando-se um dos métodos: :doc:`/user_guide/events/reregistration/reregistration_010_010` ou :doc:`/user_guide/events/reregistration/reregistration_010_020`.

        Por esse método, quando não existir ainda um Cadastro *Aux* para a Pessoa, o mesmo será automaticamente criado como uma cópia do Cadastro dessa Pessoa.

        O Cadastro *Aux* criado será composto por um registro de :bi:`Person (Aux)`, um registro de :bi:`Address (Aux)` (quando existir um registro de :bi:`Address` associado à Pessoa), e um registro de :bi:`Family (Aux)` (quando existir um registro de :bi:`Family` associado à Pessoa).

        O relacionamento entre os diversos registros dos Cadastros será o seguinte (quando existirem os registros, como indicado anteriormente):

            * :bi:`Person (Aux)`: 

                * :bi:`(Reference) Address` » :bi:`Address`
                * :bi:`(Reference) Address (Aux)` » :bi:`Address (Aux)`
                * :bi:`Family` » :bi:`Family`
                * :bi:`Family (Aux)` » :bi:`Family (Aux)`
                * :bi:`Related Person` » :bi:`Person`
                * :bi:`Contact Information` = Dados do registro :bi:`Address`
                * Outros Dados = Outros Dados do registro :bi:`Person`

            * :bi:`Address (Aux)`:

                * :bi:`Related Address` » :bi:`Address`
                * :bi:`Contact Information` = Dados do registro :bi:`Address`

            * :bi:`Family (Aux)`:

                * :bi:`(Reference) Address` » :bi:`Address`
                * :bi:`(Reference) Address (Aux)` » :bi:`Address (Aux)`
                * :bi:`Related Family` » :bi:`Family`
                * :bi:`Contact Information` = Dados do registro :bi:`Address`

    #. :doc:`/user_guide/events/reregistration/reregistration_020_020`

        Este procedimento pode ser utilizado somente quando **não for identificado** um registro :bi:`Person` para a Pessoa, utilizando-se um dos métodos: :doc:`/user_guide/events/reregistration/reregistration_010_010` ou :doc:`/user_guide/events/reregistration/reregistration_010_020`.

        Por esse método, quando não existir ainda um Cadastro *Aux* para a Pessoa, o mesmo deverá ser manualmente criado para conter as informações coletadas para a Pessoa. Essas informações coletadas serão manualmente inseridas nos registros pertinentes.

        O Cadastro *Aux* criado será composto por um registro de :bi:`Person (Aux)`, um registro de :bi:`Address (Aux)` (quando necessário), e um registro de :bi:`Family (Aux)` (quando necessário).

        O relacionamento entre os diversos registros dos Cadastros será o seguinte (quando existirem os registros, como indicado anteriormente):

            * :bi:`Person (Aux)`: 

                * :bi:`(Reference) Address` » **vazio**
                * :bi:`(Reference) Address (Aux)` » :bi:`Address (Aux)`
                * :bi:`Family` » **vazio**
                * :bi:`Family (Aux)` » :bi:`Family (Aux)`
                * :bi:`Related Person` » **vazio**
                * :bi:`Contact Information` = Dados do Endereço da Pessoa
                * Outros Dados = Outros Dados coletados da Pessoa

            * :bi:`Address (Aux)`:

                * :bi:`Related Address` » **vazio**
                * :bi:`Contact Information` = Dados do Endereço da Pessoa

            * :bi:`Family (Aux)`:

                * :bi:`(Reference) Address` » **vazio**
                * :bi:`(Reference) Address (Aux)` » :bi:`Address (Aux)`
                * :bi:`Related Family` » **vazio**
                * :bi:`Contact Information` = Dados do Endereço da Pessoa

.. toctree::
   :maxdepth: 2
   :caption: Itens Relacionados:

   reregistration_020_010
   reregistration_020_020
