.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .blue {color:blue} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: blue
.. role:: bi

=================================================
Preparação do Banco de Dados (1) - JCAFB-2021v-13
=================================================

:red:`(Não Executado])` Restaurar um backup do banco de dados *CLVhealth-JCAFB-2021v-13* (2020-07-11d)
------------------------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_restore`.

    #. [tkl-odoo13-jcafb21-vm] Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb21-vm** e paralizar o *Odoo*:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            ssh tkl-odoo13-jcafb21-vm -l root

            /etc/init.d/odoo stop

            su odoo

    #. [tkl-odoo13-jcafb21-vm] Executar os comandos de restauração dos arquivos de backup:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            cd /opt/odoo
            # gzip -d clvhealth_jcafb_2021v_13_2020-07-11d.sql.gz

            dropdb -i clvhealth_jcafb_2021v_13

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2021v_13
            psql -f clvhealth_jcafb_2021v_13_2020-07-11d.sql -d clvhealth_jcafb_2021v_13 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2021v_13
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2021v_13_2020-07-11d.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021v_13_2020-07-11d.tar.gz

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo desejado:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    #. [tkl-odoo13-jcafb21-vm] Configurar o parâmetro "**web.base.url**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* **Parâmetros do Sistema**:

            * Menu de acesso:
                
                * **Configurações** » **Técnico** » **Parâmetros** » **Parâmetros do Sistema**

        #. Pesquisar pelo registro com a **Chave** "**web.base.url**"

        #. Editar o registro apresentado (**Chave**: "**web.base.url**")

        #. Alterar o campo **Valor** para:

            * "**http://tkl-odoo13-jcafb21-vm**".

        #. Salvar o registro editado.

Excluir todas as Pessoas do Cadastro :bi:`Person (Aux)` (2020-07-12)
--------------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Excluir todas as Pessoas do Cadastro :bi:`Person (Aux)`:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Contatos*:

            * Menu de acesso:

                * **Contatos** » **Contatos**

        #. Ativar o filtro **Agrupar por** :bi:`Address Type`

        #. Selecionar todas as :bi:`Persons (Aux)` (**605**)

        #. Executar a Ação "**Excluir**":

            #. Utilize o botão :bi:`Ok` para executar a Ação.

    #. [tkl-odoo13-jcafb21-vm] Excluir todos os :bi:`Verification Outcomes` referentes a registros de :bi:`Person (Aux)`:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Verification Outcomes*:

            * Menu de acesso:

                * **Verification** » **Verification** » **Verification Outcomes**

        #. Ativar o filtro **Agrupar por** :bi:`Model Name`

        #. Selecionar todas os :bi:`Verification Outcomes` referentes a **clv.person_aux** (**3025**)

        #. Executar a Ação "**Excluir**":

            #. Utilize o botão :bi:`Ok` para executar a Ação.

Excluir todos os Endereços do Cadastro :bi:`Address (Aux)` (2020-07-12)
-----------------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Excluir todos os Endereços do Cadastro :bi:`Address (Aux)`:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Contatos*:

            * Menu de acesso:

                * **Contatos** » **Contatos**

        #. Ativar o filtro **Agrupar por** :bi:`Address Type`

        #. Selecionar todas os :bi:`Addresss (Aux)` (**202**)

        #. Executar a Ação "**Excluir**":

            #. Utilize o botão :bi:`Ok` para executar a Ação.

    #. [tkl-odoo13-jcafb21-vm] Excluir todos os :bi:`Verification Outcomes` referentes a registros de :bi:`Address (Aux)`:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Verification Outcomes*:

            * Menu de acesso:

                * **Verification** » **Verification** » **Verification Outcomes**

        #. Ativar o filtro **Agrupar por** :bi:`Model Name`

        #. Selecionar todas os :bi:`Verification Outcomes` referentes a **clv.address_aux** (**404**)

        #. Executar a Ação "**Excluir**":

            #. Utilize o botão :bi:`Ok` para executar a Ação.

Remover a Fase de todos os Funcionários (2020-07-12)
----------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Employee Mass Edit` para todos os Funcionários:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Employees*:

            * Menu de acesso:

                * **Funcionários** » :bi:`Employees` » :bi:`Employees`

        #. Selecionar todos os Funcionários (**248**)

        #. Executar a Ação ":bi:`Employee Mass Edit`":

            * Parâmetros utilizados:

                * *Phase*: :bi:`Remove`

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Atualizar o *Employee History* de todos os Funcionários (2020-07-12)
--------------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Employee History Update` para todos os Funcionários:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Employees*:

            * Menu de acesso:

                * **Funcionários** » :bi:`Employees` » :bi:`Employees`

        #. Selecionar todos os Funcionários (**248**)

        #. Executar a Ação ":bi:`Employee History Update`":

            * Parâmetros utilizados:

                * *Sign out date*: **01/03/2020**
                * *Sign in date*: **01/11/2019**

            #. Utilize o botão :bi:`Employee History Update` para executar a Ação.

Remover a Fase de todas as Pessoas (2020-07-12)
-----------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Person Mass Edit` para todas as Pessoas:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Persons*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Persons`

        #. Selecionar todas as Pessoas (**1540**)

        #. Executar a Ação ":bi:`Person Mass Edit`":

            * Parâmetros utilizados:

                * *Phase*: :bi:`Remove`

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Atualizar o *Person History* de todas as Pessoas (2020-07-12)
-------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Person History Update` para todas as Pessoas:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Persons*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Persons`

        #. Selecionar todas as Pessoas (**1540**)

        #. Executar a Ação ":bi:`Person History Update`":

            * Parâmetros utilizados:

                * *Sign out date*: **01/03/2020**
                * *Sign in date*: **01/11/2019**

            #. Utilize o botão :bi:`Person History Update` para executar a Ação.

Renovar o *Random ID* de todas as Pessoas (2020-07-12)
------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Person Mass Edit` para todas as Pessoas:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Persons*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Persons`

        #. Selecionar todas as Pessoas (**1540**)

        #. Executar a Ação ":bi:`Person Mass Edit`":

            * Parâmetros utilizados:

                * *Random ID*: "**/**"

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Remover a Fase de todas as Famílias (2020-07-12)
------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Family Mass Edit` para todas as Famílias:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Families*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Families`

        #. Selecionar todas as Famílias (**441**)

        #. Executar a Ação ":bi:`Family Mass Edit`":

            * Parâmetros utilizados:

                * *Phase*: :bi:`Remove`

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Atualizar o *Family History* de todas as Famílias (2020-07-12)
--------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Family History Update` para todas as Famílias:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Families*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Families`

        #. Selecionar todas as Famílias (**441**)

        #. Executar a Ação ":bi:`Family History Update`":

            * Parâmetros utilizados:

                * *Sign out date*: **01/03/2020**
                * *Sign in date*: **01/11/2019**

            #. Utilize o botão :bi:`Family History Update` para executar a Ação.

Remover a Fase de todos os Endereços (2020-07-12)
-------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Address Mass Edit` para todas as Pessoas:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Addresses*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Addresses`

        #. Selecionar todos os Endereços (**665**)

        #. Executar a Ação ":bi:`Address Mass Edit`":

            * Parâmetros utilizados:

                * *Phase*: :bi:`Remove`

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Atualizar o *Address History* de todos os Endereços (2020-07-12)
----------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Address History Update` para todos os Endereços:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Addresss*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Addresss`

        #. Selecionar todos os Endereços (**665**)

        #. Executar a Ação ":bi:`Address History Update`":

            * Parâmetros utilizados:

                * *Sign out date*: **01/03/2020**
                * *Sign in date*: **01/11/2019**

            #. Utilize o botão :bi:`Address History Update` para executar a Ação.

Remover o *Responsible Empĺoyee* de todos os Endereços (2020-07-12)
-------------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Address Mass Edit` para todas as Pessoas:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Addresses*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Addresses`

        #. Selecionar todas as Pessoas (**665**)

        #. Executar a Ação ":bi:`Address Mass Edit`":

            * Parâmetros utilizados:

                * *Responsible Empĺoyee*: :bi:`Remove`

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Adicionar a nova *Phase* (JCAFB-2021v) para a *CLVhealth-JCAFB-2021v-13* (2020-07-10)
-------------------------------------------------------------------------------------

    #. Incluir a nova Fase **JCAFB-2021v**:

        #. Acessar a *View* *Phases*:

            * Menu de acesso:
                * :bi:`Base` » :bi:`Configuration` » :bi:`Phases`

        #. Incluir uma nova Fase:

            * Parâmetros editados:

                * *Phase*: "**JCAFB-2021v**"
                * *Description*: "**Jornada Virtual simulando uma quinta visita à comunidade da cidade de Fernão-SP**"

Atualizar o "*Global Settings*" para a *CLVhealth-JCAFB-2021v-13* (2020-07-10)
------------------------------------------------------------------------------

    #. Acessar a *View* *Global Settings*:

        * Menu de acesso:

            * :bi:`Base` » :bi:`Global Settings` » :bi:`Global Settings`

        #. Configurar o parâmetro :bi:`Phase` » :bi:`Phase`: **JCAFB-2021v**

Preparar os "*Employees*" para a JCAFB-2021v (2020-07-14)
---------------------------------------------------------

    #. Acessar a *View* *Funcionários*:

        * Menu de acesso:

            * :bi:`Funcionários` » :bi:`Employees` » :bi:`Employees`

        #. Configurar o parâmetro :bi:`Phase` como **JCAFB-2021v** para todos os *Employees* da **JCAFB-2021v**.

        #. Configurar o parâmetro **Cargo** para todos os *Employees* da **JCAFB-2021v**.

        #. Remover o parâmetro :bi:`Department` de todos os *Employees*.

        #. Remover o parâmetro :bi:`Job` de todos os *Employees* não associados à **JCAFB-2021v**.

        #. :red:`(Não Executado])` Redefinir a **Senha** de todos os os *Employees* da **JCAFB-2021v**.

Atualizar o(s) módulo(s) [clv_employee_jcafb] (2020-07-15)
----------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Lista de Módulos:

        * clv_employee_jcafb

    #. [tkl-odoo13-jcafb21-vm] **Executar** a atualização do(s) Módulo(s):

        #. Estabelecer uma sessão ssh (session 1) com o servidor **tkl-odoo13-jcafb21-vm** e executar o *Odoo* no modo manual:

            ::

                # ***** tkl-odoo13-jcafb21-vm (session 1)
                #

                ssh tkl-odoo13-jcafb21-vm -l root

                /etc/init.d/odoo stop

                su odoo
                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

        #. Estabelecer uma sessão ssh (session 2) com o servidor **tkl-odoo13-jcafb21-vm** e executar o **install.py**:

            ::

                # ***** tkl-odoo13-jcafb21-vm (session 2)
                #

                ssh tkl-odoo13-jcafb21-vm -l odoo

                cd /opt/odoo/clvsol_clvhealth_jcafb/project
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_employee_jcafb
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo desejado:

            ::

                # ***** tkl-odoo13-jcafb21-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Renovar o *Token* de todos os Funcionários (2020-07-15)
-------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Employee Mass Edit` para todas os Funcionários:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Funcionários*:

            * Menu de acesso:

                * :bi:`Funcionários` » :bi:`Funcionários`

        #. Selecionar todos os Funcionários (**248**)

        #. Executar a Ação ":bi:`Employee Mass Edit`":

            * Parâmetros utilizados:

                * *Token*: :bi:`Remove`

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

        #. Selecionar todos os Funcionários (**248**)

        #. Executar a Ação ":bi:`Employee Mass Edit`":

            * Parâmetros utilizados:

                * *Token*: :bi:`Set` "**/**"

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Redefinir a **Senha** de todos os Funcionários da **JCAFB-2021v** (2020-07-15)
------------------------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Employee Mass Edit` para todas os Funcionários da **JCAFB-2021v**:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Funcionários*:

            * Menu de acesso:

                * :bi:`Funcionários` » :bi:`Funcionários`

        #. Selecionar todos os Funcionários da **JCAFB-2021v** (**28**)

        #. Executar a Ação ":bi:`Employee Mass Edit`":

            * Parâmetros utilizados:

                * *Reset User Password*: :bi:`marcado`

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Redefinir a senha do usuário de referência da JCAFB-2021v (2020-07-15)
----------------------------------------------------------------------

    #. Redefinir a senha do usuário de referência:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Users*:

            * Menu de acesso:

                * :bi:`Configurações` » :bi:`Utilizadores e Empresas` » :bi:`Usuários`

        #. Selecionar o usuário de referência.

        #. Executar a Ação "**Alterar Senha**":

            * Parâmetros:
                * Nova Senha: *******
            
            #. Utilize o botão "**Alterar Senha**" para executar a ação.

.. toctree::   :maxdepth: 2
