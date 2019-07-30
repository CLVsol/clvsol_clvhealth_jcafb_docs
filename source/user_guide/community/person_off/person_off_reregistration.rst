.. raw:: html

    <style> .red {color:red} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: bi

.. index:: Recadastramento de Pessoas

==============================
**Recadastramento de Pessoas**
==============================

.. _(1) Procura pela Pessoa a ser recadastrada:

(1) Procura pela Pessoa a ser recadastrada (via **Contatos**)
-------------------------------------------------------------

    #. Procurar pela Pessoa a ser recadastrada na *view* **Contatos**:

        #. Acessar a *view* **Contatos**:

            * Menu de acesso:
                * **Contatos** » **Contatos**

        #. Selecionar a **visualização em lista**.

        #. Aplicar o filtro **Agrupar Por** » :bi:`Address Type`.

        #. Pesquisar pelo nome da Pessoa a ser recadastrada:

            #. Se a Pessoa for encontrada **somente** com *Address Type* :bi:`Person`:

                #. Abrir o registro de contato encontrado.

                #. Acionar o botão da *view* :bi:`Persons`.

                #. Abrir o registro da Pessoa apresentado na *view* :bi:`Persons`.

                #. Executar o procedimento ":doc:`/user_guide/community/person/person_associate_to_person_off`" para o registro aberto:

                    #. Exercutar a Ação ":bi:`Person Associate to Person (Off)`":

                        #. Parâmetros apresentados:
                            * *Create new Person (Off)* (**Observação**: Parâmetro não modificável)
                            * *Create new Family (Off)* (**Observação**: Parâmetro não modificável)
                            * *Create new Address (Off)* (**Observação**: Parâmetro não modificável)

                        #. Utilize o botão :bi:`Associate do Perton (Off)` para executar a Ação.

                    #. Abrir o registro da Pessoa apresentado na *view* :bi:`Persons (Off)`.

            #. Se a Pessoa for encontrada com *Address Type* :bi:`Person (Off)`:

                #. Abrir o registro de contato encontrado com *Address Type* :bi:`Person (Off)` .

                #. Acionar o botão da *view* :bi:`Persons (Off)`.

                #. Abrir o registro da Pessoa apresentado na *view* :bi:`Persons (Off)`.

            #. Se a Pessoa **não for encontrada** com *Address Type* :bi:`Person` ou :bi:`Person (Off)`:

                #. Acessar a *view* :bi:`Persons`:

                    * Menu de acesso:
                        * :bi:`Community` » :bi:`Off` » :bi:`Persons (Off)`

                #. Criar um novo registro da Pessoa a ser recadastrada.

(2) Procura pela Pessoa a ser recadastrada (via :bi:`Persons`)
--------------------------------------------------------------

    #. Procurar pela Pessoa a ser recadastrada na *view* :bi:`Persons`:

        #. Acessar a *view* :bi:`Persons`:

            * Menu de acesso:
                * :bi:`Community` » :bi:`Community` » :bi:`Persons`

        #. Pesquisar pela Pessoa a ser recadastrada.

    #. **Caso o registro dessa Pessoa seja encontrado** na *view* :bi:`Persons`, executar o procedimento ":doc:`/user_guide/community/person/person_associate_to_person_off`" para o registro encontrado.

        #. Selecionar o registro da Pessoa encontrado.

        #. Exercutar a Ação ":bi:`Person Associate to Person (Off)`":

            * Parâmetros apresentados:
                * *Create new Person (Off)* (**Observação**: Parâmetro não modificável)
                * *Create new Family (Off)* (**Observação**: Parâmetro não modificável)
                * *Create new Address (Off)* (**Observação**: Parâmetro não modificável)

            #. Utilize o botão :bi:`Associate do Perton (Off)` para executar a Ação.

    #. **Caso um registro dessa Pessoa NÃO seja encontrado** na *view* :bi:`Persons`, Procurar pela Pessoa a ser recadastrada na *view* :bi:`Persons (Off)`:

        #. Acessar a *view* :bi:`Persons (Off)`:

            * Menu de acesso:
                * :bi:`Community` » :bi:`Off` » :bi:`Persons (Off)`

        #. Pesquisar pela Pessoa a ser recadastrada.

    	#. **Caso o registro dessa Pessoa seja encontrado** na *view* :bi:`Persons (Off)`,

    	#. **Caso um registro dessa Pessoa NÃO seja encontrado** na *view* :bi:`Persons (Off)`,

.. _(2) Recadastramento de uma Pessoa já existente:

(3) Recadastramento de uma Pessoa já existente
----------------------------------------------

.. _(3) Recadastramento de uma nova Pessoa:

(4) Recadastramento de uma nova Pessoa
--------------------------------------

.. toctree::
   :maxdepth: 2
   :caption: Ações:
