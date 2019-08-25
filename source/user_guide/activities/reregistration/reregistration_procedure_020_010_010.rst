.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: Todos os dados da Pessoa serão mantidos (Procedimento)

=======================================
Todos os dados da Pessoa serão mantidos
=======================================

    #. Procurar pelo registro :bi:`Person` associado à Pessoa utilizando um dos procedimentos:

        * :doc:`reregistration_procedure_010_010`
        * :doc:`reregistration_procedure_010_020`

    #. A partir do registro :bi:`Person` encontrado, exercutar a Ação ":bi:`Person Associate to Person (Aux)`":

        #. Parâmetros apresentados:

            * *Create new Person (Aux)*: deve ser **habilitado**
            * *Create new Family (Aux)*: deve ser **habilitado**
            * *Create new Address (Aux)*: deve ser **habilitado**

        #. Utilizar o botão **[** :bi:`Associate do Perton (Aux)` **]**  para executar a Ação.

    #. Abrir o registro :bi:`Person (Aux)` associado à Pessoa apresentado na *view* :bi:`Persons (Aux)`:

    #. Abrir o registro :bi:`Address (Aux)` associado ao registro :bi:`Person (Aux)`:

        #. Não será necessário a execução de qualquer procedimento adicional no registro :bi:`Address (Aux)`.

        #. Alterar o :bi:`Register State` para ":bi:`Verified`", utilizando o botão :bi:`Revised` e em seguida o botão :bi:`Verified`.

    #. Retornar ao registro :bi:`Person (Aux)`.

    #. :green:`(Opcional)` Abrir o registro :bi:`Family (Aux)` associado ao registro :bi:`Person (Aux)`:

        #. Não será necessário a execução de qualquer procedimento adicional no registro :bi:`Family (Aux)`.

        #. Alterar o :bi:`Register State` para ":bi:`Verified`", utilizando o botão :bi:`Revised` e em seguida o botão :bi:`Verified`.

    #. Retornar ao registro :bi:`Person (Aux)`.

        #. Não será necessário a execução de qualquer procedimento adicional no registro :bi:`Person (Aux)`.

        #. Alterar o :bi:`Register State` para ":bi:`Verified`", utilizando o botão :bi:`Revised` e em seguida o botão :bi:`Verified`.

.. toctree::
   :maxdepth: 2
   :caption: Itens Relacionados:
