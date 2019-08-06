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

    Este procedimento pode ser utilizado somente quando **for identificado** um registro :bi:`Person` para a Pessoa, utilizando-se um dos métodos: ":doc:`reregistration_procedure_010_010`" ou ":doc:`reregistration_procedure_010_020`".

    Por esse método, quando não existir ainda um Cadastro Auxiliar para a Pessoa, o mesmo será automaticamente criado como uma cópia do Cadastro dessa Pessoa.

    Se porventura já existir um Cadastro Auxiliar para a Pessoa, o mesmo será selecionado para dar proceguimento ao processo de recadastramento da Pessoa.

    O Cadastro Auxiliar criado será composto por um registro de :bi:`Person (Aux)`, um registro de :bi:`Address (Aux)` (quando existir um registro de :bi:`Address` associado à Pessoa), e um registro de :bi:`Family (Aux)` (quando existir um registro de :bi:`Family` associado à Pessoa).

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

    A criação do **Cadastro Auxiliar** para uma **Pessoa já cadastrada** é feita utilizando o procedimento ":doc:`reregistration_procedure_020_010`".

.. toctree::
   :maxdepth: 2
   :caption: Procedimentos:
