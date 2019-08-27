.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: Atualização de dados do Endereço da Pessoa, não caracterizando uma mudança de Endereço

======================================================================================
Atualização de dados do Endereço da Pessoa, não caracterizando uma mudança de Endereço
======================================================================================

    Os dados :bi:`Address` do :bi:`Contact Information` são compartilhados por todas as Entidades do **Cadastro** (:bi:`Person`, :bi:`Address` e :bi:`Family`) e do **Cadastro Auxiliar** (:bi:`Person (Aux)`, :bi:`Address (Aux)` e :bi:`Family (Aux)`), descrevendo o Endereço dessas Entidades.

    Atualizações não caracterizando uma mudança de Endereço são aquelas que corrigem e/ou complementam a descrição do Endereço sem alterá-lo.

    No contexto do Recadastramento, essas atualizações devem ser aplicadas manualmente no regitro :bi:`Address (Aux)` e posteriormente replicadas nos registros :bi:`Family (Aux)` e :bi:`Person (Aux)`.

    Caso **exista uma Família** associada ao Endereço da Pessoa, a Pessoa continuará associada a essa Família e os itens indicados como ":green:`(Opcional)`" deverão ser considerados.

    Caso **não exista uma Família** associada ao Endereço da Pessoa, mas se opte por associar a esse Endereço uma Família, a Pessoa será associada a essa Família e os itens indicados como ":green:`(Opcional)`" deverão ser considerados.

    Caso **não exista uma Família** associada ao Endereço da Pessoa, mas se opte por não associar a esse Endereço uma Família, os itens indicados como ":green:`(Opcional)`" deverão ser desconsiderados.

Cadastro
--------

    O **Cadastro** identificado poderá conter os seguintes registros:

        * :bi:`Person`: relativo à Pessoa
        * :bi:`Address`: relativo ao Endereço da Pessoa
        * :green:`(Opcional)` :bi:`Family`: relativo à Família da Pessoa

Cadastro Auxiliar
-----------------

    O **Cadastro Auxiliar** criado poderá conter os seguintes registros:

        * :bi:`Person (Aux)`
        * :bi:`Address (Aux)`
        * :green:`(Opcional)` :bi:`Family (Aux)``

Relacionamento entre os registros dos Cadastros
-----------------------------------------------

    * :green:`(Opcional)` :bi:`Family`:

        * *Address* » :bi:`Address`
        * *Contact Information* = Dados de Endereço de :bi:`Address`

    * :bi:`Person`:

        * *Address* » :bi:`Address`
        * :green:`(Opcional)` *Family* » :bi:`Family`
        * *Contact Information* = Dados de Endereço de :bi:`Address`

    * :bi:`Address (Aux)`:

        * *Related Address* » :bi:`Address`
        * *Contact Information* = Dados de Endereço de :bi:`Address`, acrescidos das atualizações de dados do Endereço da Pessoa
        * Outros Dados = Outros Dados de :bi:`Address`

    * :green:`(Opcional)` :bi:`Family (Aux)`:

        * *Address* » :bi:`Address`
        * *Address (Aux)* » :bi:`Address (Aux)`
        * :green:`(Opcional)` *Related Family* » :bi:`Family`
        * *Contact Information* = Dados de Endereço de :bi:`Address`
        * Outros Dados = Outros Dados de :bi:`Family`

    * :bi:`Person (Aux)`:

        * *Address* » :bi:`Address`
        * *Address (Aux)* » :bi:`Address (Aux)`
        * :green:`(Opcional)` *Family* » :bi:`Family`
        * :green:`(Opcional)` *Family (Aux)* » :bi:`Family (Aux)`
        * *Related Person* » :bi:`Person`
        * *Contact Information* = Dados de Endereço de :bi:`Address`
        * Outros Dados = Outros Dados de :bi:`Person`

Fluxo de Trabalho (*Workflow*)
------------------------------

    #. **Cadastro**:

        #. Procurar pelo registro :bi:`Person` associado à Pessoa utilizando um dos métodos:

            * :doc:`reregistration_workflow_010_010`
            * :doc:`reregistration_workflow_010_020`

        #. Confirmar que dados do registro :bi:`Person`, relacionados à Pessoa, não caracterizando uma mudança de Endereço, necessitam ser atualizados.

        #. Confirmar que os dados do registro :bi:`Address`, relacionados ao Endereço da Pessoa, não caracterizando uma mudança de Endereço, necessitam ser atualizados.

        #. :green:`(Opcional)` Confirmar que os dados do registro :bi:`Family`, relacionados à Família da Pessoa, não caracterizando uma mudança de Endereço, necessitam ser atualizados.

    #. **Cadastro Auxiliar**:

        #. Os registros do  **Cadastro Auxiliar** relacionados à Pessoa devem ser criados a partir do registro :bi:`Person`, executando a Ação ":BI:`Person (Aux) Associate to Family (Aux)`":

                * A criação de :bi:`Person (Aux)`, deve ser **habilitada**.
                * A criação de :bi:`Address (Aux)`, deve ser **habilitada**.
                * A criação de :bi:`Family (Aux)`, deve ser **habilitada**.

    #. :bi:`Address (Aux)`:

        #. As atualizações dos campos *Address* do :bi:`Contact Information`, não caracterizando uma mudança de Endereço devem ser aplicadas no registro :bi:`Address (Aux)`.

    #. :green:`(Opcional)` Registro :bi:`Person (Aux)`:

        #. Caso o campo *Family (Aux)* esteja **vazio**, criar um novo registro :bi:`Family (Aux)`, executando a Ação ":bi:`Person (Aux) Associate to Family (Aux)`":

                * A criação de um registro :bi:`Family (Aux)`, deve ser **habilitada**.

    #. :green:`(Opcional)` Registro :bi:`Family (Aux)`:

        #. As atualizações dos campos *Address* do :bi:`Contact Information`, não caracterizando uma mudança de Endereço devem ser replicadas no registro :bi:`Family (Aux)`.

    #. :bi:`Person (Aux)`:

        #. As atualizações dos campos *Address* do :bi:`Contact Information`, não caracterizando uma mudança de Endereço devem ser replicadas no registro :bi:`Person (Aux)`.

    O processamento deste *Workflow* é executado utilizando o procedimento ":doc:`reregistration_procedure_020_010_030`".

.. toctree::
   :maxdepth: 2
   :caption: Procedimentos:
