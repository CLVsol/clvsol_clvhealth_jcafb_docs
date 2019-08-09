.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: Criação/Atualização do Cadastro Auxiliar para uma Pessoa já cadastrada

==============================================================================
Criação/Atualização do **Cadastro Auxiliar** para uma **Pessoa já cadastrada**
==============================================================================

O processo de criação/atualização do **Cadastro Auxiliar** para uma Pessoa **já cadastrada** é utilizado quando a Pessoa tiver sido declarada como **já cadastrada**.

Este processo é, basicamente, um processo de atualização das informações em uma cópia do **Cadastro** atual da Pessoa. 

Portanto, quando não existir ainda um **Cadastro Auxiliar** para a Pessoa, o mesmo deverá ser automaticamente criado como uma cópia do **Cadastro** dessa Pessoa.

Se porventura já existir um **Cadastro Auxiliar** para a Pessoa, o mesmo será selecionado para dar proseguimento ao processo de recadastramento da Pessoa.

O **Cadastro Auxiliar** criado poderá ser composto pelas seguintes **Entidades (Aux)**:

    * :bi:`Person (Aux)`:

        * quando existir um registro :bi:`Person` associado à Pessoa

        * e quando habilitada a criação de :bi:`Person (Aux)`

            * A criação de :bi:`Person (Aux)`, deve ser sempre habilitada.

    * :bi:`Address (Aux)`:

        * quando existir um registro :bi:`Address` associado à Pessoa

        * e quando habilitada a criação de :bi:`Address (Aux)`

            * A criação de um registro :bi:`Address (Aux)` deve ser **habilitada**, quando se constatar que a Pessoa foi mantida no Endereço atual cadastrado.

            * A criação de um registro :bi:`Address (Aux)` deve ser **desabilitada**, quando se constatar que a Pessoa foi transferida para o Endereço associado a este registro :bi:`Address`.

                * Neste caso, um registro :bi:`Address (Aux)` deverá ser **criado automaticamente** a partir do registro :bi:`Address` associado ao Endereço já cadastrado, 

            * A criação de um registro :bi:`Address (Aux)` deve ser **desabilitada**, quando se constatar que a Pessoa foi transferida para um Endereço não cadastrado da comunidade atendida.

                * Neste caso, um registro :bi:`Address (Aux)` deverá ser **criado manualmente**

            * A criação de um registro :bi:`Address (Aux)` deve ser **desabilitada**, quando se constatar que a Pessoa foi transferida para um Endereço desconhecido ou fora da comunidade atendida.

            * A criação de um registro :bi:`Address (Aux)` deve ser **desabilitada**, quando se constatar que a Pessoa faleceu.

    * :bi:`Family (Aux)`:

        * quando existir um registro :bi:`Family` associado à Pessoa

        * e quando habilitada a criação de :bi:`Family (Aux)`

            * A criação de um registro :bi:`Family (Aux)` deve ser **habilitada**, quando se constatar que a Pessoa será mantida na Família atual cadastrada.

            * A criação de um registro :bi:`Family (Aux)` deve ser **desabilitada**, quando se constatar que a Pessoa foi transferida para outra Família já cadastrada.

                * Neste acaso, um registro :bi:`Family (Aux)` deverá ser **criado automaticamente** a partir de um registro :bi:`Family` associado à Família já cadastrada.

            * A criação de um registro :bi:`Family (Aux)` deve ser **desabilitada**, quando se constatar que a Pessoa foi transferida para uma Família não cadastrada.

                * Neste caso, um registro :bi:`Family (Aux)` deverá ser **criado manualmente**.

            * A criação de um registro :bi:`Family (Aux)` deve ser **desabilitada**, quando se constatar que a Pessoa foi transferida para uma Famĩlia desconhecida ou fora da comunidade.

            * A criação de um registro :bi:`Family (Aux)` deve ser **desabilitada**,quando se constatar que a Pessoa faleceu. 

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
   :maxdepth: 1
   :caption: Opções de Cadastramento:

   reregistration_workflow_020_010_010
   reregistration_workflow_020_010_020
   reregistration_workflow_020_010_030
   reregistration_workflow_020_010_040
   reregistration_workflow_020_010_045
   reregistration_workflow_020_010_050
   reregistration_workflow_020_010_055
   reregistration_workflow_020_010_060
   reregistration_workflow_020_010_070
   reregistration_workflow_020_010_080
   reregistration_workflow_020_010_090
