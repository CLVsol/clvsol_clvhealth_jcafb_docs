.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: A Pessoa reside em um Endereço já cadastrado

============================================
A Pessoa reside em um Endereço já cadastrado
============================================

    Caso **exista uma Família** associada ao Endereço da Pessoa, a Pessoa será associada a essa Família e os itens indicados como ":green:`(Opcional)`" deverão ser considerados.

    Caso **não exista uma Família** associada ao Endereço da Pessoa, mas se opte por associar a esse Endereço uma Família, a Pessoa será associada a essa Família e os itens indicados como ":green:`(Opcional)`" deverão ser considerados.

    Caso **não exista uma Família** associada ao Endereço da Pessoa, mas se opte por não associar a esse Endereço uma Família, os itens indicados como ":green:`(Opcional)`" deverão ser desconsiderados.

Cadastro
--------

    O **Cadastro** identificado poderá conter os seguintes registros:

        * :bi:`Address`: relativo ao Endereço da Pessoa
        * :green:`(Opcional)` :bi:`Family`: relativo ao Endereço da Pessoa

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

    * :bi:`Address (Aux)`:

        * *Related Address* » :bi:`Address`
        * *Contact Information* = Dados de Endereço de :bi:`Address`
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
        * *Related Person* » **vazio**
        * *Contact Information* = Dados de Endereço de :bi:`Address`
        * Outros Dados = Outros Dados informados para a Pessoa

Fluxo de Trabalho (*Workflow*)
------------------------------

    #. *View* **Contatos**:

        #. Procurar pelo(s) registro(s) :bi:`Person` e/ou :bi:`Person (Aux)` associado(s) à Pessoa utilizando o método:

            * :doc:`reregistration_workflow_010_010`

        **Observação 1**: Nenhum registro :bi:`Person` deverá ser encontrado.

        **Observação 2**: Nenhum registro :bi:`Person (Aux)` deverá ser encontrado, a menos que a nova Pessoa já esteja em processo de recadastramento.

    #. *View* **Contatos** ou *View* :bi:`Addresses`:

        #. Procurar pelo registro :bi:`Address` associado ao Endereço informado para a Pessoa utilizando um dos métodos:

            * :doc:`reregistration_workflow_010_050`
            * :doc:`reregistration_workflow_010_060`

        #. Confirmar que todos os dados do registro :bi:`Address`, relacionado ao Endereço da Pessoa, serão mantidos.

        #. Verificar a existência de um registro :bi:`Family` associado ao registro :bi:`Address`.

        #. :green:`(Opcional)` Confirmar que todos os dados do registro :bi:`Family`, relacionado ao Endereço da Pessoa, serão mantidos.

    #. *View* :bi:`Person (Aux)`:

        #. Criar manualmente um novo registro :bi:`Person (Aux)`, preenchido com as informações apresentadas para a Pessoa, exceto as informaçôes do Endereço e da Família.

    #. Registro :bi:`Person (Aux)`:

        #. Associar o registro :bi:`Address` encontrado ao campo *Address*.

        #. Preencher os campos de *Contact Information* com os dados de Endereço do registro :bi:`Address`.

    #. Registro :bi:`Person (Aux)`:

        #. Criar um novo registro :bi:`Address (Aux)`, executando a Ação ":bi:`Person (Aux) Associate to Address (Aux)`":

            * A criação de um registro :bi:`Address (Aux)`, deve ser **habilitada**.

    #. Registro :bi:`Address (Aux)`:

        #. Não será necessário qualquer ação de atualização do registro :bi:`Address (Aux)`.

    #. :green:`(Opcional)` Registro :bi:`Person (Aux)`:

        #. Associar o registro :bi:`Family` (associado ao registro :bi:`Address`) ao campo *Family*, executando a Ação ":bi:`Person (Aux) Associate to Family`".

        #. Criar um novo registro :bi:`Family (Aux)`, executando a Ação ":bi:`Person (Aux) Associate to Family (Aux)`":

                * A criação de um registro :bi:`Family (Aux)`, deve ser **habilitada**.

    #. :green:`(Opcional)` Registro :bi:`Family (Aux)`:

        #. Não será necessário qualquer ação de atualização do registro :bi:`Family (Aux)`.

    O processamento deste *Workflow* é executado utilizando o procedimento ":doc:`reregistration_procedure_020_020_010`".

.. toctree::
   :maxdepth: 2
   :caption: Itens Relacionados:
