.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: Procura pelas Entidades nos Cadastros existentes

========================================================
Procura pelas **Entidades** nos **Cadastros** existentes
========================================================

De posse dos dados referentes a uma Entidade, o primeiro passo é a pesquisa pela existência prévia de registros relacionados a essa Entidade tanto no **Cadastro** quanto no **Cadastro Auxiliar**.

Após a execução da pesquisa por uma Pessoa:

    * Uma Pessoa será declarada como "**já cadastrada**" quando estiver associada a um registro ":bi:`Person`", independentemente de estar ou não associada a um registro ":bi:`Person (Aux)`".

    * Uma Pessoa será declarada como "**não cadastrada**" quando não estiver associada a um registro ":bi:`Person`", independentemente de estar ou não associada a um registro ":bi:`Person (Aux)`".

    * Uma Pessoa será declarada como "**em fase de recadastramento**"" quando estiver associada a um registro ":bi:`Person (Aux)`" com informações que não tenham ainda sido consolidadas em um registro ":bi:`Person`" a ela asssociado.

    * Uma Pessoa será declarada como "**recadastrada**"" quando estiver associada a um registro ":bi:`Person (Aux)`" com informações que já tenham sido consolidadas em um registro ":bi:`Person`" a ela asssociado.

Após a execução da pesquisa por um Endereço:

    * Um Endereço será declarada como "**já cadastrado**" quando estiver associado a um registro ":bi:`Address`", independentemente de estar ou não associado a um registro ":bi:`Address (Aux)`".

    * Um Endereço será declarada como "**não cadastrado**" quando não estiver associado a um registro ":bi:`Address`", independentemente de estar ou não associado a um registro ":bi:`Address (Aux)`".

    * Um Endereço será declarada como "**em fase de recadastramento**"" quando estiver associado a um registro ":bi:`Address (Aux)`" com informações que não tenham ainda sido consolidadas em um registro ":bi:`Address`"" a ele asssociado.

    * Um Endereço será declarada como "**recadastrado**"" quando estiver associado a um registro ":bi:`Address (Aux)`" com informações que já tenham sido consolidadas em um registro ":bi:`Address`"" a ele asssociado.

.. toctree::
   :maxdepth: 2
   :caption: Tópicos Relacionados:

   reregistration_workflow_010_010
   reregistration_workflow_010_020
   reregistration_workflow_010_030
   reregistration_workflow_010_040
   reregistration_workflow_010_050
   reregistration_workflow_010_060
