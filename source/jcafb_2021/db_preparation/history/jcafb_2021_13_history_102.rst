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
Preparação do Banco de Dados (2) - JCAFB-2021v-13
=================================================

Executar o *Verification Batch* "*Default Batch*" (2020-07-16)
--------------------------------------------------------------

    #. Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb21-vm** e executar o *Odoo* no modo manual:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            ssh tkl-odoo13-jcafb21-vm -l root

            /etc/init.d/odoo stop

            su odoo

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    #. [tkl-odoo13-jcafb21-vm] Executar o :bi:`Verification Batch` "**Default Batch**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Executar a ação :bi:`Verification Batch Exec` para o "**Default Batch**":

            * Menu de acesso:
                
                * :bi:`Verification` » :bi:`Verification` » :bi:`Verification` » :bi:`Batches` » **Ação** » :bi:`Verification Batch Exec`

            * :bi:`Execution time: 0:10:21.496`

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo padrão:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            ^C

            exit

            /etc/init.d/odoo start

Configurar as permissões do usuário de referência da JCAFB-2021v (2020-07-16)
-----------------------------------------------------------------------------

    #. Configurar as permissões do usuário de referência:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Users*:

            * Menu de acesso:

                * :bi:`Configurações` » :bi:`Utilizadores e Empresas` » :bi:`Usuários`

        #. Selecionar o usuário de referência.

        #. Configurar as permissões:

            * Recursos Humanos
            
                * Funcionários: **Administrador**

            * Marketing

                * Questionário: **Administrador**

            * Outro

                * *Address (Aux)*: :bi:`Manager (Address (Aux))`
                * *Address*: :bi:`Manager (Address)`
                * *Aux*: :bi:`Manager (Aux)`
                * *Community*: :bi:`Manager (Community)`
                * *Event*: :bi:`Manager (Event)`
                * *Export*: :bi:`Manager (Export)`
                * *External Sync*:
                * *Family*: :bi:`Manager (Family)`
                * *File System*: :bi:`Manager (File System)`
                * *Global Tag*: :bi:`Manager (Global Tag)`
                * *Person (Aux)*: :bi:`Manager (Person (Aux))`
                * *Person Selection*:
                * *Person*: :bi:`Manager (Person)`
                * *Phase*: :bi:`User (Phase)`
                * *Processing*:
                * *Report*:
                * *Set*: :bi:`Manager (Set)`
                * *Summary*: :bi:`Manager (Summary)`
                * *Survey*:  :bi:`Manager (Survey)`
                * *Verification*: :bi:`Manager (Verification)`

            * *Base*:

                * :bi:`Annotation User (Base)`,
                * :bi:`Log User (Base)`,
                * :bi:`Manager (Base)` ​
                * :bi:`Register User (Base)`,
                * :bi:`Super User (Base)`,
                * :bi:`User (Base)`,

            * *Document*:

                * :bi:`Manager (Document)` ​
                * :bi:`User (Document)` ​
            
            * *Lab Test*:

                * :bi:`Manager (Lab Test)`
                * :bi:`User (Lab Test)`

            * Ferramentas Extras:

                * **Criação de Contato**

Atualizar as permissões de todos os Usuários da JCAFB-2021v (2020-07-16)
------------------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação *Employee User Groups Update* para os *Employees* da JCAFB-2021v:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Employees*:

            * Menu de acesso:

                * *Funcionários* » *Employees* » *Employees*

        #. Selecionar os *Employees* da JCAFB-2021v (**28**)

        #. Exercutar a Ação "**Employee User Groups Update**":

            #. Selecionar o :bi:`Reference Employee`: Usuário de referência (selecionado no ítem anterior).

            #. Selecionar o parâmetro :bi:`Access Rights:` » :bi:`Set`.

            #. Precionar o botão :bi:`Get Reference Employee Access Rights`.

            #. Utilize o botão :bi:`Update` para executar a Ação.

Atualizar o(s) módulo(s) [ver lista] (2020-07-17)
-------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Lista de Módulos:

        * clv_document
        * clv_partner_entity
        * clv_address
        * clv_family

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_document
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_partner_entity
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo desejado:

            ::

                # ***** tkl-odoo13-jcafb21-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Ativar *Automatic Name* de todos os Endereços (2020-07-17)
----------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Address Mass Edit` para todas as Pessoas:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Addresses*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Addresses`

        #. Selecionar todos os Endereços (**665**)

        #. Exercutar a Ação ":bi:`Address Mass Edit`":

            * Parâmetros utilizados:

                * *Automatic Name*: :bi:`Set` **marcado**

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Ativar *Automatic Name* de todas as Famílias (2020-07-17)
---------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Family Mass Edit` para todas as Famílias:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Families*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Families`

        #. Selecionar todas as Famílias (**441**)

        #. Exercutar a Ação ":bi:`Family Mass Edit`":

            * Parâmetros utilizados:

                * *Automatic Name*: :bi:`Set` **marcado**

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Atualizar o *Entity Code* de todas as Pessoas (2020-07-17)
----------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Person Mass Edit` para todas as Pessoas:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Persons*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Persons`

        #. Selecionar todas as Pessoas (**1540**)

        #. Exercutar a Ação ":bi:`Person Mass Edit`":

            * Parâmetros utilizados:

                * *Partner Entity Code*: **Set**

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Atualizar o *Entity Code* de todas as Famílias (2020-07-17)
-----------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Family Mass Edit` para todas as Famílias:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Families*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Families`

        #. Selecionar todas as Famílias (**441**)

        #. Exercutar a Ação ":bi:`Family Mass Edit`":

            * Parâmetros utilizados:

                * *Partner Entity Code*: **Set**

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Atualizar o *Entity Code* de todas os Endereços (2020-07-17)
------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Address Mass Edit` para todas os Endereços:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Addresses*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Addresses`

        #. Selecionar todas os Endereços (**665**)

        #. Exercutar a Ação ":bi:`Address Mass Edit`":

            * Parâmetros utilizados:

                * *Partner Entity Code*: **Set**

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Atualizar os fontes do projeto (2020-07-18)
-------------------------------------------

    #. **Atualizar** os fontes do projeto

        ::

            ssh tkl-odoo13-jcafb21-vm -l odoo

        ::

            /etc/init.d/odoo stop

        ::

            # ***** clvheatlh-jcafb-2020-aws-pro
            #

            cd /opt/odoo/clvsol_odoo_client
            git pull

            cd /opt/odoo/clvsol_clvhealth_jcafb
            git pull

            cd /opt/odoo/clvsol_l10n_brazil
            git pull

            cd /opt/odoo/clvsol_odoo_addons
            git pull

            cd /opt/odoo/clvsol_odoo_addons_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_l10n_br
            git pull

            cd /opt/odoo/clvsol_odoo_addons_l10n_br_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_history
            git pull

            cd /opt/odoo/clvsol_odoo_addons_history_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_verification
            git pull

            cd /opt/odoo/clvsol_odoo_addons_verification_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_summary
            git pull

            cd /opt/odoo/clvsol_odoo_addons_summary_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_export
            git pull

            cd /opt/odoo/clvsol_odoo_addons_export_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_report
            git pull

            cd /opt/odoo/clvsol_odoo_addons_report_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_process
            git pull

            cd /opt/odoo/clvsol_odoo_addons_process_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_sync
            git pull

            cd /opt/odoo/clvsol_odoo_addons_sync_jcafb
            git pull

        ::

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

Atualizar o(s) módulo(s) [clv_address_aux] (2020-07-18)
-------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Lista de Módulos:

        * clv_address_aux

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_address_aux
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo desejado:

            ::

                # ***** tkl-odoo13-jcafb21-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Associar todas as Pessoas a uma Pessoa (Aux) (2020-07-19)
---------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação *Person Associate to Person (Aux)* para todas as Pessoas:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Persons*:

            * Menu de acesso:

                * *Community* > *Community* > *Persons*

        #. Selecionar todas as Pessoas (**1540**)

        #. Exercutar a Ação "**Person Associate to Person (Aux)**":

            * Parâmetros utilizados:

                * *Create new Person (Aux)*: **marcado**
                * *Create new Address (Aux)*: **marcado**

            #. Utilize o botão *Associate to Person (Aux)* para executar a Ação.

Associar todos os Endereços a um Endereço (Aux) (2020-07-19)
------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação *Address Associate to Address (Aux)* para todos os Endereços:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Addresses*:

            * Menu de acesso:

                * *Community* > *Community* > *Addresses*

        #. Selecionar todos os Endereços (**665**)

        #. Exercutar a Ação "**Address Associate to Address (Aux)**":

            * Parâmetros utilizados:

                * *Create new Address (Aux)*: **marcado**

            #. Utilize o botão *Associate to Address (Aux)* para executar a Ação.

Remover a Fase de todas as Pessoas (Aux) (2020-07-19)
-----------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Person (Aux) Mass Edit` para todas as Pessoas (Aux):

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Persons (Aux)*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Auxiliary` » :bi:`Persons (Aux)`

        #. Selecionar todas as Pessoas (Aux) (**1540**)

        #. Exercutar a Ação ":bi:`Person (Aux) Mass Edit`":

            * Parâmetros utilizados:

                * *Phase*: :bi:`Remove`

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Remover a Fase de todos os Endereços (Aux) (2020-07-19)
-------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Address (Aux) Mass Edit` para todas as Pessoas:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Addresses (Aux)*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Auxiliary` » :bi:`Addresses (Aux)`

        #. Selecionar todos os Endereços (Aux) (**665**)

        #. Exercutar a Ação ":bi:`Address (Aux) Mass Edit`":

            * Parâmetros utilizados:

                * *Phase*: :bi:`Remove`

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Executar o *Verification Batch* "*Default Batch*" (2020-07-19)
--------------------------------------------------------------

    #. Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb21-vm** e executar o *Odoo* no modo manual:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            ssh tkl-odoo13-jcafb21-vm -l root

            /etc/init.d/odoo stop

            su odoo

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    #. [tkl-odoo13-jcafb21-vm] Executar o :bi:`Verification Batch` "**Default Batch**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Executar a ação :bi:`Verification Batch Exec` para o "**Default Batch**":

            * Menu de acesso:
                
                * :bi:`Verification` » :bi:`Verification` » :bi:`Verification` » :bi:`Batches` » **Ação** » :bi:`Verification Batch Exec`

            * :bi:`Execution time: 0:32:10.777`

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo padrão:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            ^C

            exit

            /etc/init.d/odoo start

Atualizar o(s) módulo(s) [clv_person_aux_verification_jcafb] (2020-07-20)
-------------------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Lista de Módulos:

        * clv_person_aux_verification_jcafb

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_person_aux_verification_jcafb
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo desejado:

            ::

                # ***** tkl-odoo13-jcafb21-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Excluir todas as Pessoas do Cadastro :bi:`Person (Aux)` (2020-07-20)
--------------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Excluir todas as Pessoas do Cadastro :bi:`Person (Aux)`:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Contatos*:

            * Menu de acesso:

                * **Contatos** » **Contatos**

        #. Ativar o filtro **Agrupar por** :bi:`Address Type`

        #. Selecionar todas as :bi:`Persons (Aux)` (**1540**)

        #. Exercutar a Ação "**Excluir**":

            #. Utilize o botão :bi:`Ok` para executar a Ação.

    #. [tkl-odoo13-jcafb21-vm] Excluir todos os :bi:`Verification Outcomes` referentes a registros de :bi:`Person (Aux)`:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Verification Outcomes*:

            * Menu de acesso:

                * **Verification** » **Verification** » **Verification Outcomes**

        #. Ativar o filtro **Agrupar por** :bi:`Model Name`

        #. Selecionar todas os :bi:`Verification Outcomes` referentes a **clv.person_aux** (**7700**)

        #. Exercutar a Ação "**Excluir**":

            #. Utilize o botão :bi:`Ok` para executar a Ação.

Excluir todos os Endereços do Cadastro :bi:`Address (Aux)` (2020-07-20)
-----------------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Excluir todos os Endereços do Cadastro :bi:`Address (Aux)`:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Contatos*:

            * Menu de acesso:

                * **Contatos** » **Contatos**

        #. Ativar o filtro **Agrupar por** :bi:`Address Type`

        #. Selecionar todas os :bi:`Addresss (Aux)` (**665**)

        #. Exercutar a Ação "**Excluir**":

            #. Utilize o botão :bi:`Ok` para executar a Ação.

    #. [tkl-odoo13-jcafb21-vm] Excluir todos os :bi:`Verification Outcomes` referentes a registros de :bi:`Address (Aux)`:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Verification Outcomes*:

            * Menu de acesso:

                * **Verification** » **Verification** » **Verification Outcomes**

        #. Ativar o filtro **Agrupar por** :bi:`Model Name`

        #. Selecionar todas os :bi:`Verification Outcomes` referentes a **clv.address_aux** (**1330**)

        #. Exercutar a Ação "**Excluir**":

            #. Utilize o botão :bi:`Ok` para executar a Ação.

Associar todas as Pessoas a uma Pessoa (Aux) (2020-07-20)
---------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação *Person Associate to Person (Aux)* para todas as Pessoas:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Persons*:

            * Menu de acesso:

                * *Community* > *Community* > *Persons*

        #. Selecionar todas as Pessoas (**1540**)

        #. Exercutar a Ação "**Person Associate to Person (Aux)**":

            * Parâmetros utilizados:

                * *Create new Person (Aux)*: **marcado**
                * *Create new Address (Aux)*: **marcado**

            #. Utilize o botão *Associate to Person (Aux)* para executar a Ação.

Associar todos os Endereços a um Endereço (Aux) (2020-07-20)
------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação *Address Associate to Address (Aux)* para todos os Endereços:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Addresses*:

            * Menu de acesso:

                * *Community* > *Community* > *Addresses*

        #. Selecionar todos os Endereços (**665**)

        #. Exercutar a Ação "**Address Associate to Address (Aux)**":

            * Parâmetros utilizados:

                * *Create new Address (Aux)*: **marcado**

            #. Utilize o botão *Associate to Address (Aux)* para executar a Ação.

Remover a Fase de todas as Pessoas (Aux) (2020-07-20)
-----------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Person (Aux) Mass Edit` para todas as Pessoas (Aux):

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Persons (Aux)*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Auxiliary` » :bi:`Persons (Aux)`

        #. Selecionar todas as Pessoas (Aux) (**1540**)

        #. Exercutar a Ação ":bi:`Person (Aux) Mass Edit`":

            * Parâmetros utilizados:

                * *Phase*: :bi:`Remove`

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Remover a Fase de todos os Endereços (Aux) (2020-07-20)
-------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Address (Aux) Mass Edit` para todas as Pessoas:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Addresses (Aux)*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Auxiliary` » :bi:`Addresses (Aux)`

        #. Selecionar todos os Endereços (Aux) (**665**)

        #. Exercutar a Ação ":bi:`Address (Aux) Mass Edit`":

            * Parâmetros utilizados:

                * *Phase*: :bi:`Remove`

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Executar o *Verification Batch* "*Default Batch*" (2020-07-20)
--------------------------------------------------------------

    #. Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb21-vm** e executar o *Odoo* no modo manual:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            ssh tkl-odoo13-jcafb21-vm -l root

            /etc/init.d/odoo stop

            su odoo

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    #. [tkl-odoo13-jcafb21-vm] Executar o :bi:`Verification Batch` "**Default Batch**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Executar a ação :bi:`Verification Batch Exec` para o "**Default Batch**":

            * Menu de acesso:
                
                * :bi:`Verification` » :bi:`Verification` » :bi:`Verification` » :bi:`Batches` » **Ação** » :bi:`Verification Batch Exec`

            * :bi:`Execution time: 0:34:52.552`

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo padrão:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            ^C

            exit

            /etc/init.d/odoo start

Excluir todas as Pessoas do Cadastro :bi:`Person (Aux)` (2020-07-20)
--------------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Excluir todas as Pessoas do Cadastro :bi:`Person (Aux)`:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Contatos*:

            * Menu de acesso:

                * **Contatos** » **Contatos**

        #. Ativar o filtro **Agrupar por** :bi:`Address Type`

        #. Selecionar todas as :bi:`Persons (Aux)` (**1540**)

        #. Exercutar a Ação "**Excluir**":

            #. Utilize o botão :bi:`Ok` para executar a Ação.

    #. [tkl-odoo13-jcafb21-vm] Excluir todos os :bi:`Verification Outcomes` referentes a registros de :bi:`Person (Aux)`:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Verification Outcomes*:

            * Menu de acesso:

                * **Verification** » **Verification** » **Verification Outcomes**

        #. Ativar o filtro **Agrupar por** :bi:`Model Name`

        #. Selecionar todas os :bi:`Verification Outcomes` referentes a **clv.person_aux** (**7700**)

        #. Exercutar a Ação "**Excluir**":

            #. Utilize o botão :bi:`Ok` para executar a Ação.

Excluir todos os Endereços do Cadastro :bi:`Address (Aux)` (2020-07-20)
-----------------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Excluir todos os Endereços do Cadastro :bi:`Address (Aux)`:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Contatos*:

            * Menu de acesso:

                * **Contatos** » **Contatos**

        #. Ativar o filtro **Agrupar por** :bi:`Address Type`

        #. Selecionar todas os :bi:`Addresss (Aux)` (**665**)

        #. Exercutar a Ação "**Excluir**":

            #. Utilize o botão :bi:`Ok` para executar a Ação.

    #. [tkl-odoo13-jcafb21-vm] Excluir todos os :bi:`Verification Outcomes` referentes a registros de :bi:`Address (Aux)`:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Verification Outcomes*:

            * Menu de acesso:

                * **Verification** » **Verification** » **Verification Outcomes**

        #. Ativar o filtro **Agrupar por** :bi:`Model Name`

        #. Selecionar todas os :bi:`Verification Outcomes` referentes a **clv.address_aux** (**1330**)

        #. Exercutar a Ação "**Excluir**":

            #. Utilize o botão :bi:`Ok` para executar a Ação.

Associar todas as Pessoas a uma Pessoa (Aux) (2020-07-20)
---------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação *Person Associate to Person (Aux)* para todas as Pessoas:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Persons*:

            * Menu de acesso:

                * *Community* > *Community* > *Persons*

        #. Selecionar todas as Pessoas (**1540**)

        #. Exercutar a Ação "**Person Associate to Person (Aux)**":

            * Parâmetros utilizados:

                * *Create new Person (Aux)*: **marcado**
                * *Create new Address (Aux)*: **marcado**

            #. Utilize o botão *Associate to Person (Aux)* para executar a Ação.

Associar todos os Endereços a um Endereço (Aux) (2020-07-20)
------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação *Address Associate to Address (Aux)* para todos os Endereços:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Addresses*:

            * Menu de acesso:

                * *Community* > *Community* > *Addresses*

        #. Selecionar todos os Endereços (**665**)

        #. Exercutar a Ação "**Address Associate to Address (Aux)**":

            * Parâmetros utilizados:

                * *Create new Address (Aux)*: **marcado**

            #. Utilize o botão *Associate to Address (Aux)* para executar a Ação.

Remover a Fase de todas as Pessoas (Aux) (2020-07-20)
-----------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Person (Aux) Mass Edit` para todas as Pessoas (Aux):

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Persons (Aux)*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Auxiliary` » :bi:`Persons (Aux)`

        #. Selecionar todas as Pessoas (Aux) (**1540**)

        #. Exercutar a Ação ":bi:`Person (Aux) Mass Edit`":

            * Parâmetros utilizados:

                * *Phase*: :bi:`Remove`

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Remover a Fase de todos os Endereços (Aux) (2020-07-20)
-------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Address (Aux) Mass Edit` para todas as Pessoas:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Addresses (Aux)*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Auxiliary` » :bi:`Addresses (Aux)`

        #. Selecionar todos os Endereços (Aux) (**665**)

        #. Exercutar a Ação ":bi:`Address (Aux) Mass Edit`":

            * Parâmetros utilizados:

                * *Phase*: :bi:`Remove`

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Executar o *Verification Batch* "*Default Batch*" (2020-07-20)
--------------------------------------------------------------

    #. Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb21-vm** e executar o *Odoo* no modo manual:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            ssh tkl-odoo13-jcafb21-vm -l root

            /etc/init.d/odoo stop

            su odoo

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    #. [tkl-odoo13-jcafb21-vm] Executar o :bi:`Verification Batch` "**Default Batch**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Executar a ação :bi:`Verification Batch Exec` para o "**Default Batch**":

            * Menu de acesso:
                
                * :bi:`Verification` » :bi:`Verification` » :bi:`Verification` » :bi:`Batches` » **Ação** » :bi:`Verification Batch Exec`

            * :bi:`Execution time: 0:32:40.850`

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo padrão:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            ^C

            exit

            /etc/init.d/odoo start

Atualizar o(s) módulo(s) [clv_survey] (2020-07-21)
--------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Lista de Módulos:

        * clv_survey

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_survey
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo desejado:

            ::

                # ***** tkl-odoo13-jcafb21-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Atualizar o(s) módulo(s) [clv_survey, clv_survey_sync_jcafb] (2020-07-22)
-------------------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Lista de Módulos:

        * clv_survey
        * clv_survey_sync_jcafb

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_survey
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo desejado:

            ::

                # ***** tkl-odoo13-jcafb21-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Atualizar o(s) módulo(s) [clv_document_sync_jcafb] (2020-07-23)
---------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Lista de Módulos:

        * clv_document_sync_jcafb

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_document_sync_jcafb
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo desejado:

            ::

                # ***** tkl-odoo13-jcafb21-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Atualizar o(s) módulo(s) [clv_survey, clv_document] (2020-07-23)
----------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Lista de Módulos:

        * clv_survey
        * clv_document

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_survey
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_document
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo desejado:

            ::

                # ***** tkl-odoo13-jcafb21-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Atualizar o(s) módulo(s) [clv_survey] (2020-07-27)
--------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Lista de Módulos:

        * clv_survey

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_survey
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo desejado:

            ::

                # ***** tkl-odoo13-jcafb21-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Atualizar o(s) módulo(s) [clv_survey] (2020-07-27)
--------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Lista de Módulos:

        * clv_survey

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_survey
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo desejado:

            ::

                # ***** tkl-odoo13-jcafb21-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Atualizar o(s) módulo(s) [ver lista] (2020-07-29)
-------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Lista de Módulos:

        * clv_person_history_jcafb
        * clv_family_jcafb
        * clv_family_history_jcafb
        * clv_address_jcafb
        * clv_address_history_jcafb

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_person_history_jcafb
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_family_jcafb
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_address_jcafb
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo desejado:

            ::

                # ***** tkl-odoo13-jcafb21-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Atualizar o(s) módulo(s) [ver lista] (2020-07-30)
-------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Lista de Módulos:

        * clv_document
        * clv_document_jcafb

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_document
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo desejado:

            ::

                # ***** tkl-odoo13-jcafb21-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Atualizar o(s) módulo(s) [ver lista] (2020-08-03)
-------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Lista de Módulos:

        * clv_lab_test
        * clv_lab_test_jcafb

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_lab_test
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo desejado:

            ::

                # ***** tkl-odoo13-jcafb21-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Configurar "*Global Settings*" para a *CLVhealth-JCAFB-2020v-13* (2020-08-04)
-----------------------------------------------------------------------------

    #. Acessar a *View* *Global Settings*:

        * Menu de acesso:

            * :bi:`Base` » :bi:`Global Settings` » :bi:`Global Settings`

        #. Configurar o parâmetro :bi:`Person` » :bi:`Reference Date`: **31/01/2021**

Atualisar a Idade de Referência para todas as Pessoas (2020-08-04)
------------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Person Mass Edit` para todas as Pessoas:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Persons*:

            * Menu de acesso:

                * :bi:`Communities` » :bi:`Communities` » :bi:`Persons`

        #. Selecionar todas as Pessoas (**1540**)

        #. Exercutar a Ação ":bi:`Person Mass Edit`":

            * Parâmetros utilizados:

                * *Person Reference Age Refresh*: **marcado**

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Atualizar o *State* das Pessoas *Selected* (2020-08-04)
-------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Person Mass Edit` para as Pessoas :bi:`Selected`:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Persons*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Persons`

        #. Selecionar todas as Pessoas :bi:`Selected` (**189**)

        #. Exercutar a Ação ":bi:`Person Mass Edit`":

            * Parâmetros utilizados:

                * *State*: **Set** **Available**

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Atualizar o *State* das Famílias *Selected* (2020-08-04)
--------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Family Mass Edit` para as Famílias :bi:`Selected`:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Families*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Families`

        #. Selecionar todas as Famílias (**146**)

        #. Exercutar a Ação ":bi:`Family Mass Edit`":

            * Parâmetros utilizados:

                * *State*: **Set** **Available**

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Atualizar o *State* dos Endereços *Selected* (2020-08-04)
---------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Address Mass Edit` para os Endereços :bi:`Selected`:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Addresses*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Addresses`

        #. Selecionar todas os Endereços (**144**)

        #. Exercutar a Ação ":bi:`Address Mass Edit`":

            * Parâmetros utilizados:

                * *State*: **Set** **Available**

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Atualizar o(s) módulo(s) [ver lista] (2020-08-07)
-------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Lista de Módulos:

        * clv_employee_jcafb
        * clv_survey

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
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_survey 
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo desejado:

            ::

                # ***** tkl-odoo13-jcafb21-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Atualizar o(s) módulo(s) [clv_person_aux] (2020-08-09)
------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Lista de Módulos:

        * clv_person_aux

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_person_aux
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo desejado:

            ::

                # ***** tkl-odoo13-jcafb21-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Atualizar o(s) módulo(s) [ver lista] (2020-08-10)
-------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Lista de Módulos:

        * clv_address_aux_verification_jcafb
        * clv_address_verification_jcafb
        * clv_person_aux_verification_jcafb
        * clv_person_verification_jcafb
        * clv_family_verification_jcafb

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_address_aux_verification_jcafb
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_address_verification_jcafb
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_person_aux_verification_jcafb
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_person_verification_jcafb
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_family_verification_jcafb
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo desejado:

            ::

                # ***** tkl-odoo13-jcafb21-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Atualizar o(s) módulo(s) [clv_person_aux] (2020-08-10)
------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Lista de Módulos:

        * clv_person_aux

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_person_aux
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo desejado:

            ::

                # ***** tkl-odoo13-jcafb21-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Atualizar o(s) módulo(s) [clv_person_aux_verification_jcafb] (2020-08-11)
-------------------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Lista de Módulos:

        * clv_person_aux_verification_jcafb

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_person_aux_verification_jcafb
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo desejado:

            ::

                # ***** tkl-odoo13-jcafb21-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Atualizar o(s) módulo(s) [clv_family_verification_jcafb] (2020-08-11)
---------------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Lista de Módulos:

        * clv_family_verification_jcafb

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_family_verification_jcafb
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo desejado:

            ::

                # ***** tkl-odoo13-jcafb21-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Criar um backup do banco de dados *CLVhealth-JCAFB-2021v-13* (2020-08-12a)
--------------------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb21-vm** e paralizar o *Odoo*:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            ssh tkl-odoo13-jcafb21-vm -l root

            /etc/init.d/odoo stop

            su odoo

    #. [tkl-odoo13-jcafb21-vm] Executar os comandos de criação dos arquivos de backup:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #
            # data_dir = /var/lib/odoo/.local/share/Odoo
            #

            cd /opt/odoo
            pg_dump clvhealth_jcafb_2021v_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2021v_13_2020-08-12a.sql

            gzip clvhealth_jcafb_2021v_13_2020-08-12a.sql
            pg_dump clvhealth_jcafb_2021v_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2021v_13_2020-08-12a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2021v_13_2020-08-12a.tar.gz clvhealth_jcafb_2021v_13

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021v_13_2020-08-12a.tar.gz clvhealth_jcafb

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo desejado:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    Criados os seguintes arquivos:

        * /opt/odoo/clvhealth_jcafb_2021v_13_2020-08-12a.sql
        * /opt/odoo/clvhealth_jcafb_2021v_13_2020-08-12a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2021v_13_2020-08-12a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021v_13_2020-08-12a.tar.gz

.. index:: clvhealth_jcafb_2021v_13_2020-08-12a.sql
.. index:: clvhealth_jcafb_2021v_13_2020-08-12a.sql.gz
.. index:: filestore_clvhealth_jcafb_2021v_13_2020-08-12a
.. index:: clvsol_filestore_clvhealth_jcafb_2021v_13_2020-08-12a

Restaurar um backup do banco de dados *CLVhealth-JCAFB-2021v-13* (2020-08-12a)
------------------------------------------------------------------------------

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
            # gzip -d clvhealth_jcafb_2021v_13_2020-08-12a.sql.gz

            dropdb -i clvhealth_jcafb_2021v_13

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2021v_13
            psql -f clvhealth_jcafb_2021v_13_2020-08-12a.sql -d clvhealth_jcafb_2021v_13 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2021v_13
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2021v_13_2020-08-12a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021v_13_2020-08-12a.tar.gz

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

Atualizar o(s) módulo(s) [ver lista] (2020-08-13)
-------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Lista de Módulos:

        * clv_base
        * clv_base_jcafb
        * clv_phase_jcafb
        * clv_address_aux_jcafb
        * clv_address_aux_history
        * clv_address_aux_verification_jcafb
        * clv_person_aux_jcafb
        * clv_person_aux_history
        * clv_person_aux_verification_jcafb

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_base
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo desejado:

            ::

                # ***** tkl-odoo13-jcafb21-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Criar um backup do banco de dados *CLVhealth-JCAFB-2021v-13* (2020-08-13a)
--------------------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb21-vm** e paralizar o *Odoo*:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            ssh tkl-odoo13-jcafb21-vm -l root

            /etc/init.d/odoo stop

            su odoo

    #. [tkl-odoo13-jcafb21-vm] Executar os comandos de criação dos arquivos de backup:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #
            # data_dir = /var/lib/odoo/.local/share/Odoo
            #

            cd /opt/odoo
            pg_dump clvhealth_jcafb_2021v_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2021v_13_2020-08-13a.sql

            gzip clvhealth_jcafb_2021v_13_2020-08-13a.sql
            pg_dump clvhealth_jcafb_2021v_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2021v_13_2020-08-13a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2021v_13_2020-08-13a.tar.gz clvhealth_jcafb_2021v_13

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021v_13_2020-08-13a.tar.gz clvhealth_jcafb

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo desejado:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    Criados os seguintes arquivos:

        * /opt/odoo/clvhealth_jcafb_2021v_13_2020-08-13a.sql
        * /opt/odoo/clvhealth_jcafb_2021v_13_2020-08-13a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2021v_13_2020-08-13a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021v_13_2020-08-13a.tar.gz

.. index:: clvhealth_jcafb_2021v_13_2020-08-13a.sql
.. index:: clvhealth_jcafb_2021v_13_2020-08-13a.sql.gz
.. index:: filestore_clvhealth_jcafb_2021v_13_2020-08-13a
.. index:: clvsol_filestore_clvhealth_jcafb_2021v_13_2020-08-13a

Restaurar um backup do banco de dados *CLVhealth-JCAFB-2021v-13* (2020-08-13a)
------------------------------------------------------------------------------

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
            # gzip -d clvhealth_jcafb_2021v_13_2020-08-13a.sql.gz

            dropdb -i clvhealth_jcafb_2021v_13

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2021v_13
            psql -f clvhealth_jcafb_2021v_13_2020-08-13a.sql -d clvhealth_jcafb_2021v_13 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2021v_13
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2021v_13_2020-08-13a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021v_13_2020-08-13a.tar.gz

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

Criar um backup do banco de dados *CLVhealth-JCAFB-2021v-13* (2020-08-13b)
--------------------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb21-vm** e paralizar o *Odoo*:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            ssh tkl-odoo13-jcafb21-vm -l root

            /etc/init.d/odoo stop

            su odoo

    #. [tkl-odoo13-jcafb21-vm] Executar os comandos de criação dos arquivos de backup:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #
            # data_dir = /var/lib/odoo/.local/share/Odoo
            #

            cd /opt/odoo
            pg_dump clvhealth_jcafb_2021v_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2021v_13_2020-08-13b.sql

            gzip clvhealth_jcafb_2021v_13_2020-08-13b.sql
            pg_dump clvhealth_jcafb_2021v_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2021v_13_2020-08-13b.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2021v_13_2020-08-13b.tar.gz clvhealth_jcafb_2021v_13

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021v_13_2020-08-13b.tar.gz clvhealth_jcafb

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo desejado:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    Criados os seguintes arquivos:

        * /opt/odoo/clvhealth_jcafb_2021v_13_2020-08-13b.sql
        * /opt/odoo/clvhealth_jcafb_2021v_13_2020-08-13b.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2021v_13_2020-08-13b.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021v_13_2020-08-13b.tar.gz

.. index:: clvhealth_jcafb_2021v_13_2020-08-13b.sql
.. index:: clvhealth_jcafb_2021v_13_2020-08-13b.sql.gz
.. index:: filestore_clvhealth_jcafb_2021v_13_2020-08-13b
.. index:: clvsol_filestore_clvhealth_jcafb_2021v_13_2020-08-13b

Restaurar um backup do banco de dados *CLVhealth-JCAFB-2021v-13* (2020-08-13b)
------------------------------------------------------------------------------

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
            # gzip -d clvhealth_jcafb_2021v_13_2020-08-13b.sql.gz

            dropdb -i clvhealth_jcafb_2021v_13

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2021v_13
            psql -f clvhealth_jcafb_2021v_13_2020-08-13b.sql -d clvhealth_jcafb_2021v_13 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2021v_13
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2021v_13_2020-08-13b.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021v_13_2020-08-13b.tar.gz

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

.. toctree::   :maxdepth: 2
