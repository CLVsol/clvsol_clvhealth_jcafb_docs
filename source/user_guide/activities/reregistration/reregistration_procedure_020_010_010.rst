.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: Todos os dados da Pessoa serão mantidos (Procedimento)

=======================================
Todos os dados da Pessoa serão mantidos
=======================================

    * *Workflow*: ":doc:`reregistration_workflow_020_010_010`".

    Caso **exista uma Família** associada ao Endereço atual da Pessoa, a Pessoa continuará associada a essa Família e os itens indicados como ":green:`(Opcional)`" deverão ser considerados.

    Caso **não exista uma Família** associada ao Endereço atual da Pessoa, os itens indicados como ":green:`(Opcional)`" deverão ser desconsiderados.

Procedimentos
-------------

    #. Procurar pelo registro :bi:`Person` associado à Pessoa utilizando um dos procedimentos:

        * :doc:`reregistration_procedure_010_010`
        * :doc:`reregistration_procedure_010_020`

    #. Confirmar que todos os dados do registro :bi:`Person` associado à Pessoa serão mantidos.

    #. Confirmar que todos os dados do registro :bi:`Address`, associado ao registro :bi:`Person`, serão mantidos.

    #. :green:`(Opcional)` Confirmar que todos os dados do registro :bi:`Family`, associado ao registro :bi:`Person`, serão mantidos.

    #. A partir do registro :bi:`Person` encontrado, exercutar a Ação ":bi:`Person Associate to Person (Aux)`":

        #. Parâmetros apresentados:

            * *Create new Person (Aux)*: **habilitado**
            * *Create new Family (Aux)*: **habilitado**

        #. Utilizar o botão [:bi:`Associate do Perton (Aux)`] para executar a Ação.

    #. Abrir o registro :bi:`Person (Aux)` associado à Pessoa apresentado na *view* :bi:`Persons (Aux)`.

    #. Abrir o registro :bi:`Address (Aux)` associado ao campo *Address (Aux)*:

        #. Não será necessário a execução de qualquer procedimento adicional no registro :bi:`Address (Aux)`.

        #. Alterar o :bi:`Register State` para ":bi:`Revised`", utilizando o botão [:bi:`Revised`].

    #. Retornar ao registro :bi:`Person (Aux)`.

        #. Não será necessário a execução de qualquer procedimento adicional no registro :bi:`Person (Aux)`.

        #. Alterar o :bi:`Register State` para ":bi:`Revised`", utilizando o botão [:bi:`Revised`].

.. toctree::
   :maxdepth: 2
   :caption: Tópicos Relacionados:
