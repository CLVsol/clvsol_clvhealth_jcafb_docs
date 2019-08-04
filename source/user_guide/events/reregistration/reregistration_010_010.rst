.. raw:: html

    <style> .red {color:red} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: bi

.. index:: Procura pela Pessoa utilizando a view Contatos

======================================================
Procura pela Pessoa utilizando a *view* '**Contatos**'
======================================================

    Este é o método de pesquisa mais abrangente, e o preferencial quando não se dispuser do Código da Pessoa a ser pesquisada.

    A procura pela Pessoa utilizando a *view* **Contatos** é realizada quando se dispõe somente da informação do **Nome** da mesma (situação em que é incerta a existência de um cadastro para essa Pessoa).

    Neste caso não é possível realizar a pesquisa utilizando o Codigo da Pessoa.

    #. Acessar a *view* **Contatos**:

        * Menu de acesso:
            * **Contatos** » **Contatos**

    #. Selecionar a **visualização em lista**.

    #. Aplicar o filtro: **Agrupar Por** » :bi:`Address Type`.

    #. Pesquisar pelo nome da Pessoa:

        #. Se a Pessoa for encontrada com *Address Type* :bi:`Person`, independentemente da existência de um registro com *Address Type* :bi:`Person (Aux)`:

            #. Abrir o registro de contato encontrado.

            #. Acionar o botão **[** :bi:`Persons` **]**.

            #. Abrir o registro da Pessoa apresentado na *view* :bi:`Persons`.

            #. Executar o procecimento ":doc:`reregistration_020_010`".

        #. Se a Pessoa for encontrada somente com *Address Type* :bi:`Person (Aux)`:

            #. Abrir o registro de contato encontrado com *Address Type* :bi:`Person (Aux)` .

            #. Acionar o botão **[** :bi:`Persons (Aux)` **]**.

            #. Abrir o registro da Pessoa apresentado na *view* :bi:`Persons (Aux)`.

            #. Executar o procecimento ":doc:`reregistration_020_020`".

        #. Se a Pessoa **não for encontrada**:

            #. Acessar a *view* :bi:`Persons (Aux)`:

                * Menu de acesso:
                    * :bi:`Community` » :bi:`Aux` » :bi:`Persons (Aux)`

            #. Criar um novo registro para a Pessoa.

            #. Executar o procecimento ":doc:`reregistration_020_020`".

.. toctree::
   :maxdepth: 2
   :caption: Itens Relacionados:
