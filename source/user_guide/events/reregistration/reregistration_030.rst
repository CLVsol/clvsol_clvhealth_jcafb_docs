.. raw:: html

    <style> .red {color:red} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: bi

.. index:: Atualização do Cadastro Auxiliar de uma Pessoa "já cadastrada"

==================================================================
Atualização do Cadastro Auxiliar de uma Pessoa "**já cadastrada**"
==================================================================

    #. :doc:`reregistration_030_010`

        #. Todos os dados de Cadastro da Pessoa serão mantidos

            Não é necessário qualquer ação de atualização do registro :bi:`Person (Aux)` da Pessoa.

        #. Atualização de um outro dado da Pessoa exceto dados do Endereço e da Família

            As atualizações necessárias devem ser aplicadas manualmente no registro :bi:`Person (Aux)` da Pessoa.

        #. A Pessoa mudou-se para um outro Endereço **existente** no Cadastro Geral

            O :bi:`(Reference) Address` do registro :bi:`Person (Aux)` deve ser manualmente substituido pelo :bi:`Address` do novo Endereço para o qual a Pessoa se mudou.

            O :bi:`(Reference) Address (Aux)` do registro :bi:`Person (Aux)` deve ser mantido.

            As informações de :bi:`Contact Information` devem ser subistituídas pelas informações de :bi:`Contact Information` do novo Endereço.

        #. A Pessoa mudou-se para um outro Endereço **não existente** no Cadastro Geral

            O :bi:`(Reference) Address` do registro :bi:`Person (Aux)` deve ser manualmente excluído.

            O :bi:`(Reference) Address (Aux)` do registro :bi:`Person (Aux)` deve ser mantido.

            As informações de :bi:`Contact Information` devem ser subistituídas pelas informações de :bi:`Contact Information` do novo Endereço.

        #. A Pessoa mudou-se para um outro Endereço **desconhecido**

            O :bi:`(Reference) Address` do registro :bi:`Person (Aux)` deve ser manualmente excluído.

            O :bi:`(Reference) Address (Aux)` do registro :bi:`Person (Aux)` deve ser mantido.

            As informações de :bi:`Contact Information` devem ser subistituídas por informações que indiquem o desconhecimento do novo Endereço.

        #. A Pessoa mudou-se para um outro Endereço **fora da comunidade** atendida pela JCAFB

            O :bi:`(Reference) Address` do registro :bi:`Person (Aux)` deve ser manualmente excluído.

            O :bi:`(Reference) Address (Aux)` do registro :bi:`Person (Aux)` deve ser mantido.

            As informações de :bi:`Contact Information` devem ser subistituídas por informações que indiquem o novo Endereço fora da comunidade.

        #. A Pessoa atualmente está ausente da comunidade atendida pela JCAFB (devido ao falecimento ou outro modivo de forma maior)

    #. :doc:`reregistration_030_020`

        #. Todos os dados de Cadastro do Endereço serão mantidos

            Não é necessário qualquer ação de atualização do registro :bi:`Address (Aux)` da Pessoa.

        #. Atualização/Correção de alguma informação de Contato do Endereço exceto mudança de Endereço

            As atualizações necessárias devem ser aplicadas manualmente no registro :bi:`Address (Aux)` da Pessoa.

        #. A Pessoa mudou-se para um outro Endereço **existente** no Cadastro Geral

            O :bi:`Related Address` do registro :bi:`Address (Aux)` deve ser manualmente substituido pelo :bi:`Address` do novo Endereço para o qual a Pessoa se mudou.

            As informações de :bi:`Contact Information` devem ser subistituídas pelas informações de :bi:`Contact Information` do novo Endereço.

        #. A Pessoa mudou-se para um outro Endereço **não existente** no Cadastro Geral

            O :bi:`(Related) Address` do registro :bi:`Address (Aux)` deve ser manualmente excluído.

            As informações de :bi:`Contact Information` devem ser subistituídas pelas informações de :bi:`Contact Information` do novo Endereço.

        #. A Pessoa mudou-se para um outro Endereço **desconhecido**

            O :bi:`(Related) Address` do registro :bi:`Address (Aux)` deve ser manualmente excluído.

            As informações de :bi:`Contact Information` devem ser subistituídas pelas informações que indiquem o desconhecimento do novo Endereço.

        #. A Pessoa mudou-se para um outro Endereço **fora da comunidade** atendida pela JCAFB

            O :bi:`(Related) Address` do registro :bi:`Address (Aux)` deve ser manualmente excluído.

            As informações de :bi:`Contact Information` devem ser subistituídas por informações que indiquem o novo Endereço fora da comunidade.

    #. :doc:`reregistration_030_030`

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
   :caption: Itens Relacionados:

   reregistration_030_010
   reregistration_030_020
   reregistration_030_030
