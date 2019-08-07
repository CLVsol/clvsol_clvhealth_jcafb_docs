.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: Criação do Cadastro Auxiliar para uma Pessoa já cadastrada

==================================================================
Criação do **Cadastro Auxiliar** para uma **Pessoa já cadastrada**
==================================================================

Este procedimento deve ser utilizado quando a Pessoa tiver sido declarada como **já cadastrada**.

Por esse método, quando não existir ainda um **Cadastro Auxiliar** para a Pessoa, o mesmo poderá ser automaticamente criado como uma cópia do **Cadastro** dessa Pessoa.

Se porventura já existir um **Cadastro Auxiliar** para a Pessoa, o mesmo será selecionado para dar proceguimento ao processo de recadastramento da Pessoa.

O **Cadastro Auxiliar** criado automáticamente poderá ser composto pelas **Entidades (Aux)**:

    * :bi:`Person (Aux)`:
        * quando habilitada a criação de :bi:`Person (Aux)`
            * a criação de :bi:`Person (Aux)`, deve ser sempre habilitada

    * :bi:`Address (Aux)`:
        * quando existir um registro :bi:`Address` associado à Pessoa
        * e quando habilitada a criação de :bi:`Address (Aux)`
            * A criação de um registro :bi:`Address (Aux)`, deve ser **habilitada** quando se constatar que da Pessoa foi mantida no Endereço atual cadastrado.
            * Um registro :bi:`Address (Aux)` deverá ser **criado automaticamente** a partir de um registro :bi:`Address` já cadastrado quando se constatar que a Pessoa foi transferida para o Endereço associado a este registro :bi:`Address`.
            * Um registro :bi:`Address (Aux)` deverá ser **criado manualmente** quando se constatar que a Pessoa foi transferida para um Endereço não cadastrado da comunidade atendida.
            * Um registro :bi:`Address (Aux)` deverá ser **vazio** quando se constatar que a Pessoa foi transferida para um Endereço desconhecido ou fora da comunidade atendida.
            * Um registro :bi:`Address (Aux)` deverá ser **vazio** quando se constatar que a Pessoa faleceu.

    * :bi:`Family (Aux)`:
        * quando existir um registro :bi:`Family` associado à Pessoa
        * e quando habilitada a criação de :bi:`Family (Aux)`
            * A criação de um registro :bi:`Family (Aux)`, deve ser habilitada quando se constatar que a Pessoa será mantida na Família atual cadastrada.
            * Um registro :bi:`Family (Aux)` deverá ser **criado automaticamente** a partir de um registro :bi:`Family` já cadastrado quando se constatar que a Pessoa foi transferida para a Família associada a este registro :bi:`Family`.
            * Um registro :bi:`Family (Aux)` deverá ser **criado manualmente** quando se constatar que a Pessoa foi transferida para uma Família não cadastrada da comunidade atendida.
            * Um registro :bi:`Family (Aux)` deverá ser **vazio** quando se constatar que a Pessoa foi transferida para uma Famĩlia desconhecida ou fora da comunidade atendida.
            * Um registro :bi:`Family (Aux)` deverá ser **vazio** quando se constatar que a Pessoa faleceu.

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

A criação do **Cadastro Auxiliar** para uma **Pessoa já cadastrada** é feita conforme o procedimento ":doc:`reregistration_procedure_020_010`".

.. toctree::
   :maxdepth: 2
   :caption: Procedimentos:
