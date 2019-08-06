.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: Os Cadastros

================
Os **Cadastros**
================

Os **Cadastros** são os elementos centrais de percistência de todas as informações geradas e coletadas durante a realização das atividades da JCAFB.


.. _Cadastro Básico (Cadastro):

Cadastro Básico (**Cadastro**)
------------------------------

O **Cadastro Básico**, ou simplesmente **Cadastro**, é composto pelas 3 **Entidades de Cadastro**, ou simplesmente **Entidades**, inter-relacionadas:

    * :bi:`Person`,
    * :bi:`Family` e 
    * :bi:`Address`,

Um registro :bi:`Person` possui, além dos parâmetros específicos a uma Pessoa e os parâmetros de :bi:`Contact Information`, um relacionamento com um registro :bi:`Address` e um relacionamento com um registro :bi:`Family`.

Um registro :bi:`Family` possui, além dos parâmetros específicos a uma Família e os parâmetros de :bi:`Contact Information`, um relacionamento com um registro :bi:`Address`.

O :bi:`Address` associado a um registro :bi:`Family` deve ser o mesmo :bi:`Address` associado a todos os registros :bi:`Person` das Pessoas que compõem essa Família.

Um registro :bi:`Address` possui, somente os parâmetros específicos a um Endereço e os parâmetros de :bi:`Contact Information`.

As informações :bi:`Address` do :bi:`Contact Information` das 3 Entidades relacionadas entre si devem ser as mesmas. Esta é a forma que permite manter com mais facilidade a consistência do relacionamento entre as 3 Entidades.

.. _Cadastro Auxiliar:

**Cadastro Auxiliar**
---------------------

O **Cadastro Auxiliar** é composto pelas 3 **Entidades** adicionais, inter-relacionadas:

    * :bi:`Person (Aux)`,
    * :bi:`Family (Aux)` e 
    * :bi:`Address (Aux)`,

Um registro :bi:`Person (Aux)` possui, além dos parâmetros específicos a uma Pessoa e os parâmetros de :bi:`Contact Information`, um relacionamento com um registro :bi:`Address (Aux)` e um relacionamento com um registro :bi:`Family (Aux)`.

Um registro :bi:`Family (Aux)` possui, além dos parâmetros específicos a uma Família (Aux) e os parâmetros de :bi:`Contact Information`, um relacionamento com um registro :bi:`Address (Aux)`.

O :bi:`Address (Aux)` associado a um registro :bi:`Family (Aux)` deve ser o mesmo :bi:`Address (Aux)` associado a todos os registros :bi:`Person (Aux)` das Pessoas (Aux) que compõem essa Família (Aux).

Um registro :bi:`Address (Aux)` possui, somente os parâmetros específicos a um Endereço (Aux) e os parâmetros de :bi:`Contact Information`.

As informações :bi:`Address` do :bi:`Contact Information` das 3 Entidades (Aux) relacionadas entre si devem ser as mesmas. Esta é a forma que permite manter com mais facilidade a consistência do relacionamento entre as 3 Entidades (Aux).

.. _Relacionamento entre o Cadastro e o Cadastro Auxiliar:

Relacionamento entre o **Cadastro** e o **Cadastro Auxiliar**
-------------------------------------------------------------

Além do inter-relacionamento entre as Entidades que compõem cada um dos Cadastros, existe o relacionamento entre as Entidades do **Cadastro** e as Entidades do **Cadastro Auxiliar**.

Um registro :bi:`Person (Aux)` possui um relacionamento com um registro :bi:`Person` (:bi:`Related Person`), um relacionamento com um registro :bi:`Address` e um relacionamento com um registro :bi:`Family`.

Um registro :bi:`Family (Aux)` possui um relacionamento com um registro :bi:`Family` (:bi:`Related Family`) e um relacionamento com um registro :bi:`Address`.

O :bi:`Address` associado a um registro :bi:`Family (Aux)` deve ser o mesmo :bi:`Address` associado a todos os registros :bi:`Person (Aux)` das Pessoas (Aux) que compõem essa Família (Aux).

Um registro :bi:`Address (Aux)` possui um relacionamento com um registro :bi:`Address` (:bi:`Related Address`).

As informações :bi:`Address` do :bi:`Contact Information` das 3 Entidades relacionadas com as 3 Entidades (Aux) devem ser as mesmas. Esta é a forma que permite manter com mais facilidade a consistência do relacionamento entre as Entidades dos dois Cadastros.

.. toctree::
   :maxdepth: 2
   :caption: Itens Relacionados:
