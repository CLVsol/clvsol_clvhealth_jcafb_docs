.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: Atualização dos dados de Family (Aux) de uma Pessoa já cadastrada

===========================================================================
Atualização dos dados de :bi:`Family (Aux)` de uma **Pessoa já cadastrada**
===========================================================================

    #. Todos os dados de Cadastro da Família serão mantidos

        Não é necessário qualquer ação de atualização do registro :bi:`Family (Aux)` da Pessoa.

    #. Atualização/Correção de alguma informação de Contato da Família exceto mudança de Endereço

        As atualizações necessárias devem ser aplicadas manualmente no registro :bi:`Family (Aux)` da Pessoa.

    #. A Pessoa mudou-se para um outro Endereço **existente** no Cadastro Geral

        O :bi:`(Reference) Address` do registro :bi:`Family (Aux)` deve ser manualmente substituido pelo :bi:`Address` do novo Endereço para o qual a Pessoa se mudou.

        O :bi:`(Reference) Address (Aux)` do registro :bi:`Family (Aux)` deve ser mantido.

        As informações de :bi:`Contact Information` devem ser subistituídas pelas informações de :bi:`Contact Information` do novo Endereço.

    #. A Pessoa mudou-se para um outro Endereço **não existente** no Cadastro Geral

        O :bi:`(Reference) Address` do registro :bi:`Family (Aux)` deve ser manualmente excluído.

        O :bi:`(Reference) Address (Aux)` do registro :bi:`FAmily (Aux)` deve ser mantido.

        As informações de :bi:`Contact Information` devem ser subistituídas pelas informações de :bi:`Contact Information` do novo Endereço.

    #. A Pessoa mudou-se para um outro Endereço **desconhecido**

        O :bi:`(Reference) Address` do registro :bi:`Family (Aux)` deve ser manualmente excluído.

        O :bi:`(Reference) Address (Aux)` do registro :bi:`Family (Aux)` deve ser mantido.

        As informações de :bi:`Contact Information` devem ser subistituídas por informações que indiquem o desconhecimento do novo Endereço.

    #. A Pessoa mudou-se para um outro Endereço **fora da comunidade** atendida pela JCAFB

        O :bi:`(Reference) Address` do registro :bi:`Family (Aux)` deve ser manualmente excluído.

        O :bi:`(Reference) Address (Aux)` do registro :bi:`Family (Aux)` deve ser mantido.

        As informações de :bi:`Contact Information` devem ser subistituídas por informações que indiquem o novo Endereço fora da comunidade.

.. toctree::
   :maxdepth: 2
   :caption: Procedimentos:
