.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: Criação do Cadastro Auxiliar para uma Pessoa

================================================
Criação do **Cadastro Auxiliar** para uma Pessoa
================================================

    Se, após a execução do procedimento ":doc:`reregistration_workflow_010`" não for identificado um registro associado à Pessoa em ":bi:`Persons (Aux)`", independentemente da Pessoa ter sido declarada "**já cadastrada**" ou "**não cadastrada**", essa Pessoa deve ser cadastrada/recadastrada e, portanto, incluída no **Cadastro Auxiliar**.

    No caso de uma Pessoa "**já cadastrada**", os registros relativos a ela serão automaticamente criados no **Cadastro Auxiliar** (:bi:`Persons (Aux)`, :bi:`Addresses (Aux)` e :bi:`Families (Aux)`) a partir das informações dos registros equivalentes presentes no **Cadastro** (:bi:`Persons`, :bi:`Addresses` e :bi:`Families`).

    Neste caso, os registros em ":bi:`Addresses (Aux)`" e ":bi:`Families (Aux)`" podem já ter sido criados previamente (e serão automaticamente associados ao registro em ":bi:`Persons (Aux)`") caso uma outra Pessoa resitente no mesmo Endereço ou fazendo parte da mesma Família já esteja em processo de recadastramento. O processo ':doc:`reregistration_workflow_030`' deve ser executado em seguida.

    No caso de uma Pessoa "**não cadastrada**", os registros no **Cadastro Auxiliar** relativos a ela (:bi:`Persons (Aux)`, :bi:`Addresses (Aux)` e :bi:`Families (Aux)`) deverão ser, criados com as informações apresentadas para a Pessoa.

    Neste caso, os registros em ":bi:`Addresses (Aux)`" e ":bi:`Families (Aux)`" podem já ter sido criados previamente (e poderão ser associados ao registro em ":bi:`Persons (Aux)`") caso uma outra Pessoa resitente no mesmo Endereço ou fazendo parte da mesma Família já esteja em processo de cadastramento/recadastramento. O processo ':doc:`reregistration_workflow_040`' deve ser executado em seguida.

.. toctree::
   :maxdepth: 2
   :caption: Conteúdo:

   reregistration_workflow_020_010
   reregistration_workflow_020_020
