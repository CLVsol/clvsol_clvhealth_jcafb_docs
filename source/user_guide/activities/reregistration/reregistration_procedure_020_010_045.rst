.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: A Pessoa mudou-se para um Endereço já cadastrado, sem a Família (Procedimento)

===============================================================
A Pessoa mudou-se para um Endereço já cadastrado, sem a Família
===============================================================

Procedimentos
-------------

    * *Workflow*: ":doc:`reregistration_workflow_020_010_045`".

    #. Procurar pelo registro :bi:`Person` associado à Pessoa utilizando um dos procedimentos:

        * :doc:`reregistration_procedure_010_010`
        * :doc:`reregistration_procedure_010_020`

    #. Confirmar que todos os dados do registro :bi:`Person`, relacionados à Pessoa, serão mantidos.

    #. Confirmar a mudança de Endereço da Pessoa.

    #. Confirmar a mudança de Família da Pessoa.

    #. Procurar pelo registro :bi:`Address` :green:`(novo)` associado ao novo Endereço informado para a Pessoa utilizando um dos procedimentos:

        * :doc:`reregistration_workflow_010_050`
        * :doc:`reregistration_workflow_010_060`

    #. Confirmar que todos os dados do registro :bi:`Address` :green:`(novo)` serão mantidos.

    #. Confirmar a mudança de Família da Pessoa.

    #. A partir do registro :bi:`Person` encontrado, exercutar a Ação ":bi:`Person Associate to Person (Aux)`":

        #. Parâmetros apresentados:

            * *Create new Person (Aux)*: **habilitado**
            * *Create new Family (Aux)*: **desabilitado**
            * *Create new Address (Aux)*: **desabilitado**

        #. Utilizar o botão [:bi:`Associate do Perton (Aux)`] para executar a Ação.

    #. Abrir o registro :bi:`Person (Aux)` associado à Pessoa apresentado na *view* :bi:`Persons (Aux)`.

    #. Editar o registro :bi:`Person (Aux)`:

        #. Remover do campo *Address* a associação ao registro :bi:`Address` :green:`(antigo)`, utilizando o botão [:bi:`Remove Reference Address`].

        #. Associar, manualmente, o campo *Address* ao registro :bi:`Address` :green:`(novo)` encontrado anteriormente.

        #. Salvar o registro.

    #. A partir do registro :bi:`Person (Aux)` exercutar a Ação ":bi:`Person (Aux) Associate to Address (Aux)`":

        #. Parâmetros apresentados:

            * *Create new Address (Aux)*: **habilitado**

        #. Utilizar o botão [:bi:`Associate do Address (Aux)`] para executar a Ação.

    #. Abrir o registro :bi:`Address (Aux)` associado à Pessoa apresentado na *view* :bi:`Addresses (Aux)`.

        #. Não será necessário a execução de qualquer procedimento adicional no registro :bi:`Address (Aux)`.

        #. Alterar o :bi:`Register State` para ":bi:`Revised`", utilizando o botão [:bi:`Revised`].

    #. Retornar ao registro :bi:`Person (Aux)`.

    #. Editar o registro :bi:`Person (Aux)`:

        #. Remover do campo *Family* a associação ao registro :bi:`FAmily` :green:`(antiga)`, utilizando o botão [:bi:`Remove Family`].

        #. Salvar o registro.

    #. A partir do registro :bi:`Person (Aux)`, associar o campo *Family* ao registro :bi:`Family`, exercutando a Ação ":bi:`Person (Aux) Associate to Family`":

        #. Utilizar o botão [:bi:`Associate do Family`] para executar a Ação.

        **Observação**: Caso **não exista previamente uma Família** associada ao novo Endereço da Pessoa, o campo *Family* permanecerá **vazio**.

    #. A partir do registro :bi:`Person (Aux)` exercutar a Ação ":bi:`Person (Aux) Associate to Family (Aux)`":

        #. Parâmetros apresentados:

            * *Create new Family (Aux)*: **habilitado**

        #. Utilizar o botão [:bi:`Associate do Family (Aux)`]  para executar a Ação.

    #. Abrir o registro :bi:`Family (Aux)` associado à Pessoa apresentado na *view* :bi:`Families (Aux)`.

        #. Não será necessário a execução de qualquer procedimento adicional no registro :bi:`Family (Aux)`.

        #. Alterar o :bi:`Register State` para ":bi:`Revised`", utilizando o botão [:bi:`Revised`].

    #. Retornar ao registro :bi:`Person (Aux)`.

    #. A partir do registro :bi:`Person (Aux)`:

        #. Não será necessário a execução de qualquer procedimento adicional no registro :bi:`Person (Aux)`.

        #. Alterar o :bi:`Register State` para ":bi:`Revised`", utilizando o botão [:bi:`Revised`].

.. toctree::
   :maxdepth: 2
   :caption: Tópicos Relacionados:
