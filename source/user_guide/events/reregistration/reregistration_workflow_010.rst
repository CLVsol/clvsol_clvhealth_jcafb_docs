.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: Procura pelas Entidades nos Cadastros existentes

====================================================
Procura pelas Entidades nos **Cadastros** existentes
====================================================

De posse dos dados de uma Pessoa, o primeiro passo é a pesquisa pela existência prévia de registros relaltivos a essa Pessoa tanto no **Cadastro** quanto no **Cadastro Auxiliar**.

Após a execução da pesquisa por uma Pessoa:

    * Uma Pessoa será declarada como "**já cadastrada**" quando **possuir um registro prévio** em ":bi:`Persons`", independentemente de possuir ou não um registro prévio em ":bi:`Persons (Aux)`".

    * Uma Pessoa será declarada como "**não cadastrada**" quando **não possuir um registro prévio** em ":bi:`Persons`", independentemente de possuir ou não um registro em ":bi:`Persons (Aux)`".

    * Uma Pessoa será declarada como **em fase de recadastramento** quando possuir um registro associado a ela em ":bi:`Persons (Aux)`" com informações que não tenham ainda sido consolidadas em (:bi:`Persons`).

Após a execução da pesquisa por uma Família:

    * Uma Família será declarada como "**já cadastrada**" quando **possuir um registro prévio** em ":bi:`Families`", independentemente de possuir ou não um registro prévio em ":bi:`Families (Aux)`".

    * Uma Família será declarada como "**não cadastrada**" quando **não possuir um registro prévio** em ":bi:`Families`", independentemente de possuir ou não um registro em ":bi:`Families (Aux)`".

    * Uma Família será declarada como **em fase de recadastramento** quando possuir um registro associado a ela em ":bi:`Families (Aux)`" com informações que não tenham ainda sido consolidadas em (:bi:`Families`).

Após a execução da pesquisa por um Endereço:

    * Um Endereço será declarada como "**já cadastrada**" quando **possuir um registro prévio** em ":bi:`Addresses`", independentemente de possuir ou não um registro prévio em ":bi:`Addresses (Aux)`".

    * Um Endereço será declarada como "**não cadastrada**" quando **não possuir um registro prévio** em ":bi:`Addresses`", independentemente de possuir ou não um registro em ":bi:`Addresses (Aux)`".

    * Um Endereço será declarada como **em fase de recadastramento** quando possuir um registro associado a ela em ":bi:`Addresses (Aux)`" com informações que não tenham ainda sido consolidadas em (:bi:`Addresses`).

.. toctree::
   :maxdepth: 2
   :caption: Conteúdo:

   reregistration_workflow_010_010
   reregistration_workflow_010_020
   reregistration_workflow_010_030
   reregistration_workflow_010_040
   reregistration_workflow_010_050
   reregistration_workflow_010_060
