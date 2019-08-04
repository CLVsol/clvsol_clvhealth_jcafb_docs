.. raw:: html

    <style> .red {color:red} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: bi

.. index:: Procura pela Pessoa nos Cadastros existentes

============================================
Procura pela Pessoa nos Cadastros existentes
============================================

    De posse dos dados de uma Pessoa a ser recadastrada, é necessário pesquisar pela existência prévia de registros relaltivos a essa Pessoa no **Cadastro** e/ou no **Cadastro Auxiliar**.

    Uma Pessoa será declarada como "**já cadastrada**" quando **possuir um registro prévio** no **Cadastro**, independentemente de possuir ou não um registro prévio no **Cadastro Auxiliar**.

    Uma Pessoa será declarada como "**não cadastrada**" quando **não possuir um registro prévio** no **Cadastro**, independentemente de possuir ou não um registro prévio no **Cadastro Auxiliar**. 

    #. :doc:`reregistration_010_010`

        Este é o método de pesquisa mais abrangente, e o preferencial quando não se dispuser do Código da Pessoa a ser pesquisada.

        A procura pela Pessoa utilizando a *view* **Contatos** é realizada quando se dispõe somente da informação do **Nome** da mesma (situação em que é incerta a existência de um cadastro para essa Pessoa).

        Neste caso não é possível realizar a pesquisa utilizando o Codigo da Pessoa.

    #. :doc:`reregistration_010_020`
     
        Este é o método de pesquisa mais restrito, e o preferencial quando se dispuser do Código da Pessoa a ser pesquisada.

        A procura pela Pessoa utilizando a *view* :bi:`Persons` é realizada quando se dispõe da informação do **Código** dessa Pessoa (situação em que é certa a existência de um cadastro para essa Pessoa).

        Este método pode ser utilizado também para pesquisas utilizando o Nome da Pessoa, quando não se conhece o Código da Pessoa. Mas neste caso é mais conveniente usar o método anterior ":doc:`reregistration_010_010`" que é mais abrangente, e permite a identificação do Cadatro *Aux* da Pessoa, quando já existente.

.. toctree::
   :maxdepth: 2
   :caption: Itens Relacionados:

   reregistration_010_010
   reregistration_010_020
