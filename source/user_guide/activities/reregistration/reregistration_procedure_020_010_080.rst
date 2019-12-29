.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: A Pessoa está ausente da comunidade atendida pela JCAFB (Procedimento)

=======================================================
A Pessoa está ausente da comunidade atendida pela JCAFB
=======================================================

    * *Workflow*: ":doc:`reregistration_workflow_020_010_080`".

    Caso **exista uma Família** associada ao Endereço da Pessoa, os itens indicados como ":green:`(Opcional)`" deverão ser considerados.

    Caso **não exista uma Família** associada ao Endereço da Pessoa, os itens indicados como ":green:`(Opcional)`" deverão ser desconsiderados.

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

    #. Editar o registro :bi:`Person (Aux)` associado à Pessoa apresentado na *view* :bi:`Persons (Aux)`.

        #. Marcar o campo :bi:`Is Absent`.

        #. Inserir no campo :bi:`Notes..` a informação de que a Pessoa está ausente da comunidade atendida pela JCAFB.

        #. Salvar o registro.

    #. Registro :bi:`Person (Aux)`.

        #. Não será necessário a execução de qualquer procedimento adicional no registro :bi:`Person (Aux)`.

        #. Alterar o :bi:`Register State` para ":bi:`Revised`", utilizando o botão [:bi:`Revised`].

.. toctree::
   :maxdepth: 2
   :caption: Tópicos Relacionados:
