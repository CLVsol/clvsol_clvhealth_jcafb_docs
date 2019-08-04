.. raw:: html

    <style> .red {color:red} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: bi

.. index:: Recadastramento

===================
**Recadastramento**
===================

.. _O Processo de Recadastramento:

O Processo de Recadastramento
-----------------------------

O Processo de **Recadastramento** é a base das atividades de planejamento e preparação, que antecedem todas as demais atividades da JCAFB em janeiro do ano seguinte.

O Processo de **Recadastramento** é baseado no processo de **Recadastramento de Pessoas**, śendo este concomitante ao **Recadastramento de Endereços** e ao **Recadastramento de Famílias**.

De forma geral, serão objetos do recadastramento somente Pessoas residentes em Endereços localizados na comunidade atendida no ciclo atual da JCAFB.

Pessoas residentes em outros locais, mesmo que tenham participado em anos anteriores de alguma atividade durante o ciclo atual da JCAFB, não necessitam ser recadastradas, a menos que a alteração no cadastro seja para sinalizar a mudança de status de residente para não residente na comunidade atendida ou que tenham falecido em período anterior ao recadastramento.

O recadastramento é realizado inicialmente utilizando o **Cadastro Auxiliar** (ou **Cadastro (Aux)**) composto pelos 3 objetos básicos do Cadastro:

    * :bi:`Person (Aux)`,
    * :bi:`Family (Aux)` e 
    * :bi:`Address (Aux)`.

Posteriormenbte, todos os dados do **Cadastro Auxiliar** são consolidados no **Cadastro Básico** (ou simplesmente **Cadastro**) composto pelos 3 objetos básicos de Cadastro:

    * :bi:`Person`,
    * :bi:`Family` e 
    * :bi:`Address`,
 
 Essa consolidação se dá quando todas as alterações identificadas (atualizações de dados, inclusões de Pessoas, Famílias e Endereços) são transferidas do Cadastro Auxiliar para o Cadastro Básico.

.. _Fluxo de Trabalho (Workflow) do Recadastramento:

Fluxo de Trabalho (*Workflow*) do Recadastramento
-------------------------------------------------

Em linhas gerais, o processo de recadastramento segue o seguinte Fluxo de Trabalho (*Workflow*):

    #. :doc:`reregistration_010`

        De posse dos dados de uma Pessoa a ser recadastrada, é necessário pesquisar pela existência prévia de registros relaltivos a essa Pessoa no **Cadastro** e/ou no **Cadastro Auxiliar**.

        Uma Pessoa será declarada como "**já cadastrada**" quando **possuir um registro prévio** no **Cadastro**, independentemente de possuir ou não um registro prévio no **Cadastro Auxiliar**.

        Uma Pessoa será declarada como "**não cadastrada**" quando **não possuir um registro prévio** no **Cadastro**, independentemente de possuir ou não um registro prévio no **Cadastro Auxiliar**. 

    #. :doc:`reregistration_020`

        Se, após a execução da ":doc:`reregistration_010`" não for identificado um registro associado à Pessoa pesquisada no **Cadastro Auxiliar**, independentemente da Pessoa ter sido declarada "**já cadastrada**" ou "**não cadastrada**", essa Pessoa deve ser cadastrada/recadastrada no **Cadastro Auxiliar**.

    #. :doc:`reregistration_030`

    #. :doc:`reregistration_040`

.. toctree::
   :maxdepth: 2
   :caption: Itens Relacionados:
