.. raw:: html

    <style> .red {color:red} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: bi

.. index:: Recadastramento de Pessoas

==============================
**Recadastramento de Pessoas**
==============================

O processo de **Recadastramento de Pessoas** é a base de todas as tarefas de planejamento da JCAFB que antecede a realização da Jornada em janeiro de cada ano, sendo concomitante ao **Recadastramento de Endereços** e ao **Recadastramento de Famílias**.

De forma geral, serão objeto do recadastramento somente Pessoas residentes em Endereços localizados na comunidade atendida no ciclo atual da JCAFB.

Pessoas residentes em outros locais, mesmo que tenham participado de alguma atividade durante o ciclo atual da JCAFB em anos anteriores, não necessitam ser recadastradas, a menos que a alteração no cadastro seja para sinalizar a mudança de status de residente para não residente na comunidade atendida ou que tenham falecido no período anterior ao recadastramento.

O recadastramento é realizado inicialmente utilizando o **Cadastro Auxiliar** (:bi:`Off`) composto pelos 3 objetos básicos de cadastro:

    * :bi:`Person (Off)`,
    * :bi:`Family (Off)` e 
    * :bi:`Address (Off)`.

Na fase final do recadastramento, todos os dados do **Cadastro Auxiliar** são consolidados no **Cadastro Geral**, quando então todas as alterações identificadas (atualizações de dados, inclusões de Pessoas, Famílias e Endereços)
são transferidas de um cadastro para o outro.

.. _Fluxo de Trabalho (Workflow) do Recadastramento:

Fluxo de Trabalho (*Workflow*) do Recadastramento
-------------------------------------------------

