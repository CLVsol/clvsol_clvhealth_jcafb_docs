.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

===========================================================================
Migração do Banco de Dados - JCAFB-2021 - Servidor [tkl-odoo13-jcafb-vm]
===========================================================================

Inicializar o conteúdo do diretório **clvsol_filestore/clvhealth_jcafb** (2020-06-10)
-------------------------------------------------------------------------------------

	#. [tkl-odoo13-jcafb-vm] Criar, manualmente, os diretórios:

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

	#. Copiar, manualmente, a partir do servidor **tkl-odoo12-jcafb-vm** para o servidor **tkl-odoo13-jcafb-vm**, o conteúdo dos diretórios listados anteriormente.

		* "tkl-odoo12-jcafb-vm:/opt/odoo/clvsol_filestore/clvhealth_jcafb" **->** "tkl-odoo13-jcafb-vm:/opt/odoo/clvsol_filestore/clvhealth_jcafb"

.. index:: clvsol_filestore
.. index:: clvsol_filestore/clvhealth_jcafb
.. index:: clvsol_filestore/clvhealth_jcafb/export_files
.. index:: clvsol_filestore/clvhealth_jcafb/lab_test_files
.. index:: clvsol_filestore/clvhealth_jcafb/summary_files
.. index:: clvsol_filestore/clvhealth_jcafb/survey_files

Criar uma nova instância do *CLVhealth-JCAFB-2021* (2020-06-10)
---------------------------------------------------------------

	* **Execution time: 0:13:45.861**

    #. [tkl-odoo13-jcafb-vm] Estabelecer uma sessão ssh (session 1) com o servidor **tkl-odoo13-jcafb-vm** e paralizar o *Odoo*:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            ssh tkl-odoo13-jcafb-vm -l root

            /etc/init.d/odoo stop

            su odoo

    #. [tkl-odoo13-jcafb-vm] Excluir a instância do *CLVhealth-JCAFB-2021* existente:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            cd /opt/odoo
            dropdb -i clvhealth_jcafb_2021

            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2021

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb-vm** ao modo manual:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    #. Estabelecer uma sessão ssh (session 2) com o servidor **tkl-odoo13-jcafb-vm** e executar o **install.py**:

        ::

            # ***** tkl-odoo13-jcafb-vm (session 2)
            #

            ssh tkl-odoo13-jcafb-vm -l odoo

            cd /opt/odoo/clvsol_clvhealth_jcafb/project
            
            python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021"
            # Execution time: 0:08:22.364

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb-vm** ao modo desejado:

        ::

            # ***** tkl-odoo13-jcafb-vm (session 1)
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

Criar o *External Sync Host* "https://192.168.25.183" (2020-06-10)
------------------------------------------------------------------

    #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb-vm <https://tkl-odoo13-jcafb-vm>`_

    #. Criar o *External Sync Host* **https://192.168.25.183**:

        * Menu de acesso:
            
            * *External Sync* > *Configuration* > *Hosts* > Criar

        * Parâmetros utilizados:
            
            * External Host Name: "**https://192.168.25.183**"
            * External Database Name: "**clvhealth_jcafb_2020**"
            * External User: "**admin**"
            * External User Password: "*******"

.. _Lista de Schedules jcafb_2021_history_001 (1):

Lista de *Schedules* instalados (1) (2020-06-10)
------------------------------------------------

    * Lista de *Schedules* instalados:

        * :green:`(Enabled)` res.users [Migration]

        * :green:`(Enabled)` res.country (res.country)
        * :green:`(Enabled)` res.country.state (res.country.state)
        * :green:`(Enabled)` res.city (res.city)

        * :green:`(Enabled)` res.users (res.users)

        * :green:`(Enabled)` clv.file_system.directory (clv.file_system.directory)

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
        * :green:`(Enabled)` clv.lab_test.result (clv.lab_test.result) [2]
        * :red:`(Disabled)` clv.lab_test.criterion (clv.lab_test.criterion)

        * :green:`(Enabled)` survey.survey (survey.survey)
        * :green:`(Enabled)` survey.question (survey.question)
        * :green:`(Enabled)` survey.label (survey.label)
        * :green:`(Enabled)` survey.user_input (survey.user_input)
        * :green:`(Enabled)` survey.user_input [Adapt]
        * :green:`(Enabled)` clv.document (clv.document) [2]
        * :red:`(Disabled)` survey.user_input_line (survey.user_input_line)
        * :red:`(Disabled)` survey.question (survey.page)
        * :red:`(Disabled)` survey.question [Adapt]
        * :red:`(Disabled)` survey.user_input [Adapt 2]

        * :green:`(Enabled)` clv.verification.marker (clv.verification.marker)

        * :green:`(Enabled)` clv.set (clv.set)
        * :green:`(Enabled)` clv.set.element (clv.set.element)

        * :green:`(Enabled)` ir.model (ir.model)
        * :green:`(Enabled)` ir.model.fields (ir.model.fields)

        * :green:`(Enabled)` clv.model_export.template (clv.model_export.template)
        * :green:`(Enabled)` clv.model_export.template.field (clv.model_export.template.field)
        * :red:`(Enabled)` clv.model_export.template.document_item (clv.model_export.template.document_item)
        * :red:`(Enabled)` clv.model_export.template.lab_test_criterion (clv.model_export.template.lab_test_criterion)
        * :red:`(Enabled)` clv.model_export (clv.model_export)

Executar o *External Sync Batch* "*Default Batch*" (1) (2020-06-08)
-------------------------------------------------------------------

    #. [tkl-odoo13-jcafb-vm] Configurar os :bi:`External Sync Schedules` :green:`Novos`:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb-vm <https://tkl-odoo13-jcafb-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit`, todos os :bi:`External Sync Schedules`:

            * Lista de *Schedules*:
                
                * :ref:`Lista de Schedules jcafb_2021_history_001 (1)`

            * Menu de acesso:
                
                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Schedules` » **Ação** » :bi:`External Sync Schedule Mass Edit`

            * Parâmetros alterados:
                
                * *External Host*: "**https://192.168.25.183**"
                * *Max Task Registers*: "**250.000**"

    #. Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb-vm** e executar o *Odoo* no modo manual:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            ssh tkl-odoo13-jcafb-vm -l root

            /etc/init.d/odoo stop

            su odoo

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    #. [tkl-odoo13-jcafb-vm] Executar o :bi:`External Sync Batch` "**Default Batch**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb-vm <https://tkl-odoo13-jcafb-vm>`_

        #. Executar a ação :bi:`External Sync Batch Exec` para o "**Default Batch**":

            * Menu de acesso:
                
                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Batches` » **Ação** » :bi:`External Sync Batch Exec`

            * *Members*:
                
                * :ref:`Lista de Schedules jcafb_2021_history_001 (1)`

            * :bi:`Execution time: 1:30:34.662`

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb-vm** ao modo padrão:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            ^C

            exit

            /etc/init.d/odoo start

Lista de *Schedules* executados (1) (2020-06-10)
------------------------------------------------

    * Lista de *Schedules* instalados:

        * :green:`[Execution time: 0:00:20.769]` res.users [Migration]

        * :green:`[Execution time: 0:00:05.525 + 0:00:06.295]` res.country (res.country)
        * :green:`[Execution time: 0:00:02.977 + 0:00:21.194]` res.country.state (res.country.state)
        * :green:`[Execution time: 0:00:25.246 + 0:03:08.519]` res.city (res.city)

        * :green:`[Execution time: 0:00:01.331 + 0:00:08.517]` res.users (res.users)

        * :green:`[Execution time: 0:00:00.710 + 0:00:00.453]` clv.file_system.directory (clv.file_system.directory)

        * :green:`[Execution time: 0:00:00.344 + 0:00:01.025]` clv.global_tag (clv.global_tag)

        * :green:`[Execution time: 0:00:00.231 + 0:00:00.289]` clv.phase (clv.phase)

        * :green:`[Execution time: 0:00:00.561 + 0:00:01.713]` hr.department (hr.department) [rec]
        * :green:`[Execution time: 0:00:00.329 + 0:00:02.198]` hr.department (hr.department)
        * :green:`[Execution time: 0:00:00.308 + 0:00:00.700]` hr.job (hr.job) [rec]
        * :green:`[Execution time: 0:00:00.225 + 0:00:00.752]` hr.job (hr.job)
        * :green:`[Execution time: 0:00:01.524 + 0:00:08.652]` hr.employee (hr.employee) [rec]
        * :green:`[Execution time: 0:00:00.959 + 0:00:28.781]` hr.employee (hr.employee)
        * :green:`[Execution time: 0:00:01.655 + 0:00:11.181]` hr.employee.history (hr.employee.history)

        * :green:`[Execution time: 0:00:00.232 + 0:00:00.249]` clv.address.category (clv.address.category)
        * :green:`[Execution time: 0:00:06.489 + 0:01:59.476]` clv.address (clv.address)
        * :green:`[Execution time: 0:00:14.081 + 0:01:46.101]` clv.address.history (clv.address.history)

        * :green:`[Execution time: 0:00:01.531 + 0:00:41.852]` clv.address.aux (clv.address.aux)

        * :green:`[Execution time: 0:00:00.204 + 0:00:00.168]` clv.family.category (clv.family.category)
        * :green:`[Execution time: 0:00:02.720 + 0:00:59.237]` clv.family (clv.family)
        * :green:`[Execution time: 0:00:04.323 + 0:00:46.405]` clv.family.history (clv.family.history)

        * :green:`[Execution time: 0:00:00.283 + 0:00:00.378]` clv.person.category (clv.person.category)
        * :green:`[Execution time: 0:00:00.311 + 0:00:00.334]` clv.person.marker (clv.person.marker)
        * :green:`[Execution time: 0:00:12.113 + 0:04:05.660]` clv.person (clv.person)
        * :green:`[Execution time: 0:00:04.440 + 0:00:16.221]` clv.person (clv.person) [2]
        * :green:`[Execution time: 0:00:34.850 + 0:06:18.355]` clv.person.history (clv.person.history)

        * :green:`[Execution time: 0:00:05.208 + 0:02:04.492]` clv.person.aux (clv.person.aux)

        * :green:`[Execution time: 0:00:00.388 + 0:00:01.908]` clv.event (clv.event)
        * :green:`[Execution time: 0:00:13.946 + 0:01:07.189]` clv.event.attendee (clv.event.attendee)

        * :green:`[Execution time: 0:00:00.531 + 0:00:00.500]` clv.document.category (clv.document.category)
        * :green:`[Execution time: 0:00:00.547 + 0:00:01.549]` clv.document.type (clv.document.type)
        * :green:`[Execution time: 0:01:09.152 + 0:13:15.204]` clv.document (clv.document)
        * :red:`[Execution time: 2:00:00.365 + 3:53:22.704]` clv.document.item (clv.document.item)

        * :green:`[Execution time: 0:00:00.504 + 0:00:00.474]` clv.lab_test.unit (clv.lab_test.unit)
        * :green:`[Execution time: 0:00:00.604 + 0:00:00.554]` clv.lab_test.parasite (clv.lab_test.parasite)
        * :green:`[Execution time: 0:00:00.619 + 0:00:00.457]` clv.lab_test.crystal (clv.lab_test.crystal)
        * :green:`[Execution time: 0:00:00.727 + 0:00:01.352]` clv.lab_test.type (clv.lab_test.type)
        * :green:`[Execution time: 0:00:48.020 + 0:05:12.129]` clv.lab_test.request (clv.lab_test.request)
        * :green:`[Execution time: 0:00:28.838 + 0:04:33.556]` clv.lab_test.result (clv.lab_test.result)
        * :green:`[Execution time: 0:00:19.067 + 0:02:33.849]` clv.lab_test.report (clv.lab_test.report)
        * :green:`[Execution time: 0:00:25.224 + 0:03:15.153]` clv.lab_test.result (clv.lab_test.result) [2]
        * :red:`[Execution time: 1:33:42.869 + 2:38:36.031]` clv.lab_test.criterion (clv.lab_test.criterion)

        * :green:`[Execution time: 0:00:01.736 + 0:00:01.736]` survey.survey (survey.survey)
        * :green:`[Execution time: 0:00:12.915 + 0:01:12.519]` survey.question (survey.question)
        * :green:`[Execution time: 0:00:46.254 + 0:02:48.272]` survey.label (survey.label)
        * :green:`[Execution time: 0:00:45.606 + 0:04:21.342]` survey.user_input (survey.user_input)
        * :green:`[Execution time: 0:00:18.624]` survey.user_input [Adapt]
        * :green:`[Execution time: 0:01:13.908 + 0:13:13.874]` clv.document (clv.document) [2]
        * :red:`[Execution time: 1:51:23.606 + 9:35:20.980]` survey.user_input_line (survey.user_input_line)
        * :red:`[Execution time: 0:00:32.476 + 0:00:38.807]` survey.question (survey.page)
        * :red:`[Execution time: 0:04:23.466]` survey.question [Adapt]
        * :red:`[Execution time: 0:04:59.838]` survey.user_input [Adapt 2]

        * :green:`[Execution time: 0:00:00.412 + 0:00:00.813]` clv.verification.marker (clv.verification.marker)

        * :green:`[Execution time: 0:00:00.277 + 0:00:00.243]` clv.set (clv.set)
        * :green:`[Execution time: 0:00:10.921 + 0:00:42.521]` clv.set.element (clv.set.element)

        * :green:`[Execution time: 0:00:05.063 + 0:00:09.876]` ir.model (ir.model)
        * :green:`[Execution time: 0:01:38.745 + 0:03:31.643]` ir.model.fields (ir.model.fields)

        * :green:`[Execution time: 0:00:00.433 + 0:00:00.743]` clv.model_export.template (clv.model_export.template)
        * :green:`[Execution time: 0:00:01.119 + 0:00:05.147]` clv.model_export.template.field (clv.model_export.template.field)
        * :red:`[Execution time: 0:00:14.603 + 0:00:23.069]` clv.model_export.template.document_item (clv.model_export.template.document_item)
        * :red:`[Execution time: 0:00:13.192 + 0:00:30.570]` clv.model_export.template.lab_test_criterion (clv.model_export.template.lab_test_criterion)
        * :red:`[Execution time: 0:00:01.088 + 0:00:03.194]` clv.model_export (clv.model_export)

Criar um backup do banco de dados *CLVhealth-JCAFB-2021* (2020-06-09a)
----------------------------------------------------------------------

    #. [tkl-odoo13-jcafb-vm] Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb-vm** e paralizar o *Odoo*:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            ssh tkl-odoo13-jcafb-vm -l root

            /etc/init.d/odoo stop

            su odoo

    #. [tkl-odoo13-jcafb-vm] Executar os comandos de criação dos arquivos de backup:

        ::

            # ***** tkl-odoo13-jcafb-vm
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

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb-vm** ao modo desejado:

        ::

            # ***** tkl-odoo13-jcafb-vm
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

:red:`(Não Executado])` Restaurar um backup do banco de dados *CLVhealth-JCAFB-2021* (2020-06-09a)
--------------------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_restore`.

    #. [tkl-odoo13-jcafb-vm] Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb-vm** e paralizar o *Odoo*:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            ssh tkl-odoo13-jcafb-vm -l root

            /etc/init.d/odoo stop

            su odoo

    #. [tkl-odoo13-jcafb-vm] Executar os comandos de restauração dos arquivos de backup:

        ::

            # ***** tkl-odoo13-jcafb-vm
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

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb-vm** ao modo desejado:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    #. [tkl-odoo13-jcafb-vm] Configurar o parâmetro "**web.base.url**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb-vm <https://tkl-odoo13-jcafb-vm>`_

        #. Acessar a *View* **Parâmetros do Sistema**:

            * Menu de acesso:
                
                * **Configurações** » **Técnico** » **Parâmetros** » **Parâmetros do Sistema**

        #. Pesquisar pelo registro com a **Chave** "**web.base.url**"

        #. Editar o registro apresentado (**Chave**: "**web.base.url**")

        #. Alterar o campo **Valor** para:

            * "**http://tkl-odoo13-jcafb-vm**".

        #. Salvar o registro editado.

Executar o *External Sync Schedule* "clv.document.item (clv.document.item)" (2020-06-10)
----------------------------------------------------------------------------------------

    #. Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb-vm** e executar o *Odoo* no modo manual:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            ssh tkl-odoo13-jcafb-vm -l root

            /etc/init.d/odoo stop

            su odoo

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    #. [tkl-odoo13-jcafb-vm] Executar o :bi:`External Sync Schedule` "**clv.document.item (clv.document.item)**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb-vm <https://tkl-odoo13-jcafb-vm>`_

        #. Executar a ação :bi:`External Sync Schedule Exec` para o "**clv.document.item (clv.document.item)**":

            * Menu de acesso:
                
                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Schedules` » **Ação** » :bi:`External Sync Schedule Exec`

    #. [tkl-odoo13-jcafb-vm] Configurar o :bi:`External Sync Schedule` "**clv.document.item (clv.document.item)**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb-vm <https://tkl-odoo13-jcafb-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit`, o :bi:`External Sync Schedule` "**clv.document.item (clv.document.item)**":

            * Menu de acesso:

                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Schedules` » **Ação** » :bi:`External Sync Schedule Mass Edit`

            * Parâmetros alterados:

                * *Disable Identification*: "**marcado**"

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb-vm** ao modo padrão:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #                * *Disable Identification*: "**marcado**"


            ^C

            exit

            /etc/init.d/odoo start

Criar um backup do banco de dados *CLVhealth-JCAFB-2021* (2020-06-10a)
----------------------------------------------------------------------

    #. [tkl-odoo13-jcafb-vm] Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb-vm** e paralizar o *Odoo*:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            ssh tkl-odoo13-jcafb-vm -l root

            /etc/init.d/odoo stop

            su odoo

    #. [tkl-odoo13-jcafb-vm] Executar os comandos de criação dos arquivos de backup:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #
            # data_dir = /var/lib/odoo/.local/share/Odoo
            #

            cd /opt/odoo
            pg_dump clvhealth_jcafb_2021 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2021_2020-06-10a.sql

            gzip clvhealth_jcafb_2021_2020-06-10a.sql
            pg_dump clvhealth_jcafb_2021 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2021_2020-06-10a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2021_2020-06-10a.tar.gz clvhealth_jcafb_2021

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021_2020-06-10a.tar.gz clvhealth_jcafb

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb-vm** ao modo desejado:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    Criados os seguintes arquivos:
        * /opt/odoo/clvhealth_jcafb_2021_2020-06-10a.sql
        * /opt/odoo/clvhealth_jcafb_2021_2020-06-10a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2021_2020-06-10a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021_2020-06-10a.tar.gz

:red:`(Não Executado])` Restaurar um backup do banco de dados *CLVhealth-JCAFB-2021* (2020-06-10a)
--------------------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_restore`.

    #. [tkl-odoo13-jcafb-vm] Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb-vm** e paralizar o *Odoo*:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            ssh tkl-odoo13-jcafb-vm -l root

            /etc/init.d/odoo stop

            su odoo

    #. [tkl-odoo13-jcafb-vm] Executar os comandos de restauração dos arquivos de backup:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            cd /opt/odoo
            # gzip -d clvhealth_jcafb_2021_2020-06-10a.sql.gz

            dropdb -i clvhealth_jcafb_2021

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2021
            psql -f clvhealth_jcafb_2021_2020-06-10a.sql -d clvhealth_jcafb_2021 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2021
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2021_2020-06-10a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021_2020-06-10a.tar.gz

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb-vm** ao modo desejado:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    #. [tkl-odoo13-jcafb-vm] Configurar o parâmetro "**web.base.url**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb-vm <https://tkl-odoo13-jcafb-vm>`_

        #. Acessar a *View* **Parâmetros do Sistema**:

            * Menu de acesso:
                
                * **Configurações** » **Técnico** » **Parâmetros** » **Parâmetros do Sistema**

        #. Pesquisar pelo registro com a **Chave** "**web.base.url**"

        #. Editar o registro apresentado (**Chave**: "**web.base.url**")

        #. Alterar o campo **Valor** para:

            * "**http://tkl-odoo13-jcafb-vm**".

        #. Salvar o registro editado.

Executar o *External Sync Schedule* "clv.lab_test.criterion (clv.lab_test.criterion)" (2020-06-10)
--------------------------------------------------------------------------------------------------

    #. Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb-vm** e executar o *Odoo* no modo manual:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            ssh tkl-odoo13-jcafb-vm -l root

            /etc/init.d/odoo stop

            su odoo

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    #. [tkl-odoo13-jcafb-vm] Executar o :bi:`External Sync Schedule` "**clv.lab_test.criterion (clv.lab_test.criterion)**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb-vm <https://tkl-odoo13-jcafb-vm>`_

        #. Executar a ação :bi:`External Sync Schedule Exec` para o "**clv.lab_test.criterion (clv.lab_test.criterion)**":

            * Menu de acesso:
                
                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Schedules` » **Ação** » :bi:`External Sync Schedule Exec`

    #. [tkl-odoo13-jcafb-vm] Configurar o :bi:`External Sync Schedule` "**clv.lab_test.criterion (clv.lab_test.criterion)**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb-vm <https://tkl-odoo13-jcafb-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit`, o :bi:`External Sync Schedule` "**clv.lab_test.criterion (clv.lab_test.criterion)**":

            * Menu de acesso:

                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Schedules` » **Ação** » :bi:`External Sync Schedule Mass Edit`

            * Parâmetros alterados:

                * *Disable Identification*: "**marcado**"

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb-vm** ao modo padrão:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #                * *Disable Identification*: "**marcado**"


            ^C

            exit

            /etc/init.d/odoo start

Criar um backup do banco de dados *CLVhealth-JCAFB-2021* (2020-06-11a)
----------------------------------------------------------------------

    #. [tkl-odoo13-jcafb-vm] Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb-vm** e paralizar o *Odoo*:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            ssh tkl-odoo13-jcafb-vm -l root

            /etc/init.d/odoo stop

            su odoo

    #. [tkl-odoo13-jcafb-vm] Executar os comandos de criação dos arquivos de backup:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #
            # data_dir = /var/lib/odoo/.local/share/Odoo
            #

            cd /opt/odoo
            pg_dump clvhealth_jcafb_2021 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2021_2020-06-11a.sql

            gzip clvhealth_jcafb_2021_2020-06-11a.sql
            pg_dump clvhealth_jcafb_2021 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2021_2020-06-11a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2021_2020-06-11a.tar.gz clvhealth_jcafb_2021

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021_2020-06-11a.tar.gz clvhealth_jcafb

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb-vm** ao modo desejado:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    Criados os seguintes arquivos:
        * /opt/odoo/clvhealth_jcafb_2021_2020-06-11a.sql
        * /opt/odoo/clvhealth_jcafb_2021_2020-06-11a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2021_2020-06-11a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021_2020-06-11a.tar.gz

:red:`(Não Executado])` Restaurar um backup do banco de dados *CLVhealth-JCAFB-2021* (2020-06-11a)
--------------------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_restore`.

    #. [tkl-odoo13-jcafb-vm] Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb-vm** e paralizar o *Odoo*:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            ssh tkl-odoo13-jcafb-vm -l root

            /etc/init.d/odoo stop

            su odoo

    #. [tkl-odoo13-jcafb-vm] Executar os comandos de restauração dos arquivos de backup:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            cd /opt/odoo
            # gzip -d clvhealth_jcafb_2021_2020-06-11a.sql.gz

            dropdb -i clvhealth_jcafb_2021

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2021
            psql -f clvhealth_jcafb_2021_2020-06-11a.sql -d clvhealth_jcafb_2021 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2021
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2021_2020-06-11a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021_2020-06-11a.tar.gz

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb-vm** ao modo desejado:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    #. [tkl-odoo13-jcafb-vm] Configurar o parâmetro "**web.base.url**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb-vm <https://tkl-odoo13-jcafb-vm>`_

        #. Acessar a *View* **Parâmetros do Sistema**:

            * Menu de acesso:
                
                * **Configurações** » **Técnico** » **Parâmetros** » **Parâmetros do Sistema**

        #. Pesquisar pelo registro com a **Chave** "**web.base.url**"

        #. Editar o registro apresentado (**Chave**: "**web.base.url**")

        #. Alterar o campo **Valor** para:

            * "**http://tkl-odoo13-jcafb-vm**".

        #. Salvar o registro editado.

Executar o *External Sync Schedule* "survey.user_input_line (survey.user_input_line)" (2020-06-11)
--------------------------------------------------------------------------------------------------

    #. Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb-vm** e executar o *Odoo* no modo manual:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            ssh tkl-odoo13-jcafb-vm -l root

            /etc/init.d/odoo stop

            su odoo

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    #. [tkl-odoo13-jcafb-vm] Executar o :bi:`External Sync Schedule` "**survey.user_input_line (survey.user_input_line)**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb-vm <https://tkl-odoo13-jcafb-vm>`_

        #. Executar a ação :bi:`External Sync Schedule Exec` para o "**survey.user_input_line (survey.user_input_line)**":

            * Menu de acesso:
                
                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Schedules` » **Ação** » :bi:`External Sync Schedule Exec`

    #. [tkl-odoo13-jcafb-vm] Configurar o :bi:`External Sync Schedule` "**survey.user_input_line (survey.user_input_line)**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb-vm <https://tkl-odoo13-jcafb-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit`, o :bi:`External Sync Schedule` "**survey.user_input_line (survey.user_input_line)**":

            * Menu de acesso:

                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Schedules` » **Ação** » :bi:`External Sync Schedule Mass Edit`

            * Parâmetros alterados:

                * *Disable Identification*: "**marcado**"

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb-vm** ao modo padrão:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #                * *Disable Identification*: "**marcado**"


            ^C

            exit

            /etc/init.d/odoo start

Criar um backup do banco de dados *CLVhealth-JCAFB-2021* (2020-06-11b)
----------------------------------------------------------------------

    #. [tkl-odoo13-jcafb-vm] Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb-vm** e paralizar o *Odoo*:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            ssh tkl-odoo13-jcafb-vm -l root

            /etc/init.d/odoo stop

            su odoo

    #. [tkl-odoo13-jcafb-vm] Executar os comandos de criação dos arquivos de backup:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #
            # data_dir = /var/lib/odoo/.local/share/Odoo
            #

            cd /opt/odoo
            pg_dump clvhealth_jcafb_2021 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2021_2020-06-11b.sql

            gzip clvhealth_jcafb_2021_2020-06-11b.sql
            pg_dump clvhealth_jcafb_2021 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2021_2020-06-11b.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2021_2020-06-11b.tar.gz clvhealth_jcafb_2021

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021_2020-06-11b.tar.gz clvhealth_jcafb

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb-vm** ao modo desejado:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    Criados os seguintes arquivos:
        * /opt/odoo/clvhealth_jcafb_2021_2020-06-11b.sql
        * /opt/odoo/clvhealth_jcafb_2021_2020-06-11b.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2021_2020-06-11b.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021_2020-06-11b.tar.gz

:red:`(Não Executado])` Restaurar um backup do banco de dados *CLVhealth-JCAFB-2021* (2020-06-11b)
--------------------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_restore`.

    #. [tkl-odoo13-jcafb-vm] Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb-vm** e paralizar o *Odoo*:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            ssh tkl-odoo13-jcafb-vm -l root

            /etc/init.d/odoo stop

            su odoo

    #. [tkl-odoo13-jcafb-vm] Executar os comandos de restauração dos arquivos de backup:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            cd /opt/odoo
            # gzip -d clvhealth_jcafb_2021_2020-06-11b.sql.gz

            dropdb -i clvhealth_jcafb_2021

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2021
            psql -f clvhealth_jcafb_2021_2020-06-11b.sql -d clvhealth_jcafb_2021 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2021
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2021_2020-06-11b.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021_2020-06-11b.tar.gz

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb-vm** ao modo desejado:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    #. [tkl-odoo13-jcafb-vm] Configurar o parâmetro "**web.base.url**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb-vm <https://tkl-odoo13-jcafb-vm>`_

        #. Acessar a *View* **Parâmetros do Sistema**:

            * Menu de acesso:
                
                * **Configurações** » **Técnico** » **Parâmetros** » **Parâmetros do Sistema**

        #. Pesquisar pelo registro com a **Chave** "**web.base.url**"

        #. Editar o registro apresentado (**Chave**: "**web.base.url**")

        #. Alterar o campo **Valor** para:

            * "**http://tkl-odoo13-jcafb-vm**".

        #. Salvar o registro editado.

Executar o *External Sync Schedule* "survey.question (survey.page)" (2020-06-12)
--------------------------------------------------------------------------------

    #. Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb-vm** e executar o *Odoo* no modo manual:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            ssh tkl-odoo13-jcafb-vm -l root

            /etc/init.d/odoo stop

            su odoo

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    #. [tkl-odoo13-jcafb-vm] Executar o :bi:`External Sync Schedule` "**survey.question (survey.page)**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb-vm <https://tkl-odoo13-jcafb-vm>`_

        #. Executar a ação :bi:`External Sync Schedule Exec` para o "**survey.question (survey.page)**":

            * Menu de acesso:
                
                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Schedules` » **Ação** » :bi:`External Sync Schedule Exec`

    #. [tkl-odoo13-jcafb-vm] Configurar o :bi:`External Sync Schedule` "**survey.question (survey.page)**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb-vm <https://tkl-odoo13-jcafb-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit`, o :bi:`External Sync Schedule` "**survey.question (survey.page)**":

            * Menu de acesso:

                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Schedules` » **Ação** » :bi:`External Sync Schedule Mass Edit`

            * Parâmetros alterados:

                * *Disable Identification*: "**marcado**"

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb-vm** ao modo padrão:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #                * *Disable Identification*: "**marcado**"


            ^C

            exit

            /etc/init.d/odoo start

Executar o *External Sync Schedule* "survey.question [Adapt]" (2020-06-12)
--------------------------------------------------------------------------

    #. Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb-vm** e executar o *Odoo* no modo manual:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            ssh tkl-odoo13-jcafb-vm -l root

            /etc/init.d/odoo stop

            su odoo

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    #. [tkl-odoo13-jcafb-vm] Executar o :bi:`External Sync Schedule` "**survey.question [Adapt]**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb-vm <https://tkl-odoo13-jcafb-vm>`_

        #. Executar a ação :bi:`External Sync Schedule Exec` para o "**survey.question [Adapt]**":

            * Menu de acesso:
                
                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Schedules` » **Ação** » :bi:`External Sync Schedule Exec`

    #. [tkl-odoo13-jcafb-vm] Configurar o :bi:`External Sync Schedule` "**survey.question [Adapt]**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb-vm <https://tkl-odoo13-jcafb-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit`, o :bi:`External Sync Schedule` "**survey.question [Adapt]**":

            * Menu de acesso:

                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Schedules` » **Ação** » :bi:`External Sync Schedule Mass Edit`

            * Parâmetros alterados:

                * *Disable Identification*: "**marcado**"

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb-vm** ao modo padrão:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #                * *Disable Identification*: "**marcado**"


            ^C

            exit

            /etc/init.d/odoo start

Executar o *External Sync Schedule* "clv.model_export.template.document_item (clv.model_export.template.document_item)" (2020-06-12)
------------------------------------------------------------------------------------------------------------------------------------

    #. Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb-vm** e executar o *Odoo* no modo manual:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            ssh tkl-odoo13-jcafb-vm -l root

            /etc/init.d/odoo stop

            su odoo

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    #. [tkl-odoo13-jcafb-vm] Executar o :bi:`External Sync Schedule` "**clv.model_export.template.document_item (clv.model_export.template.document_item)**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb-vm <https://tkl-odoo13-jcafb-vm>`_

        #. Executar a ação :bi:`External Sync Schedule Exec` para o "**clv.model_export.template.document_item (clv.model_export.template.document_item)**":

            * Menu de acesso:
                
                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Schedules` » **Ação** » :bi:`External Sync Schedule Exec`

    #. [tkl-odoo13-jcafb-vm] Configurar o :bi:`External Sync Schedule` "**clv.model_export.template.document_item (clv.model_export.template.document_item)**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb-vm <https://tkl-odoo13-jcafb-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit`, o :bi:`External Sync Schedule` "**clv.model_export.template.document_item (clv.model_export.template.document_item)**":

            * Menu de acesso:

                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Schedules` » **Ação** » :bi:`External Sync Schedule Mass Edit`

            * Parâmetros alterados:

                * *Disable Identification*: "**marcado**"

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb-vm** ao modo padrão:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #                * *Disable Identification*: "**marcado**"


            ^C

            exit

            /etc/init.d/odoo start

Executar o *External Sync Schedule* "clv.model_export.template.lab_test_criterion (clv.model_export.template.lab_test_criterion)" (2020-06-12)
----------------------------------------------------------------------------------------------------------------------------------------------

    #. Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb-vm** e executar o *Odoo* no modo manual:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            ssh tkl-odoo13-jcafb-vm -l root

            /etc/init.d/odoo stop

            su odoo

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    #. [tkl-odoo13-jcafb-vm] Executar o :bi:`External Sync Schedule` "**clv.model_export.template.lab_test_criterion (clv.model_export.template.lab_test_criterion)**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb-vm <https://tkl-odoo13-jcafb-vm>`_

        #. Executar a ação :bi:`External Sync Schedule Exec` para o "**clv.model_export.template.lab_test_criterion (clv.model_export.template.lab_test_criterion)**":

            * Menu de acesso:
                
                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Schedules` » **Ação** » :bi:`External Sync Schedule Exec`

    #. [tkl-odoo13-jcafb-vm] Configurar o :bi:`External Sync Schedule` "**clv.model_export.template.lab_test_criterion (clv.model_export.template.lab_test_criterion)**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb-vm <https://tkl-odoo13-jcafb-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit`, o :bi:`External Sync Schedule` "**clv.model_export.template.lab_test_criterion (clv.model_export.template.lab_test_criterion)**":

            * Menu de acesso:

                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Schedules` » **Ação** » :bi:`External Sync Schedule Mass Edit`

            * Parâmetros alterados:

                * *Disable Identification*: "**marcado**"

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb-vm** ao modo padrão:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #                * *Disable Identification*: "**marcado**"


            ^C

            exit

            /etc/init.d/odoo start

Executar o *External Sync Schedule* "clv.model_export (clv.model_export)" (2020-06-12)
--------------------------------------------------------------------------------------

    #. Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb-vm** e executar o *Odoo* no modo manual:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            ssh tkl-odoo13-jcafb-vm -l root

            /etc/init.d/odoo stop

            su odoo

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    #. [tkl-odoo13-jcafb-vm] Executar o :bi:`External Sync Schedule` "**clv.model_export (clv.model_export)**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb-vm <https://tkl-odoo13-jcafb-vm>`_

        #. Executar a ação :bi:`External Sync Schedule Exec` para o "**clv.model_export (clv.model_export)**":

            * Menu de acesso:
                
                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Schedules` » **Ação** » :bi:`External Sync Schedule Exec`

    #. [tkl-odoo13-jcafb-vm] Configurar o :bi:`External Sync Schedule` "**clv.model_export (clv.model_export)**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb-vm <https://tkl-odoo13-jcafb-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit`, o :bi:`External Sync Schedule` "**clv.model_export (clv.model_export)**":

            * Menu de acesso:

                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Schedules` » **Ação** » :bi:`External Sync Schedule Mass Edit`

            * Parâmetros alterados:

                * *Disable Identification*: "**marcado**"

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb-vm** ao modo padrão:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #                * *Disable Identification*: "**marcado**"


            ^C

            exit

            /etc/init.d/odoo start

Criar um backup do banco de dados *CLVhealth-JCAFB-2021* (2020-06-12a)
----------------------------------------------------------------------

    #. [tkl-odoo13-jcafb-vm] Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb-vm** e paralizar o *Odoo*:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            ssh tkl-odoo13-jcafb-vm -l root

            /etc/init.d/odoo stop

            su odoo

    #. [tkl-odoo13-jcafb-vm] Executar os comandos de criação dos arquivos de backup:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #
            # data_dir = /var/lib/odoo/.local/share/Odoo
            #

            cd /opt/odoo
            pg_dump clvhealth_jcafb_2021 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2021_2020-06-12a.sql

            gzip clvhealth_jcafb_2021_2020-06-12a.sql
            pg_dump clvhealth_jcafb_2021 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2021_2020-06-12a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2021_2020-06-12a.tar.gz clvhealth_jcafb_2021

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021_2020-06-12a.tar.gz clvhealth_jcafb

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb-vm** ao modo desejado:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    Criados os seguintes arquivos:
        * /opt/odoo/clvhealth_jcafb_2021_2020-06-12a.sql
        * /opt/odoo/clvhealth_jcafb_2021_2020-06-12a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2021_2020-06-12a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021_2020-06-12a.tar.gz

Criar um backup do banco de dados *CLVhealth-JCAFB-2021* (2020-06-12b)
----------------------------------------------------------------------

    #. [tkl-odoo13-jcafb-vm] Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb-vm** e paralizar o *Odoo*:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            ssh tkl-odoo13-jcafb-vm -l root

            /etc/init.d/odoo stop

            su odoo

    #. [tkl-odoo13-jcafb-vm] Executar os comandos de criação dos arquivos de backup:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #
            # data_dir = /var/lib/odoo/.local/share/Odoo
            #

            cd /opt/odoo
            pg_dump clvhealth_jcafb_2021 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2021_2020-06-12b.sql

            gzip clvhealth_jcafb_2021_2020-06-12b.sql
            pg_dump clvhealth_jcafb_2021 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2021_2020-06-12b.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2021_2020-06-12b.tar.gz clvhealth_jcafb_2021

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021_2020-06-12b.tar.gz clvhealth_jcafb

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb-vm** ao modo desejado:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    Criados os seguintes arquivos:
        * /opt/odoo/clvhealth_jcafb_2021_2020-06-12b.sql
        * /opt/odoo/clvhealth_jcafb_2021_2020-06-12b.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2021_2020-06-12b.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021_2020-06-12b.tar.gz

.. index:: clvhealth_jcafb_2021_2020-06-12b.sql
.. index:: filestore_clvhealth_jcafb_2021_2020-06-12b
.. index:: clvsol_filestore_clvhealth_jcafb_2021_2020-06-12b

Restaurar um backup do banco de dados *CLVhealth-JCAFB-2021* (2020-06-12b)
--------------------------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_restore`.

    #. [tkl-odoo13-jcafb-vm] Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb-vm** e paralizar o *Odoo*:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            ssh tkl-odoo13-jcafb-vm -l root

            /etc/init.d/odoo stop

            su odoo

    #. [tkl-odoo13-jcafb-vm] Executar os comandos de restauração dos arquivos de backup:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            cd /opt/odoo
            # gzip -d clvhealth_jcafb_2021_2020-06-12b.sql.gz

            dropdb -i clvhealth_jcafb_2021

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2021
            psql -f clvhealth_jcafb_2021_2020-06-12b.sql -d clvhealth_jcafb_2021 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2021
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2021_2020-06-12b.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021_2020-06-12b.tar.gz

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb-vm** ao modo desejado:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    #. [tkl-odoo13-jcafb-vm] Configurar o parâmetro "**web.base.url**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb-vm <https://tkl-odoo13-jcafb-vm>`_

        #. Acessar a *View* **Parâmetros do Sistema**:

            * Menu de acesso:
                
                * **Configurações** » **Técnico** » **Parâmetros** » **Parâmetros do Sistema**

        #. Pesquisar pelo registro com a **Chave** "**web.base.url**"

        #. Editar o registro apresentado (**Chave**: "**web.base.url**")

        #. Alterar o campo **Valor** para:

            * "**http://tkl-odoo13-jcafb-vm**".

        #. Salvar o registro editado.

.. toctree::   :maxdepth: 2
