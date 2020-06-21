.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

==========================================
Migração do Banco de Dados - JCAFB-2020-13
==========================================

Inicializar o conteúdo do diretório **clvsol_filestore/clvhealth_jcafb** [tkl-odoo13-jcafb-vm] (2020-06-18)
-----------------------------------------------------------------------------------------------------------

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

Criar uma nova instância do *CLVhealth-JCAFB-2020-13* (2020-06-18)
------------------------------------------------------------------

	* **Execution time: 0:09:02.095**

    #. [tkl-odoo13-jcafb-vm] Estabelecer uma sessão ssh (session 1) com o servidor **tkl-odoo13-jcafb-vm** e paralizar o *Odoo*:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            ssh tkl-odoo13-jcafb-vm -l root

            /etc/init.d/odoo stop

            su odoo

    #. [tkl-odoo13-jcafb-vm] Excluir a instância do *CLVhealth-JCAFB-2020-13* existente:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            cd /opt/odoo
            dropdb -i clvhealth_jcafb_2020_13

            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020_13

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
            
            python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020_13"
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

Criar o *External Sync Host* "https://192.168.25.183" (2020-06-18)
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

Lista de *Schedules* instalados (1) (2020-06-18)
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
        * :green:`(Enabled)` survey.survey [Adapt]
        * :green:`(Enabled)` survey.question (survey.question)
        * :green:`(Enabled)` survey.label (survey.label)
        * :green:`(Enabled)` survey.user_input (survey.user_input)
        * :green:`(Enabled)` survey.user_input [Adapt]
        * :green:`(Enabled)` clv.document (clv.document) [2]
        * :red:`(Disabled)` survey.user_input_line (survey.user_input_line)
        * :red:`(Disabled)` survey.question (survey.page)
        * :red:`(Disabled)` survey.question [Adapt]
        * :red:`(Disabled)` survey.user_input [Adapt 2]

        * :green:`(Enabled)` clv.partner_entity.street_pattern (clv.partner_entity.street_pattern)
        * :green:`(Enabled)` clv.verification.marker (clv.verification.marker)

        * :green:`(Enabled)` clv.set (clv.set)
        * :green:`(Enabled)` clv.set.element (clv.set.element)

        * :green:`(Enabled)` ir.model (ir.model)
        * :green:`(Enabled)` ir.model.fields (ir.model.fields)

        * :green:`(Enabled)` clv.model_export.template (clv.model_export.template)
        * :green:`(Enabled)` clv.model_export.template.field (clv.model_export.template.field)
        * :red:`(Disabled)` clv.model_export.template.document_item (clv.model_export.template.document_item)
        * :red:`(Disabled)` clv.model_export.template.lab_test_criterion (clv.model_export.template.lab_test_criterion)
        * :red:`(Disabled)` clv.model_export (clv.model_export)

        * :green:`(Enabled)` clv.person_sel.age_group (clv.person_sel.age_group
        * :green:`(Enabled)` clv.person_sel.district (clv.person_sel.district)
        * :green:`(Enabled)` clv.person_sel.group (clv.person_sel.group)
        * :green:`(Enabled)` clv.person_sel.summary (clv.person_sel.summary)

Executar o *External Sync Batch* "*Default Batch*" (1) (2020-06-18)
-------------------------------------------------------------------

    #. [tkl-odoo13-jcafb-vm] Configurar todos os :bi:`External Sync Schedules`:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb-vm <https://tkl-odoo13-jcafb-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit`, todos os :bi:`External Sync Schedules`:

            * Lista de *Schedules*:
                
                * :ref:`Lista de Schedules jcafb_2021_history_001 (1)`

            * Menu de acesso:
                
                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Schedules` » **Ação** » :bi:`External Sync Schedule Mass Edit`

            * Parâmetros alterados:
                
                * *External Host*: "**https://192.168.25.183**"
                * *Max Task Registers*: "**250.000**"
                * *Disable Inclusion*: "**marcado**"
                * *Disable Sync*: "**marcado**"

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

            * :bi:`Execution time: 0:08:47.627`

    #. [tkl-odoo13-jcafb-vm] Configurar os :bi:`External Sync Schedules` :green:`(Enabled)`:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb-vm <https://tkl-odoo13-jcafb-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit (2)`, os :bi:`External Sync Schedules`:

            * Lista de *Schedules*:
                
                * :ref:`Lista de Schedules jcafb_2021_history_001 (1)`

            * Menu de acesso:
                
                * :bi:`External Sync` » :bi:`Confituration` » :bi:`External Sync` » :bi:`Batch Members` » **Ação** » :bi:`External Sync Schedule Mass Edit (2)`

            * Parâmetros alterados:
                
                * *Disable Identification*: "**marcado**"

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb-vm** ao modo padrão:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            ^C

            exit

            /etc/init.d/odoo start

Lista de *Schedules* executados (1) (2020-06-18)
------------------------------------------------

    * Lista de *Schedules* instalados:

        * :green:`[Execution time: 0:00:31.625]` res.users [Migration]

        * :green:`[Execution time: 0:00:07.963 + 0:00:10.793]` res.country (res.country)
        * :green:`[Execution time: 0:00:10.561 + 0:00:58.500]` res.country.state (res.country.state)
        * :green:`[Execution time: 0:00:28.236 + 0:07:54.443]` res.city (res.city)

        * :green:`[Execution time: 0:00:01.412 + 0:00:05.831]` res.users (res.users)

        * :green:`[Execution time: 0:00:00.270 + 0:00:00.510]` clv.file_system.directory (clv.file_system.directory)

        * :green:`[Execution time: 0:00:00.342 + 0:00:01.149]` clv.global_tag (clv.global_tag)

        * :green:`[Execution time: 0:00:00.242 + 0:00:00.351]` clv.phase (clv.phase)

        * :green:`[Execution time: 0:00:00.580 + 0:00:01.730]` hr.department (hr.department) [rec]
        * :green:`[Execution time: 0:00:00.390 + 0:00:02.074]` hr.department (hr.department)
        * :green:`[Execution time: 0:00:00.313 + 0:00:00.636]` hr.job (hr.job) [rec]
        * :green:`[Execution time: 0:00:00.244 + 0:00:00.926]` hr.job (hr.job)
        * :green:`[Execution time: 0:00:01.614 + 0:00:05.732]` hr.employee (hr.employee) [rec]
        * :green:`[Execution time: 0:00:00.739 + 0:00:40.627]` hr.employee (hr.employee)
        * :green:`[Execution time: 0:00:01.494 + 0:00:40.159]` hr.employee.history (hr.employee.history)

        * :green:`[Execution time: 0:00:00.244 + 0:00:00.339]` clv.address.category (clv.address.category)
        * :green:`[Execution time: 0:00:03.655 + 0:04:00.290]` clv.address (clv.address)
        * :green:`[Execution time: 0:00:08.885 + 0:04:39.341]` clv.address.history (clv.address.history)

        * :green:`[Execution time: 0:00:01.327 + 0:01:07.540]` clv.address.aux (clv.address.aux)

        * :green:`[Execution time: 0:00:00.211 + 0:00:00.194]` clv.family.category (clv.family.category)
        * :green:`[Execution time: 0:00:02.585 + 0:02:14.771]` clv.family (clv.family)
        * :green:`[Execution time: 0:00:04.192 + 0:02:31.712]` clv.family.history (clv.family.history)

        * :green:`[Execution time: 0:00:00.233 + 0:00:00.361]` clv.person.category (clv.person.category)
        * :green:`[Execution time: 0:00:00.246 + 0:00:00.416]` clv.person.marker (clv.person.marker)
        * :green:`[Execution time: 0:00:09.066 + 0:10:33.754]` clv.person (clv.person)
        * :green:`[Execution time: 0:00:04.405 + 0:00:41.473]` clv.person (clv.person) [2]
        * :green:`[Execution time: 0:00:37.330 + 0:15:50.246]` clv.person.history (clv.person.history)

        * :green:`[Execution time: 0:00:04.346 + 0:04:09.338]` clv.person.aux (clv.person.aux)

        * :green:`[Execution time: 0:00:00.429 + 0:00:03.033]` clv.event (clv.event)
        * :green:`[Execution time: 0:00:09.734 + 0:02:24.325]` clv.event.attendee (clv.event.attendee)

        * :green:`[Execution time: 0:00:00.294 + 0:00:00.467]` clv.document.category (clv.document.category)
        * :green:`[Execution time: 0:00:00.512 + 0:00:01.291]` clv.document.type (clv.document.type)
        * :green:`[Execution time: 0:00:54.980 + 0:33:23.174]` clv.document (clv.document)
        * :red:`[Execution time: 1:48:24.857 + 4:56:41.308]` clv.document.item (clv.document.item)

        * :green:`[Execution time: 0:00:00.301 + 0:00:00.489]` clv.lab_test.unit (clv.lab_test.unit)
        * :green:`[Execution time: 0:00:00.337 + 0:00:00.597]` clv.lab_test.parasite (clv.lab_test.parasite)
        * :green:`[Execution time: 0:00:00.317 + 0:00:00.477]` clv.lab_test.crystal (clv.lab_test.crystal)
        * :green:`[Execution time: 0:00:00.374 + 0:00:01.609]` clv.lab_test.type (clv.lab_test.type)
        * :green:`[Execution time: 0:00:34.856 + 0:11:52.921]` clv.lab_test.request (clv.lab_test.request)
        * :green:`[Execution time: 0:00:25.424 + 0:13:37.395]` clv.lab_test.result (clv.lab_test.result)
        * :green:`[Execution time: 0:00:18.384 + 0:09:23.720]` clv.lab_test.report (clv.lab_test.report)
        * :green:`[Execution time: 0:00:15.832 + 0:10:02.002]` clv.lab_test.result (clv.lab_test.result) [2]
        * :red:`[Execution time: 1:18:08.198 + 2:50:47.893]` clv.lab_test.criterion (clv.lab_test.criterion)

        * :green:`[Execution time: 0:00:00.654 + 0:00:04.718]` survey.survey (survey.survey)
        * :green:`[Execution time: 0:00:00.055]` survey.survey [Adapt]
        * :green:`[Execution time: 0:00:10.825 + 0:02:01.564]` survey.question (survey.question)
        * :green:`[Execution time: 0:00:36.318 + 0:05:10.085]` survey.label (survey.label)
        * :green:`[Execution time: 0:00:36.673 + 0:08:50.187]` survey.user_input (survey.user_input)
        * :green:`[Execution time: 0:00:12.277]` survey.user_input [Adapt]
        * :green:`[Execution time: 0:00:49.742 + 0:36:37.393]` clv.document (clv.document) [2]
        * :red:`[Execution time: 2:42:05.182 + 7:34:59.743]` survey.user_input_line (survey.user_input_line)
        * :red:`[Execution time: 0:00:13.557 + 0:00:30.880]` survey.question (survey.page)
        * :red:`[Execution time: 0:03:29.078]` survey.question [Adapt]
        * :red:`[Execution time: 0:04:25.244]` survey.user_input [Adapt 2]

        * :green:`[Execution time: 0:00:09.277 + 0:00:04.096]` clv.partner_entity.street_pattern (clv.partner_entity.street_pattern)
        * :green:`[Execution time: 0:00:00.394 + 0:00:00.924]` clv.verification.marker (clv.verification.marker)

        * :green:`[Execution time: 0:00:00.229 + 0:00:00.360]` clv.set (clv.set)
        * :green:`[Execution time: 0:00:08.349 + 0:01:49.136]` clv.set.element (clv.set.element)

        * :green:`[Execution time: 0:00:04.322 + 0:00:10.745]` ir.model (ir.model)
        * :green:`[Execution time: 0:01:23.325 + 0:03:36.888]` ir.model.fields (ir.model.fields)

        * :green:`[Execution time: 0:00:00.353 + 0:00:02.044]` clv.model_export.template (clv.model_export.template)
        * :green:`[Execution time: 0:00:00.933 + 0:00:09.512]` clv.model_export.template.field (clv.model_export.template.field)
        * :red:`[Execution time: 0:00:12.738 + 0:00:27.396]` clv.model_export.template.document_item (clv.model_export.template.document_item)
        * :red:`[Execution time: 0:00:10.777 + 0:00:28.124]` clv.model_export.template.lab_test_criterion (clv.model_export.template.lab_test_criterion)
        * :red:`[Execution time: 0:00:00.972 + 0:00:02.467]` clv.model_export (clv.model_export)

        * :green:`[Execution time: 0:00:00.288 + 0:00:01.243]` clv.person_sel.age_group (clv.person_sel.age_group
        * :green:`[Execution time: 0:00:00.330 + 0:00:01.454]` clv.person_sel.district (clv.person_sel.district)
        * :green:`[Execution time: 0:00:01.154 + 0:00:11.957]` clv.person_sel.group (clv.person_sel.group)
        * :green:`[Execution time: 0:00:00.415 + 0:00:01.657]` clv.person_sel.summary (clv.person_sel.summary)

Executar o *External Sync Schedule* "clv.document.item (clv.document.item)" (2020-06-18)
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

Executar o *External Sync Schedule* "clv.lab_test.criterion (clv.lab_test.criterion)" (2020-06-18)
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

Executar o *External Sync Schedule* "survey.user_input_line (survey.user_input_line)" (2020-06-18)
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

Executar o *External Sync Batch* "*Default Batch*" (2) (2020-06-18)
-------------------------------------------------------------------

    #. [tkl-odoo13-jcafb-vm] Configurar todos os :bi:`External Sync Schedules`:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb-vm <https://tkl-odoo13-jcafb-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit`, todos os :bi:`External Sync Schedules`:

            * Lista de *Schedules*:
                
                * :ref:`Lista de Schedules jcafb_2021_history_001 (1)`

            * Menu de acesso:
                
                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Schedules` » **Ação** » :bi:`External Sync Schedule Mass Edit`

            * Parâmetros alterados:
                
                * *Disable Inclusion*: "**desmarcado**"
                * *Disable Sync*: "**desmarcado**"

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

            * :bi:`Execution time: 3:16:58.972`

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb-vm** ao modo padrão:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            ^C

            exit

            /etc/init.d/odoo start

Executar o *External Sync Schedule* "clv.document.item (clv.document.item)" (2020-06-19)
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

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb-vm** ao modo padrão:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #                * *Disable Identification*: "**marcado**"


            ^C

            exit

            /etc/init.d/odoo start

Executar o *External Sync Schedule* "clv.lab_test.criterion (clv.lab_test.criterion)" (2020-06-19)
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

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb-vm** ao modo padrão:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #                * *Disable Identification*: "**marcado**"


            ^C

            exit

            /etc/init.d/odoo start

Executar o *External Sync Schedule* "survey.user_input_line (survey.user_input_line)" (2020-06-19)
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

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb-vm** ao modo padrão:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #                * *Disable Identification*: "**marcado**"


            ^C

            exit

            /etc/init.d/odoo start

Executar o *External Sync Schedule* "survey.question (survey.page)" (2020-06-20)
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

Executar o *External Sync Schedule* "survey.question [Adapt]" (2020-06-20)
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

Executar o *External Sync Schedule* "survey.user_input [Adapt 2]" (2020-06-20)
------------------------------------------------------------------------------

    #. Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb-vm** e executar o *Odoo* no modo manual:

        ::

            # ***** tkl-odoo13-jcafb-vm
            #

            ssh tkl-odoo13-jcafb-vm -l root

            /etc/init.d/odoo stop

            su odoo

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    #. [tkl-odoo13-jcafb-vm] Executar o :bi:`External Sync Schedule` "**survey.user_input [Adapt 2]**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb-vm <https://tkl-odoo13-jcafb-vm>`_

        #. Executar a ação :bi:`External Sync Schedule Exec` para o "**survey.user_input [Adapt 2]**":

            * Menu de acesso:
                
                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Schedules` » **Ação** » :bi:`External Sync Schedule Exec`

    #. [tkl-odoo13-jcafb-vm] Configurar o :bi:`External Sync Schedule` "**survey.user_input [Adapt 2]**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb-vm <https://tkl-odoo13-jcafb-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit`, o :bi:`External Sync Schedule` "**survey.user_input [Adapt 2]**":

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

Executar o *External Sync Schedule* "clv.model_export.template.document_item (clv.model_export.template.document_item)" (2020-06-20)
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

Executar o *External Sync Schedule* "clv.model_export.template.lab_test_criterion (clv.model_export.template.lab_test_criterion)" (2020-06-20)
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

Executar o *External Sync Schedule* "clv.model_export (clv.model_export)" (2020-06-20)
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

Criar um backup do banco de dados *CLVhealth-JCAFB-2020-13* (2020-06-20a)
-------------------------------------------------------------------------

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
            pg_dump clvhealth_jcafb_2020_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_13_2020-06-20a.sql

            gzip clvhealth_jcafb_2020_13_2020-06-20a.sql
            pg_dump clvhealth_jcafb_2020_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_13_2020-06-20a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-06-20a.tar.gz clvhealth_jcafb_2020_13

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-06-20a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_13_2020-06-20a.sql
        * /opt/odoo/clvhealth_jcafb_2020_13_2020-06-20a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-06-20a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-06-20a.tar.gz

.. index:: clvhealth_jcafb_2020_13_2020-06-20a.sql
.. index:: clvhealth_jcafb_2020_13_2020-06-20a.sql.gz
.. index:: filestore_clvhealth_jcafb_2020_13_2020-06-20a
.. index:: clvsol_filestore_clvhealth_jcafb_2020_13_2020-06-20a

Restaurar um backup do banco de dados *CLVhealth-JCAFB-2020-13* (2020-06-20a)
-----------------------------------------------------------------------------

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
            # gzip -d clvhealth_jcafb_2020_13_2020-06-20a.sql.gz

            dropdb -i clvhealth_jcafb_2020_13

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020_13
            psql -f clvhealth_jcafb_2020_13_2020-06-20a.sql -d clvhealth_jcafb_2020_13 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020_13
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-06-20a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-06-20a.tar.gz

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

Preparar os "*Global Settings*" para a JCAFB-2020-13 (2020-06-20)
-----------------------------------------------------------------

    #. Acessar a *View* *Global Settings*:

        * Menu de acesso:

            * :bi:`Base` » :bi:`Global Settings` » :bi:`Global Settings`

        #. Configurar o parâmetro :bi:`Phase` » :bi:`Phase`: **JCAFB-2020**

        #. Configurar o parâmetro :bi:`Person` » :bi:`Reference Date`: **31/01/2020**

Atualisar a Idade de Referência para todas as Pessoas (2020-06-20)
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

Executar a Verificação para todos os Endereços (2020-06-20)
-----------------------------------------------------------

    #. [tkl-odoo12-jcafb-ng-vm] Executar a Ação :bi:`Address Verification Execute` para todos os Endereços:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-ng-vm <https://tkl-odoo12-jcafb-ng-vm>`_

        #. Acessar a *View* *Employees*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Addresses`

        #. Selecionar todos os Endereços (**665**)

        #. Exercutar a Ação ":bi:`Address Verification Execute`":

            #. Utilize o botão :bi:`Address Verification Execute` para executar a Ação.

Executar a Verificação para todas as Famílias (2020-06-20)
----------------------------------------------------------

    #. [tkl-odoo12-jcafb-ng-vm] Executar a Ação :bi:`Family Verification Execute` para todos os Famílias:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-ng-vm <https://tkl-odoo12-jcafb-ng-vm>`_

        #. Acessar a *View* *Employees*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Families`

        #. Selecionar todos os Famílias (**441**)

        #. Exercutar a Ação ":bi:`Family Verification Execute`":

            #. Utilize o botão :bi:`Family Verification Execute` para executar a Ação.

Executar a Verificação para todas as Pessoas (2020-06-20)
---------------------------------------------------------

    #. [tkl-odoo12-jcafb-ng-vm] Executar a Ação :bi:`Person Verification Execute` para todos os Pessoas:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-ng-vm <https://tkl-odoo12-jcafb-ng-vm>`_

        #. Acessar a *View* *Employees*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Persons`

        #. Selecionar todos os Pessoas (**1540**)

        #. Exercutar a Ação ":bi:`Person Verification Execute`":

            #. Utilize o botão :bi:`Person Verification Execute` para executar a Ação.

Executar a Verificação para todos os Endereços (Aux) (2020-06-20)
-----------------------------------------------------------------

    #. [tkl-odoo12-jcafb-ng-vm] Executar a Ação :bi:`Address (Aux) Verification Execute` para todos os Endereços (Aux):

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-ng-vm <https://tkl-odoo12-jcafb-ng-vm>`_

        #. Acessar a *View* *Employees*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Auxiliary` » :bi:`Addresses (Aux)`

        #. Selecionar todos os Endereços (Aux) (**202**)

        #. Exercutar a Ação ":bi:`Address (Aux) Verification Execute`":

            #. Utilize o botão :bi:`Address (Aux) Verification Execute` para executar a Ação.

Executar a Verificação para todas as Pessoas (Aux) (2020-06-20)
---------------------------------------------------------------

    #. [tkl-odoo12-jcafb-ng-vm] Executar a Ação :bi:`Person (Aux) Verification Execute` para todos os Pessoas (Aux):

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-ng-vm <https://tkl-odoo12-jcafb-ng-vm>`_

        #. Acessar a *View* *Employees*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Auxiliary` » :bi:`Persons (Aux)`

        #. Selecionar todos os Pessoas (Aux) (**605**)

        #. Exercutar a Ação ":bi:`Person (Aux) Verification Execute`":

            #. Utilize o botão :bi:`Person (Aux) Verification Execute` para executar a Ação.

Criar um backup do banco de dados *CLVhealth-JCAFB-2020-13* (2020-06-20b)
-------------------------------------------------------------------------

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
            pg_dump clvhealth_jcafb_2020_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_13_2020-06-20b.sql

            gzip clvhealth_jcafb_2020_13_2020-06-20b.sql
            pg_dump clvhealth_jcafb_2020_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_13_2020-06-20b.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-06-20b.tar.gz clvhealth_jcafb_2020_13

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-06-20b.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_13_2020-06-20b.sql
        * /opt/odoo/clvhealth_jcafb_2020_13_2020-06-20b.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-06-20b.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-06-20b.tar.gz

.. index:: clvhealth_jcafb_2020_13_2020-06-20b.sql
.. index:: clvhealth_jcafb_2020_13_2020-06-20b.sql.gz
.. index:: filestore_clvhealth_jcafb_2020_13_2020-06-20b
.. index:: clvsol_filestore_clvhealth_jcafb_2020_13_2020-06-20b

:red:`(Não Executado])` Restaurar um backup do banco de dados *CLVhealth-JCAFB-2020-13* (2020-06-20b)
-----------------------------------------------------------------------------------------------------

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
            # gzip -d clvhealth_jcafb_2020_13_2020-06-20b.sql.gz

            dropdb -i clvhealth_jcafb_2020_13

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020_13
            psql -f clvhealth_jcafb_2020_13_2020-06-20b.sql -d clvhealth_jcafb_2020_13 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020_13
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-06-20b.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-06-20b.tar.gz

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

Inicializar o conteúdo do diretório **clvsol_filestore/clvhealth_jcafb** [tkl-odoo13-jcafb20-vm] (2020-06-18)
-------------------------------------------------------------------------------------------------------------

    #. [tkl-odoo13-jcafb20-vm] Criar, manualmente, os diretórios:

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

    #. Copiar, manualmente, a partir do servidor **tkl-odoo13-jcafb-vm** para o servidor **tkl-odoo13-jcafb20-vm**, o conteúdo dos diretórios listados anteriormente.

        * "tkl-odoo13-jcafb-vm:/opt/odoo/clvsol_filestore/clvhealth_jcafb" **->** "tkl-odoo13-jcafb20-vm:/opt/odoo/clvsol_filestore/clvhealth_jcafb"

.. index:: clvsol_filestore
.. index:: clvsol_filestore/clvhealth_jcafb
.. index:: clvsol_filestore/clvhealth_jcafb/export_files
.. index:: clvsol_filestore/clvhealth_jcafb/lab_test_files
.. index:: clvsol_filestore/clvhealth_jcafb/summary_files
.. index:: clvsol_filestore/clvhealth_jcafb/survey_files

Restaurar um backup do banco de dados *CLVhealth-JCAFB-2020-13* (2020-06-20b)
-----------------------------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_restore`.

    #. [tkl-odoo13-jcafb20-vm] Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb20-vm** e paralizar o *Odoo*:

        ::

            # ***** tkl-odoo13-jcafb20-vm
            #

            ssh tkl-odoo13-jcafb20-vm -l root

            /etc/init.d/odoo stop

            su odoo

    #. [tkl-odoo13-jcafb20-vm] Executar os comandos de restauração dos arquivos de backup:

        ::

            # ***** tkl-odoo13-jcafb20-vm
            #

            cd /opt/odoo
            # gzip -d clvhealth_jcafb_2020_13_2020-06-20b.sql.gz

            dropdb -i clvhealth_jcafb_2020_13

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020_13
            psql -f clvhealth_jcafb_2020_13_2020-06-20b.sql -d clvhealth_jcafb_2020_13 -U postgres -h localhost -p 5432 -q

            mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020_13
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-06-20b.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-06-20b.tar.gz

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb20-vm** ao modo desejado:

        ::

            # ***** tkl-odoo13-jcafb20-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    #. [tkl-odoo13-jcafb20-vm] Configurar o parâmetro "**web.base.url**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb20-vm <https://tkl-odoo13-jcafb20-vm>`_

        #. Acessar a *View* **Parâmetros do Sistema**:

            * Menu de acesso:
                
                * **Configurações** » **Técnico** » **Parâmetros** » **Parâmetros do Sistema**

        #. Pesquisar pelo registro com a **Chave** "**web.base.url**"

        #. Editar o registro apresentado (**Chave**: "**web.base.url**")

        #. Alterar o campo **Valor** para:

            * "**http://tkl-odoo13-jcafb20-vm**".

        #. Salvar o registro editado.

:red:`(Não Executado])` Criar os Sumários para todos os Grupos (JCAFB-2020-13) (2020-06-15)
-------------------------------------------------------------------------------------------

    #. [tkl-odoo12-jcafb-ng-vm] Executar a Ação :bi:`Employee Summary Set Up` para todos os Grupos de Campo e Reserva Técnica (JCAFB-2020-13):

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-ng-vm <https://tkl-odoo12-jcafb-ng-vm>`_

        #. Acessar a *View* *Funcionários*:

            * Menu de acesso:

                * :bi:`Funcionários` » :bi:`Employees` » :bi:`Employees`

        #. Selecionar todos os Grupos de Campo (**16**) e Reserva Técnica (**5**)

        #. Exercutar a Ação ":bi:`Employee Summary Set Up`":

            #. Utilize o botão :bi:`Employee Summary Set Up` para executar a Ação.

:red:`(Não Executado])` Criar os Sumários para os Endereços (JCAFB-2020-13) (2020-06-15)
----------------------------------------------------------------------------------------

    #. [tkl-odoo12-jcafb-ng-vm] Executar a Ação :bi:`Address Summary Set Up` para todos os Endereços (JCAFB-2020-13):

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-ng-vm <https://tkl-odoo12-jcafb-ng-vm>`_

        #. Acessar a *View* *Endereços*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Addresses`

        #. Selecionar todos os Endereços (JCAFB-2020-13) *Available* (**210**), *Selected* (**146**) e *Unselected* (**78**)

        #. Exercutar a Ação ":bi:`Address Summary Set Up`":

            #. Utilize o botão :bi:`Address Summary Set Up` para executar a Ação.

:red:`(Não Executado])` Criar os Sumários para as Famílias (JCAFB-2020-13) (2020-06-15)
---------------------------------------------------------------------------------------

    #. [tkl-odoo12-jcafb-ng-vm] Executar a Ação :bi:`Family Summary Set Up` para todos as Famílias (JCAFB-2020-13):

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-ng-vm <https://tkl-odoo12-jcafb-ng-vm>`_

        #. Acessar a *View* *Endereços*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Families`

        #. Selecionar todos as Famílias (JCAFB-2020-13) *Available* (**132**), *Selected* (**148**) e *Unselected* (**82**)

        #. Exercutar a Ação ":bi:`Family Summary Set Up`":

            #. Utilize o botão :bi:`Family Summary Set Up` para executar a Ação.

:red:`(Não Executado])` Criar os Sumários para as Pessoas (JCAFB-2020-13) (2020-06-15)
--------------------------------------------------------------------------------------

    #. [tkl-odoo12-jcafb-ng-vm] Executar a Ação :bi:`Person Summary Set Up` para todos as Pessoas (JCAFB-2020-13):

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-ng-vm <https://tkl-odoo12-jcafb-ng-vm>`_

        #. Acessar a *View* *Endereços*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Persons`

        #. Selecionar todos as Pessoas (JCAFB-2020-13) *Available* (**861**), *Selected* (**191**) e *Unselected* (**127**)

        #. Exercutar a Ação ":bi:`Person Summary Set Up`":

            #. Utilize o botão :bi:`Person Summary Set Up` para executar a Ação.

:red:`(Não Executado])` Criar os Sumários para as Pessoas (Aux) (2020-06-15)
----------------------------------------------------------------------------

    #. [tkl-odoo12-jcafb-ng-vm] Executar a Ação :bi:`Person (Aux) Summary Set Up` para todos as Pessoas (Aux) (JCAFB-2020-13):

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-ng-vm <https://tkl-odoo12-jcafb-ng-vm>`_

        #. Acessar a *View* *Endereços*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Auxiliary` » :bi:`Persons (Aux)`

        #. Selecionar todos as Pessoas (Aux) (JCAFB-2020-13) *Available* (**313**), *Selected* (**197**),  *Unselected* (**50**) e *Waiting* (**7**)

        #. Exercutar a Ação ":bi:`Person (Aux) Summary Set Up`":

            #. Utilize o botão :bi:`Person (Aux) Summary Set Up` para executar a Ação.

.. toctree::   :maxdepth: 2
