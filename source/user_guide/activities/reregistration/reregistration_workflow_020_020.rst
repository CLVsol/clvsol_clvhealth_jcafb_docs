.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: Criação/Atualização do Cadastro Auxiliar (Pessoa não cadastrada)

========================================================================
Criação/Atualização do **Cadastro Auxiliar** (**Pessoa não cadastrada**)
========================================================================

    O processo de criação/atualização do **Cadastro Auxiliar** para uma Pessoa **não cadastrada** é utilizado quando a Pessoa tiver sido declarada como **não cadastrada**.

    Portanto, quando não existir ainda um **Cadastro Auxiliar** para a Pessoa, o mesmo deverá ser manualmente criado para conter as informações disponíveis para a Pessoa. Essas informações serão manualmente inseridas nos registros pertinentes.

O **Cadastro Auxiliar** criado poderá ser composto pelas **Entidades (Aux)**:

    * :bi:`Person (Aux)`:

        * O registro será preenchido com as informações coletadas para a Pessoa.

    * :bi:`Address (Aux)`:

        * O registro será preenchido com as informações coletadas para a Pessoa:

            * O registro :bi:`Address (Aux)` deverá ser **criado automaticamente** a partir de um registro :bi:`Address` já cadastrado, quando se constatar que a Pessoa reside no Endereço associado a este registro :bi:`Address`.

            * O registro :bi:`Address (Aux)` deverá ser **criado manualmente**, quando se constatar que a Pessoa reside em um Endereço não cadastrado.

            * O registro :bi:`Address (Aux)` **não será criado**, quando se constatar que a Pessoa reside em um Endereço fora da comunidade atendida.

            * O registro :bi:`Address (Aux)` **não será criado**, quando se constatar que a Pessoa faleceu.

    * :bi:`Family (Aux)`:

        * O registro será preenchido com as informações coletadas para a Pessoa:

            * O registro :bi:`Family (Aux)` deverá ser **criado automaticamente** a partir de um registro :bi:`Family` já cadastrado, quando se constatar que a Pessoa é membro da Família associada a este registro :bi:`Family`.

            * O registro :bi:`Family (Aux)` deverá ser **criado manualmente**, quando se constatar que a Pessoa é membro de uma Família não cadastrada.

            * O registro :bi:`Family (Aux)` **não será criado**, quando se constatar que a Pessoa é mebro de uma Família fora da comunidade atendida.

    O relacionamento entre os diversos registros dos Cadastros será o seguinte (quando existirem os registros, como indicado anteriormente):

        * :bi:`Person (Aux)`: 

            * :bi:`Related Person` » **vazio**
            * :bi:`(Reference) Address` » **vazio**
            * :bi:`(Reference) Address (Aux)` » :bi:`Address (Aux)`
            * :bi:`Family` » **vazio**
            * :bi:`Family (Aux)` » :bi:`Family (Aux)`
            * :bi:`Contact Information` = Dados do Endereço da Pessoa
            * Outros Dados = Outros Dados coletados da Pessoa

        * :bi:`Address (Aux)`:

            * :bi:`Related Address` » **vazio**
            * :bi:`Contact Information` = Dados do Endereço da Pessoa
            * Outros Dados = Outros Dados coletados do Endereço

        * :bi:`Family (Aux)`:

            * :bi:`Related Family` » **vazio**
            * :bi:`(Reference) Address` » **vazio**
            * :bi:`(Reference) Address (Aux)` » :bi:`Address (Aux)`
            * :bi:`Contact Information` = Dados do Endereço da Pessoa
            * Outros Dados = Outros Dados coletados da Família

    A criação do **Cadastro Auxiliar** para uma **Pessoa não cadastrada** é feita utilizando o procedimento ":doc:`reregistration_procedure_020_020`".

.. toctree::
   :maxdepth: 2
   :caption: Itens Relacionados:

   reregistration_workflow_020_020_010
   reregistration_workflow_020_020_020
   reregistration_workflow_020_020_030
