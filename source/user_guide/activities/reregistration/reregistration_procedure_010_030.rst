.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: Procura por uma Família em Contatos (Procedimento)

=======================================
Procura por uma Família em **Contatos**
=======================================

    * *Workflow*: ":doc:`reregistration_workflow_010_030`".

    #. Procurar pela Família na *view* :bi:`Contatos`:

        #. Acessar a *view* **Contatos**:

            * Menu de acesso:
                * **Contatos** » **Contatos**

        #. Selecionar a **visualização em lista**.

        #. Aplicar o filtro: **Agrupar Por** » :bi:`Address Type`.

        #. Pesquisar pela Família.

    #. **Caso um registro associado a essa Família seja encontrado** com *Address Type* ":bi:`Family`", independentemente da existência ou não de um registro com *Address Type* ":bi:`Family (Aux)`":

        #. Abrir o registro de contato encontrado com *Address Type* ":bi:`Family`.

        #. Acionar o botão **[** :bi:`Family` **]**.

        #. Utilizar o registro associado à Família apresentado na *view* :bi:`Families`.

        #. A Família é declarada como "**já cadastrada**".

    #. **Caso um registro associado a essa Família seja encontrado** somente com *Address Type* ":bi:`Family (Aux)`":

        #. Abrir o registro de contato encontrado com *Address Type* ":bi:`Family (Aux)`".

        #. Acionar o botão **[** :bi:`Family (Aux)` **]**.

        #. Utilizar o registro associado à Família apresentado na *view* :bi:`Families (Aux)`.

        #. A Família será declarada como **em fase de recadastramento**.

    #.  **Caso um registro associado a essa Família NÃO seja encontrado** com qualquer *Address Type*:

        #. A Família será declarada como "**não cadastrada**".

.. toctree::
   :maxdepth: 2
   :caption: Itens Relacionados:
