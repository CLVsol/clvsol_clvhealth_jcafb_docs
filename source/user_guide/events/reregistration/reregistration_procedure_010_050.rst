.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: Procura pelo Endereço em Contatos (Procedimento)

=====================================
Procura pelo Endereço em **Contatos**
=====================================

    #. Procurar pelo Endereço na *view* :bi:`Contatos`:

        #. Acessar a *view* **Contatos**:

            * Menu de acesso:
                * **Contatos** » **Contatos**

        #. Selecionar a **visualização em lista**.

        #. Aplicar o filtro: **Agrupar Por** » :bi:`Address Type`.

        #. Pesquisar pelo nome do Endereço:

    #. **Caso um registro dessa Família seja encontrado** com *Address Type* :bi:`Address`, independentemente da existência de um registro com *Address Type* :bi:`Address (Aux)`:

        #. Abrir o registro de contato encontrado.

        #. Acionar o botão **[** :bi:`Address` **]**.

        #. Utilizar o registro do Endereço apresentado na *view* :bi:`Addresses`.

        #. A Família é declarada como "**já cadastrada**".

    #. **Caso o registro dessa Família seja encontrado** somente com *Address Type* :bi:`Address (Aux)`:

        #. Abrir o registro de contato encontrado com *Address Type* :bi:`Address (Aux)` .

        #. Acionar o botão **[** :bi:`Address (Aux)` **]**.

        #. Utilizar o registro do Endereço apresentado na *view* :bi:`Addresses (Aux)`.

        #. A Família será declarada como **em fase de recadastramento**.

    #.  **Caso um registro dessa Família NÃO seja encontrado** com qualquer *Address Type*:

        #. A Família será declarada como "**não cadastrada**".

.. toctree::
   :maxdepth: 2
   :caption: Itens Relacionados:
