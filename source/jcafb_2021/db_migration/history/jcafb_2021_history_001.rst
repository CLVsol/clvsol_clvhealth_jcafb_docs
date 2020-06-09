.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

===========================================================================
Migração do Banco de Dados - JCAFB-2021 - Servidor [tkl-odoo-160-buster-vm]
===========================================================================

Inicializar o conteúdo do diretório **clvsol_filestore/clvhealth_jcafb** (2020-06-08)
-------------------------------------------------------------------------------------

	#. [tkl-odoo-160-buster-vm] Criar, manualmente, os diretórios:

		* /opt/odoo/**clvsol_filestore**

		* /opt/odoo/clvsol_filestore/**clvhealth_jcafb**

		* /opt/odoo/clvsol_filestore/clvhealth_jcafb/**export_files**

		* /opt/odoo/clvsol_filestore/clvhealth_jcafb/export_files/**csv**

		* /opt/odoo/clvsol_filestore/clvhealth_jcafb/export_files/**sqlite**

		* /opt/odoo/clvsol_filestore/clvhealth_jcafb/export_files/**xls**

		* /opt/odoo/clvsol_filestore/clvhealth_jcafb/**lab_test_files**

		* /opt/odoo/clvsol_filestore/clvhealth_jcafb/lab_test_files/**reports**

		* /opt/odoo/clvsol_filestore/clvhealth_jcafb/lab_test_files/reports/**templates**

		* /opt/odoo/clvsol_filestore/clvhealth_jcafb/lab_test_files/reports/**xls**

		* /opt/odoo/clvsol_filestore/clvhealth_jcafb/lab_test_files/**results**

		* /opt/odoo/clvsol_filestore/clvhealth_jcafb/lab_test_files/results/**templates**

		* /opt/odoo/clvsol_filestore/clvhealth_jcafb/lab_test_files/results/**xls**

		* /opt/odoo/clvsol_filestore/clvhealth_jcafb/**summary_files**

		* /opt/odoo/clvsol_filestore/clvhealth_jcafb/**survey_files**

		* /opt/odoo/clvsol_filestore/clvhealth_jcafb/survey_files/**templates**

	#. Copiar, manualmente, a partir do servidor **tkl-odoo12-jcafb-vm** para o servidor **tkl-odoo-160-buster-vm**, o conteúdo dos diretórios listados anteriormente.

		* "tkl-odoo12-jcafb-vm:/opt/odoo/clvsol_filestore/clvhealth_jcafb" **->** "tkl-odoo-160-buster-vm:/opt/odoo/clvsol_filestore/clvhealth_jcafb"

.. index:: clvsol_filestore
.. index:: clvsol_filestore/clvhealth_jcafb
.. index:: clvsol_filestore/clvhealth_jcafb/export_files
.. index:: clvsol_filestore/clvhealth_jcafb/lab_test_files
.. index:: clvsol_filestore/clvhealth_jcafb/summary_files
.. index:: clvsol_filestore/clvhealth_jcafb/survey_files

Criar uma nova instância do *CLVhealth-JCAFB-2021* (2020-06-08)
---------------------------------------------------------------

	* **Execution time: 0:09:48.322**

    #. [tkl-odoo-160-buster-vm] Estabelecer uma sessão ssh (session 1) com o servidor **tkl-odoo-160-buster-vm** e paralizar o *Odoo*:

        ::

            # ***** tkl-odoo-160-buster-vm
            #

            ssh tkl-odoo-160-buster-vm -l root

            /etc/init.d/odoo stop

            su odoo

    #. [tkl-odoo-160-buster-vm] Excluir a instância do *CLVhealth-JCAFB-2021* existente:

        ::

            # ***** tkl-odoo-160-buster-vm
            #

            cd /opt/odoo
            dropdb -i clvhealth_jcafb_2021

            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2021

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo-160-buster-vm** ao modo manual:

        ::

            # ***** tkl-odoo-160-buster-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    #. Estabelecer uma sessão ssh (session 2) com o servidor **tkl-odoo-160-buster-vm** e executar o **install.py**:

        ::

            # ***** tkl-odoo-160-buster-vm (session 2)
            #

            ssh tkl-odoo-160-buster-vm -l odoo

            cd /opt/odoo/clvsol_clvhealth_jcafb/project
            
            python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021"
            # Execution time: 0:08:22.364

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo-160-buster-vm** ao modo desejado:

        ::

            # ***** tkl-odoo-160-buster-vm (session 1)
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

:red:`(Não Executado])` Migrar os Usuários de **clvhealth_jcafb_2020** para **clvhealth_jcafb_2021** (2020-06-08)
-----------------------------------------------------------------------------------------------------------------

    #. Estabelecer uma sessão ssh com o servidor **tkl-odoo-160-buster-vm** e executar o **res_users_migration.py**, acessando o servidor **tkl-odoo-160-buster-vm** [base de dados **clvhealth_jcafb_2020**]:

        ::

            # ***** tkl-odoo-160-buster-vm (session 2)
            #

            ssh tkl-odoo-160-buster-vm -l odoo

            cd /opt/odoo/clvsol_clvhealth_jcafb/project
            
            python3 res_users_migration.py --rserver "https://192.168.25.183" --radmin_pw "***" --rdb "clvhealth_jcafb_2020" --lserver "https://192.168.25.192" --ladmin_pw "***" --ldb "clvhealth_jcafb_2021"
            # Execution time: 0:01:10.814

    * Os "passwords" não foram migrados.
        
Criar o *External Sync Host* "https://192.168.25.183" (2020-06-08)
------------------------------------------------------------------

    #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo-160-buster-vm <https://tkl-odoo-160-buster-vm>`_

    #. Criar o *External Sync Host* **https://192.168.25.183**:

        * Menu de acesso:
            
            * *External Sync* > *Configuration* > *Hosts* > Criar

        * Parâmetros utilizados:
            
            * External Host Name: "**https://192.168.25.183**"
            * External Database Name: "**clvhealth_jcafb_2020**"
            * External User: "**admin**"
            * External User Password: "*******"

.. _Lista de Schedules jcafb_2021_history_001 (1):

Lista de *Schedules* instalados (1) (2020-06-08)
------------------------------------------------

    * Lista de *Schedules* instalados:

        * :green:`(Enabled)` res.users [Migration]

        * :green:`(Enabled)` res.country (res.country)
        * :green:`(Enabled)` res.country.state (res.country.state)
        * :green:`(Enabled)` res.city (res.city)

        * :green:`(Enabled)` res.users (res.users)

        * :green:`(Enabled)` clv.global_tag (clv.global_tag)

        * :green:`(Enabled)` clv.phase (clv.phase)

        * :green:`(Enabled)` hr.department (hr.department) [rec]
        * :green:`(Enabled)` hr.department (hr.department)
        * :green:`(Enabled)` hr.job (hr.job) [rec]
        * :green:`(Enabled)` hr.job (hr.job)
        * :green:`(Enabled)` hr.employee (hr.employee) [rec]
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
        * :green:`(Enabled)` clv.person (clv.person) [2]
        * :green:`(Enabled)` clv.person.history (clv.person.history)

        * :green:`(Enabled)` clv.person.aux (clv.person.aux)

        * :green:`(Enabled)` clv.event (clv.event)
        * :green:`(Enabled)` clv.event.attendee (clv.event.attendee)

        * :green:`(Enabled)` survey.survey (survey.survey)
        * :green:`(Enabled)` survey.question (survey.question)
        * :green:`(Enabled)` survey.label (survey.label)
        * :green:`(Enabled)` survey.user_input (survey.user_input)
        * :red:`(Disabled)` survey.user_input_line (survey.user_input_line)
        * :red:`(Disabled)` survey.question (survey.page)
        * :red:`(Disabled)` survey.question [Adapt]

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

Executar o *External Sync Batch* "*Default Batch*" (1) (2020-06-08)
-------------------------------------------------------------------

    #. [tkl-odoo-160-buster-vm] Configurar os :bi:`External Sync Schedules` :green:`Novos`:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo-160-buster-vm <https://tkl-odoo-160-buster-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit`, todos os :bi:`External Sync Schedules`:

            * Lista de *Schedules*:
                
                * :ref:`Lista de Schedules jcafb_2021_history_001 (1)`

            * Menu de acesso:
                
                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Schedules` » **Ação** » :bi:`External Sync Schedule Mass Edit`

            * Parâmetros alterados:
                
                * *External Host*: "**https://192.168.25.183**"
                * *Max Task Registers*: "**250.000**"

    #. Estabelecer uma sessão ssh com o servidor **tkl-odoo-160-buster-vm** e executar o *Odoo* no modo manual:

        ::

            # ***** tkl-odoo-160-buster-vm
            #

            ssh tkl-odoo-160-buster-vm -l root

            /etc/init.d/odoo stop

            su odoo

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    #. [tkl-odoo-160-buster-vm] Executar o :bi:`External Sync Batch` "**Default Batch**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo-160-buster-vm <https://tkl-odoo-160-buster-vm>`_

        #. Executar a ação :bi:`External Sync Batch Exec` para o "**Default Batch**":

            * Menu de acesso:
                
                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Batches` » **Ação** » :bi:`External Sync Batch Exec`

            * *Members*:
                
                * :ref:`Lista de Schedules jcafb_2021_history_001 (1)`

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo-160-buster-vm** ao modo padrão:

        ::

            # ***** tkl-odoo-160-buster-vm
            #

            ^C

            exit

            /etc/init.d/odoo start

Lista de *Schedules* executados (1) (2020-06-08)
------------------------------------------------

    * Lista de *Schedules* instalados:

        * :green:`[Execution time: 0:00:28.528]` res.users [Migration]

        * :green:`[Execution time: 0:00:09.722 + 0:00:05.897]` res.country (res.country)
        * :green:`[Execution time: 0:00:02.617 + 0:00:18.783]` res.country.state (res.country.state)
        * :green:`[Execution time: 0:00:22.253 + 0:03:02.956]` res.city (res.city)

        * :green:`[Execution time: 0:00:01.308 + 0:00:05.907]` res.users (res.users)

        * :green:`[Execution time: 0:00:00.333 + 0:00:01.038]` clv.global_tag (clv.global_tag)

        * :green:`[Execution time: 0:00:00.231 + 0:00:00.285]` clv.phase (clv.phase)

        * :green:`[Execution time: 0:00:00.576 + 0:00:01.735]` hr.department (hr.department) [rec]
        * :green:`[Execution time: 0:00:00.340 + 0:00:02.166]` hr.department (hr.department)
        * :green:`[Execution time: 0:00:00.308 + 0:00:00.599]` hr.job (hr.job) [rec]
        * :green:`[Execution time: 0:00:00.225 + 0:00:00.752]` hr.job (hr.job)
        * :green:`[Execution time: 0:00:01.497 + 0:00:05.974]` hr.employee (hr.employee) [rec]
        * :green:`[Execution time: 0:00:00.959 + 0:00:24.312]` hr.employee (hr.employee)
        * :green:`[Execution time: 0:00:01.410 + 0:00:10.450]` hr.employee.history (hr.employee.history)

        * :green:`[Execution time: 0:00:00.221 + 0:00:00.245]` clv.address.category (clv.address.category)
        * :green:`[Execution time: 0:00:03.588 + 0:01:59.476]` clv.address (clv.address)
        * :green:`[Execution time: 0:00:14.081 + 0:01:46.101]` clv.address.history (clv.address.history)

        * :green:`[Execution time: 0:00:01.531 + 0:00:41.852]` clv.address.aux (clv.address.aux)

        * :green:`[Execution time: 0:00:00.204 + 0:00:00.168]` clv.family.category (clv.family.category)
        * :green:`[Execution time: 0:00:02.580 + 0:00:59.237]` clv.family (clv.family)
        * :green:`[Execution time: 0:00:03.879 + 0:00:41.115]` clv.family.history (clv.family.history)

        * :green:`[Execution time: 0:00:00.283 + 0:00:00.378]` clv.person.category (clv.person.category)
        * :green:`[Execution time: 0:00:00.311 + 0:00:00.334]` clv.person.marker (clv.person.marker)
        * :green:`[Execution time: 0:00:09.359 + 0:04:04.241]` clv.person (clv.person)
        * :green:`[Execution time: 0:00:04.177 + 0:00:14.964]` clv.person (clv.person) [2]
        * :green:`[Execution time: 0:00:26.214 + 0:04:55.132]` clv.person.history (clv.person.history)

        * :green:`[Execution time: 0:00:04.430 + 0:01:47.081]` clv.person.aux (clv.person.aux)

        * :green:`[Execution time: 0:00:00.388 + 0:00:01.422]` clv.event (clv.event)
        * :green:`[Execution time: 0:00:09.196 + 0:00:56.288]` clv.event.attendee (clv.event.attendee)

        * :green:`[Execution time: 0:00:00.747] + 0:00:00.747]` survey.survey (survey.survey)
        * :green:`[Execution time: 0:00:09.284 + 0:01:05.372]` survey.question (survey.question)
        * :green:`[Execution time: 0:00:28.760 + 0:02:13.048]` survey.label (survey.label)
        * :green:`[Execution time: 0:00:29.014 + 0:03:12.193]` survey.user_input (survey.user_input)
        * :red:`[Execution time: 0:52:11.435 + 5:32:57.260]` survey.user_input_line (survey.user_input_line)
        * :green:`[Execution time: 0:00:09.683 + 0:00:29.606]` survey.question (survey.page)
        * :green:`[Execution time: 0:03:21.960]` survey.question [Adapt]

        * :green:`[Execution time: 0:00:00.531 + 0:00:00.500]` clv.document.category (clv.document.category)
        * :green:`[Execution time: 0:00:01.248 + 0:00:01.549]` clv.document.type (clv.document.type)
        * :green:`[Execution time: 0:05:12.062 + 0:27:41.193]` clv.document (clv.document)
        * :red:`[Execution time: 4:36:23.207]` clv.document.item (clv.document.item)

        * :green:`[Execution time: 0:00:00.504 + 0:00:00.474]` clv.lab_test.unit (clv.lab_test.unit)
        * :green:`[Execution time: 0:00:00.604 + 0:00:00.554]` clv.lab_test.parasite (clv.lab_test.parasite)
        * :green:`[Execution time: 0:00:00.619 + 0:00:00.457]` clv.lab_test.crystal (clv.lab_test.crystal)
        * :green:`[Execution time: 0:00:00.727 + 0:00:01.352]` clv.lab_test.type (clv.lab_test.type)
        * :green:`[Execution time: 0:03:03.675 + 0:10:14.663]` clv.lab_test.request (clv.lab_test.request)
        * :green:`[Execution time: 0:01:55.336 + 0:09:26.515]` clv.lab_test.result (clv.lab_test.result)
        * :green:`[Execution time: 0:01:28.455 + 0:06:03.311]` clv.lab_test.report (clv.lab_test.report)
        * :green:`[Execution time: 0:01:45.267 + 0:06:24.058]` clv.lab_test.result (clv.lab_test.result) [2]
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

Criar um backup do banco de dados *CLVhealth-JCAFB-2021* (2020-06-09a)
----------------------------------------------------------------------

    #. [tkl-odoo-160-buster-vm] Estabelecer uma sessão ssh com o servidor **tkl-odoo-160-buster-vm** e paralizar o *Odoo*:

        ::

            # ***** tkl-odoo-160-buster-vm
            #

            ssh tkl-odoo-160-buster-vm -l root

            /etc/init.d/odoo stop

            su odoo

    #. [tkl-odoo-160-buster-vm] Executar os comandos de criação dos arquivos de backup:

        ::

            # ***** tkl-odoo-160-buster-vm
            #
            # data_dir = /var/lib/odoo/.local/share/Odoo
            #

            cd /opt/odoo
            pg_dump clvhealth_jcafb_2021 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2021_2020-06-09a.sql

            gzip clvhealth_jcafb_2021_2020-06-09a.sql
            pg_dump clvhealth_jcafb_2021 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2021_2020-06-09a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2021_2020-06-09a.tar.gz clvhealth_jcafb_2021

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021_2020-06-09a.tar.gz clvhealth_jcafb

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo-160-buster-vm** ao modo desejado:

        ::

            # ***** tkl-odoo-160-buster-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    Criados os seguintes arquivos:
        * /opt/odoo/clvhealth_jcafb_2021_2020-06-09a.sql
        * /opt/odoo/clvhealth_jcafb_2021_2020-06-09a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2021_2020-06-09a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021_2020-06-09a.tar.gz

.. index:: clvhealth_jcafb_2021_2020-06-09a.sql
.. index:: filestore_clvhealth_jcafb_2021_2020-06-09a
.. index:: clvsol_filestore_clvhealth_jcafb_2021_2020-06-09a

Restaurar um backup do banco de dados *CLVhealth-JCAFB-2021* (2020-06-09a)
--------------------------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_restore`.

    #. [tkl-odoo-160-buster-vm] Estabelecer uma sessão ssh com o servidor **tkl-odoo-160-buster-vm** e paralizar o *Odoo*:

        ::

            # ***** tkl-odoo-160-buster-vm
            #

            ssh tkl-odoo-160-buster-vm -l root

            /etc/init.d/odoo stop

            su odoo

    #. [tkl-odoo-160-buster-vm] Executar os comandos de restauração dos arquivos de backup:

        ::

            # ***** tkl-odoo-160-buster-vm
            #

            cd /opt/odoo
            # gzip -d clvhealth_jcafb_2021_2020-06-09a.sql.gz

            dropdb -i clvhealth_jcafb_2021

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2021
            psql -f clvhealth_jcafb_2021_2020-06-09a.sql -d clvhealth_jcafb_2021 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2021
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2021_2020-06-09a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021_2020-06-09a.tar.gz

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo-160-buster-vm** ao modo desejado:

        ::

            # ***** tkl-odoo-160-buster-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    #. [tkl-odoo-160-buster-vm] Configurar o parâmetro "**web.base.url**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo-160-buster-vm <https://tkl-odoo-160-buster-vm>`_

        #. Acessar a *View* **Parâmetros do Sistema**:

            * Menu de acesso:
                
                * **Configurações** » **Técnico** » **Parâmetros** » **Parâmetros do Sistema**

        #. Pesquisar pelo registro com a **Chave** "**web.base.url**"

        #. Editar o registro apresentado (**Chave**: "**web.base.url**")

        #. Alterar o campo **Valor** para:

            * "**http://tkl-odoo-160-buster-vm**".

        #. Salvar o registro editado.

.. toctree::   :maxdepth: 2