Em linhas gerais, o processo de recadastramento segue o seguinte fluxo de trabalho (*workflow*):

    #. Identificação da Pessoa a ser recadastrada nos Cadastros existentes:

        #. :ref:`Procura pela Pessoa a ser recadastrada (via view Contatos)`

            Este é o método de pesquisa mais abrangente, e o preferencial quando não se dispuser do Código da Pessoa a ser pesquisada.

            A procura pela Pessoa utilizando a *view* **Contatos** é realizada quando se dispõe somente da informação do **Nome** da mesma (situação em que é incerta a existência de um cadastro para essa Pessoa).

            Neste caso não é possível realizar a pesquisa utilizando o Codigo da Pessoa.

        #. :ref:`Procura pela Pessoa a ser recadastrada (via view Persons)`
         
            Este é o método de pesquisa mais restrito, e o preferencial quando se dispuser do Código da Pessoa a ser pesquisada.

            A procura pela Pessoa utilizando a *view* :bi:`Persons` é realizada quando se dispõe da informação do **Código** dessa Pessoa (situação em que é certa a existência de um cadastro para essa Pessoa).

            Este método pode ser utilizado também para pesquisas utilizando o Nome da Pessoa, quando não se conhece o Código da Pessoa. Mas neste caso é mais conveniente usar o método anterior :ref:`Procura pela Pessoa a ser recadastrada (via view Contatos)` que é mais abrangente, e permite a identificação do Cadatro *Off* da Pessoa, quando já existente.

    #. Criação do Cadastro *Off* da Pessoa a ser recadastrada:

        #. :ref:`Criação do Cadastro Off de uma Pessoa já cadastrada`

            Este procedimento pode ser utilizado somente quando **for identificado** um registro :bi:`Person` para a Pessoa a ser recadastrada, utilizando-se um dos métodos: :ref:`Procura pela Pessoa a ser recadastrada (via view Contatos)` ou :ref:`Procura pela Pessoa a ser recadastrada (via view Persons)`.

            Por esse método, quando não existir ainda um Cadastro *Off* para a Pessoa, o mesmo será automaticamente criado como uma cópia do Cadastro dessa Pessoa.

            O Cadastro *Off* criado será composto por um registro de :bi:`Person (Off)`, um registro de :bi:`Address (Off)` (quando existir um registro de :bi:`Address` associado à Pessoa), e um registro de :bi:`Family (Off)` (quando existir um registro de :bi:`Family` associado à Pessoa).

            O relacionamento entre os diversos registros dos Cadastros será o seguinte (quando existirem os registros, como indicado anteriormente):

                * :bi:`Person (Off)`: 

                    * :bi:`(Reference) Address` » :bi:`Address`
                    * :bi:`(Reference) Address (Off)` » :bi:`Address (Off)`
                    * :bi:`Family` » :bi:`Family`
                    * :bi:`Family (Off)` » :bi:`Family (Off)`
                    * :bi:`Related Person` » :bi:`Person`
                    * :bi:`Contact Information` = Dados do registro :bi:`Address`
                    * Outros Dados = Outros Dados do registro :bi:`Person`

                * :bi:`Address (Off)`:

                    * :bi:`Related Address` » :bi:`Address`
                    * :bi:`Contact Information` = Dados do registro :bi:`Address`

                * :bi:`Family (Off)`:

                    * :bi:`(Reference) Address` » :bi:`Address`
                    * :bi:`(Reference) Address (Off)` » :bi:`Address (Off)`
                    * :bi:`Related Family` » :bi:`Family`
                    * :bi:`Contact Information` = Dados do registro :bi:`Address`

        #. :ref:`Criação do Cadastro *Off* de uma nova Pessoa`

            Este procedimento pode ser utilizado somente quando **não for identificado** um registro :bi:`Person` para a Pessoa a ser recadastrada, utilizando-se um dos métodos: :ref:`Procura pela Pessoa a ser recadastrada (via view Contatos)` ou :ref:`Procura pela Pessoa a ser recadastrada (via view Persons)`.

            Por esse método, quando não existir ainda um Cadastro *Off* para a Pessoa, o mesmo deverá ser manualmente criado para conter as informações coletadas para a Pessoa. Essas informações coletadas serão manualmente inseridas nos registros pertinentes.

            O Cadastro *Off* criado será composto por um registro de :bi:`Person (Off)`, um registro de :bi:`Address (Off)` (quando necessário), e um registro de :bi:`Family (Off)` (quando necessário).

            O relacionamento entre os diversos registros dos Cadastros será o seguinte (quando existirem os registros, como indicado anteriormente):

                * :bi:`Person (Off)`: 

                    * :bi:`(Reference) Address` » **vazio**
                    * :bi:`(Reference) Address (Off)` » :bi:`Address (Off)`
                    * :bi:`Family` » **vazio**
                    * :bi:`Family (Off)` » :bi:`Family (Off)`
                    * :bi:`Related Person` » **vazio**
                    * :bi:`Contact Information` = Dados do Endereço da Pessoa
                    * Outros Dados = Outros Dados coletados da Pessoa

                * :bi:`Address (Off)`:

                    * :bi:`Related Address` » **vazio**
                    * :bi:`Contact Information` = Dados do Endereço da Pessoa

                * :bi:`Family (Off)`:

                    * :bi:`(Reference) Address` » **vazio**
                    * :bi:`(Reference) Address (Off)` » :bi:`Address (Off)`
                    * :bi:`Related Family` » **vazio**
                    * :bi:`Contact Information` = Dados do Endereço da Pessoa

    #. Atualização do Cadastro *Off* de uma Pessoa **já cadastrada**

        #. Atualização dos dados do registro :bi:`Person (Off)` de uma Pessoa **já cadastrada**

            #. Todos os dados de Cadastro da Pessoa serão mantidos

                Não é necessário qualquer ação de atualização do registro :bi:`Person (Off)` da Pessoa.

            #. Atualização de um outro dado da Pessoa exceto dados do Endereço e da Família

                As atualizações necessárias devem ser aplicadas manualmente no registro :bi:`Person (Off)` da Pessoa.

            #. A Pessoa mudou-se para um outro Endereço **existente** no Cadastro Geral

                O :bi:`(Reference) Address` do registro :bi:`Person (Off)` deve ser manualmente substituido pelo :bi:`Address` do novo Endereço para o qual a Pessoa se mudou.

                O :bi:`(Reference) Address (Off)` do registro :bi:`Person (Off)` deve ser mantido.

                As informações de :bi:`Contact Information` devem ser subistituídas pelas informações de :bi:`Contact Information` do novo Endereço.

            #. A Pessoa mudou-se para um outro Endereço **não existente** no Cadastro Geral

                O :bi:`(Reference) Address` do registro :bi:`Person (Off)` deve ser manualmente excluído.

                O :bi:`(Reference) Address (Off)` do registro :bi:`Person (Off)` deve ser mantido.

                As informações de :bi:`Contact Information` devem ser subistituídas pelas informações de :bi:`Contact Information` do novo Endereço.

            #. A Pessoa mudou-se para um outro Endereço **desconhecido**

                O :bi:`(Reference) Address` do registro :bi:`Person (Off)` deve ser manualmente excluído.

                O :bi:`(Reference) Address (Off)` do registro :bi:`Person (Off)` deve ser mantido.

                As informações de :bi:`Contact Information` devem ser subistituídas por informações que indiquem o desconhecimento do novo Endereço.

            #. A Pessoa mudou-se para um outro Endereço **fora da comunidade** atendida pela JCAFB

                O :bi:`(Reference) Address` do registro :bi:`Person (Off)` deve ser manualmente excluído.

                O :bi:`(Reference) Address (Off)` do registro :bi:`Person (Off)` deve ser mantido.

                As informações de :bi:`Contact Information` devem ser subistituídas por informações que indiquem o novo Endereço fora da comunidade.

            #. A Pessoa atualmente está ausente da comunidade atendida pela JCAFB (devido ao falecimento ou outro modivo de forma maior)

        #. Atualização dos dados do registro :bi:`Address (Off)` de uma Pessoa **já cadastrada**

            #. Todos os dados de Cadastro do Endereço serão mantidos

                Não é necessário qualquer ação de atualização do registro :bi:`Address (Off)` da Pessoa.

            #. Atualização/Correção de alguma informação de Contato do Endereço exceto mudança de Endereço

                As atualizações necessárias devem ser aplicadas manualmente no registro :bi:`Address (Off)` da Pessoa.

            #. A Pessoa mudou-se para um outro Endereço **existente** no Cadastro Geral

                O :bi:`Related Address` do registro :bi:`Address (Off)` deve ser manualmente substituido pelo :bi:`Address` do novo Endereço para o qual a Pessoa se mudou.

                As informações de :bi:`Contact Information` devem ser subistituídas pelas informações de :bi:`Contact Information` do novo Endereço.

            #. A Pessoa mudou-se para um outro Endereço **não existente** no Cadastro Geral

                O :bi:`(Related) Address` do registro :bi:`Address (Off)` deve ser manualmente excluído.

                As informações de :bi:`Contact Information` devem ser subistituídas pelas informações de :bi:`Contact Information` do novo Endereço.

            #. A Pessoa mudou-se para um outro Endereço **desconhecido**

                O :bi:`(Related) Address` do registro :bi:`Address (Off)` deve ser manualmente excluído.

                As informações de :bi:`Contact Information` devem ser subistituídas pelas informações que indiquem o desconhecimento do novo Endereço.

            #. A Pessoa mudou-se para um outro Endereço **fora da comunidade** atendida pela JCAFB

                O :bi:`(Related) Address` do registro :bi:`Address (Off)` deve ser manualmente excluído.

                As informações de :bi:`Contact Information` devem ser subistituídas por informações que indiquem o novo Endereço fora da comunidade.

        #. Atualização dos dados do registro :bi:`Family (Off)` de uma Pessoa **já cadastrada**

            #. Todos os dados de Cadastro da Família serão mantidos

                Não é necessário qualquer ação de atualização do registro :bi:`Family (Off)` da Pessoa.

            #. Atualização/Correção de alguma informação de Contato da Família exceto mudança de Endereço

                As atualizações necessárias devem ser aplicadas manualmente no registro :bi:`Family (Off)` da Pessoa.

            #. A Pessoa mudou-se para um outro Endereço **existente** no Cadastro Geral

                O :bi:`(Reference) Address` do registro :bi:`Family (Off)` deve ser manualmente substituido pelo :bi:`Address` do novo Endereço para o qual a Pessoa se mudou.

                O :bi:`(Reference) Address (Off)` do registro :bi:`Family (Off)` deve ser mantido.

                As informações de :bi:`Contact Information` devem ser subistituídas pelas informações de :bi:`Contact Information` do novo Endereço.

            #. A Pessoa mudou-se para um outro Endereço **não existente** no Cadastro Geral

                O :bi:`(Reference) Address` do registro :bi:`Family (Off)` deve ser manualmente excluído.

                O :bi:`(Reference) Address (Off)` do registro :bi:`FAmily (Off)` deve ser mantido.

                As informações de :bi:`Contact Information` devem ser subistituídas pelas informações de :bi:`Contact Information` do novo Endereço.

            #. A Pessoa mudou-se para um outro Endereço **desconhecido**

                O :bi:`(Reference) Address` do registro :bi:`Family (Off)` deve ser manualmente excluído.

                O :bi:`(Reference) Address (Off)` do registro :bi:`Family (Off)` deve ser mantido.

                As informações de :bi:`Contact Information` devem ser subistituídas por informações que indiquem o desconhecimento do novo Endereço.

            #. A Pessoa mudou-se para um outro Endereço **fora da comunidade** atendida pela JCAFB

                O :bi:`(Reference) Address` do registro :bi:`Family (Off)` deve ser manualmente excluído.

                O :bi:`(Reference) Address (Off)` do registro :bi:`Family (Off)` deve ser mantido.

                As informações de :bi:`Contact Information` devem ser subistituídas por informações que indiquem o novo Endereço fora da comunidade.

    #. Atualização do Cadastro *Off* de uma **nova** Pessoa

        #. Atualização dos dados do registro :bi:`Person (Off)` de uma **nova** Pessoa

            #. A Pessoa reside em um Endereço **existente** no Cadastro Geral

            #. A Pessoa reside em um Endereço **não existente** no Cadastro Geral

            #. A Pessoa reside em um Endereço **fora da comunidade** atendida pela JCAFB

        #. Atualização dos dados do registro :bi:`Address (Off)` de uma **nova** Pessoa

            #. A Pessoa reside em um Endereço **existente** no Cadastro Geral

            #. A Pessoa reside em um Endereço **não existente** no Cadastro Geral

            #. A Pessoa reside em um Endereço **fora da comunidade** atendida pela JCAFB

        #. Atualização dos dados do registro :bi:`Family (Off)` de uma **nova** Pessoa

            #. A Pessoa reside em um Endereço **existente** no Cadastro Geral

            #. A Pessoa reside em um Endereço **não existente** no Cadastro Geral

            #. A Pessoa reside em um Endereço **fora da comunidade** atendida pela JCAFB

.. _Procura pela Pessoa a ser recadastrada (via view Contatos):

Procura pela Pessoa a ser recadastrada (via *view* **Contatos**)
----------------------------------------------------------------

    #. Procurar pela Pessoa a ser recadastrada na *view* **Contatos**:

        #. Acessar a *view* **Contatos**:

            * Menu de acesso:
                * **Contatos** » **Contatos**

        #. Selecionar a **visualização em lista**.

        #. Aplicar o filtro **Agrupar Por** » :bi:`Address Type`.

        #. Pesquisar pelo nome da Pessoa a ser recadastrada:

            #. Se a Pessoa for encontrada **somente** com *Address Type* :bi:`Person`:

                #. Abrir o registro de contato encontrado.

                #. Acionar o botão da *view* :bi:`Persons`.

                #. Abrir o registro da Pessoa apresentado na *view* :bi:`Persons`.

                #. Executar o procedimento ":doc:`/user_guide/community/person/person_associate_to_person_off`" para o registro aberto:

                    #. Exercutar a Ação ":bi:`Person Associate to Person (Off)`":

                        #. Parâmetros apresentados:
                            * *Create new Person (Off)* (**Observação**: Parâmetro não modificável)
                            * *Create new Family (Off)* (**Observação**: Parâmetro não modificável)
                            * *Create new Address (Off)* (**Observação**: Parâmetro não modificável)

                        #. Utilize o botão :bi:`Associate do Perton (Off)` para executar a Ação.

                    #. Abrir o registro da Pessoa apresentado na *view* :bi:`Persons (Off)`.

            #. Se a Pessoa for encontrada com *Address Type* :bi:`Person (Off)`:

                #. Abrir o registro de contato encontrado com *Address Type* :bi:`Person (Off)` .

                #. Acionar o botão da *view* :bi:`Persons (Off)`.

                #. Abrir o registro da Pessoa apresentado na *view* :bi:`Persons (Off)`.

            #. Se a Pessoa **não for encontrada** com *Address Type* :bi:`Person` ou :bi:`Person (Off)`:

                #. Acessar a *view* :bi:`Persons`:

                    * Menu de acesso:
                        * :bi:`Community` » :bi:`Off` » :bi:`Persons (Off)`

                #. Criar um novo registro da Pessoa a ser recadastrada.

.. _Procura pela Pessoa a ser recadastrada (via view Persons):

Procura pela Pessoa a ser recadastrada (via *view* :bi:`Persons`)
-----------------------------------------------------------------

    #. Procurar pela Pessoa a ser recadastrada na *view* :bi:`Persons`:

        #. Acessar a *view* :bi:`Persons`:

            * Menu de acesso:
                * :bi:`Community` » :bi:`Community` » :bi:`Persons`

        #. Pesquisar pela Pessoa a ser recadastrada.

    #. **Caso o registro dessa Pessoa seja encontrado** na *view* :bi:`Persons`, executar o procedimento ":doc:`/user_guide/community/person/person_associate_to_person_off`" para o registro encontrado.

        #. Selecionar o registro da Pessoa encontrado.

        #. Exercutar a Ação ":bi:`Person Associate to Person (Off)`":

            * Parâmetros apresentados:
                * *Create new Person (Off)* (**Observação**: Parâmetro não modificável)
                * *Create new Family (Off)* (**Observação**: Parâmetro não modificável)
                * *Create new Address (Off)* (**Observação**: Parâmetro não modificável)

            #. Utilize o botão :bi:`Associate do Perton (Off)` para executar a Ação.

    #. **Caso um registro dessa Pessoa NÃO seja encontrado** na *view* :bi:`Persons`, Procurar pela Pessoa a ser recadastrada na *view* :bi:`Persons (Off)`:

        #. Acessar a *view* :bi:`Persons (Off)`:

            * Menu de acesso:
                * :bi:`Community` » :bi:`Off` » :bi:`Persons (Off)`

        #. Pesquisar pela Pessoa a ser recadastrada.

    	#. **Caso o registro dessa Pessoa seja encontrado** na *view* :bi:`Persons (Off)`,

    	#. **Caso um registro dessa Pessoa NÃO seja encontrado** na *view* :bi:`Persons (Off)`,

.. _Criação do Cadastro Off de uma Pessoa já cadastrada:

Criação do Cadastro *Off* de uma Pessoa já cadastrada
-----------------------------------------------------

.. _Criação do Cadastro *Off* de uma nova Pessoa:

Criação do Cadastro *Off* de uma nova Pessoa
--------------------------------------------

.. toctree::
   :maxdepth: 2
   :caption: Ações:
