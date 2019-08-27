.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: Atualização de dados do Endereço da Pessoa, não caracterizando uma mudança de Endereço (Procedimento)

======================================================================================
Atualização de dados do Endereço da Pessoa, não caracterizando uma mudança de Endereço
======================================================================================

    * *Workflow*: ":doc:`reregistration_workflow_020_010_030`".

     Os dados :bi:`Address` do :bi:`Contact Information` são compartilhados por todas as Entidades do **Cadastro** (:bi:`Person`, :bi:`Address` e :bi:`Family`) e do **Cadastro Auxiliar** (:bi:`Person (Aux)`, :bi:`Address (Aux)` e :bi:`Family (Aux)`), descrevendo o Endereço dessas Entidades.

    Atualizações não caracterizando uma mudança de Endereço são aquelas que corrigem e/ou complementam a descrição do Endereço sem alterá-lo.

    No contexto do Recadastramento, essas atualizações devem ser aplicadas manualmente no regitro :bi:`Address (Aux)` e posteriormente replicadas nos registros :bi:`Family (Aux)` e :bi:`Person (Aux)`.

    Caso **exista uma Família** associada ao Endereço da Pessoa, a Pessoa continuará associada a essa Família e os itens indicados como ":green:`(Opcional)`" deverão ser considerados.

    Caso **não exista uma Família** associada ao Endereço da Pessoa, mas se opte por associar a esse Endereço uma Família, a Pessoa será associada a essa Família e os itens indicados como ":green:`(Opcional)`" deverão ser considerados.

    Caso **não exista uma Família** associada ao Endereço da Pessoa, mas se opte por não associar a esse Endereço uma Família, os itens indicados como ":green:`(Opcional)`" deverão ser desconsiderados.

Procedimentos
-------------

    #. Procurar pelo registro :bi:`Person` associado à Pessoa utilizando um dos procedimentos:

        * :doc:`reregistration_procedure_010_010`
        * :doc:`reregistration_procedure_010_020`

    #. Confirmar que dados do registro :bi:`Person`, relacionados à Pessoa, não caracterizando uma mudança de Endereço, necessitam ser atualizados.

    #. Confirmar que os dados do registro :bi:`Address`, relacionados ao Endereço da Pessoa, não caracterizando uma mudança de Endereço, necessitam ser atualizados.

    #. :green:`(Opcional)` Confirmar que os dados do registro :bi:`Family`, relacionados à Família da Pessoa, não caracterizando uma mudança de Endereço, necessitam ser atualizados.

    #. A partir do registro :bi:`Person` encontrado, exercutar a Ação ":bi:`Person Associate to Person (Aux)`":

        #. Parâmetros apresentados:

            * *Create new Person (Aux)*: **habilitado**
            * *Create new Family (Aux)*: **habilitado**
            * *Create new Address (Aux)*: **habilitado**

        #. Utilizar o botão [:bi:`Associate do Perton (Aux)`] para executar a Ação.

    #. Abrir o registro :bi:`Person (Aux)` associado à Pessoa apresentado na *view* :bi:`Persons (Aux)`.

    #. Editar o registro :bi:`Address (Aux)` associado ao campo *Address (Aux)*:

        #. Aplicar manualmente nos campos *Address* do :bi:`Contact Information` as atualizações não caracterizando uma mudança de Endereço.

        #. Inserir no campo :bi:`Notes..` uma descrição das atualizações aplicadas no registro.

        #. Salvar o registro.

    #. Registro :bi:`Address (Aux)`.

        #. Não será necessário a execução de qualquer procedimento adicional no registro :bi:`Address (Aux)`.

        #. Alterar o :bi:`Register State` para ":bi:`Revised`", utilizando o botão [:bi:`Revised`].

    #. Retornar ao registro :bi:`Person (Aux)`.

    #. :green:`(Opcional)` A partir do registro :bi:`Person (Aux)` exercutar a Ação ":bi:`Person (Aux) Associate to Family (Aux)`":

        #. Parâmetros apresentados:

            * *Create new Family (Aux)*: **habilitado**

        #. Utilizar o botão [:bi:`Associate do Family (Aux)`]  para executar a Ação.

    #. :green:`(Opcional)` Editar o registro :bi:`Family (Aux)` associado à Pessoa apresentado na *view* :bi:`Families (Aux)`:

        #. Preencher os campos de *Contact Information* com os dados de Endereço do registro :bi:`Address (Aux)` associado ao campo *Address*, utilizando o botão [:bi:`Get Reference Address (Aux) Data`].

        #. Inserir no campo :bi:`Notes..` uma descrição das atualizações aplicadas no registro.

        #. Salvar o registro.

    #. :green:`(Opcional)` Registro :bi:`Family (Aux)`:

        #. Não será necessário a execução de qualquer procedimento adicional no registro :bi:`Family (Aux)`.

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
