.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: A Pessoa reside em um Endereço já cadastrado (Procedimento)

============================================
A Pessoa reside em um Endereço já cadastrado
============================================

    Caso **exista uma Família** associada ao Endereço da Pessoa, a Pessoa será associada a essa Família, e os itens indicados como ":green:`(Opcional)`" deverão ser considerados.

    Caso **não exista uma Família** associada ao Endereço da Pessoa, os itens indicados como ":green:`(Opcional)`" deverão ser desconsiderados.

    #. Procurar por registros :bi:`Person` e/ou :bi:`Person(Aux)` associado(s) à Pessoa utilizando o procedimento:

        * :doc:`reregistration_procedure_010_010`

    #. Confirmar que nenhum registro :bi:`Person` e/ou :bi:`Person (Aux)` seja(m) encontrado(s).

    #. Procurar por um registro :bi:`Address` associado ao Endereço da Pessoa utilizando um dos procedimentos:

        * :doc:`reregistration_procedure_010_050`
        * :doc:`reregistration_procedure_010_060`

    #. Confirmar que todos os dados dos registros :bi:`Address` e :bi:`Family`, relacionados ao Endereço da Pessoa, serão mantidos.

    #. Acessar a *view* :bi:`Persons (Aux)`:

        * Menu de acesso:
            * :bi:`Community` » :bi:`Auxiliary` » :bi:`Persons (Aux)`

    #. Criar um novo registro :bi:`Person (Aux)`:

        #. Preencher o registro :bi:`Person (Aux)` com as informações apresentadas para a Pessoa, exceto informaçôes relativas ao Endereço e à Família.

        #. Associar, manualmente, o campo *Address* ao registro :bi:`Address` encontrado anteriormente.

        #. Preencher os campos de *Contact Information* com os dados de Endereço do registro :bi:`Address` associado ao campo *Address*, utilizando o botão [:bi:`Get Reference Address Data`].

        #. Salvar o registro.

    #. A partir do registro :bi:`Person (Aux)` exercutar a Ação ":bi:`Person (Aux) Associate to Address (Aux)`":

        #. Parâmetros apresentados:

            * *Create new Address (Aux)*: **habilitado**

        #. Utilizar o botão [:bi:`Associate do Address (Aux)`] para executar a Ação.

    #. Abrir o registro :bi:`Address (Aux)` associado à Pessoa apresentado na *view* :bi:`Addresses (Aux)`.

        #. Não será necessário a execução de qualquer procedimento adicional no registro :bi:`Address (Aux)`.

        #. Alterar o :bi:`Register State` para ":bi:`Verified`", utilizando o botão [:bi:`Revised`] e em seguida o botão [:bi:`Verified`].

    #. Retornar ao registro :bi:`Person (Aux)`.

    #. :green:`(Opcional)` A partir do registro :bi:`Person (Aux)`, associar o campo :bi:`Family` do registro :bi:`Person (Aux)` ao registro registro :bi:`Family` associado ao registro :bi:`Address` indicado no campo :bi:`Address`, exercutando a Ação ":bi:`Person (Aux) Associate to Family`":

        #. Utilizar o botão [:bi:`Associate do Family`] para executar a Ação.

    #. :green:`(Opcional)` A partir do registro :bi:`Person (Aux)` exercutar a Ação ":bi:`Person (Aux) Associate to Family (Aux)`":

        #. Parâmetros apresentados:

            * *Create new Family (Aux)*: **habilitado**

        #. Utilizar o botão [:bi:`Associate do Family (Aux)`]  para executar a Ação.

    #. :green:`(Opcional)` Abrir o registro :bi:`Family (Aux)` associado à Pessoa apresentado na *view* :bi:`Families (Aux)`.

        #. Não será necessário a execução de qualquer procedimento adicional no registro :bi:`Family (Aux)`.

        #. Alterar o :bi:`Register State` para ":bi:`Verified`", utilizando o botão [:bi:`Revised`] e em seguida o botão [:bi:`Verified`].

    #. Retornar ao registro :bi:`Person (Aux)`.

        #. Não será necessário a execução de qualquer procedimento adicional no registro :bi:`Person (Aux)`.

        #. Alterar o :bi:`Register State` para ":bi:`Revised`", utilizando o botão [:bi:`Revised`].

.. toctree::
   :maxdepth: 2
   :caption: Tópicos Relacionados:
