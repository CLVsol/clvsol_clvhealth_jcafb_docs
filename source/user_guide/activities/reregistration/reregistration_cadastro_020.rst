.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: Cadastro Auxiliar

=====================
**Cadastro Auxiliar**
=====================

O **Cadastro Auxiliar** é composto pelas 3 **Entidades (Aux)**:

    * :bi:`Person (Aux)`:

        * Um registro :bi:`Person (Aux)` possui, além dos parâmetros específicos a uma Pessoa:

            * as informações de :bi:`Contact Information`,
            * um relacionamento com um registro :bi:`Address (Aux)`,
            * um relacionamento com um registro :bi:`Family (Aux)`.

    * :bi:`Family (Aux)`:

        * Um registro :bi:`Family (Aux)` possui, além dos parâmetros específicos a uma Família:

            * as informações de :bi:`Contact Information`,
            * um relacionamento com um registro :bi:`Address (Aux)`.

    * :bi:`Address (Aux)`:

        * Um registro :bi:`Address (Aux)` possui, além dos parâmetros específicos a um Endereço:

            * as informações de :bi:`Contact Information`.

O :bi:`Address (Aux)` associado a um registro :bi:`Family (Aux)` deve ser o mesmo :bi:`Address (Aux)` associado a todos os registros :bi:`Person (Aux)` das Pessoas que compõem essa Família.

As informações de Endereço do :bi:`Contact Information` das 3 **Entidades (Aux)** inter-relacionadas devem ser idênticas.

.. toctree::
   :maxdepth: 2
   :caption: Itens Relacionados:
