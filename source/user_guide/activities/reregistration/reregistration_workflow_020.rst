.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: Criação/Atualização do Cadastro Auxiliar

============================================
Criação/Atualização do **Cadastro Auxiliar**
============================================

    Se, após a pesquisa por uma **Pessoa** nos **Cadastros**, não for identificado um registro associado à Pessoa em ":bi:`Persons (Aux)`", independentemente da Pessoa ter sido declarada "**já cadastrada**" ou "**não cadastrada**", essa Pessoa deve ser cadastrada/recadastrada e, portanto, incluída no **Cadastro Auxiliar**.

    No caso de uma Pessoa "**já cadastrada**", os registros relativos a ela serão automaticamente criados no **Cadastro Auxiliar** (:bi:`Person (Aux)`, :bi:`Address (Aux)` e :bi:`Family (Aux)`) a partir das informações dos registros equivalentes presentes no **Cadastro** (:bi:`Person`, :bi:`Address` e :bi:`Familiy`).

    Neste caso, os registros ":bi:`Address (Aux)`" e ":bi:`Family (Aux)`" relativos à Pessoa podem já ter sido criados previamente (e serão automaticamente associados ao registro ":bi:`Person (Aux)`") caso uma outra Pessoa resitente no mesmo Endereço e fazendo parte da mesma Família já esteja em processo de recadastramento.

    No caso de uma Pessoa "**não cadastrada**", os registros no **Cadastro Auxiliar** relativos a ela (:bi:`Person (Aux)`, :bi:`Addresse (Aux)` e :bi:`Family (Aux)`) serão criados com as informações apresentadas para a Pessoa.

    Neste caso, os registros ":bi:`Address (Aux)`" e ":bi:`Family (Aux)`" relativos à Pessoa podem já ter sido criados previamente (e deverão ser associados ao registro ":bi:`Person (Aux)`") caso uma outra Pessoa resitente no mesmo Endereço e fazendo parte da mesma Família já esteja em processo de recadastramento.

.. toctree::
   :maxdepth: 2
   :caption: Tópicos Relacionados:

   reregistration_workflow_020_010
   reregistration_workflow_020_020
