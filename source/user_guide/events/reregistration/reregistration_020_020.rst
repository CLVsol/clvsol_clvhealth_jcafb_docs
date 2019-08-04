.. raw:: html

    <style> .red {color:red} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: bi

.. index:: Criação do Cadastro Auxiliar de uma Pessoa não cadastrada

===============================================================
Criação do "**Cadastro Auxiliar**" de uma Pessoa não cadastrada
===============================================================

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
