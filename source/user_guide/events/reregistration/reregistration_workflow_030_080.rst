.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: [Pessoa já cadastrada] A Pessoa está ausente da comunidade atendida pela JCAFB

==============================================================================
[Pessoa já cadastrada] A Pessoa está ausente da comunidade atendida pela JCAFB
==============================================================================

.. _Cadastro Auxiliar (8):

Cadastro Auxiliar
-----------------

    O **Cadastro Auxiliar** criado automáticamente poderá ser composto pelas seguintes **Entidades (Aux)**:

        * :bi:`Person (Aux)`:

            * A criação de :bi:`Person (Aux)`, **deve ser habilitada**.

        * :bi:`Address (Aux)`:

            * A criação de :bi:`Address (Aux)`, **deve ser habilitada**.

        * :bi:`Family (Aux)`:

            * A criação de :bi:`Family (Aux)`, **deve ser habilitada**.

    O relacionamento entre os diversos registros dos Cadastros será o seguinte (quando existirem os registros, como indicado anteriormente):

        * :bi:`Person (Aux)`: 

            * :bi:`Related Person` » :bi:`Person`
            * :bi:`(Reference) Address` » :bi:`Address`
            * :bi:`(Reference) Address (Aux)` » :bi:`Address (Aux)`
            * :bi:`Family` » :bi:`Family`
            * :bi:`Family (Aux)` » :bi:`Family (Aux)`
            * :bi:`Contact Information` = Dados do registro :bi:`Address`
            * Outros Dados = Outros Dados do registro :bi:`Person`

        * :bi:`Address (Aux)`:

            * :bi:`Related Address` » :bi:`Address`
            * :bi:`Contact Information` = Dados do registro :bi:`Address`
            * Outros Dados = Outros Dados do registro :bi:`Address`

        * :bi:`Family (Aux)`:

            * :bi:`Related Family` » :bi:`Family`
            * :bi:`(Reference) Address` » :bi:`Address`
            * :bi:`(Reference) Address (Aux)` » :bi:`Address (Aux)`
            * :bi:`Contact Information` = Dados do registro :bi:`Address`
            * Outros Dados = Outros Dados do registro :bi:`Family`

Criações/Atualizações
---------------------

    #. **Cadastro Auxiliar**:

        #. O **Cadastro Auxiliar** relacionado à Pessoa deve ser criado automaticamente conforme as condições descritas em ":ref:`Cadastro Auxiliar (8)`".

    #. :bi:`Address (Aux)`:

        #. Não será necessário qualquer ação de atualização do registro :bi:`Address (Aux)` relacionado à Pessoa.

    #. :bi:`Family (Aux)`:

        #. Não será necessário qualquer ação de atualização do registro :bi:`Family (Aux)` relacionado à Pessoa.

    #. :bi:`Person (Aux)`:

        #. :red:`(Precisa ser Modificado)` Não será necessário qualquer ação de atualização do registro :bi:`Person (Aux)` relacionado à Pessoa.

        #. :red:`(Precisa ser Modificado)` Indicar de alguma forma que a Pessoa está ausente da comunidade atendida pela JCAFB.

.. toctree::
   :maxdepth: 2
   :caption: Procedimentos:
