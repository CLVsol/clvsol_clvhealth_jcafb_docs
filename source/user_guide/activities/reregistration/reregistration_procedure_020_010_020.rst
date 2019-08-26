.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: Atualização de dados relativos à Pessoa não relacionados ao Endereço, à Família ou às Relações Familiares (Procedimento)

=========================================================================================================
Atualização de dados relativos à Pessoa não relacionados ao Endereço, à Família ou às Relações Familiares
=========================================================================================================

    Caso **exista uma Família** associada ao Endereço da Pessoa, a Pessoa continuará associada a essa Família e os itens indicados como ":green:`(Opcional)`" deverão ser considerados.

    Caso **não exista uma Família** associada ao Endereço da Pessoa, mas se opte por associar a esse Endereço uma Família, a Pessoa será associada a essa Família e os itens indicados como ":green:`(Opcional)`" deverão ser considerados.

    Caso **não exista uma Família** associada ao Endereço da Pessoa, mas se opte por não associar a esse Endereço uma Família, os itens indicados como ":green:`(Opcional)`" deverão ser desconsiderados.

    Os dados não relacionados ao Endereço, à Família ou às Relações Familiares englobam todos os dados do registro :bi:`Person` relacionado à Pessoa, **exceto**:

        * :bi:`Address`

        * :bi:`Family`

        * **Relações Familiares**:

            * :bi:`Spouse`
            * :bi:`Father`
            * :bi:`Mother`
            * :bi:`Responsible`
            * :bi:`Caregiver`

Procedimentos
-------------

    #. Procurar pelo registro :bi:`Person` associado à Pessoa utilizando um dos procedimentos:

        * :doc:`reregistration_procedure_010_010`
        * :doc:`reregistration_procedure_010_020`

    #. Confirmar que dados do registro :bi:`Person`, relacionados à Pessoa mas não relacionados ao Endereço, à Família ou às Relações Familiares, necessitam ser atualizados.

    #. Confirmar que todos os dados do registro :bi:`Address`, relacionados ao Endereço da Pessoa, serão mantidos.

    #. :green:`(Opcional)` Confirmar que todos os dados do registro :bi:`Family`, relacionados à Família da Pessoa, serão mantidos.

    #. A partir do registro :bi:`Person` encontrado, exercutar a Ação ":bi:`Person Associate to Person (Aux)`":

        #. Parâmetros apresentados:

            * *Create new Person (Aux)*: **habilitado**
            * *Create new Family (Aux)*: **habilitado**
            * *Create new Address (Aux)*: **habilitado**

        #. Utilizar o botão [:bi:`Associate do Perton (Aux)`] para executar a Ação.

    #. Abrir o registro :bi:`Person (Aux)` associado à Pessoa apresentado na *view* :bi:`Persons (Aux)`.

    #. Abrir o registro :bi:`Address (Aux)` associado ao campo *Address (Aux)*:

        #. Não será necessário a execução de qualquer procedimento adicional no registro :bi:`Address (Aux)`.

        #. Alterar o :bi:`Register State` para ":bi:`Revised`", utilizando o botão [:bi:`Revised`].

    #. Retornar ao registro :bi:`Person (Aux)`.

    #. :green:`(Opcional)` A partir do registro :bi:`Person (Aux)` exercutar a Ação ":bi:`Person (Aux) Associate to Family (Aux)`":

        #. Parâmetros apresentados:

            * *Create new Family (Aux)*: **habilitado**

        #. Utilizar o botão [:bi:`Associate do Family (Aux)`]  para executar a Ação.

    #. :green:`(Opcional)` Abrir o registro :bi:`Family (Aux)` associado à Pessoa apresentado na *view* :bi:`Families (Aux)`.

        #. Não será necessário a execução de qualquer procedimento adicional no registro :bi:`Family (Aux)`.

        #. Alterar o :bi:`Register State` para ":bi:`Revised`", utilizando o botão [:bi:`Revised`].

    #. Retornar ao registro :bi:`Person (Aux)`.

    #. Editar o registro :bi:`Person (Aux)`.

        #. Aplicar as atualizações necessárias diretamente no registro :bi:`Person (Aux)`.

        #. Inserir no campo :bi:`Notes..` uma descrição das atualizações aplicadas no registro.

        #. Salvar o registro.

    #. A partir do registro :bi:`Person (Aux)`:

        #. Não será necessário a execução de qualquer procedimento adicional no registro :bi:`Person (Aux)`.

        #. Alterar o :bi:`Register State` para ":bi:`Revised`", utilizando o botão [:bi:`Revised`].

.. toctree::
   :maxdepth: 2
   :caption: Tópicos Relacionados:
