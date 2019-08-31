.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: A Pessoa mudou-se para um Endereço fora da comunidade atendida pela JCAFB juntamente com a Família (Procedimento)

===================================================================================================
A Pessoa mudou-se para um Endereço fora da comunidade atendida pela JCAFB, juntamente com a Família
===================================================================================================

Procedimentos
-------------

    * *Workflow*: ":doc:`reregistration_workflow_020_010_070`".

    #. Procurar pelo registro :bi:`Person` associado à Pessoa utilizando um dos procedimentos:

        * :doc:`reregistration_procedure_010_010`
        * :doc:`reregistration_procedure_010_020`

    #. Confirmar que todos os dados do registro :bi:`Person`, relacionados à Pessoa, serão mantidos.

    #. Confirmar a mudança de Endereço da Pessoa.

    #. Confirmar que todos os dados do registro :bi:`Family`, relacionados à Família da Pessoa, serão mantidos.

    #. Acessar a *view* :bi:`Addresses (Aux)`:

        * Menu de acesso:

            * :bi:`Community` » :bi:`Auxiliary` » :bi:`Addresses (Aux)`

    #. Criar um novo registro :bi:`Address (Aux)`:

        #. Preencher o registro :bi:`Address (Aux)` com informações que indiquem o novo Endereço da Pessoa fora da comunidade.

        #. Salvar o registro.

    #. Registro :bi:`Address (Aux)`.

        #. Não será necessário a execução de qualquer procedimento adicional no registro :bi:`Address (Aux)`.

        #. Alterar o :bi:`Register State` para ":bi:`Revised`", utilizando o botão [:bi:`Revised`].

    #. A partir do registro :bi:`Person` encontrado, exercutar a Ação ":bi:`Person Associate to Person (Aux)`":

        #. Parâmetros apresentados:

            * *Create new Person (Aux)*: **habilitado**
            * *Create new Family (Aux)*: **desabilitado**
            * *Create new Address (Aux)*: **desabilitado**

        #. Utilizar o botão [:bi:`Associate do Perton (Aux)`] para executar a Ação.

    #. Abrir o registro :bi:`Person (Aux)` associado à Pessoa apresentado na *view* :bi:`Persons (Aux)`.

    #. Editar o registro :bi:`Person (Aux)`:

        #. Remover do campo *Address* a associação ao registro :bi:`Address` :green:`(antigo)`, utilizando o botão [:bi:`Remove Reference Address`].

        #. Associar, manualmente, o campo *Address (Aux)* ao registro :bi:`Address (Aux)` criado anteriormente.

        #. Preencher os campos de *Contact Information* com os dados de Endereço do registro :bi:`Address (Aux)` associado ao campo *Address*, utilizando o botão [:bi:`Get Reference Address (Aux) Data`].

        #. Salvar o registro.

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
