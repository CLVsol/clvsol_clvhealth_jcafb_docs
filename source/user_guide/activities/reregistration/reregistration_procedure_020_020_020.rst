.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: A Pessoa reside em um Endereço não cadastrado (Procedimento)

=============================================
A Pessoa reside em um Endereço não cadastrado
=============================================

    Caso se opte por associar ao Endereço da Pessoa uma Família, a Pessoa será associada a essa Família os itens indicados como ":green:`(Opcional)`" deverão ser considerados.

    Caso se opte por não associar ao Endereço da Pessoa a uma Família, os itens indicados como ":green:`(Opcional)`" deverão ser desconsiderados.

Procedimentos
-------------

    #. Procurar pelo(s) registro(s) :bi:`Person` e/ou :bi:`Person (Aux)` associado(s) à Pessoa utilizando o procedimento:

        * :doc:`reregistration_procedure_010_010`

    #. Confirmar que o(s) registro(s) :bi:`Person` e/ou :bi:`Person (Aux)` não seja(m) encontrado(s).

    #. Procurar por um registro :bi:`Address` associado ao Endereço da Pessoa utilizando o procedimento:

        * :doc:`reregistration_procedure_010_050`

    #. Confirmar que o(s) registro(s) :bi:`Address` e/ou :bi:`Address (Aux)` não seja(m) encontrado(s).

    #. Acessar a *view* :bi:`Addresses (Aux)`:

        * Menu de acesso:

            * :bi:`Community` » :bi:`Auxiliary` » :bi:`Addresses (Aux)`

    #. Criar um novo registro :bi:`Address (Aux)`:

        #. Preencher o registro :bi:`Address (Aux)` com as informações apresentadas para o Endereço da Pessoa.

        #. Salvar o registro.

    #. Registro :bi:`Address (Aux)`.

        #. Não será necessário a execução de qualquer procedimento adicional no registro :bi:`Address (Aux)`.

        #. Alterar o :bi:`Register State` para ":bi:`Revised`", utilizando o botão [:bi:`Revised`].

    #. Acessar a *view* :bi:`Persons (Aux)`:

        * Menu de acesso:

            * :bi:`Community` » :bi:`Auxiliary` » :bi:`Persons (Aux)`

    #. Criar um novo registro :bi:`Person (Aux)`:

        #. Preencher o registro :bi:`Person (Aux)` com as informações apresentadas para a Pessoa, exceto informaçôes relativas ao Endereço e à Família.

        #. Salvar o registro.

    #. Editar o registro :bi:`Person (Aux)`:

        #. Associar, manualmente, o campo *Address (Aux)* ao registro :bi:`Address (Aux)` criado anteriormente.

        #. Preencher os campos de *Contact Information* com os dados de Endereço do registro :bi:`Address (Aux)` associado ao campo *Address*, utilizando o botão [:bi:`Get Reference Address (Aux) Data`].

        #. Salvar o registro.

    #. :green:`(Opcional)` A partir do registro :bi:`Person (Aux)` exercutar a Ação ":bi:`Person (Aux) Associate to Family (Aux)`":

        #. Parâmetros apresentados:

            * *Create new Family (Aux)*: **habilitado**

        #. Utilizar o botão [:bi:`Associate do Family (Aux)`]  para executar a Ação.

    #. :green:`(Opcional)` Abrir o registro :bi:`Family (Aux)` associado à Pessoa apresentado na *view* :bi:`Families (Aux)`.

        #. Não será necessário a execução de qualquer procedimento adicional no registro :bi:`Family (Aux)`.

        #. Alterar o :bi:`Register State` para ":bi:`Revised`", utilizando o botão [:bi:`Revised`].

    #. Retornar ao registro :bi:`Person (Aux)`.

        #. Não será necessário a execução de qualquer procedimento adicional no registro :bi:`Person (Aux)`.

        #. Alterar o :bi:`Register State` para ":bi:`Revised`", utilizando o botão [:bi:`Revised`].

.. toctree::
   :maxdepth: 2
   :caption: Tópicos Relacionados:
