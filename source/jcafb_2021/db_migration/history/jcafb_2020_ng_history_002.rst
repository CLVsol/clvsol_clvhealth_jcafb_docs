.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

==================================================================================================
[2020-05-(01-16)] - Migração do Banco de Dados - JCAFB-2020-NG - Servidor [tkl-odoo12-jcafb-ng-vm]
==================================================================================================

Atualizar o Odoo (2020-04-30)
-----------------------------

	#. [tkl-odoo12-jcafb-ng-vm] Upgrade the server software:

	    ::

	        ssh tkl-odoo12-jcafb-ng-vm -l root

	    ::

	        apt-get update
	        apt-get -y upgrade

	    ::

	        exit

Atualizar o `OCA/l10n-brazil <https://github.com/OCA/l10n-brazil>`_ (2020-04-30)
--------------------------------------------------------------------------------

	#. [tkl-odoo12-jcafb-ng-vm] To install "**OCA/l10n-brazil**", use the following commands (as odoo):

	    ::

	        ssh tkl-odoo12-jcafb-ng-vm -l odoo

	    ::

	        cd /opt/odoo/oca_l10n-brazil
	        git pull

	    ::

	        exit

:red:`(Não Executado])` Desabilitar a instalação do(s) módulo(s) [ver lista] (2020-04-30)
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
        * clv_set_sync_jcafb
        * clv_export_sync_jcafb

Criar uma nova instância do *CLVhealth-JCAFB-2020-NG* (2020-04-30)
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

Migrar os Usuários de **clvhealth_jcafb_2020** para **clvhealth_jcafb_2020_ng** (2020-04-30)
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
        
Criar o *External Sync Host* "https://192.168.25.183" (2020-04-30)
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

Criar um backup do banco de dados *CLVhealth-JCAFB-2020_NG* (2020-04-30a)
-------------------------------------------------------------------------

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
	        pg_dump clvhealth_jcafb_2020_ng -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_ng_2020-04-30a.sql

	        gzip clvhealth_jcafb_2020_ng_2020-04-30a.sql
	        pg_dump clvhealth_jcafb_2020_ng -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_ng_2020-04-30a.sql

	        cd /var/lib/odoo/.local/share/Odoo/filestore
	        tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-04-30a.tar.gz clvhealth_jcafb_2020_ng

	        cd /opt/odoo/clvsol_filestore
	        tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-04-30a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_ng_2020-04-30a.sql
        * /opt/odoo/clvhealth_jcafb_2020_ng_2020-04-30a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-04-30a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-04-30a.tar.gz

:red:`(Não Executado])` Restaurar um backup do banco de dados *CLVhealth-JCAFB-2020-NG* (2020-04-30a)
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
            # gzip -d clvhealth_jcafb_2020_ng_2020-04-30a.sql.gz

            dropdb -i clvhealth_jcafb_2020_ng

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020_ng
            psql -f clvhealth_jcafb_2020_ng_2020-04-30a.sql -d clvhealth_jcafb_2020_ng -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020_ng
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-04-30a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-04-30a.tar.gz

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

:red:`(Não Executado])` Instalar o(s) módulo(s) [ver lista] (2020-04-30)
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
        * clv_set_sync_jcafb
        * clv_export_sync_jcafb

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

.. _Lista de Schedules 20200430(1):

Lista de *Schedules* instalados (1) (2020-04-30)
------------------------------------------------

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

        * :green:`(Enabled)` clv.set (clv.set)
        * :green:`(Enabled)` clv.set.element (clv.set.element)

        * :green:`(Enabled)` ir.model (ir.model)
        * :green:`(Enabled)` ir.model.fields (ir.model.fields)

        * :green:`(Enabled)` clv.model_export.template (clv.model_export.template)
        * :green:`(Enabled)` clv.model_export.template.field (clv.model_export.template.field)
        * :green:`(Enabled)` clv.model_export.template.document_item (clv.model_export.template.document_item)
        * :green:`(Enabled)` clv.model_export.template.lab_test_criterion (clv.model_export.template.lab_test_criterion)
        * :green:`(Enabled)` clv.model_export (clv.model_export)
        * :green:`(Enabled)` clv.model_export.field (clv.model_export.field)
        * :green:`(Enabled)` clv.model_export.document_item (clv.model_export.document_item)
        * :green:`(Enabled)` clv.model_export.lab_test_criterion (clv.model_export.lab_test_criterion)

Executar o *External Sync Batch* "*Default Batch*" (1) (2020-04-30)
-------------------------------------------------------------------

    #. [tkl-odoo12-jcafb-ng-vm] Configurar os :bi:`External Sync Schedules` :green:`Novos`:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-ng-vm <https://tkl-odoo12-jcafb-ng-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit`, os :bi:`External Sync Schedules` :green:`Novos`:

            * Lista de *Schedules*:
                
                * :ref:`Lista de Schedules 20200430(1)`

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
                
                * :ref:`Lista de Schedules 20200430(1)`

            * *Synchronization Log*:
                
                * :ref:`External Sync Batch - Default Batch - 20200430(1)`

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-ng-vm** ao modo padrão:

        ::

            # ***** tkl-odoo12-jcafb-ng-vm
            #

            ^C

            exit

            /etc/init.d/odoo start

Lista de *Schedules* executados (1) (2020-04-30)
------------------------------------------------

    * Lista de *Schedules* instalados:

        * :green:`[Execution time: 0:00:08.993]` res.country (res.country)
        * :green:`[Execution time: 0:00:20.868]` res.country.state (res.country.state)
        * :green:`[Execution time: 0:03:17.597]` res.city (res.city)

        * :green:`[Execution time: 0:00:08.648]` res.users (res.users)

        * :green:`[Execution time: 0:00:01.466]` clv.global_tag (clv.global_tag)

        * :green:`[Execution time: 0:00:00.406]` clv.phase (clv.phase)

        * :green:`[Execution time: 0:00:03.482]` hr.department (hr.department)
        * :green:`[Execution time: 0:00:01.349]` hr.job (hr.job)
        * :green:`[Execution time: 0:00:30.890]` hr.employee (hr.employee)
        * :green:`[Execution time: 0:00:11.979]` hr.employee.history (hr.employee.history)

        * :green:`[Execution time: 0:00:00.271]` clv.address.category (clv.address.category)
        * :green:`[Execution time: 0:01:50.870]` clv.address (clv.address)
        * :green:`[Execution time: 0:01:38.291]` clv.address.history (clv.address.history)

        * :green:`[Execution time: 0:00:33.808]` clv.address.aux (clv.address.aux)

        * :green:`[Execution time: 0:00:00.184]` clv.family.category (clv.family.category)
        * :green:`[Execution time: 0:01:04.967]` clv.family (clv.family)
        * :green:`[Execution time: 0:00:46.423]` clv.family.history (clv.family.history)

        * :green:`[Execution time: 0:00:00.263]` clv.person.category (clv.person.category)
        * :green:`[Execution time: 0:00:00.351]` clv.person.marker (clv.person.marker)
        * :green:`[Execution time: 0:04:38.947]` clv.person (clv.person)
        * :green:`[Execution time: 0:05:18.981]` clv.person.history (clv.person.history)

        * :green:`[Execution time: 0:02:02.485]` clv.person.aux (clv.person.aux)

        * :green:`[Execution time: 0:00:00.417]` survey.stage (survey.stage)
        * :green:`[Execution time: 0:00:03.680]` survey.survey (survey.survey)
        * :green:`[Execution time: 0:00:10.273]` survey.page (survey.page)
        * :green:`[Execution time: 0:00:53.991]` survey.question (survey.question)
        * :green:`[Execution time: 0:02:24.425]` survey.label (survey.label)
        * :green:`[Execution time: 0:04:03.935]` survey.user_input (survey.user_input)
        * :red:`[Execution time: 4:49:22.883]` survey.user_input_line (survey.user_input_line)

        * :green:`[Execution time: 0:00:01.731]` clv.event (clv.event)
        * :green:`[Execution time: 0:01:07.809]` clv.event.attendee (clv.event.attendee)

        * :green:`[Execution time: 0:00:00.567]` clv.document.category (clv.document.category)
        * :green:`[Execution time: 0:00:03.035]` clv.document.type (clv.document.type)
        * :green:`[Execution time: 0:13:34.838]` clv.document (clv.document)
        * :red:`[Execution time: 4:36:23.207]` clv.document.item (clv.document.item)

        * :green:`[Execution time: 0:00:00.528]` clv.lab_test.unit (clv.lab_test.unit)
        * :green:`[Execution time: 0:00:00.622]` clv.lab_test.parasite (clv.lab_test.parasite)
        * :green:`[Execution time: 0:00:00.524]` clv.lab_test.crystal (clv.lab_test.crystal)
        * :green:`[Execution time: 0:00:01.181]` clv.lab_test.type (clv.lab_test.type)
        * :green:`[Execution time: 0:05:25.819]` clv.lab_test.request (clv.lab_test.request)
        * :green:`[Execution time: 0:04:43.400]` clv.lab_test.result (clv.lab_test.result)
        * :green:`[Execution time: 0:03:16.983]` clv.lab_test.report (clv.lab_test.report)
        * :red:`[Execution time: 3:00:10.402]` clv.lab_test.criterion (clv.lab_test.criterion)

        * :green:`[Execution time: 0:00:00.813]` clv.verification.marker (clv.verification.marker)

        * :green:`[Execution time: 0:00:00.277]` clv.set (clv.set)
        * :green:`[Execution time: 0:00:42.521]` clv.set.element (clv.set.element)

        * :green:`[Execution time: 0:00:11.053]` ir.model (ir.model)
        * :green:`[Execution time: 0:03:41.626]` ir.model.fields (ir.model.fields)

        * :green:`[Execution time: 0:00:00.884]` clv.model_export.template (clv.model_export.template)
        * :green:`[Execution time: 0:00:03.997]` clv.model_export.template.field (clv.model_export.template.field)
        * :green:`[Execution time: 0:00:11.147]` clv.model_export.template.document_item (clv.model_export.template.document_item)
        * :green:`[Execution time: 0:00:09.802]` clv.model_export.template.lab_test_criterion (clv.model_export.template.lab_test_criterion)
        * :green:`[Execution time: 0:00:03.456]` clv.model_export (clv.model_export)
        * :green:`[Execution time: 0:00:04.320]` clv.model_export.field (clv.model_export.field)
        * :green:`[Execution time: 0:00:12.712]` clv.model_export.document_item (clv.model_export.document_item)
        * :green:`[Execution time: 0:00:10.154]` clv.model_export.lab_test_criterion (clv.model_export.lab_test_criterion)

Criar um backup do banco de dados *CLVhealth-JCAFB-2020_NG* (2020-04-30b)
-------------------------------------------------------------------------

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
            pg_dump clvhealth_jcafb_2020_ng -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_ng_2020-04-30b.sql

            gzip clvhealth_jcafb_2020_ng_2020-04-30b.sql
            pg_dump clvhealth_jcafb_2020_ng -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_ng_2020-04-30b.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-04-30b.tar.gz clvhealth_jcafb_2020_ng

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-04-30b.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_ng_2020-04-30b.sql
        * /opt/odoo/clvhealth_jcafb_2020_ng_2020-04-30b.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-04-30b.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-04-30b.tar.gz

:red:`(Não Executado])` Restaurar um backup do banco de dados *CLVhealth-JCAFB-2020-NG* (2020-04-30b)
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
            # gzip -d clvhealth_jcafb_2020_ng_2020-04-30b.sql.gz

            dropdb -i clvhealth_jcafb_2020_ng

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020_ng
            psql -f clvhealth_jcafb_2020_ng_2020-04-30b.sql -d clvhealth_jcafb_2020_ng -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020_ng
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-04-30b.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-04-30b.tar.gz

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

Executar o *External Sync Batch* "*Default Batch*" (2) (2020-04-30)
-------------------------------------------------------------------

    #. [tkl-odoo12-jcafb-ng-vm] Configurar os :bi:`External Sync Schedules` :green:`Novos`:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-ng-vm <https://tkl-odoo12-jcafb-ng-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit`, os :bi:`External Sync Schedules` :green:`Novos`:

            * Lista de *Schedules*:
                
                * :ref:`Lista de Schedules 20200430(1)`

            * Menu de acesso:
                
                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Schedules` » **Ação** » :bi:`External Sync Schedule Mass Edit`

            * Parâmetros alterados:
                
                * *Disable Identification*: "*marcado**"

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
                
                * :ref:`Lista de Schedules 20200430(1)`

            * *Synchronization Log*:
                
                * :ref:`External Sync Batch - Default Batch - 20200430(2)`

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-ng-vm** ao modo padrão:

        ::

            # ***** tkl-odoo12-jcafb-ng-vm
            #

            ^C

            exit

            /etc/init.d/odoo start

Lista de *Schedules* executados (2) (2020-04-30)
------------------------------------------------

    * Lista de *Schedules* instalados:

        * :green:`[Execution time: 0:00:00.278]` res.country (res.country)
        * :green:`[Execution time: 0:00:00.527]` res.country.state (res.country.state)
        * :green:`[Execution time: 0:00:00.193]` res.city (res.city)

        * :green:`[Execution time: 0:00:00.188]` res.users (res.users)

        * :green:`[Execution time: 0:00:00.234]` clv.global_tag (clv.global_tag)

        * :green:`[Execution time: 0:00:00.199]` clv.phase (clv.phase)

        * :green:`[Execution time: 0:00:00.200]` hr.department (hr.department)
        * :green:`[Execution time: 0:00:00.185]` hr.job (hr.job)
        * :green:`[Execution time: 0:00:00.212]` hr.employee (hr.employee)
        * :green:`[Execution time: 0:00:00.181]` hr.employee.history (hr.employee.history)

        * :green:`[Execution time: 0:00:00.183]` clv.address.category (clv.address.category)
        * :green:`[Execution time: 0:00:00.216]` clv.address (clv.address)
        * :green:`[Execution time: 0:00:00.258]` clv.address.history (clv.address.history)

        * :green:`[Execution time: 0:00:00.193]` clv.address.aux (clv.address.aux)

        * :green:`[Execution time: 0:00:00.185]` clv.family.category (clv.family.category)
        * :green:`[Execution time: 0:00:00.220]` clv.family (clv.family)
        * :green:`[Execution time: 0:00:00.187]` clv.family.history (clv.family.history)

        * :green:`[Execution time: 0:00:00.200]` clv.person.category (clv.person.category)
        * :green:`[Execution time: 0:00:00.203]` clv.person.marker (clv.person.marker)
        * :green:`[Execution time: 0:00:19.932]` clv.person (clv.person)
        * :green:`[Execution time: 0:00:00.177]` clv.person.history (clv.person.history)

        * :green:`[Execution time: 0:00:00.177]` clv.person.aux (clv.person.aux)

        * :green:`[Execution time: 0:00:00.181]` survey.stage (survey.stage)
        * :green:`[Execution time: 0:00:00.183]` survey.survey (survey.survey)
        * :green:`[Execution time: 0:00:00.177]` survey.page (survey.page)
        * :green:`[Execution time: 0:00:00.194]` survey.question (survey.question)
        * :green:`[Execution time: 0:00:00.171]` survey.label (survey.label)
        * :green:`[Execution time: 0:04:27.606]` survey.user_input (survey.user_input)
        * :red:`[Execution time: 4:49:22.883]` survey.user_input_line (survey.user_input_line)

        * :green:`[Execution time: 0:00:00.215]` clv.event (clv.event)
        * :green:`[Execution time: 0:00:00.185]` clv.event.attendee (clv.event.attendee)

        * :green:`[Execution time: 0:00:00.187]` clv.document.category (clv.document.category)
        * :green:`[Execution time: 0:00:00.188]` clv.document.type (clv.document.type)
        * :green:`[Execution time: 0:00:00.216]` clv.document (clv.document)
        * :red:`[Execution time: 4:36:23.207]` clv.document.item (clv.document.item)

        * :green:`[Execution time: 0:00:00.186]` clv.lab_test.unit (clv.lab_test.unit)
        * :green:`[Execution time: 0:00:00.190]` clv.lab_test.parasite (clv.lab_test.parasite)
        * :green:`[Execution time: 0:00:00.192]` clv.lab_test.crystal (clv.lab_test.crystal)
        * :green:`[Execution time: 0:00:00.185]` clv.lab_test.type (clv.lab_test.type)
        * :green:`[Execution time: 0:00:00.297]` clv.lab_test.request (clv.lab_test.request)
        * :green:`[Execution time: 0:03:49.973]` clv.lab_test.result (clv.lab_test.result)
        * :green:`[Execution time: 0:00:00.282]` clv.lab_test.report (clv.lab_test.report)
        * :red:`[Execution time: 3:00:10.402]` clv.lab_test.criterion (clv.lab_test.criterion)

        * :green:`[Execution time: 0:00:00.290]` clv.verification.marker (clv.verification.marker)

        * :green:`[Execution time: 0:00:00.244]` clv.set (clv.set)
        * :green:`[Execution time: 0:00:00.223]` clv.set.element (clv.set.element)

        * :green:`[Execution time: 0:00:00.679]` ir.model (ir.model)
        * :green:`[Execution time: 0:00:10.256]` ir.model.fields (ir.model.fields)

        * :green:`[Execution time: 0:00:00.202]` clv.model_export.template (clv.model_export.template)
        * :green:`[Execution time: 0:00:00.196]` clv.model_export.template.field (clv.model_export.template.field)
        * :green:`[Execution time: 0:00:10.834]` clv.model_export.template.document_item (clv.model_export.template.document_item)
        * :green:`[Execution time: 0:00:10.219]` clv.model_export.template.lab_test_criterion (clv.model_export.template.lab_test_criterion)
        * :green:`[Execution time: 0:00:00.171]` clv.model_export (clv.model_export)
        * :green:`[Execution time: 0:00:00.183]` clv.model_export.field (clv.model_export.field)
        * :green:`[Execution time: 0:00:11.125]` clv.model_export.document_item (clv.model_export.document_item)
        * :green:`[Execution time: 0:00:10.171]` clv.model_export.lab_test_criterion (clv.model_export.lab_test_criterion)

Criar um backup do banco de dados *CLVhealth-JCAFB-2020_NG* (2020-04-30c)
-------------------------------------------------------------------------

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
            pg_dump clvhealth_jcafb_2020_ng -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_ng_2020-04-30c.sql

            gzip clvhealth_jcafb_2020_ng_2020-04-30c.sql
            pg_dump clvhealth_jcafb_2020_ng -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_ng_2020-04-30c.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-04-30c.tar.gz clvhealth_jcafb_2020_ng

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-04-30c.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_ng_2020-04-30c.sql
        * /opt/odoo/clvhealth_jcafb_2020_ng_2020-04-30c.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-04-30c.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-04-30c.tar.gz

:red:`(Não Executado])` Restaurar um backup do banco de dados *CLVhealth-JCAFB-2020-NG* (2020-04-30c)
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
            # gzip -d clvhealth_jcafb_2020_ng_2020-04-30c.sql.gz

            dropdb -i clvhealth_jcafb_2020_ng

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020_ng
            psql -f clvhealth_jcafb_2020_ng_2020-04-30c.sql -d clvhealth_jcafb_2020_ng -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020_ng
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-04-30c.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-04-30c.tar.gz

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

.. _Lista de Schedules 20200501(2):

Lista de *Schedules* instalados (2) (2020-05-01)
------------------------------------------------

    * Lista de *Schedules* instalados:

        * (Enabled) res.country (res.country)
        * (Enabled) res.country.state (res.country.state)
        * (Enabled) res.city (res.city)

        * (Enabled) res.users (res.users)

        * (Enabled) clv.global_tag (clv.global_tag)

        * (Enabled) clv.phase (clv.phase)

        * (Enabled) hr.department (hr.department)
        * (Enabled) hr.job (hr.job)
        * (Enabled) hr.employee (hr.employee)
        * (Enabled) hr.employee.history (hr.employee.history)

        * (Enabled) clv.address.category (clv.address.category)
        * (Enabled) clv.address (clv.address)
        * (Enabled) clv.address.history (clv.address.history)

        * (Enabled) clv.address.aux (clv.address.aux)

        * (Enabled) clv.family.category (clv.family.category)
        * (Enabled) clv.family (clv.family)
        * (Enabled) clv.family.history (clv.family.history)

        * (Enabled) clv.person.category (clv.person.category)
        * (Enabled) clv.person.marker (clv.person.marker)
        * (Enabled) clv.person (clv.person)
        * (Enabled) clv.person.history (clv.person.history)

        * (Enabled) clv.person.aux (clv.person.aux)

        * (Enabled) survey.stage (survey.stage)
        * (Enabled) survey.survey (survey.survey)
        * (Enabled) survey.page (survey.page)
        * (Enabled) survey.question (survey.question)
        * (Enabled) survey.label (survey.label)
        * (Enabled) survey.user_input (survey.user_input)
        * :green:`(Enabled)` survey.user_input_line (survey.user_input_line)

        * (Enabled) clv.event (clv.event)
        * (Enabled) clv.event.attendee (clv.event.attendee)

        * (Enabled) clv.document.category (clv.document.category)
        * (Enabled) clv.document.type (clv.document.type)
        * (Enabled) clv.document (clv.document)
        * :red:`(Disabled)` clv.document.item (clv.document.item)

        * (Enabled) clv.lab_test.unit (clv.lab_test.unit)
        * (Enabled) clv.lab_test.parasite (clv.lab_test.parasite)
        * (Enabled) clv.lab_test.crystal (clv.lab_test.crystal)
        * (Enabled) clv.lab_test.type (clv.lab_test.type)
        * (Enabled) clv.lab_test.request (clv.lab_test.request)
        * (Enabled) clv.lab_test.result (clv.lab_test.result)
        * (Enabled) clv.lab_test.report (clv.lab_test.report)
        * :red:`(Disabled)` clv.lab_test.criterion (clv.lab_test.criterion)

        * (Enabled) clv.verification.marker (clv.verification.marker)

        * (Enabled) clv.set (clv.set)
        * (Enabled) clv.set.element (clv.set.element)

        * (Enabled) ir.model (ir.model)
        * (Enabled) ir.model.fields (ir.model.fields)

        * (Enabled) clv.model_export.template (clv.model_export.template)
        * (Enabled) clv.model_export.template.field (clv.model_export.template.field)
        * (Enabled) clv.model_export.template.document_item (clv.model_export.template.document_item)
        * (Enabled) clv.model_export.template.lab_test_criterion (clv.model_export.template.lab_test_criterion)
        * (Enabled) clv.model_export (clv.model_export)
        * (Enabled) clv.model_export.field (clv.model_export.field)
        * (Enabled) clv.model_export.document_item (clv.model_export.document_item)
        * (Enabled) clv.model_export.lab_test_criterion (clv.model_export.lab_test_criterion)

Executar o *External Sync Batch* "*Default Batch*" [survey.user_input_line] (2020-05-01)
----------------------------------------------------------------------------------------

    #. [tkl-odoo12-jcafb-ng-vm] Configurar o :bi:`External Sync Schedule` "**survey.user_input_line (survey.user_input_line)**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-ng-vm <https://tkl-odoo12-jcafb-ng-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit`, o :bi:`External Sync Schedule` "**survey.user_input_line (survey.user_input_line)**":

            * Lista de *Schedules*:

                * :ref:`Lista de Schedules  20200501(2)`

            * Menu de acesso:

                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Schedules` » **Ação** » :bi:`External Sync Schedule Mass Edit`

            * Parâmetros alterados:

                * *External Host*: "**https://192.168.25.183**"
                * *Max Task Registers*: "**200.000**"
                * *Disable Identification*: "**desmarcado**"

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

                * :ref:`Lista de Schedules 20200501(2)`

            * *Synchronization Log*:

                * :ref:`External Sync Batch - Default Batch - 20200501(3)`

    #. [tkl-odoo12-jcafb-ng-vm] Configurar o :bi:`External Sync Schedule` "**survey.user_input_line (survey.user_input_line)**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-ng-vm <https://tkl-odoo12-jcafb-ng-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit`, o :bi:`External Sync Schedule` "**survey.user_input_line (survey.user_input_line)**":

            * Lista de *Schedules*:

                * :ref:`Lista de Schedules  20200501(2)`

            * Menu de acesso:

                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Schedules` » **Ação** » :bi:`External Sync Schedule Mass Edit`

            * Parâmetros alterados:

                * *Disable Identification*: "**marcado**"

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-ng-vm** ao modo padrão:

        ::

            # ***** tkl-odoo12-jcafb-ng-vm
            #                * *Disable Identification*: "**marcado**"


            ^C

            exit

            /etc/init.d/odoo start

Lista de *Schedules* executados (3) (2020-05-01)
------------------------------------------------

    * Lista de *Schedules* instalados:

        * :green:`[Execution time: 0:00:05.057]` res.country (res.country)
        * :green:`[Execution time: 0:00:02.706]` res.country.state (res.country.state)
        * :green:`[Execution time: 0:00:02.347]` res.city (res.city)

        * :green:`[Execution time: 0:00:02.307]` res.users (res.users)

        * :green:`[Execution time: 0:00:00.189]` clv.global_tag (clv.global_tag)

        * :green:`[Execution time: 0:00:00.185]` clv.phase (clv.phase)

        * :green:`[Execution time: 0:00:00.178]` hr.department (hr.department)
        * :green:`[Execution time: 0:00:00.195]` hr.job (hr.job)
        * :green:`[Execution time: 0:00:00.271]` hr.employee (hr.employee)
        * :green:`[Execution time: 0:00:00.183]` hr.employee.history (hr.employee.history)

        * :green:`[Execution time: 0:00:00.201]` clv.address.category (clv.address.category)
        * :green:`[Execution time: 0:00:00.220]` clv.address (clv.address)
        * :green:`[Execution time: 0:00:00.177]` clv.address.history (clv.address.history)

        * :green:`[Execution time: 0:00:00.178]` clv.address.aux (clv.address.aux)

        * :green:`[Execution time: 0:00:00.191]` clv.family.category (clv.family.category)
        * :green:`[Execution time: 0:00:00.226]` clv.family (clv.family)
        * :green:`[Execution time: 0:00:00.208]` clv.family.history (clv.family.history)

        * :green:`[Execution time: 0:00:00.187]` clv.person.category (clv.person.category)
        * :green:`[Execution time: 0:00:00.187]` clv.person.marker (clv.person.marker)
        * :green:`[Execution time: 0:00:00.217]` clv.person (clv.person)
        * :green:`[Execution time: 0:00:00.184]` clv.person.history (clv.person.history)

        * :green:`[Execution time: 0:00:00.188]` clv.person.aux (clv.person.aux)

        * :green:`[Execution time: 0:00:00.182]` survey.stage (survey.stage)
        * :green:`[Execution time: 0:00:00.177]` survey.survey (survey.survey)
        * :green:`[Execution time: 0:00:00.178]` survey.page (survey.page)
        * :green:`[Execution time: 0:00:00.183]` survey.question (survey.question)
        * :green:`[Execution time: 0:00:00.181]` survey.label (survey.label)
        * :green:`[Execution time: 0:00:32.100]` survey.user_input (survey.user_input)
        * :green:`[Execution time: 0:55:15.857 + 5:44:02.387]` survey.user_input_line (survey.user_input_line)

        * :green:`[Execution time: 0:00:00.258]` clv.event (clv.event)
        * :green:`[Execution time: 0:00:00.230]` clv.event.attendee (clv.event.attendee)

        * :green:`[Execution time: 0:00:00.226]` clv.document.category (clv.document.category)
        * :green:`[Execution time: 0:00:00.210]` clv.document.type (clv.document.type)
        * :green:`[Execution time: 0:00:00.231]` clv.document (clv.document)
        * :red:`[Execution time: 4:36:23.207]` clv.document.item (clv.document.item)

        * :green:`[Execution time: 0:00:00.209]` clv.lab_test.unit (clv.lab_test.unit)
        * :green:`[Execution time: 0:00:00.204]` clv.lab_test.parasite (clv.lab_test.parasite)
        * :green:`[Execution time: 0:00:00.206]` clv.lab_test.crystal (clv.lab_test.crystal)
        * :green:`[Execution time: 0:00:00.199]` clv.lab_test.type (clv.lab_test.type)
        * :green:`[Execution time: 0:00:00.237]` clv.lab_test.request (clv.lab_test.request)
        * :green:`[Execution time: 0:00:00.222]` clv.lab_test.result (clv.lab_test.result)
        * :green:`[Execution time: 0:00:00.232]` clv.lab_test.report (clv.lab_test.report)
        * :red:`[Execution time: 3:00:10.402]` clv.lab_test.criterion (clv.lab_test.criterion)

        * :green:`[Execution time: 0:00:00.201]` clv.verification.marker (clv.verification.marker)

        * :green:`[Execution time: 0:00:00.201]` clv.set (clv.set)
        * :green:`[Execution time: 0:00:00.202]` clv.set.element (clv.set.element)

        * :green:`[Execution time: 0:00:00.760]` ir.model (ir.model)
        * :green:`[Execution time: 0:00:11.159]` ir.model.fields (ir.model.fields)

        * :green:`[Execution time: 0:00:00.232]` clv.model_export.template (clv.model_export.template)
        * :green:`[Execution time: 0:00:00.199]` clv.model_export.template.field (clv.model_export.template.field)
        * :green:`[Execution time: 0:00:18.059]` clv.model_export.template.document_item (clv.model_export.template.document_item)
        * :green:`[Execution time: 0:00:16.712]` clv.model_export.template.lab_test_criterion (clv.model_export.template.lab_test_criterion)
        * :green:`[Execution time: 0:00:00.204]` clv.model_export (clv.model_export)
        * :green:`[Execution time: 0:00:00.201]` clv.model_export.field (clv.model_export.field)
        * :green:`[Execution time: 0:00:18.330]` clv.model_export.document_item (clv.model_export.document_item)
        * :green:`[Execution time: 0:00:15.902]` clv.model_export.lab_test_criterion (clv.model_export.lab_test_criterion)

Criar um backup do banco de dados *CLVhealth-JCAFB-2020_NG* (2020-05-01a)
-------------------------------------------------------------------------

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
            pg_dump clvhealth_jcafb_2020_ng -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_ng_2020-05-01a.sql

            gzip clvhealth_jcafb_2020_ng_2020-05-01a.sql
            pg_dump clvhealth_jcafb_2020_ng -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_ng_2020-05-01a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-05-01a.tar.gz clvhealth_jcafb_2020_ng

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-05-01a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_ng_2020-05-01a.sql
        * /opt/odoo/clvhealth_jcafb_2020_ng_2020-05-01a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-05-01a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-05-01a.tar.gz

Restaurar um backup do banco de dados *CLVhealth-JCAFB-2020-NG* (2020-05-01a)
-----------------------------------------------------------------------------

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
            # gzip -d clvhealth_jcafb_2020_ng_2020-05-01a.sql.gz

            dropdb -i clvhealth_jcafb_2020_ng

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020_ng
            psql -f clvhealth_jcafb_2020_ng_2020-05-01a.sql -d clvhealth_jcafb_2020_ng -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020_ng
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-05-01a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-05-01a.tar.gz

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

.. _Lista de Schedules 20200502(3):

Lista de *Schedules* instalados (3) (2020-05-02)
------------------------------------------------

    * Lista de *Schedules* instalados:

        * (Enabled) res.country (res.country)
        * (Enabled) res.country.state (res.country.state)
        * (Enabled) res.city (res.city)

        * (Enabled) res.users (res.users)

        * (Enabled) clv.global_tag (clv.global_tag)

        * (Enabled) clv.phase (clv.phase)

        * (Enabled) hr.department (hr.department)
        * (Enabled) hr.job (hr.job)
        * (Enabled) hr.employee (hr.employee)
        * (Enabled) hr.employee.history (hr.employee.history)

        * (Enabled) clv.address.category (clv.address.category)
        * (Enabled) clv.address (clv.address)
        * (Enabled) clv.address.history (clv.address.history)

        * (Enabled) clv.address.aux (clv.address.aux)

        * (Enabled) clv.family.category (clv.family.category)
        * (Enabled) clv.family (clv.family)
        * (Enabled) clv.family.history (clv.family.history)

        * (Enabled) clv.person.category (clv.person.category)
        * (Enabled) clv.person.marker (clv.person.marker)
        * (Enabled) clv.person (clv.person)
        * (Enabled) clv.person.history (clv.person.history)

        * (Enabled) clv.person.aux (clv.person.aux)

        * (Enabled) survey.stage (survey.stage)
        * (Enabled) survey.survey (survey.survey)
        * (Enabled) survey.page (survey.page)
        * (Enabled) survey.question (survey.question)
        * (Enabled) survey.label (survey.label)
        * (Enabled) survey.user_input (survey.user_input)
        * (Enabled) survey.user_input_line (survey.user_input_line)

        * (Enabled) clv.event (clv.event)
        * (Enabled) clv.event.attendee (clv.event.attendee)

        * (Enabled) clv.document.category (clv.document.category)
        * (Enabled) clv.document.type (clv.document.type)
        * (Enabled) clv.document (clv.document)
        * :green:`(Enabled)` clv.document.item (clv.document.item)

        * (Enabled) clv.lab_test.unit (clv.lab_test.unit)
        * (Enabled) clv.lab_test.parasite (clv.lab_test.parasite)
        * (Enabled) clv.lab_test.crystal (clv.lab_test.crystal)
        * (Enabled) clv.lab_test.type (clv.lab_test.type)
        * (Enabled) clv.lab_test.request (clv.lab_test.request)
        * (Enabled) clv.lab_test.result (clv.lab_test.result)
        * (Enabled) clv.lab_test.report (clv.lab_test.report)
        * :red:`(Disabled)` clv.lab_test.criterion (clv.lab_test.criterion)

        * (Enabled) clv.verification.marker (clv.verification.marker)

        * (Enabled) clv.set (clv.set)
        * (Enabled) clv.set.element (clv.set.element)

        * (Enabled) ir.model (ir.model)
        * (Enabled) ir.model.fields (ir.model.fields)

        * (Enabled) clv.model_export.template (clv.model_export.template)
        * (Enabled) clv.model_export.template.field (clv.model_export.template.field)
        * (Enabled) clv.model_export.template.document_item (clv.model_export.template.document_item)
        * (Enabled) clv.model_export.template.lab_test_criterion (clv.model_export.template.lab_test_criterion)
        * (Enabled) clv.model_export (clv.model_export)
        * (Enabled) clv.model_export.field (clv.model_export.field)
        * (Enabled) clv.model_export.document_item (clv.model_export.document_item)
        * (Enabled) clv.model_export.lab_test_criterion (clv.model_export.lab_test_criterion)

Executar o *External Sync Batch* "*Default Batch*" [clv.document.item] (2020-05-02)
-----------------------------------------------------------------------------------

    #. [tkl-odoo12-jcafb-ng-vm] Configurar o :bi:`External Sync Schedule` "**clv.document.item (clv.document.item)**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-ng-vm <https://tkl-odoo12-jcafb-ng-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit`, o :bi:`External Sync Schedule` "**clv.document.item (clv.document.item)**":

            * Lista de *Schedules*:

                * :ref:`Lista de Schedules  20200502(3)`

            * Menu de acesso:

                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Schedules` » **Ação** » :bi:`External Sync Schedule Mass Edit`

            * Parâmetros alterados:

                * *External Host*: "**https://192.168.25.183**"
                * *Max Task Registers*: "**250.000**"
                * *Disable Identification*: "**desmarcado**"

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

                * :ref:`Lista de Schedules 20200502(3)`

            * *Synchronization Log*:

                * :ref:`External Sync Batch - Default Batch - 20200502(4)`

    #. [tkl-odoo12-jcafb-ng-vm] Configurar o :bi:`External Sync Schedule` "**clv.document.item (clv.document.item)**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-ng-vm <https://tkl-odoo12-jcafb-ng-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit`, o :bi:`External Sync Schedule` "**clv.document.item (clv.document.item)**":

            * Lista de *Schedules*:

                * :ref:`Lista de Schedules  20200502(3)`

            * Menu de acesso:

                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Schedules` » **Ação** » :bi:`External Sync Schedule Mass Edit`

            * Parâmetros alterados:

                * *Disable Identification*: "**marcado**"

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-ng-vm** ao modo padrão:

        ::

            # ***** tkl-odoo12-jcafb-ng-vm
            #                * *Disable Identification*: "**marcado**"


            ^C

            exit

            /etc/init.d/odoo start

Lista de *Schedules* executados (4) (2020-05-02)
------------------------------------------------

    * Lista de *Schedules* instalados:

        * :green:`[Execution time: 0:00:00.296]` res.country (res.country)
        * :green:`[Execution time: 0:00:00.769]` res.country.state (res.country.state)
        * :green:`[Execution time: 0:00:00.253]` res.city (res.city)

        * :green:`[Execution time: 0:00:00.239]` res.users (res.users)

        * :green:`[Execution time: 0:00:00.209]` clv.global_tag (clv.global_tag)

        * :green:`[Execution time: 0:00:00.213]` clv.phase (clv.phase)

        * :green:`[Execution time: 0:00:00.202]` hr.department (hr.department)
        * :green:`[Execution time: 0:00:00.202]` hr.job (hr.job)
        * :green:`[Execution time: 0:00:00.244]` hr.employee (hr.employee)
        * :green:`[Execution time: 0:00:00.202]` hr.employee.history (hr.employee.history)

        * :green:`[Execution time: 0:00:00.293]` clv.address.category (clv.address.category)
        * :green:`[Execution time: 0:00:00.234]` clv.address (clv.address)
        * :green:`[Execution time: 0:00:00.211]` clv.address.history (clv.address.history)

        * :green:`[Execution time: 0:00:00.239]` clv.address.aux (clv.address.aux)

        * :green:`[Execution time: 0:00:00.231]` clv.family.category (clv.family.category)
        * :green:`[Execution time: 0:00:00.258]` clv.family (clv.family)
        * :green:`[Execution time: 0:00:00.261]` clv.family.history (clv.family.history)

        * :green:`[Execution time: 0:00:00.213]` clv.person.category (clv.person.category)
        * :green:`[Execution time: 0:00:00.206]` clv.person.marker (clv.person.marker)
        * :green:`[Execution time: 0:00:00.224]` clv.person (clv.person)
        * :green:`[Execution time: 0:00:00.204]` clv.person.history (clv.person.history)

        * :green:`[Execution time: 0:00:00.244]` clv.person.aux (clv.person.aux)

        * :green:`[Execution time: 0:00:00.206]` survey.stage (survey.stage)
        * :green:`[Execution time: 0:00:00.213]` survey.survey (survey.survey)
        * :green:`[Execution time: 0:00:00.208]` survey.page (survey.page)
        * :green:`[Execution time: 0:00:00.207]` survey.question (survey.question)
        * :green:`[Execution time: 0:00:00.204]` survey.label (survey.label)
        * :green:`[Execution time: 0:01:14.866]` survey.user_input (survey.user_input)
        * :green:`[Execution time: 0:00:00.211]` survey.user_input_line (survey.user_input_line)

        * :green:`[Execution time: 0:00:00.237]` clv.event (clv.event)
        * :green:`[Execution time: 0:00:00.209]` clv.event.attendee (clv.event.attendee)

        * :green:`[Execution time: 0:00:00.202]` clv.document.category (clv.document.category)
        * :green:`[Execution time: 0:00:00.211]` clv.document.type (clv.document.type)
        * :green:`[Execution time: 0:00:00.235]` clv.document (clv.document)
        * :green:`[Execution time: 2:40:32.729 + 5:15:44.365]` clv.document.item (clv.document.item)

        * :green:`[Execution time: 0:00:00.281]` clv.lab_test.unit (clv.lab_test.unit)
        * :green:`[Execution time: 0:00:00.287]` clv.lab_test.parasite (clv.lab_test.parasite)
        * :green:`[Execution time: 0:00:00.239]` clv.lab_test.crystal (clv.lab_test.crystal)
        * :green:`[Execution time: 0:00:00.237]` clv.lab_test.type (clv.lab_test.type)
        * :green:`[Execution time: 0:00:00.305]` clv.lab_test.request (clv.lab_test.request)
        * :green:`[Execution time: 0:00:00.285]` clv.lab_test.result (clv.lab_test.result)
        * :green:`[Execution time: 0:00:00.259]` clv.lab_test.report (clv.lab_test.report)
        * :red:`[Execution time: 3:00:10.402]` clv.lab_test.criterion (clv.lab_test.criterion)

        * :green:`[Execution time: 0:00:00.252]` clv.verification.marker (clv.verification.marker)

        * :green:`[Execution time: 0:00:00.751]` clv.set (clv.set)
        * :green:`[Execution time: 0:00:00.272]` clv.set.element (clv.set.element)

        * :green:`[Execution time: 0:00:00.760]` ir.model (ir.model)
        * :green:`[Execution time: 0:00:11.694]` ir.model.fields (ir.model.fields)

        * :green:`[Execution time: 0:00:00.248]` clv.model_export.template (clv.model_export.template)
        * :green:`[Execution time: 0:00:00.274]` clv.model_export.template.field (clv.model_export.template.field)
        * :green:`[Execution time: 0:00:30.935]` clv.model_export.template.document_item (clv.model_export.template.document_item)
        * :green:`[Execution time: 0:00:27.204]` clv.model_export.template.lab_test_criterion (clv.model_export.template.lab_test_criterion)
        * :green:`[Execution time: 0:00:00.250]` clv.model_export (clv.model_export)
        * :green:`[Execution time: 0:00:00.224]` clv.model_export.field (clv.model_export.field)
        * :green:`[Execution time: 0:00:30.338]` clv.model_export.document_item (clv.model_export.document_item)
        * :green:`[Execution time: 0:00:27.211]` clv.model_export.lab_test_criterion (clv.model_export.lab_test_criterion)

Criar um backup do banco de dados *CLVhealth-JCAFB-2020_NG* (2020-05-02a)
-------------------------------------------------------------------------

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
            pg_dump clvhealth_jcafb_2020_ng -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_ng_2020-05-02a.sql

            gzip clvhealth_jcafb_2020_ng_2020-05-02a.sql
            pg_dump clvhealth_jcafb_2020_ng -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_ng_2020-05-02a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-05-02a.tar.gz clvhealth_jcafb_2020_ng

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-05-02a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_ng_2020-05-02a.sql
        * /opt/odoo/clvhealth_jcafb_2020_ng_2020-05-02a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-05-02a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-05-02a.tar.gz

:red:`(Não Executado])` Restaurar um backup do banco de dados *CLVhealth-JCAFB-2020-NG* (2020-05-02a)
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
            # gzip -d clvhealth_jcafb_2020_ng_2020-05-02a.sql.gz

            dropdb -i clvhealth_jcafb_2020_ng

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020_ng
            psql -f clvhealth_jcafb_2020_ng_2020-05-02a.sql -d clvhealth_jcafb_2020_ng -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020_ng
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-05-02a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-05-02a.tar.gz

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

.. _Lista de Schedules 20200503(4):

Lista de *Schedules* instalados (4) (2020-05-03)
------------------------------------------------

    * Lista de *Schedules* instalados:

        * (Enabled) res.country (res.country)
        * (Enabled) res.country.state (res.country.state)
        * (Enabled) res.city (res.city)

        * (Enabled) res.users (res.users)

        * (Enabled) clv.global_tag (clv.global_tag)

        * (Enabled) clv.phase (clv.phase)

        * (Enabled) hr.department (hr.department)
        * (Enabled) hr.job (hr.job)
        * (Enabled) hr.employee (hr.employee)
        * (Enabled) hr.employee.history (hr.employee.history)

        * (Enabled) clv.address.category (clv.address.category)
        * (Enabled) clv.address (clv.address)
        * (Enabled) clv.address.history (clv.address.history)

        * (Enabled) clv.address.aux (clv.address.aux)

        * (Enabled) clv.family.category (clv.family.category)
        * (Enabled) clv.family (clv.family)
        * (Enabled) clv.family.history (clv.family.history)

        * (Enabled) clv.person.category (clv.person.category)
        * (Enabled) clv.person.marker (clv.person.marker)
        * (Enabled) clv.person (clv.person)
        * (Enabled) clv.person.history (clv.person.history)

        * (Enabled) clv.person.aux (clv.person.aux)

        * (Enabled) survey.stage (survey.stage)
        * (Enabled) survey.survey (survey.survey)
        * (Enabled) survey.page (survey.page)
        * (Enabled) survey.question (survey.question)
        * (Enabled) survey.label (survey.label)
        * (Enabled) survey.user_input (survey.user_input)
        * (Enabled) survey.user_input_line (survey.user_input_line)

        * (Enabled) clv.event (clv.event)
        * (Enabled) clv.event.attendee (clv.event.attendee)

        * (Enabled) clv.document.category (clv.document.category)
        * (Enabled) clv.document.type (clv.document.type)
        * (Enabled) clv.document (clv.document)
        * (Enabled) clv.document.item (clv.document.item)

        * (Enabled) clv.lab_test.unit (clv.lab_test.unit)
        * (Enabled) clv.lab_test.parasite (clv.lab_test.parasite)
        * (Enabled) clv.lab_test.crystal (clv.lab_test.crystal)
        * (Enabled) clv.lab_test.type (clv.lab_test.type)
        * (Enabled) clv.lab_test.request (clv.lab_test.request)
        * (Enabled) clv.lab_test.result (clv.lab_test.result)
        * (Enabled) clv.lab_test.report (clv.lab_test.report)
        * :green:`(Enabled)` clv.lab_test.criterion (clv.lab_test.criterion)

        * (Enabled) clv.verification.marker (clv.verification.marker)

        * (Enabled) clv.set (clv.set)
        * (Enabled) clv.set.element (clv.set.element)

        * (Enabled) ir.model (ir.model)
        * (Enabled) ir.model.fields (ir.model.fields)

        * (Enabled) clv.model_export.template (clv.model_export.template)
        * (Enabled) clv.model_export.template.field (clv.model_export.template.field)
        * (Enabled) clv.model_export.template.document_item (clv.model_export.template.document_item)
        * (Enabled) clv.model_export.template.lab_test_criterion (clv.model_export.template.lab_test_criterion)
        * (Enabled) clv.model_export (clv.model_export)
        * (Enabled) clv.model_export.field (clv.model_export.field)
        * (Enabled) clv.model_export.document_item (clv.model_export.document_item)
        * (Enabled) clv.model_export.lab_test_criterion (clv.model_export.lab_test_criterion)

Executar o *External Sync Batch* "*Default Batch*" [clv.lab_test.criterion] (2020-05-03)
----------------------------------------------------------------------------------------

    #. [tkl-odoo12-jcafb-ng-vm] Configurar o :bi:`External Sync Schedule` "**clv.document.item (clv.document.item)**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-ng-vm <https://tkl-odoo12-jcafb-ng-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit`, o :bi:`External Sync Schedule` "**clv.lab_test.criterion (clv.lab_test.criterion)**":

            * Lista de *Schedules*:

                * :ref:`Lista de Schedules  20200503(4)`

            * Menu de acesso:

                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Schedules` » **Ação** » :bi:`External Sync Schedule Mass Edit`

            * Parâmetros alterados:

                * *External Host*: "**https://192.168.25.183**"
                * *Max Task Registers*: "**250.000**"
                * *Disable Identification*: "**desmarcado**"

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

                * :ref:`Lista de Schedules 20200503(4)`

            * *Synchronization Log*:

                * :ref:`External Sync Batch - Default Batch - 20200503(5)`

    #. [tkl-odoo12-jcafb-ng-vm] Configurar o :bi:`External Sync Schedule` "**clv.document.item (clv.document.item)**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-ng-vm <https://tkl-odoo12-jcafb-ng-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit`, o :bi:`External Sync Schedule` "**clv.lab_test.criterion (clv.lab_test.criterion)**":

            * Lista de *Schedules*:

                * :ref:`Lista de Schedules  20200503(4)`

            * Menu de acesso:

                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Schedules` » **Ação** » :bi:`External Sync Schedule Mass Edit`

            * Parâmetros alterados:

                * *Disable Identification*: "**marcado**"

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-ng-vm** ao modo padrão:

        ::

            # ***** tkl-odoo12-jcafb-ng-vm
            #                * *Disable Identification*: "**marcado**"


            ^C

            exit

            /etc/init.d/odoo start

Lista de *Schedules* executados (5) (2020-05-03)
------------------------------------------------

    * Lista de *Schedules* instalados:

        * :green:`[Execution time: 0:00:04.926]` res.country (res.country)
        * :green:`[Execution time: 0:00:07.513]` res.country.state (res.country.state)
        * :green:`[Execution time: 0:00:00.244]` res.city (res.city)

        * :green:`[Execution time: 0:00:00.264]` res.users (res.users)

        * :green:`[Execution time: 0:00:00.244]` clv.global_tag (clv.global_tag)

        * :green:`[Execution time: 0:00:00.246]` clv.phase (clv.phase)

        * :green:`[Execution time: 0:00:00.242]` hr.department (hr.department)
        * :green:`[Execution time: 0:00:00.264]` hr.job (hr.job)
        * :green:`[Execution time: 0:00:00.326]` hr.employee (hr.employee)
        * :green:`[Execution time: 0:00:00.250]` hr.employee.history (hr.employee.history)

        * :green:`[Execution time: 0:00:00.300]` clv.address.category (clv.address.category)
        * :green:`[Execution time: 0:00:00.254]` clv.address (clv.address)
        * :green:`[Execution time: 0:00:00.263]` clv.address.history (clv.address.history)

        * :green:`[Execution time: 0:00:00.226]` clv.address.aux (clv.address.aux)

        * :green:`[Execution time: 0:00:00.243]` clv.family.category (clv.family.category)
        * :green:`[Execution time: 0:00:00.275]` clv.family (clv.family)
        * :green:`[Execution time: 0:00:00.247]` clv.family.history (clv.family.history)

        * :green:`[Execution time: 0:00:00.267]` clv.person.category (clv.person.category)
        * :green:`[Execution time: 0:00:00.276]` clv.person.marker (clv.person.marker)
        * :green:`[Execution time: 0:00:00.307]` clv.person (clv.person)
        * :green:`[Execution time: 0:00:00.272]` clv.person.history (clv.person.history)

        * :green:`[Execution time: 0:00:00.234]` clv.person.aux (clv.person.aux)

        * :green:`[Execution time: 0:00:00.267]` survey.stage (survey.stage)
        * :green:`[Execution time: 0:00:00.232]` survey.survey (survey.survey)
        * :green:`[Execution time: 0:00:00.231]` survey.page (survey.page)
        * :green:`[Execution time: 0:00:00.243]` survey.question (survey.question)
        * :green:`[Execution time: 0:00:00.253]` survey.label (survey.label)
        * :green:`[Execution time: 0:01:47.232]` survey.user_input (survey.user_input)
        * :green:`[Execution time: 0:00:00.220]` survey.user_input_line (survey.user_input_line)

        * :green:`[Execution time: 0:00:00.248]` clv.event (clv.event)
        * :green:`[Execution time: 0:00:00.224]` clv.event.attendee (clv.event.attendee)

        * :green:`[Execution time: 0:00:00.216]` clv.document.category (clv.document.category)
        * :green:`[Execution time: 0:00:00.217]` clv.document.type (clv.document.type)
        * :green:`[Execution time: 0:00:00.242]` clv.document (clv.document)
        * :green:`[Execution time: 0:00:00.221]` clv.document.item (clv.document.item)

        * :green:`[Execution time: 0:00:00.222]` clv.lab_test.unit (clv.lab_test.unit)
        * :green:`[Execution time: 0:00:00.227]` clv.lab_test.parasite (clv.lab_test.parasite)
        * :green:`[Execution time: 0:00:00.217]` clv.lab_test.crystal (clv.lab_test.crystal)
        * :green:`[Execution time: 0:00:00.220]` clv.lab_test.type (clv.lab_test.type)
        * :green:`[Execution time: 0:00:00.250]` clv.lab_test.request (clv.lab_test.request)
        * :green:`[Execution time: 0:00:00.245]` clv.lab_test.result (clv.lab_test.result)
        * :green:`[Execution time: 0:00:00.243]` clv.lab_test.report (clv.lab_test.report)
        * :green:`[Execution time: 1:41:20.477 + 3:17:09.865]` clv.lab_test.criterion (clv.lab_test.criterion)

        * :green:`[Execution time: 0:00:00.271]` clv.verification.marker (clv.verification.marker)

        * :green:`[Execution time: 0:00:00.266]` clv.set (clv.set)
        * :green:`[Execution time: 0:00:00.276]` clv.set.element (clv.set.element)

        * :green:`[Execution time: 0:00:00.686]` ir.model (ir.model)
        * :green:`[Execution time: 0:00:10.925]` ir.model.fields (ir.model.fields)

        * :green:`[Execution time: 0:00:00.273]` clv.model_export.template (clv.model_export.template)
        * :green:`[Execution time: 0:00:00.247]` clv.model_export.template.field (clv.model_export.template.field)
        * :green:`[Execution time: 0:00:00.242]` clv.model_export.template.document_item (clv.model_export.template.document_item)
        * :green:`[Execution time: 0:00:26.675]` clv.model_export.template.lab_test_criterion (clv.model_export.template.lab_test_criterion)
        * :green:`[Execution time: 0:00:00.241]` clv.model_export (clv.model_export)
        * :green:`[Execution time: 0:00:00.238]` clv.model_export.field (clv.model_export.field)
        * :green:`[Execution time: 0:00:00.238]` clv.model_export.document_item (clv.model_export.document_item)
        * :green:`[Execution time: 0:00:26.904]` clv.model_export.lab_test_criterion (clv.model_export.lab_test_criterion)

Criar um backup do banco de dados *CLVhealth-JCAFB-2020_NG* (2020-05-03a)
-------------------------------------------------------------------------

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
            pg_dump clvhealth_jcafb_2020_ng -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_ng_2020-05-03a.sql

            gzip clvhealth_jcafb_2020_ng_2020-05-03a.sql
            pg_dump clvhealth_jcafb_2020_ng -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_ng_2020-05-03a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-05-03a.tar.gz clvhealth_jcafb_2020_ng

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-05-03a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_ng_2020-05-03a.sql
        * /opt/odoo/clvhealth_jcafb_2020_ng_2020-05-03a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-05-03a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-05-03a.tar.gz

Restaurar um backup do banco de dados *CLVhealth-JCAFB-2020-NG* (2020-05-03a)
-----------------------------------------------------------------------------

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
            # gzip -d clvhealth_jcafb_2020_ng_2020-05-03a.sql.gz

            dropdb -i clvhealth_jcafb_2020_ng

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020_ng
            psql -f clvhealth_jcafb_2020_ng_2020-05-03a.sql -d clvhealth_jcafb_2020_ng -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020_ng
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-05-03a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-05-03a.tar.gz

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

Atualizar o(s) módulo(s) [clv_export] (2020-05-06)
--------------------------------------------------

    * Referência: :doc:`/setup/module_update`.


    #. [tkl-odoo12-jcafb-ng-vm] Lista de Módulos:

        * clv_export

    #. [tkl-odoo12-jcafb-ng-vm] **Executar** a atualização do(s) Módulo(s):

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" - m clv_export
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-ng-vm** ao modo desejado:

            ::

                # ***** tkl-odoo12-jcafb-ng-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Criar um backup do banco de dados *CLVhealth-JCAFB-2020_NG* (2020-05-06a)
-------------------------------------------------------------------------

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
            pg_dump clvhealth_jcafb_2020_ng -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_ng_2020-05-06a.sql

            gzip clvhealth_jcafb_2020_ng_2020-05-06a.sql
            pg_dump clvhealth_jcafb_2020_ng -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_ng_2020-05-06a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-05-06a.tar.gz clvhealth_jcafb_2020_ng

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-05-06a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_ng_2020-05-06a.sql
        * /opt/odoo/clvhealth_jcafb_2020_ng_2020-05-06a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-05-06a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-05-06a.tar.gz

Restaurar um backup do banco de dados *CLVhealth-JCAFB-2020-NG* (2020-05-06a)
-----------------------------------------------------------------------------

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
            # gzip -d clvhealth_jcafb_2020_ng_2020-05-06a.sql.gz

            dropdb -i clvhealth_jcafb_2020_ng

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020_ng
            psql -f clvhealth_jcafb_2020_ng_2020-05-06a.sql -d clvhealth_jcafb_2020_ng -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020_ng
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-05-06a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-05-06a.tar.gz

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

Atualizar o(s) módulo(s) [ver lista] (2020-05-08)
-------------------------------------------------

    * Referência: :doc:`/setup/module_update`.


    #. [tkl-odoo12-jcafb-ng-vm] Lista de Módulos:

        * clv_external_sync_jcafb
        * clv_base
        * clv_address
        * clv_address_jcafb
        * clv_address_history
        * clv_address_history_jcafb

    #. [tkl-odoo12-jcafb-ng-vm] **Executar** a atualização do(s) Módulo(s):

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" - m clv_base
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-ng-vm** ao modo desejado:

            ::

                # ***** tkl-odoo12-jcafb-ng-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Criar um backup do banco de dados *CLVhealth-JCAFB-2020_NG* (2020-05-12a)
-------------------------------------------------------------------------

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
            pg_dump clvhealth_jcafb_2020_ng -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_ng_2020-05-12a.sql

            gzip clvhealth_jcafb_2020_ng_2020-05-12a.sql
            pg_dump clvhealth_jcafb_2020_ng -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_ng_2020-05-12a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-05-12a.tar.gz clvhealth_jcafb_2020_ng

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-05-12a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_ng_2020-05-12a.sql
        * /opt/odoo/clvhealth_jcafb_2020_ng_2020-05-12a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-05-12a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-05-12a.tar.gz

Restaurar um backup do banco de dados *CLVhealth-JCAFB-2020-NG* (2020-05-12a)
-----------------------------------------------------------------------------

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
            # gzip -d clvhealth_jcafb_2020_ng_2020-05-12a.sql.gz

            dropdb -i clvhealth_jcafb_2020_ng

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020_ng
            psql -f clvhealth_jcafb_2020_ng_2020-05-12a.sql -d clvhealth_jcafb_2020_ng -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020_ng
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-05-12a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-05-12a.tar.gz

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

Atualizar o(s) módulo(s) [ver lista] (2020-05-16)
-------------------------------------------------

    * Referência: :doc:`/setup/module_update`.


    #. [tkl-odoo12-jcafb-ng-vm] Lista de Módulos:

        * clv_person
        * clv_person_jcafb
        * clv_person_verification_jcafb
        * clv_document
        * clv_lab_test
        * clv_event

    #. [tkl-odoo12-jcafb-ng-vm] **Executar** a atualização do(s) Módulo(s):

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" - m clv_person
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" - m clv_document
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" - m clv_lab_test
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" - m clv_event
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-ng-vm** ao modo desejado:

            ::

                # ***** tkl-odoo12-jcafb-ng-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Criar um backup do banco de dados *CLVhealth-JCAFB-2020_NG* (2020-05-16a)
-------------------------------------------------------------------------

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
            pg_dump clvhealth_jcafb_2020_ng -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_ng_2020-05-16a.sql

            gzip clvhealth_jcafb_2020_ng_2020-05-16a.sql
            pg_dump clvhealth_jcafb_2020_ng -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_ng_2020-05-16a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-05-16a.tar.gz clvhealth_jcafb_2020_ng

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-05-16a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_ng_2020-05-16a.sql
        * /opt/odoo/clvhealth_jcafb_2020_ng_2020-05-16a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-05-16a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-05-16a.tar.gz

Restaurar um backup do banco de dados *CLVhealth-JCAFB-2020-NG* (2020-05-16a)
-----------------------------------------------------------------------------

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
            # gzip -d clvhealth_jcafb_2020_ng_2020-05-16a.sql.gz

            dropdb -i clvhealth_jcafb_2020_ng

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020_ng
            psql -f clvhealth_jcafb_2020_ng_2020-05-16a.sql -d clvhealth_jcafb_2020_ng -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020_ng
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-05-16a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-05-16a.tar.gz

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

Atualizar o(s) módulo(s) [ver lista] (2020-05-16)
-------------------------------------------------

    * Referência: :doc:`/setup/module_update`.


    #. [tkl-odoo12-jcafb-ng-vm] Lista de Módulos:

        * clv_address
        * clv_address_jcafb
        * clv_address_verification_jcafb

    #. [tkl-odoo12-jcafb-ng-vm] **Executar** a atualização do(s) Módulo(s):

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" - m clv_address
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-ng-vm** ao modo desejado:

            ::

                # ***** tkl-odoo12-jcafb-ng-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Criar um backup do banco de dados *CLVhealth-JCAFB-2020_NG* (2020-05-16b)
-------------------------------------------------------------------------

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
            pg_dump clvhealth_jcafb_2020_ng -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_ng_2020-05-16b.sql

            gzip clvhealth_jcafb_2020_ng_2020-05-16b.sql
            pg_dump clvhealth_jcafb_2020_ng -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_ng_2020-05-16b.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-05-16b.tar.gz clvhealth_jcafb_2020_ng

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-05-16b.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_ng_2020-05-16b.sql
        * /opt/odoo/clvhealth_jcafb_2020_ng_2020-05-16b.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-05-16b.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-05-16b.tar.gz

:red:`(Não Executado])` Restaurar um backup do banco de dados *CLVhealth-JCAFB-2020-NG* (2020-05-16b)
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
            # gzip -d clvhealth_jcafb_2020_ng_2020-05-16b.sql.gz

            dropdb -i clvhealth_jcafb_2020_ng

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020_ng
            psql -f clvhealth_jcafb_2020_ng_2020-05-16b.sql -d clvhealth_jcafb_2020_ng -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020_ng
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-05-16b.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-05-16b.tar.gz

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

Atualizar o(s) módulo(s) [ver lista] (2020-05-16)
-------------------------------------------------

    * Referência: :doc:`/setup/module_update`.


    #. [tkl-odoo12-jcafb-ng-vm] Lista de Módulos:

        * clv_family
        * clv_family_jcafb

    #. [tkl-odoo12-jcafb-ng-vm] **Executar** a atualização do(s) Módulo(s):

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" - m clv_family
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-ng-vm** ao modo desejado:

            ::

                # ***** tkl-odoo12-jcafb-ng-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Criar um backup do banco de dados *CLVhealth-JCAFB-2020_NG* (2020-05-16c)
-------------------------------------------------------------------------

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
            pg_dump clvhealth_jcafb_2020_ng -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_ng_2020-05-16c.sql

            gzip clvhealth_jcafb_2020_ng_2020-05-16c.sql
            pg_dump clvhealth_jcafb_2020_ng -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_ng_2020-05-16c.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-05-16c.tar.gz clvhealth_jcafb_2020_ng

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-05-16c.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_ng_2020-05-16c.sql
        * /opt/odoo/clvhealth_jcafb_2020_ng_2020-05-16c.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-05-16c.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-05-16c.tar.gz

:red:`(Não Executado])` Restaurar um backup do banco de dados *CLVhealth-JCAFB-2020-NG* (2020-05-16c)
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
            # gzip -d clvhealth_jcafb_2020_ng_2020-05-16c.sql.gz

            dropdb -i clvhealth_jcafb_2020_ng

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020_ng
            psql -f clvhealth_jcafb_2020_ng_2020-05-16c.sql -d clvhealth_jcafb_2020_ng -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020_ng
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-05-16c.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-05-16c.tar.gz

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

Atualizar o(s) módulo(s) [ver lista] (2020-05-16)
-------------------------------------------------

    * Referência: :doc:`/setup/module_update`.


    #. [tkl-odoo12-jcafb-ng-vm] Lista de Módulos:

        * clv_family_jcafb
        * clv_address_aux
        * clv_address_aux_jcafb

    #. [tkl-odoo12-jcafb-ng-vm] **Executar** a atualização do(s) Módulo(s):

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" - m clv_family
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" - m clv_address_aux
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-ng-vm** ao modo desejado:

            ::

                # ***** tkl-odoo12-jcafb-ng-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Criar um backup do banco de dados *CLVhealth-JCAFB-2020_NG* (2020-05-16d)
-------------------------------------------------------------------------

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
            pg_dump clvhealth_jcafb_2020_ng -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_ng_2020-05-16d.sql

            gzip clvhealth_jcafb_2020_ng_2020-05-16d.sql
            pg_dump clvhealth_jcafb_2020_ng -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_ng_2020-05-16d.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-05-16d.tar.gz clvhealth_jcafb_2020_ng

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-05-16d.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_ng_2020-05-16d.sql
        * /opt/odoo/clvhealth_jcafb_2020_ng_2020-05-16d.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-05-16d.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-05-16d.tar.gz

.. index:: clvhealth_jcafb_2020_ng_2020-05-16d.sql
.. index:: filestore_clvhealth_jcafb_2020_ng_2020-05-16d
.. index:: clvsol_filestore_clvhealth_jcafb_2020_ng_2020-05-16d

:red:`(Não Executado])` Restaurar um backup do banco de dados *CLVhealth-JCAFB-2020-NG* (2020-05-16d)
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
            # gzip -d clvhealth_jcafb_2020_ng_2020-05-16d.sql.gz

            dropdb -i clvhealth_jcafb_2020_ng

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020_ng
            psql -f clvhealth_jcafb_2020_ng_2020-05-16d.sql -d clvhealth_jcafb_2020_ng -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020_ng
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-05-16d.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-05-16d.tar.gz

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

Atualizar o(s) módulo(s) [ver lista] (2020-05-16)
-------------------------------------------------

    * Referência: :doc:`/setup/module_update`.


    #. [tkl-odoo12-jcafb-ng-vm] Lista de Módulos:

        * clv_person_aux
        * clv_person_aux_jcafb

    #. [tkl-odoo12-jcafb-ng-vm] **Executar** a atualização do(s) Módulo(s):

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" - m clv_person_aux
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-ng-vm** ao modo desejado:

            ::

                # ***** tkl-odoo12-jcafb-ng-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Criar um backup do banco de dados *CLVhealth-JCAFB-2020_NG* (2020-05-16e)
-------------------------------------------------------------------------

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
            pg_dump clvhealth_jcafb_2020_ng -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_ng_2020-05-16e.sql

            gzip clvhealth_jcafb_2020_ng_2020-05-16e.sql
            pg_dump clvhealth_jcafb_2020_ng -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_ng_2020-05-16e.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-05-16e.tar.gz clvhealth_jcafb_2020_ng

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-05-16e.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_ng_2020-05-16e.sql
        * /opt/odoo/clvhealth_jcafb_2020_ng_2020-05-16e.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-05-16e.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-05-16e.tar.gz

:red:`(Não Executado])` Restaurar um backup do banco de dados *CLVhealth-JCAFB-2020-NG* (2020-05-16e)
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
            # gzip -d clvhealth_jcafb_2020_ng_2020-05-16e.sql.gz

            dropdb -i clvhealth_jcafb_2020_ng

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020_ng
            psql -f clvhealth_jcafb_2020_ng_2020-05-16e.sql -d clvhealth_jcafb_2020_ng -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020_ng
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-05-16e.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-05-16e.tar.gz

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

Atualizar o(s) módulo(s) [ver lista] (2020-05-15)
-------------------------------------------------

    * Referência: :doc:`/setup/module_update`.


    #. [tkl-odoo12-jcafb-ng-vm] Lista de Módulos:

        * clv_document
        * clv_document_jcafb

    #. [tkl-odoo12-jcafb-ng-vm] **Executar** a atualização do(s) Módulo(s):

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" - m clv_document
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-ng-vm** ao modo desejado:

            ::

                # ***** tkl-odoo12-jcafb-ng-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Criar um backup do banco de dados *CLVhealth-JCAFB-2020_NG* (2020-05-17a)
-------------------------------------------------------------------------

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
            pg_dump clvhealth_jcafb_2020_ng -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_ng_2020-05-17a.sql

            gzip clvhealth_jcafb_2020_ng_2020-05-17a.sql
            pg_dump clvhealth_jcafb_2020_ng -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_ng_2020-05-17a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-05-17a.tar.gz clvhealth_jcafb_2020_ng

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-05-17a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_ng_2020-05-17a.sql
        * /opt/odoo/clvhealth_jcafb_2020_ng_2020-05-17a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-05-17a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-05-17a.tar.gz

:red:`(Não Executado])` Restaurar um backup do banco de dados *CLVhealth-JCAFB-2020-NG* (2020-05-17a)
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
            # gzip -d clvhealth_jcafb_2020_ng_2020-05-17a.sql.gz

            dropdb -i clvhealth_jcafb_2020_ng

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020_ng
            psql -f clvhealth_jcafb_2020_ng_2020-05-17a.sql -d clvhealth_jcafb_2020_ng -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020_ng
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-05-17a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-05-17a.tar.gz

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

Executar a Verificação para todos os Endereços (2020-05-18)
-----------------------------------------------------------

    #. [tkl-odoo12-jcafb-ng-vm] Executar a Ação :bi:`Address Verification Execute` para todos os Endereços:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-ng-vm <https://tkl-odoo12-jcafb-ng-vm>`_

        #. Acessar a *View* *Employees*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Addresses`

        #. Selecionar todos os Endereços (**665**)

        #. Exercutar a Ação ":bi:`Address Verification Execute`":

            #. Utilize o botão :bi:`Address Verification Execute` para executar a Ação.

Executar a Verificação para todas as Famílias (2020-05-18)
----------------------------------------------------------

    #. [tkl-odoo12-jcafb-ng-vm] Executar a Ação :bi:`Family Verification Execute` para todos os Famílias:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-ng-vm <https://tkl-odoo12-jcafb-ng-vm>`_

        #. Acessar a *View* *Employees*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Families`

        #. Selecionar todos os Famílias (**441**)

        #. Exercutar a Ação ":bi:`Family Verification Execute`":

            #. Utilize o botão :bi:`Family Verification Execute` para executar a Ação.

Executar a Verificação para todas as Pessoas (2020-05-18)
---------------------------------------------------------

    #. [tkl-odoo12-jcafb-ng-vm] Executar a Ação :bi:`Person Verification Execute` para todos os Pessoas:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-ng-vm <https://tkl-odoo12-jcafb-ng-vm>`_

        #. Acessar a *View* *Employees*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Persons`

        #. Selecionar todos os Pessoas (**1540**)

        #. Exercutar a Ação ":bi:`Person Verification Execute`":

            #. Utilize o botão :bi:`Person Verification Execute` para executar a Ação.

Executar a Verificação para todos os Endereços (Aux) (2020-05-18)
-----------------------------------------------------------------

    #. [tkl-odoo12-jcafb-ng-vm] Executar a Ação :bi:`Address (Aux) Verification Execute` para todos os Endereços (Aux):

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-ng-vm <https://tkl-odoo12-jcafb-ng-vm>`_

        #. Acessar a *View* *Employees*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Auxiliary` » :bi:`Addresses (Aux)`

        #. Selecionar todos os Endereços (Aux) (**202**)

        #. Exercutar a Ação ":bi:`Address (Aux) Verification Execute`":

            #. Utilize o botão :bi:`Address (Aux) Verification Execute` para executar a Ação.

Executar a Verificação para todas as Pessoas (Aux) (2020-05-18)
---------------------------------------------------------------

    #. [tkl-odoo12-jcafb-ng-vm] Executar a Ação :bi:`Person (Aux) Verification Execute` para todos os Pessoas (Aux):

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-ng-vm <https://tkl-odoo12-jcafb-ng-vm>`_

        #. Acessar a *View* *Employees*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Auxiliary` » :bi:`Persons (Aux)`

        #. Selecionar todos os Pessoas (Aux) (**605**)

        #. Exercutar a Ação ":bi:`Person (Aux) Verification Execute`":

            #. Utilize o botão :bi:`Person (Aux) Verification Execute` para executar a Ação.

Preparar os "*Global Settings*" para a JCAFB-2020 (2020-05-18)
--------------------------------------------------------------

    #. Acessar a *View* *Global Settings*:

        * Menu de acesso:

            * :bi:`Base` » :bi:`Global Settings` » :bi:`Global Settings`

        #. Configurar o parâmetro :bi:`Phase` » :bi:`Phase`: **JCAFB-2020**

        #. Configurar o parâmetro :bi:`Person` » :bi:`Reference Date`: **31/01/2020**

Atualizar o(s) módulo(s) [ver lista] (2020-05-18)
-------------------------------------------------

    * Referência: :doc:`/setup/module_update`.


    #. [tkl-odoo12-jcafb-ng-vm] Lista de Módulos:

        * clv_person

    #. [tkl-odoo12-jcafb-ng-vm] **Executar** a atualização do(s) Módulo(s):

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" - m clv_person
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-ng-vm** ao modo desejado:

            ::

                # ***** tkl-odoo12-jcafb-ng-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Atualisar a Idade de Referência para todas as Pessoas (2020-05-18)
------------------------------------------------------------------

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Person Mass Edit` para todas as Pessoas:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Persons*:

            * Menu de acesso:

                * :bi:`Communities` » :bi:`Communities` » :bi:`Persons`

        #. Selecionar todas as Pessoas (**1540**)

        #. Exercutar a Ação ":bi:`Person Mass Edit`":

            * Parâmetros utilizados:

                * *Person Reference Age Refresh*: **marcado**

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Criar os Sumários para todos os Grupos (JCAFB-2020) (2020-05-18)
----------------------------------------------------------------

    #. [tkl-odoo12-jcafb-ng-vm] Executar a Ação :bi:`Employee Summary Set Up` para todos os Grupos de Campo e Reserva Técnica (JCAFB-2020):

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-ng-vm <https://tkl-odoo12-jcafb-ng-vm>`_

        #. Acessar a *View* *Funcionários*:

            * Menu de acesso:

                * :bi:`Funcionários` » :bi:`Employees` » :bi:`Employees`

        #. Selecionar todos os Grupos de Campo (**16**) e Reserva Técnica (**5**)

        #. Exercutar a Ação ":bi:`Employee Summary Set Up`":

            #. Utilize o botão :bi:`Employee Summary Set Up` para executar a Ação.

Criar os Sumários para os Endereços (JCAFB-2020) (2020-05-18)
-------------------------------------------------------------

    #. [tkl-odoo12-jcafb-ng-vm] Executar a Ação :bi:`Address Summary Set Up` para todos os Endereços (JCAFB-2020):

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-ng-vm <https://tkl-odoo12-jcafb-ng-vm>`_

        #. Acessar a *View* *Endereços*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Addresses`

        #. Selecionar todos os Endereços (JCAFB-2020) *Available* (**210**), *Selected* (**146**) e *Unselected* (**78**)

        #. Exercutar a Ação ":bi:`Address Summary Set Up`":

            #. Utilize o botão :bi:`Address Summary Set Up` para executar a Ação.

Criar os Sumários para as Famílias (JCAFB-2020) (2020-05-18)
------------------------------------------------------------

    #. [tkl-odoo12-jcafb-ng-vm] Executar a Ação :bi:`Family Summary Set Up` para todos as Famílias (JCAFB-2020):

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-ng-vm <https://tkl-odoo12-jcafb-ng-vm>`_

        #. Acessar a *View* *Endereços*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Families`

        #. Selecionar todos as Famílias (JCAFB-2020) *Available* (**132**), *Selected* (**148**) e *Unselected* (**82**)

        #. Exercutar a Ação ":bi:`Family Summary Set Up`":

            #. Utilize o botão :bi:`Family Summary Set Up` para executar a Ação.

Criar os Sumários para as Pessoas (JCAFB-2020) (2020-05-18)
------------------------------------------------------------

    #. [tkl-odoo12-jcafb-ng-vm] Executar a Ação :bi:`Person Summary Set Up` para todos as Pessoas (JCAFB-2020):

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-ng-vm <https://tkl-odoo12-jcafb-ng-vm>`_

        #. Acessar a *View* *Endereços*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Persons`

        #. Selecionar todos as Pessoas (JCAFB-2020) *Available* (**861**), *Selected* (**191**) e *Unselected* (**127**)

        #. Exercutar a Ação ":bi:`Person Summary Set Up`":

            #. Utilize o botão :bi:`Person Summary Set Up` para executar a Ação.

Criar os Sumários para as Pessoas (Aux) (JCAFB-2020) (2020-05-18)
-----------------------------------------------------------------

    #. [tkl-odoo12-jcafb-ng-vm] Executar a Ação :bi:`Person (Aux) Summary Set Up` para todos as Pessoas (Aux) (JCAFB-2020):

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-ng-vm <https://tkl-odoo12-jcafb-ng-vm>`_

        #. Acessar a *View* *Endereços*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Auxiliary` » :bi:`Persons (Aux)`

        #. Selecionar todos as Pessoas (Aux) (JCAFB-2020) *Available* (**313**), *Selected* (**197**),  *Unselected* (**50**) e *Waiting* (**7**)

        #. Exercutar a Ação ":bi:`Person (Aux) Summary Set Up`":

            #. Utilize o botão :bi:`Person (Aux) Summary Set Up` para executar a Ação.

Criar um backup do banco de dados *CLVhealth-JCAFB-2020_NG* (2020-05-18a)
-------------------------------------------------------------------------

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
            pg_dump clvhealth_jcafb_2020_ng -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_ng_2020-05-18a.sql

            gzip clvhealth_jcafb_2020_ng_2020-05-18a.sql
            pg_dump clvhealth_jcafb_2020_ng -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_ng_2020-05-18a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-05-18a.tar.gz clvhealth_jcafb_2020_ng

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-05-18a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_ng_2020-05-18a.sql
        * /opt/odoo/clvhealth_jcafb_2020_ng_2020-05-18a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-05-18a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-05-18a.tar.gz

.. index:: clvhealth_jcafb_2020_ng_2020-05-18a.sql
.. index:: filestore_clvhealth_jcafb_2020_ng_2020-05-18a
.. index:: clvsol_filestore_clvhealth_jcafb_2020_ng_2020-05-18a

:red:`(Não Executado])` Restaurar um backup do banco de dados *CLVhealth-JCAFB-2020-NG* (2020-05-18a)
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
            # gzip -d clvhealth_jcafb_2020_ng_2020-05-18a.sql.gz

            dropdb -i clvhealth_jcafb_2020_ng

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020_ng
            psql -f clvhealth_jcafb_2020_ng_2020-05-18a.sql -d clvhealth_jcafb_2020_ng -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020_ng
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-05-18a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-05-18a.tar.gz

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

:red:`(Não Executado])` Executar o *External Sync Schedule* "clv.address.tag (clv.global.tag)" (2020-05-09)
-----------------------------------------------------------------------------------------------------------

    #. [tkl-odoo12-jcafb-ng-vm] Marcar como :bi:`Updated` o :bi:`External Synchronization` de todos os :bi:`External Syncs` do *Model* "**clv.address.tag**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-ng-vm <https://tkl-odoo12-jcafb-ng-vm>`_

        #. :red:`(Não Executado])` Configurar, com a ajuda da ação :bi:`External Sync Mass Edit`, todos os :bi:`External Syncs` do *Model* "**clv.address.tag**" (**nnnn**):

            * Menu de acesso:
                
                * :bi:`External Sync` » :bi:`External Syncs` » **Ação** » :bi:`External Sync Mass Edit`

            * Parâmetros alterados:
                
                * *External Synchronization*: **Set** "**Updated**"

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit`, o :bi:`External Sync Schedule` "**clv.address.tag (clv.global.tag)**":

            * Menu de acesso:

                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Schedules` » **Ação** » :bi:`External Sync Schedule Mass Edit`

            * Parâmetros alterados:

                * *External Host*: "**https://192.168.25.183**"
                * *Max Task Registers*: "**250.000**"
                * *Disable Identification*: "**desmarcado**"

    #. Estabelecer uma sessão ssh com o servidor **tkl-odoo12-jcafb-ng-vm** e executar o *Odoo* no modo manual:

        ::

            # ***** tkl-odoo12-jcafb-ng-vm
            #

            ssh tkl-odoo12-jcafb-ng-vm -l root

            /etc/init.d/odoo stop

            su odoo

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    #. [tkl-odoo12-jcafb-ng-vm] Executar o :bi:`External Sync Schedule` "**clv.address.tag (clv.global.tag)**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-ng-vm <https://tkl-odoo12-jcafb-ng-vm>`_

        #. Executar a ação :bi:`External Sync Schedule Exec` para o "**clv.address.tag (clv.global.tag)**":

            * Menu de acesso:
                
                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Schedules` » **Ação** » :bi:`External Sync Schedule Exec`

            * *Synchronization Log*:
                
                * :ref:`External Sync Schedule - clv.address.tag (clv.global.tag) - 20200509(6)`

    #. [tkl-odoo12-jcafb-ng-vm] Configurar o :bi:`External Sync Schedule` "**clv.document.item (clv.document.item)**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-ng-vm <https://tkl-odoo12-jcafb-ng-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit`, o :bi:`External Sync Schedule` "**clv.address.tag (clv.global.tag)**":

            * Menu de acesso:

                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Schedules` » **Ação** » :bi:`External Sync Schedule Mass Edit`

            * Parâmetros alterados:

                * *Disable Identification*: "**marcado**"

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-ng-vm** ao modo padrão:

        ::

            # ***** tkl-odoo12-jcafb-ng-vm
            #                * *Disable Identification*: "**marcado**"


            ^C

            exit

            /etc/init.d/odoo start

.. toctree::
   :maxdepth: 2

   jcafb_2020_ng_history_002_sync_log
