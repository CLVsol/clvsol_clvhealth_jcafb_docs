.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

==================================================================================================
[2020-03-(05-30)] - Migração do Banco de Dados - JCAFB-2020-NG - Servidor [tkl-odoo12-jcafb-ng-vm]
==================================================================================================

Atualizar o Odoo (2020-03-30)
-----------------------------

	#. [tkl-odoo12-jcafb-ng-vm] Upgrade the server software:

	    ::

	        ssh tkl-odoo12-jcafb-ng-vm -l root

	    ::

	        apt-get update
	        apt-get -y upgrade

	    ::

	        exit

Atualizar o `OCA/l10n-brazil <https://github.com/OCA/l10n-brazil>`_ (2020-03-30)
--------------------------------------------------------------------------------

	#. [tkl-odoo12-jcafb-ng-vm] To install "**OCA/l10n-brazil**", use the following commands (as odoo):

	    ::

	        ssh tkl-odoo12-jcafb-ng-vm -l odoo

	    ::

	        cd /opt/odoo/oca_l10n-brazil
	        git pull

	    ::

	        exit

:red:`(Não Executado])` Desabilitar a instalação do(s) módulo(s) [ver lista] (2020-03-30)
-----------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/module_installation`.

    #. [tkl-odoo12-jcafb-ng-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, **desabilitando** o(s) Módulo(s):

        * clv_base_sync_jcafb
        * clv_global_tag_sync_jcafb
        * clv_phase_sync_jcafb
        * clv_employee_sync_jcafb
        * clv_employee_history_sync_jcafb
        * clv_address_sync_jcafb
        * clv_address_history_sync_jcafb
        * clv_address_aux_sync_jcafb
        * clv_family_sync_jcafb
        * clv_family_history_sync_jcafb
        * clv_person_sync_jcafb
        * clv_person_history_sync_jcafb
        * clv_person_aux_sync_jcafb
        * clv_survey_sync_jcafb
        * clv_event_sync_jcafb
        * clv_document_sync_jcafb
        * clv_lab_test_sync_jcafb
        * clv_verification_sync_jcafb

Criar uma nova instância do *CLVhealth-JCAFB-2020-NG* (2020-03-30)
------------------------------------------------------------------

    #. [tkl-odoo12-jcafb-ng-vm] Estabelecer uma sessão ssh (session 1) com o servidor **tkl-odoo12-jcafb-ng-vm** e paralizar o *Odoo*:

        ::

            # ***** tkl-odoo12-jcafb-ng-vm
            #

            ssh tkl-odoo12-jcafb-ng-vm -l root

            /etc/init.d/odoo stop

            su odoo

    #. [tkl-odoo12-jcafb-ng-vm] Excluir a instância do *CLVhealth-JCAFB-2020* existente:

        ::

            # ***** tkl-odoo12-jcafb-ng-vm
            #

            cd /opt/odoo
            dropdb -i clvhealth_jcafb_2020_ng

            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020_ng

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-ng-vm** ao modo manual:

        ::

            # ***** tkl-odoo12-jcafb-ng-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    #. Estabelecer uma sessão ssh (session 2) com o servidor **tkl-odoo12-jcafb-ng-vm** e executar o **install.py**:

        ::

            # ***** tkl-odoo12-jcafb-ng-vm (session 2)
            #

            ssh tkl-odoo12-jcafb-ng-vm -l odoo

            cd /opt/odoo/clvsol_clvhealth_jcafb/project
            
            python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020-ng"
            # Execution time: 0:08:22.364

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-ng-vm** ao modo desejado:

        ::

            # ***** tkl-odoo12-jcafb-ng-vm (session 1)
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

Migrar os Usuários de **clvhealth_jcafb_2020** para **clvhealth_jcafb_2020_ng** (2020-03-30)
--------------------------------------------------------------------------------------------

    #. Estabelecer uma sessão ssh com o servidor **tkl-odoo12-jcafb-ng-vm** e executar o **res_users_migration.py**, acessando o servidor **tkl-odoo12-jcafb-ng-vm** [base de dados **clvhealth_jcafb_2020**]:

        ::

            # ***** tkl-odoo12-jcafb-ng-vm (session 2)
            #

            ssh tkl-odoo12-jcafb-ng-vm -l odoo

            cd /opt/odoo/clvsol_clvhealth_jcafb/project
            
            python3 res_users_migration.py --rserver "https://192.168.25.183" --radmin_pw "***" --rdb "clvhealth_jcafb_2020" --lserver "https://192.168.25.186" --ladmin_pw "***" --ldb "clvhealth_jcafb_2020_ng"
            # Execution time: 0:01:10.814

    * Os "passwords" não foram migrados.
        
Criar o *External Sync Host* "https://192.168.25.183" (2020-03-30)
------------------------------------------------------------------

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-ng-vm <https://tkl-odoo12-jcafb-ng-vm>`_

        #. Criar o *External Sync Host* **https://192.168.25.183**:

            * Menu de acesso:
                
                * *External Sync* > *Configuration* > *Hosts* > Criar

            * Parâmetros utilizados:
                
                * External Host Name: "**https://192.168.25.183**"
                * External Database Name: "**clvhealth_jcafb_2020**"
                * External User: "**admin**"
                * External User Password: "*******"

:red:`(Não Executado])` Criar um backup do banco de dados *CLVhealth-JCAFB-2020_NG* (2020-03-30a)
-------------------------------------------------------------------------------------------------

	* Referência: :doc:`/setup/clvhealth_jcafb_backup`.

	#. [tkl-odoo12-jcafb-ng-vm] Estabelecer uma sessão ssh com o servidor **tkl-odoo12-jcafb-ng-vm** e paralizar o *Odoo*:

	    ::

	        # ***** tkl-odoo12-jcafb-ng-vm
	        #

	        ssh tkl-odoo12-jcafb-ng-vm -l root

	        /etc/init.d/odoo stop

	        su odoo

	#. [tkl-odoo12-jcafb-ng-vm] Executar os comandos de criação dos arquivos de backup:

	    ::

	        # ***** tkl-odoo12-jcafb-ng-vm
	        #
	        # data_dir = /var/lib/odoo/.local/share/Odoo
	        #

	        cd /opt/odoo
	        pg_dump clvhealth_jcafb_2020_ng -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_ng_2020-03-30a.sql

	        gzip clvhealth_jcafb_2020_ng_2020-03-30a.sql
	        pg_dump clvhealth_jcafb_2020_ng -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_ng_2020-03-30a.sql

	        cd /var/lib/odoo/.local/share/Odoo/filestore
	        tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-03-30a.tar.gz clvhealth_jcafb_2020_ng

	        cd /opt/odoo/clvsol_filestore
	        tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-03-30a.tar.gz clvhealth_jcafb

	#. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-ng-vm** ao modo desejado:

	    ::

	        # ***** tkl-odoo12-jcafb-ng-vm
	        #

	        cd /opt/odoo
	        /usr/bin/odoo -c /etc/odoo/odoo-man.conf

	        ^C

	        exit

	        /etc/init.d/odoo start

    Criados os seguintes arquivos:
        * /opt/odoo/clvhealth_jcafb_2020_ng_2020-03-30a.sql
        * /opt/odoo/clvhealth_jcafb_2020_ng_2020-03-30a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-03-30a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-03-30a.tar.gz

.. index:: clvhealth_jcafb_2020_ng_2020-03-30a.sql
.. index:: filestore_clvhealth_jcafb_2020_ng_2020-03-30a
.. index:: clvsol_filestore_clvhealth_jcafb_2020_ng_2020-03-30a

:red:`(Não Executado])` Restaurar um backup do banco de dados *CLVhealth-JCAFB-2020-NG* (2020-03-30a)
-----------------------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_restore`.

    #. [tkl-odoo12-jcafb-ng-vm] Estabelecer uma sessão ssh com o servidor **tkl-odoo12-jcafb-ng-vm** e paralizar o *Odoo*:

        ::

            # ***** tkl-odoo12-jcafb-ng-vm
            #

            ssh tkl-odoo12-jcafb-ng-vm -l root

            /etc/init.d/odoo stop

            su odoo

    #. [tkl-odoo12-jcafb-ng-vm] Executar os comandos de restauração dos arquivos de backup:

        ::

            # ***** tkl-odoo12-jcafb-ng-vm
            #

            cd /opt/odoo
            # gzip -d clvhealth_jcafb_2020_ng_2020-03-30a.sql.gz

            dropdb -i clvhealth_jcafb_2020_ng

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020_ng
            psql -f clvhealth_jcafb_2020_ng_2020-03-30a.sql -d clvhealth_jcafb_2020_ng -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020_ng
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-03-30a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-03-30a.tar.gz

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-ng-vm** ao modo desejado:

        ::

            # ***** tkl-odoo12-jcafb-ng-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    #. [tkl-odoo12-jcafb-ng-vm] Configurar o parâmetro "**web.base.url**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-ng-vm <https://tkl-odoo12-jcafb-ng-vm>`_

        #. Acessar a *View* **Parâmetros do Sistema**:

            * Menu de acesso:
                
                * **Configurações** » **Técnico** » **Parâmetros** » **Parâmetros do Sistema**

        #. Pesquisar pelo registro com a **Chave** "**web.base.url**";

        #. Editar o registro apresentado (**Chave**: "**web.base.url**")

        #. Alterar o campo **Valor** para:

            * "**tkl-odoo12-jcafb-ng-vm**".

        #. Salvar o registro editado.

:red:`(Não Executado])` Instalar o(s) módulo(s) [ver lista] (2020-03-30)
------------------------------------------------------------------------

    * Referência: :doc:`/setup/module_installation`.

    #. [tkl-odoo12-jcafb-ng-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, **habilitando** o(s) Módulo(s):

        * clv_base_sync_jcafb
        * clv_global_tag_sync_jcafb
        * clv_phase_sync_jcafb
        * clv_employee_sync_jcafb
        * clv_employee_history_sync_jcafb
        * clv_address_sync_jcafb
        * clv_address_history_sync_jcafb
        * clv_address_aux_sync_jcafb
        * clv_family_sync_jcafb
        * clv_family_history_sync_jcafb
        * clv_person_sync_jcafb
        * clv_person_history_sync_jcafb
        * clv_person_aux_sync_jcafb
        * clv_survey_sync_jcafb
        * clv_event_sync_jcafb
        * clv_document_sync_jcafb
        * clv_lab_test_sync_jcafb
        * clv_verification_sync_jcafb

    #. [tkl-odoo12-jcafb-ng-vm] **Executar** a instalação do(s) Módulo(s) adicionado(s)/habilitado(s):

        #. Estabelecer uma sessão ssh (session 1) com o servidor **tkl-odoo12-jcafb-ng-vm** e executar o *Odoo* no modo manual:

            ::

                # ***** tkl-odoo12-jcafb-ng-vm (session 1)
                #

                ssh tkl-odoo12-jcafb-ng-vm -l root

                /etc/init.d/odoo stop

                su odoo
                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

        #. Estabelecer uma sessão ssh (session 2) com o servidor **tkl-odoo12-jcafb-ng-vm** e executar o **install.py**:

            ::

                # ***** tkl-odoo12-jcafb-ng-vm (session 2)
                #

                ssh tkl-odoo12-jcafb-ng-vm -l odoo

                cd /opt/odoo/clvsol_clvhealth_jcafb/project
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020_ng"
                # Execution time: 0:01:43.776

            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-ng-vm** ao modo desejado:

            ::

                # ***** tkl-odoo12-jcafb-ng-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

.. _Lista de Schedules 20200330:

Lista de *Schedules* instalados (2020-03-30)
--------------------------------------------

    * Lista de *Schedules* instalados:

        * :green:`(Enabled)` res.country (res.country)
        * :green:`(Enabled)` res.country.state (res.country.state)
        * :green:`(Enabled)` res.city (res.city)

        * :green:`(Enabled)` res.users (res.users)

        * :green:`(Enabled)` clv.global_tag (clv.global_tag)

        * :green:`(Enabled)` clv.phase (clv.phase)

        * :green:`(Enabled)` hr.department (hr.department)
        * :green:`(Enabled)` hr.job (hr.job)
        * :green:`(Enabled)` hr.employee (hr.employee)
        * :green:`(Enabled)` hr.employee.history (hr.employee.history)

        * :green:`(Enabled)` clv.address.category (clv.address.category)
        * :green:`(Enabled)` clv.address (clv.address)
        * :green:`(Enabled)` clv.address.history (clv.address.history)

        * :green:`(Enabled)` clv.address.aux (clv.address.aux)

        * :green:`(Enabled)` clv.family.category (clv.family.category)
        * :green:`(Enabled)` clv.family (clv.family)
        * :green:`(Enabled)` clv.family.history (clv.family.history)

        * :green:`(Enabled)` clv.person.category (clv.person.category)
        * :green:`(Enabled)` clv.person.marker (clv.person.marker)
        * :green:`(Enabled)` clv.person (clv.person)
        * :green:`(Enabled)` clv.person.history (clv.person.history)

        * :green:`(Enabled)` clv.person.aux (clv.person.aux)

        * :green:`(Enabled)` survey.stage (survey.stage)
        * :green:`(Enabled)` survey.survey (survey.survey)
        * :green:`(Enabled)` survey.page (survey.page)
        * :green:`(Enabled)` survey.question (survey.question)
        * :green:`(Enabled)` survey.label (survey.label)
        * :green:`(Enabled)` survey.user_input (survey.user_input)
        * :red:`(Disabled)` survey.user_input_line (survey.user_input_line)

        * :green:`(Enabled)` clv.event (clv.event)
        * :green:`(Enabled)` clv.event.attendee (clv.event.attendee)

        * :green:`(Enabled)` clv.document.category (clv.document.category)
        * :green:`(Enabled)` clv.document.type (clv.document.type)
        * :green:`(Enabled)` clv.document (clv.document)
        * :red:`(Disabled)` clv.document.item (clv.document.item)

        * :green:`(Enabled)` clv.lab_test.unit (clv.lab_test.unit)
        * :green:`(Enabled)` clv.lab_test.parasite (clv.lab_test.parasite)
        * :green:`(Enabled)` clv.lab_test.crystal (clv.lab_test.crystal)
        * :green:`(Enabled)` clv.lab_test.type (clv.lab_test.type)
        * :green:`(Enabled)` clv.lab_test.request (clv.lab_test.request)
        * :green:`(Enabled)` clv.lab_test.result (clv.lab_test.result)
        * :green:`(Enabled)` clv.lab_test.report (clv.lab_test.report)
        * :red:`(Disabled)` clv.lab_test.criterion (clv.lab_test.criterion)

        * :green:`(Enabled)` clv.verification.marker (clv.verification.marker)

Executar o *External Sync Batch* "*Default Batch*" (2020-03-30)
---------------------------------------------------------------

    #. [tkl-odoo12-jcafb-ng-vm] Configurar os :bi:`External Sync Schedules` :green:`Novos`:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-ng-vm <https://tkl-odoo12-jcafb-ng-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit`, os :bi:`External Sync Schedules` :green:`Novos`:

            * Lista de *Schedules*:
                
                * :ref:`Lista de Schedules 20200330`

            * Menu de acesso:
                
                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Schedules` » **Ação** » :bi:`External Sync Schedule Mass Edit`

            * Parâmetros alterados:
                
                * *External Host*: "**https://192.168.25.183**"
                * *Max Task Registers*: "**200.000**"

    #. Estabelecer uma sessão ssh com o servidor **tkl-odoo12-jcafb-ng-vm** e executar o *Odoo* no modo manual:

        ::

            # ***** tkl-odoo12-jcafb-ng-vm
            #

            ssh tkl-odoo12-jcafb-ng-vm -l root

            /etc/init.d/odoo stop

            su odoo

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    #. [tkl-odoo12-jcafb-ng-vm] Executar o :bi:`External Sync Batch` "**Default Batch**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-ng-vm <https://tkl-odoo12-jcafb-ng-vm>`_

        #. Executar a ação :bi:`External Sync Batch Exec` para o "**Default Batch**":

            * Menu de acesso:
                
                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Batches` » **Ação** » :bi:`External Sync Batch Exec`

            * *Members*:
                
                * :ref:`Lista de Schedules 20200330`

            * *Synchronization Log*:
                
                * :ref:`External Sync Batch - Default Batch - 20200330`

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-ng-vm** ao modo padrão:

        ::

            # ***** tkl-odoo12-jcafb-ng-vm
            #

            ^C

            exit

            /etc/init.d/odoo start

Executar o *External Sync Batch* "*Default Batch*" (2) (2020-03-30)
-------------------------------------------------------------------

    #. [tkl-odoo12-jcafb-ng-vm] Configurar os :bi:`External Sync Schedules` :green:`Novos`:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-ng-vm <https://tkl-odoo12-jcafb-ng-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit`, os :bi:`External Sync Schedules` :green:`Novos`:

            * Lista de *Schedules*:
                
                * :ref:`Lista de Schedules 20200330`

            * Menu de acesso:
                
                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Schedules` » **Ação** » :bi:`External Sync Schedule Mass Edit`

            * Parâmetros alterados:
                
                * *External Host*: "**https://192.168.25.183**"
                * *Max Task Registers*: "**200.000**"

    #. Estabelecer uma sessão ssh com o servidor **tkl-odoo12-jcafb-ng-vm** e executar o *Odoo* no modo manual:

        ::

            # ***** tkl-odoo12-jcafb-ng-vm
            #

            ssh tkl-odoo12-jcafb-ng-vm -l root

            /etc/init.d/odoo stop

            su odoo

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    #. [tkl-odoo12-jcafb-ng-vm] Executar o :bi:`External Sync Batch` "**Default Batch**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-ng-vm <https://tkl-odoo12-jcafb-ng-vm>`_

        #. Executar a ação :bi:`External Sync Batch Exec` para o "**Default Batch**":

            * Menu de acesso:
                
                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Batches` » **Ação** » :bi:`External Sync Batch Exec`

            * *Members*:
                
                * :ref:`Lista de Schedules 20200330`

            * *Synchronization Log*:
                
                * :ref:`External Sync Batch - Default Batch - 20200330(2)`

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-ng-vm** ao modo padrão:

        ::

            # ***** tkl-odoo12-jcafb-ng-vm
            #

            ^C

            exit

            /etc/init.d/odoo start

Lista de *Schedules* executados (2020-03-30)
--------------------------------------------

    * Lista de *Schedules* instalados:

        * :green:`[Execution time: 0:00:07.029]` res.country (res.country)
        * :green:`[Execution time: 0:00:19.444]` res.country.state (res.country.state)
        * :green:`[Execution time: 0:03:04.227]` res.city (res.city)

        * :green:`[Execution time: 0:00:08.164]` res.users (res.users)

        * :green:`[Execution time: 0:00:01.301]` clv.global_tag (clv.global_tag)

        * :green:`[Execution time: 0:00:00.332]` clv.phase (clv.phase)

        * :green:`[Execution time: 0:00:03.071]` hr.department (hr.department)
        * :green:`[Execution time: 0:00:01.055]` hr.job (hr.job)
        * :green:`[Execution time: 0:00:30.093]` hr.employee (hr.employee)
        * :green:`[Execution time: 0:00:11.928]` hr.employee.history (hr.employee.history)

        * :green:`[Execution time: 0:00:00.241]` clv.address.category (clv.address.category)
        * :green:`[Execution time: 0:01:55.671]` clv.address (clv.address)
        * :green:`[Execution time: 0:01:38.385]` clv.address.history (clv.address.history)

        * :green:`[Execution time: 0:00:32.994]` clv.address.aux (clv.address.aux)

        * :green:`[Execution time: 0:00:00.190]` clv.family.category (clv.family.category)
        * :green:`[Execution time: 0:01:09.708]` clv.family (clv.family)
        * :green:`[Execution time: 0:00:42.131]` clv.family.history (clv.family.history)

        * :green:`[Execution time: 0:00:00.280]` clv.person.category (clv.person.category)
        * :green:`[Execution time: 0:00:00.348]` clv.person.marker (clv.person.marker)
        * :green:`[Execution time: 0:04:48.689]` clv.person (clv.person)
        * :green:`[Execution time: 0:05:42.187]` clv.person.history (clv.person.history)

        * :green:`[Execution time: 0:02:02.107]` clv.person.aux (clv.person.aux)

        * :green:`[Execution time: 0:00:00.414]` survey.stage (survey.stage)
        * :green:`[Execution time: 0:00:03.077]` survey.survey (survey.survey)
        * :green:`[Execution time: 0:00:10.658]` survey.page (survey.page)
        * :green:`[Execution time: 0:00:52.787]` survey.question (survey.question)
        * :green:`[Execution time: 0:02:26.816]` survey.label (survey.label)
        * :green:`[Execution time: 0:03:39.541]` survey.user_input (survey.user_input)
        * :red:`[Execution time: 4:49:22.883]` survey.user_input_line (survey.user_input_line)

        * :green:`[Execution time: 0:00:01.786]` clv.event (clv.event)
        * :green:`[Execution time: 0:01:02.931]` clv.event.attendee (clv.event.attendee)

        * :green:`[Execution time: 0:00:00.488]` clv.document.category (clv.document.category)
        * :green:`[Execution time: 0:00:01.904]` clv.document.type (clv.document.type)
        * :green:`[Execution time: 0:13:26.957]` clv.document (clv.document)
        * :red:`[Execution time: 4:36:23.207]` clv.document.item (clv.document.item)

        * :green:`[Execution time: 0:00:00.478]` clv.lab_test.unit (clv.lab_test.unit)
        * :green:`[Execution time: 0:00:00.646]` clv.lab_test.parasite (clv.lab_test.parasite)
        * :green:`[Execution time: 0:00:00.680]` clv.lab_test.crystal (clv.lab_test.crystal)
        * :green:`[Execution time: 0:00:01.134]` clv.lab_test.type (clv.lab_test.type)
        * :green:`[Execution time: 0:05:13.299]` clv.lab_test.request (clv.lab_test.request)
        * :green:`[Execution time: 0:04:18.580]` clv.lab_test.result (clv.lab_test.result)
        * :green:`[Execution time: 0:03:06.326]` clv.lab_test.report (clv.lab_test.report)
        * :red:`[Execution time: 3:00:10.402]` clv.lab_test.criterion (clv.lab_test.criterion)

        * :green:`[Execution time: 0:00:00.764]` clv.verification.marker (clv.verification.marker)

.. toctree::
   :maxdepth: 2

   jcafb_2020_ng_history_002_sync_log