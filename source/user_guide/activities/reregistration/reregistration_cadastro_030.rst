.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: Relacionamento entre o Cadastro Auxiliar e o Cadastro

=============================================================
Relacionamento entre o **Cadastro Auxiliar** e o **Cadastro**
=============================================================

Além do inter-relacionamento entre as **Entidades** que compõem cada um dos Cadastros, existe o relacionamento entre as **Entidades (Aux)** do **Cadastro Auxiliar** e as **Entidades** do **Cadastro**:

    * Um registro :bi:`Person (Aux)` possui:

        * um relacionamento com um registro :bi:`Person` (:bi:`Related Person`),
        * um relacionamento com um registro :bi:`Address`
        * um relacionamento com um registro :bi:`Family`.

    * Um registro :bi:`Address (Aux)` possui:

        * um relacionamento com um registro :bi:`Address` (:bi:`Related Address`).

As informações de Endereço do :bi:`Contact Information` das 2 **Entidades (Aux)** relacionadas com as 3 **Entidades** devem ser as mesmas.

.. toctree::
   :maxdepth: 2
   :caption: Itens Relacionados:
