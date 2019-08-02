.. raw:: html

    <style> .red {color:red} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: bi

.. index:: Procura por uma Pessoa utilizando a view Persons

========================================================
Procura por uma Pessoa utilizando *view* ":bi:`Persons`"
========================================================

    Este é o método de pesquisa mais restrito, e o preferencial quando se dispuser do Código da Pessoa a ser pesquisada.

    A procura pela Pessoa utilizando a *view* :bi:`Persons` é realizada quando se dispõe da informação do **Código** dessa Pessoa (situação em que é certa a existência de um cadastro para essa Pessoa).

    Este método pode ser utilizado também para pesquisas utilizando o Nome da Pessoa, quando não se conhece o Código da Pessoa. Mas neste caso é mais conveniente usar o método anterior :doc:`/user_guide/events/reregistration/reregistration_010_010` que é mais abrangente, e permite a identificação do Cadatro *Aux* da Pessoa, quando já existente.

    #. Procurar pela Pessoa na *view* :bi:`Persons`:

        #. Acessar a *view* :bi:`Persons`:

            * Menu de acesso:
                * :bi:`Community` » :bi:`Community` » :bi:`Persons`

        #. Pesquisar pela Pessoa.

    #. **Caso o registro dessa Pessoa seja encontrado** na *view* :bi:`Persons`, executar o procedimento ":doc:`/user_guide/community/person/person_associate_to_person_aux`" para o registro encontrado.

        #. Selecionar o registro da Pessoa encontrado.

        #. Exercutar a Ação ":bi:`Person Associate to Person (Aux)`":

            * Parâmetros apresentados:
                * *Create new Person (Aux)* (**Observação**: Parâmetro não modificável)
                * *Create new Family (Aux)* (**Observação**: Parâmetro não modificável)
                * *Create new Address (Aux)* (**Observação**: Parâmetro não modificável)

            #. Utilize o botão :bi:`Associate do Perton (Aux)` para executar a Ação.

    #. **Caso um registro dessa Pessoa NÃO seja encontrado** na *view* :bi:`Persons`, Procurar pela Pessoa na *view* :bi:`Persons (Aux)`:

        #. Acessar a *view* :bi:`Persons (Aux)`:

            * Menu de acesso:
                * :bi:`Community` » :bi:`Aux` » :bi:`Persons (Aux)`

        #. Pesquisar pela Pessoa.

    	#. **Caso o registro dessa Pessoa seja encontrado** na *view* :bi:`Persons (Aux)`,

    	#. **Caso um registro dessa Pessoa NÃO seja encontrado** na *view* :bi:`Persons (Aux)`,

.. toctree::
   :maxdepth: 2
   :caption: Índice:
