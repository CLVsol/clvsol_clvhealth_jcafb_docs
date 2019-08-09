.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: Cadastro Básico (Cadastro)

==============================
Cadastro Básico (**Cadastro**)
==============================

O **Cadastro Básico** (**Cadastro**) é composto pelas 3 **Entidades de Cadastro** inter-relacionadas:

    * :bi:`Person`:

        * Um registro :bi:`Person` possui, além dos parâmetros específicos a uma Pessoa:

            * as informações de :bi:`Contact Information`,
            * um relacionamento com um registro :bi:`Address`,
            * um relacionamento com um registro :bi:`Family`.

    * :bi:`Family`:

        * Um registro :bi:`Family` possui, além dos parâmetros específicos a uma Família:

            * as informações de :bi:`Contact Information`,
            * um relacionamento com um registro :bi:`Address`.

    * :bi:`Address`:

        * Um registro :bi:`Address` possui, além dos parâmetros específicos a um Endereço:

            * as informações de :bi:`Contact Information`.

O :bi:`Address` associado a um registro :bi:`Family` deve ser o mesmo :bi:`Address` associado a todos os registros :bi:`Person` das Pessoas que compõem essa Família.

As informações :bi:`Address` do :bi:`Contact Information` das 3 **Entidades** inter-relacionadas devem ser identicas.

.. toctree::
   :maxdepth: 2
   :caption: Itens Relacionados:
