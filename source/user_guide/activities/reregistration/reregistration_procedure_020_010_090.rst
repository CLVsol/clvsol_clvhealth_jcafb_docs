.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: A Pessoa faleceu (Procedimento)

================
A Pessoa faleceu
================

    Caso **exista uma Família** associada ao Endereço da Pessoa, os itens indicados como ":green:`(Opcional)`" deverão ser considerados.

    Caso **não exista uma Família** associada ao Endereço da Pessoa, os itens indicados como ":green:`(Opcional)`" deverão ser desconsiderados.

Procedimentos
-------------

    #. Procurar pelo registro :bi:`Person` associado à Pessoa utilizando um dos procedimentos:

        * :doc:`reregistration_procedure_010_010`
        * :doc:`reregistration_procedure_010_020`

    #. A partir do registro :bi:`Person` encontrado, exercutar a Ação ":bi:`Person Associate to Person (Aux)`":

        #. Parâmetros apresentados:

            * *Create new Person (Aux)*: **habilitado**
            * *Create new Family (Aux)*: **desabilitado**
            * *Create new Address (Aux)*: **desabilitado**

        #. Utilizar o botão [:bi:`Associate do Perton (Aux)`] para executar a Ação.

    #. Editar o registro :bi:`Person (Aux)` associado à Pessoa apresentado na *view* :bi:`Persons (Aux)`.

        #. Remover do campo *Address* a associação ao registro :bi:`Address`, utilizando o botão [:bi:`Remove Reference Address`].

        #. Excluir as informações de *Contact Information*, utilizando o botão [:bi:`Clear Address Data`].

        #. :green:`(Opcional)` Remover do campo *Family* a associação ao registro :bi:`Family`, utilizando o botão [:bi:`Remove Family`].

        #. Inserir no campo :bi:`Notes..` a informação de que a Pessoa faleceu.

        #. Salvar o registro.

    #. Registro :bi:`Person (Aux)`.

        #. Não será necessário a execução de qualquer procedimento adicional no registro :bi:`Person (Aux)`.

        #. Alterar o :bi:`Register State` para ":bi:`Revised`", utilizando o botão [:bi:`Revised`].

.. toctree::
   :maxdepth: 2
   :caption: Tópicos Relacionados:
