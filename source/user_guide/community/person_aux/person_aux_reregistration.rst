.. raw:: html

    <style> .red {color:red} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: bi

.. index:: Recadastramento de Pessoas

==============================
**Recadastramento de Pessoas**
==============================

.. _Recadastramento de Pessoas:

Recadastramento de Pessoas
--------------------------

O processo de **Recadastramento de Pessoas** é a base de todas as tarefas de planejamento da JCAFB que antecede a realização da Jornada em janeiro de cada ano, sendo concomitante ao **Recadastramento de Endereços** e ao **Recadastramento de Famílias**.

De forma geral, serão objeto do recadastramento somente Pessoas residentes em Endereços localizados na comunidade atendida no ciclo atual da JCAFB.

Pessoas residentes em outros locais, mesmo que tenham participado de alguma atividade durante o ciclo atual da JCAFB em anos anteriores, não necessitam ser recadastradas, a menos que a alteração no cadastro seja para sinalizar a mudança de status de residente para não residente na comunidade atendida ou que tenham falecido no período anterior ao recadastramento.

O recadastramento é realizado inicialmente utilizando o **Cadastro Auxiliar** (ou :bi:`Cadastro (Aux)`) composto pelos 3 objetos básicos de cadastro:

    * :bi:`Person (Aux)`,
    * :bi:`Family (Aux)` e 
    * :bi:`Address (Aux)`.

Na fase final do recadastramento, todos os dados do **Cadastro Auxiliar** são consolidados no **Cadastro Geral** (ou simplesmente :bi:`Cadastro`) composto pelos 3 objetos básicos de cadastro:

    * :bi:`Person`,
    * :bi:`Family` e 
    * :bi:`Address`,
 
 quando então todas as alterações identificadas (atualizações de dados, inclusões de Pessoas, Famílias e Endereços) são transferidas de um cadastro para o outro.

.. _Fluxo de Trabalho (Workflow) do Recadastramento de Pessoas:

Fluxo de Trabalho (*Workflow*) do Recadastramento de Pessoas
------------------------------------------------------------

Em linhas gerais, o processo de recadastramento de uma Pessoa segue o seguinte fluxo de trabalho (*workflow*):

    #. :doc:`/user_guide/community/person_aux/person_aux_reregistration_010`

        De posse dos dados de uma Pessoa a ser recadastrada, é necessário pesquisar pela existência prévia de registros relaltivos a essa Pessoa no **Cadastro** e/ou no **Cadastro Auxiliar**.

        Uma Pessoa será declarada como "**já cadastrada**" quando **possuir um registro prévio** no **Cadastro**, independentemente de possuir ou não um registro prévio no **Cadastro Auxiliar**.

        Uma Pessoa será declarada como "**não cadastrada**" quando **não possuir um registro prévio** no **Cadastro**, independentemente de possuir ou não um registro prévio no **Cadastro Auxiliar**. 

    #. :doc:`/user_guide/community/person_aux/person_aux_reregistration_020`

        Se, após a execução da :doc:`/user_guide/community/person_aux/person_aux_reregistration_010` não for identificado um registro associado à Pessoa pesquisada no **Cadastro Auxiliar**, independentemente da Pessoa ter sido declarada "**já cadastrada**" ou "**não cadastrada**", essa Pessoa deve ser cadastrada no **Cadastro Auxiliar**.

    #. :doc:`/user_guide/community/person_aux/person_aux_reregistration_030`

    #. :doc:`/user_guide/community/person_aux/person_aux_reregistration_040`

.. toctree::
   :maxdepth: 2
   :caption: Índice:

   person_aux_reregistration_010
   person_aux_reregistration_020
   person_aux_reregistration_030
   person_aux_reregistration_040
