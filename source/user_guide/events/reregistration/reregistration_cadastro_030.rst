.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: Relacionamento entre o Cadastro e o Cadastro Auxiliar

=============================================================
Relacionamento entre o **Cadastro** e o **Cadastro Auxiliar**
=============================================================

Além do inter-relacionamento entre as **Entidades** que compõem os dois Cadastros, existe o relacionamento entre as **Entidades** do **Cadastro** e as **Entidades (Aux)** do **Cadastro Auxiliar**:

    * Um registro :bi:`Person (Aux)` possui:

        * um relacionamento com um registro :bi:`Person` (:bi:`Related Person`),
        * um relacionamento com um registro :bi:`Address`
        * um relacionamento com um registro :bi:`Family`.

    * Um registro :bi:`Family (Aux)` possui:

        * um relacionamento com um registro :bi:`Family` (:bi:`Related Family`),
        * um relacionamento com um registro :bi:`Address`.

    * Um registro :bi:`Address (Aux)` possui:

        * um relacionamento com um registro :bi:`Address` (:bi:`Related Address`).

O :bi:`Address` associado a um registro :bi:`Family (Aux)` deve ser o mesmo :bi:`Address` associado a todos os registros :bi:`Person (Aux)` das Pessoas que compõem essa Família.

As informações :bi:`Address` do :bi:`Contact Information` das 3 **Entidades** relacionadas com as 3 **Entidades (Aux)** devem ser as mesmas.

.. toctree::
   :maxdepth: 2
   :caption: Itens Relacionados:
