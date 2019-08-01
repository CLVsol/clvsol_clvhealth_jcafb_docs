.. raw:: html

    <style> .red {color:red} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: bi

.. index:: Identificação da Pessoa nos Cadastros existentes

================================================
Identificação da Pessoa nos Cadastros existentes
================================================

    De posse dos dados de uma Pessoa a ser recadastrada, é necessário pesquisar pela existência prévia de registros relaltivos a essa Pessoa no **Cadastro** e/ou no **Cadastro Auxiliar**.

    Uma Pessoa será declarada como "**já cadastrada**" quando **possuir um registro prévio** no **Cadastro**, independentemente de possuir ou não um registro prévio no **Cadastro Auxiliar**.

    Uma Pessoa será declarada como "**não cadastrada**" quando **não possuir um registro prévio** no **Cadastro**, independentemente de possuir ou não um registro prévio no **Cadastro Auxiliar**. 


    #. :ref:`Procura pela Pessoa a ser recadastrada (via view Contatos)`

        Este é o método de pesquisa mais abrangente, e o preferencial quando não se dispuser do Código da Pessoa a ser pesquisada.

        A procura pela Pessoa utilizando a *view* **Contatos** é realizada quando se dispõe somente da informação do **Nome** da mesma (situação em que é incerta a existência de um cadastro para essa Pessoa).

        Neste caso não é possível realizar a pesquisa utilizando o Codigo da Pessoa.

    #. :ref:`Procura pela Pessoa a ser recadastrada (via view Persons)`
     
        Este é o método de pesquisa mais restrito, e o preferencial quando se dispuser do Código da Pessoa a ser pesquisada.

        A procura pela Pessoa utilizando a *view* :bi:`Persons` é realizada quando se dispõe da informação do **Código** dessa Pessoa (situação em que é certa a existência de um cadastro para essa Pessoa).

        Este método pode ser utilizado também para pesquisas utilizando o Nome da Pessoa, quando não se conhece o Código da Pessoa. Mas neste caso é mais conveniente usar o método anterior :ref:`Procura pela Pessoa a ser recadastrada (via view Contatos)` que é mais abrangente, e permite a identificação do Cadatro *Off* da Pessoa, quando já existente.

.. _Procura pela Pessoa a ser recadastrada (via view Contatos):

Procura pela Pessoa a ser recadastrada (via *view* **Contatos**)
----------------------------------------------------------------

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

.. _Procura pela Pessoa a ser recadastrada (via view Persons):

Procura pela Pessoa a ser recadastrada (via *view* :bi:`Persons`)
-----------------------------------------------------------------

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

.. toctree::
   :maxdepth: 2
   :caption: Índice:
