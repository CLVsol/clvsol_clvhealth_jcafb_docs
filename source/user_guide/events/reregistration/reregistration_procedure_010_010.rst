.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: Procura pela Pessoa em Contatos (Procedimento)

===================================
Procura pela Pessoa em **Contatos**
===================================

    #. Procurar pela Pessoa na *view* :bi:`Contatos`:

        #. Acessar a *view* **Contatos**:

            * Menu de acesso:
                * **Contatos** » **Contatos**

        #. Selecionar a **visualização em lista**.

        #. Aplicar o filtro: **Agrupar Por** » :bi:`Address Type`.

        #. Pesquisar pelo nome da Pessoa:

    #. **Caso um registro dessa Pessoa seja encontrado** com *Address Type* :bi:`Person`, independentemente da existência de um registro com *Address Type* :bi:`Person (Aux)`:

        #. Abrir o registro de contato encontrado.

        #. Acionar o botão **[** :bi:`Person` **]**.

        #. Utilizar o registro da Pessoa apresentado na *view* :bi:`Persons`.

        #. A Pessoa é declarada como "**já cadastrada**".

    #. **Caso o registro dessa Pessoa seja encontrado** somente com *Address Type* :bi:`Person (Aux)`:

        #. Abrir o registro de contato encontrado com *Address Type* :bi:`Person (Aux)` .

        #. Acionar o botão **[** :bi:`Person (Aux)` **]**.

        #. Utilizar o registro da Pessoa apresentado na *view* :bi:`Persons (Aux)`.

        #. A Pessoa será declarada como **em fase de recadastramento**.

    #.  **Caso um registro dessa Pessoa NÃO seja encontrado** com qualquer *Address Type*:

        #. A Pessoa será declarada como "**não cadastrada**".

.. toctree::
   :maxdepth: 2
   :caption: Itens Relacionados:
