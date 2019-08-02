.. raw:: html

    <style> .red {color:red} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: bi

.. index:: Procura por uma Pessoa utilizando a view Contatos

=========================================================
Procura por uma Pessoa utilizando a *view* "**Contatos**"
=========================================================

    Este é o método de pesquisa mais abrangente, e o preferencial quando não se dispuser do Código da Pessoa a ser pesquisada.

    A procura pela Pessoa utilizando a *view* **Contatos** é realizada quando se dispõe somente da informação do **Nome** da mesma (situação em que é incerta a existência de um cadastro para essa Pessoa).

    Neste caso não é possível realizar a pesquisa utilizando o Codigo da Pessoa.

    #. Acessar a *view* **Contatos**:

        * Menu de acesso:
            * **Contatos** » **Contatos**

    #. Selecionar a **visualização em lista**.

    #. Aplicar o filtro **Agrupar Por** » :bi:`Address Type`.

    #. Pesquisar pelo nome da Pessoa:

        #. Se a Pessoa for encontrada **somente** com *Address Type* :bi:`Person`:

            #. Abrir o registro de contato encontrado.

            #. Acionar o botão da *view* :bi:`Persons`.

            #. Abrir o registro da Pessoa apresentado na *view* :bi:`Persons`.

            #. Executar o procedimento ":doc:`/user_guide/community/person/person_associate_to_person_aux`" para o registro aberto:

                #. Exercutar a Ação ":bi:`Person Associate to Person (Aux)`":

                    #. Parâmetros apresentados:
                        * *Create new Person (Aux)* (**Observação**: Parâmetro não modificável)
                        * *Create new Family (Aux)* (**Observação**: Parâmetro não modificável)
                        * *Create new Address (Aux)* (**Observação**: Parâmetro não modificável)

                    #. Utilize o botão :bi:`Associate do Perton (Aux)` para executar a Ação.

                #. Abrir o registro da Pessoa apresentado na *view* :bi:`Persons (Aux)`.

        #. Se a Pessoa for encontrada com *Address Type* :bi:`Person (Aux)`:

            #. Abrir o registro de contato encontrado com *Address Type* :bi:`Person (Aux)` .

            #. Acionar o botão da *view* :bi:`Persons (Aux)`.

            #. Abrir o registro da Pessoa apresentado na *view* :bi:`Persons (Aux)`.

        #. Se a Pessoa **não for encontrada** com *Address Type* :bi:`Person` ou :bi:`Person (Aux)`:

            #. Acessar a *view* :bi:`Persons`:

                * Menu de acesso:
                    * :bi:`Community` » :bi:`Aux` » :bi:`Persons (Aux)`

            #. Criar um novo registro da Pessoa.

.. toctree::
   :maxdepth: 2
   :caption: Índice:
