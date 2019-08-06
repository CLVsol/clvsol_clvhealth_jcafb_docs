.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: Procura pela Pessoa nos Cadastros existentes

================================================
Procura pela Pessoa nos **Cadastros** existentes
================================================

    De posse dos dados de uma Pessoa, o primeiro passo é a pesquisa pela existência prévia de um registro relaltivo a essa Pessoa tanto em ":bi:`Persons`" quanto em ":bi:`Persons (Aux)`".

    Uma Pessoa será declarada como "**já cadastrada**" quando **possuir um registro prévio** em ":bi:`Person`", independentemente de possuir ou não um registro prévio em ":bi:`Person (Aux)`".

    Uma Pessoa será declarada como "**não cadastrada**" quando **não possuir um registro prévio** em ":bi:`Persons`", independentemente de possuir ou não um registro em ":bi:`Persons (Aux)`".

    Uma Pessoa será declarada como **em fase de recadastramento** quando possuir um registro associado a ela em ":bi:`Persons (Aux)`" com informações que não tenham ainda sido consolidadas em (:bi:`Persons`).

.. toctree::
   :maxdepth: 2
   :caption: Conteúdo:

   reregistration_workflow_010_010
   reregistration_workflow_010_020
