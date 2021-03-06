.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: Atualização de dados do Endereço da Pessoa não caracterizando uma mudança de Endereço (Procedimento)

======================================================================================
Atualização de dados do Endereço da Pessoa, não caracterizando uma mudança de Endereço
======================================================================================

    * *Workflow*: ":doc:`reregistration_workflow_020_010_030`".

     Os dados :bi:`Address` do :bi:`Contact Information` são compartilhados por todas as Entidades do **Cadastro** (:bi:`Person`, :bi:`Address` e :bi:`Family`) e do **Cadastro Auxiliar** (:bi:`Person (Aux)` e :bi:`Address (Aux)`), descrevendo o Endereço dessas Entidades.

    Atualizações não caracterizando uma mudança de Endereço são aquelas que corrigem e/ou complementam a descrição do Endereço sem alterá-lo.

    No contexto do Recadastramento, essas atualizações devem ser aplicadas manualmente no regitro :bi:`Address (Aux)` e posteriormente replicadas no registro :bi:`Person (Aux)`.

    Caso **exista uma Família** associada ao Endereço atual da Pessoa, a Pessoa continuará associada a essa Família e os itens indicados como ":green:`(Opcional)`" deverão ser considerados.

    Caso **não exista uma Família** associada ao Endereço atual da Pessoa, os itens indicados como ":green:`(Opcional)`" deverão ser desconsiderados.

Procedimentos
-------------

    #. Procurar pelo registro :bi:`Person` associado à Pessoa utilizando um dos procedimentos:

        * :doc:`reregistration_procedure_010_010`
        * :doc:`reregistration_procedure_010_020`

    #. Confirmar que dados do registro :bi:`Person`, relacionados à Pessoa, não caracterizando uma mudança de Endereço, necessitam ser atualizados.

    #. Confirmar que os dados do registro :bi:`Address`, associado ao registro :bi:`Person`, não caracterizando uma mudança de Endereço, necessitam ser atualizados.

    #. :green:`(Opcional)` Confirmar que os dados do registro :bi:`Family`, associado ao registro :bi:`Person`, não caracterizando uma mudança de Endereço, necessitam ser atualizados.

    #. A partir do registro :bi:`Person` encontrado, exercutar a Ação ":bi:`Person Associate to Person (Aux)`":

        #. Parâmetros apresentados:

            * *Create new Person (Aux)*: **habilitado**
            * *Create new Address (Aux)*: **habilitado**

        #. Utilizar o botão [:bi:`Associate do Person (Aux)`] para executar a Ação.

    #. Abrir o registro :bi:`Person (Aux)` associado à Pessoa apresentado na *view* :bi:`Persons (Aux)`.

    #. Editar o registro :bi:`Address (Aux)` associado ao campo *Address (Aux)*:

        #. Aplicar manualmente nos campos *Address* do :bi:`Contact Information` as atualizações não caracterizando uma mudança de Endereço.

        #. Inserir no campo :bi:`Notes..` uma descrição das atualizações aplicadas no registro.

        #. Salvar o registro.

    #. Registro :bi:`Address (Aux)`.

        #. Não será necessário a execução de qualquer procedimento adicional no registro :bi:`Address (Aux)`.

        #. Alterar o :bi:`Register State` para ":bi:`Revised`", utilizando o botão [:bi:`Revised`].

    #. Retornar ao registro :bi:`Person (Aux)`.

    #. Editar o registro :bi:`Person (Aux)`.

        #. Preencher os campos de *Contact Information* com os dados de Endereço do registro :bi:`Address (Aux)` associado ao campo *Address*, utilizando o botão [:bi:`Get Reference Address (Aux) Data`].

        #. Inserir no campo :bi:`Notes..` uma descrição das atualizações aplicadas no registro.

        #. Salvar o registro.

    #. A partir do registro :bi:`Person (Aux)`:

        #. Não será necessário a execução de qualquer procedimento adicional no registro :bi:`Person (Aux)`.

        #. Alterar o :bi:`Register State` para ":bi:`Revised`", utilizando o botão [:bi:`Revised`].

.. toctree::
   :maxdepth: 2
   :caption: Tópicos Relacionados:
