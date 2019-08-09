.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: [Pessoa não cadastrada] A Pessoa reside em um Endereço **fora da comunidade** atendida pela JCAFB

=================================================================================================
[Pessoa não cadastrada] A Pessoa reside em um Endereço **fora da comunidade** atendida pela JCAFB
=================================================================================================

.. _Cadastro Auxiliar (13):

Cadastro Auxiliar
-----------------

    O **Cadastro Auxiliar** criado manualmente poderá ser composto pelas seguintes **Entidades (Aux)**:

        * :bi:`Person (Aux)`:

            * Um registro :bi:`Person (Aux)` deverá ser **criado manualmente** e preenchido com as informações coletadas para a Pessoa.

        * :bi:`Address (Aux)`:

            * Nenhum :bi:`Address (Aux)` será associado à Pessoa.

        * :bi:`Family (Aux)`:

            * Nenhum :bi:`Family (Aux)` será associado à Pessoa.

    O relacionamento entre os diversos registros dos Cadastros será o seguinte (quando existirem os registros, como indicado anteriormente):

        * :bi:`Person (Aux)`: 

            * :bi:`Related Person` » **vazio**
            * :bi:`(Reference) Address` **vazio**
            * :bi:`(Reference) Address (Aux)` » **vazio**
            * :bi:`Family` » **vazio**
            * :bi:`Family (Aux)` » **vazio**
            * :bi:`Contact Information` = Dados do registro :bi:`Address`
            * Outros Dados = Outros Dados coletadas para a Pessoa

        * :bi:`Address (Aux)`:

            * Nenhum :bi:`Address (Aux)` será associado à Pessoa.

        * :bi:`Family (Aux)`:

            * Nenhum :bi:`Family (Aux)` será associado à Pessoa.

Atualizações
------------

    #. **Cadastro Auxiliar**:

        #. O **Cadastro Auxiliar** relacionado à Pessoa deve ser criado manualmente conforme as condições descritas em ":ref:`Cadastro Auxiliar (13)`".

    #. :bi:`Person (Aux)`:

        #. As informações de :bi:`Contact Information`  do registro :bi:`Person (Aux)` devem ser preenchidas com informações que indiquem o Endereço fora da comunidade.

.. toctree::
   :maxdepth: 2
   :caption: Itens Relacionados:
