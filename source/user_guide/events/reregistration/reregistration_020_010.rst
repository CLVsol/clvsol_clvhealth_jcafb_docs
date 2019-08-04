.. raw:: html

    <style> .red {color:red} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: bi

.. index:: Criação do Cadastro Auxiliar para uma Pessoa já cadastrada

======================================================================
Criação do "**Cadastro Auxiliar**" para uma Pessoa "**já cadastrada**"
======================================================================

    Este procedimento pode ser utilizado somente quando **for identificado** um registro :bi:`Person` para a Pessoa, utilizando-se um dos métodos: ":doc:`reregistration_010_010`" ou ":doc:`reregistration_010_020`".

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

        #. Executar o procedimento ":doc:`/user_guide/community/person/person_associate_to_person_aux`" para o registro :bi:`Person` aberto durante a execução do procedimento anterior (":doc:`reregistration_010_010`" ou ":doc:`reregistration_010_020`"):

            #. Exercutar a Ação ":bi:`Person Associate to Person (Aux)`":

                #. Parâmetros apresentados:
                    * *Create new Person (Aux)* (**Observação**: Parâmetro não modificável)
                    * *Create new Family (Aux)* (**Observação**: Parâmetro não modificável)
                    * *Create new Address (Aux)* (**Observação**: Parâmetro não modificável)

                #. Utilize o botão **[** :bi:`Associate do Perton (Aux)` **]**  para executar a Ação.

            #. Abrir o registro da Pessoa apresentado na *view* :bi:`Persons (Aux)`.

        #. Executar o procecimento ":doc:`reregistration_030`".

.. toctree::
   :maxdepth: 2
   :caption: Itens Relacionados:
