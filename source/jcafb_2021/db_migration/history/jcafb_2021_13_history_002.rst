.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .blue {color:blue} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: blue
.. role:: bi

===========================================
Migração do Banco de Dados - JCAFB-2021v-13
===========================================

Inicializar o conteúdo do diretório **clvsol_filestore/clvhealth_jcafb** [tkl-odoo13-jcafb21-vm] (2020-06-21)
-------------------------------------------------------------------------------------------------------------

	#. [tkl-odoo13-jcafb21-vm] Criar, manualmente, os diretórios:

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

	#. Copiar, manualmente, a partir do servidor **tkl-odoo13-jcafb21-vm** para o servidor **tkl-odoo13-jcafb21-vm**, o conteúdo dos diretórios listados anteriormente.

		* "tkl-odoo13-jcafb21-vm:/opt/odoo/clvsol_filestore/clvhealth_jcafb" **->** "tkl-odoo13-jcafb21-vm:/opt/odoo/clvsol_filestore/clvhealth_jcafb"

.. index:: clvsol_filestore
.. index:: clvsol_filestore/clvhealth_jcafb
.. index:: clvsol_filestore/clvhealth_jcafb/export_files
.. index:: clvsol_filestore/clvhealth_jcafb/lab_test_files
.. index:: clvsol_filestore/clvhealth_jcafb/summary_files
.. index:: clvsol_filestore/clvhealth_jcafb/survey_files

Criar uma nova instância do *CLVhealth-JCAFB-2021v-13* (2020-07-11)
-------------------------------------------------------------------

	* **Execution time: 0:09:10.729**

    #. [tkl-odoo13-jcafb21-vm] Estabelecer uma sessão ssh (session 1) com o servidor **tkl-odoo13-jcafb21-vm** e paralizar o *Odoo*:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            ssh tkl-odoo13-jcafb21-vm -l root

            /etc/init.d/odoo stop

            su odoo

    #. [tkl-odoo13-jcafb21-vm] Excluir a instância do *CLVhealth-JCAFB-2021v-13* existente:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            cd /opt/odoo
            dropdb -i clvhealth_jcafb_2021v_13

            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2021v_13

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo manual:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    #. Estabelecer uma sessão ssh (session 2) com o servidor **tkl-odoo13-jcafb21-vm** e executar o **install.py**:

        ::

            # ***** tkl-odoo13-jcafb21-vm (session 2)
            #

            ssh tkl-odoo13-jcafb21-vm -l odoo

            cd /opt/odoo/clvsol_clvhealth_jcafb/project
            
            python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13"
            # Execution time: 0:08:22.364

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo desejado:

        ::

            # ***** tkl-odoo13-jcafb21-vm (session 1)
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

Criar o *External Sync Host* "https://192.168.25.188" (2020-07-11)
------------------------------------------------------------------

    #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

    #. Criar o *External Sync Host* **https://192.168.25.188**:

        * Menu de acesso:
            
            * *External Sync* > *Configuration* > *Hosts* > Criar

        * Parâmetros utilizados:
            
            * External Host Name: "**https://192.168.25.188**"
            * External Database Name: "**clvhealth_jcafb_2020_13**"
            * External User: "**admin**"
            * External User Password: "*******"

Configurar "*Global Settings*" para a *CLVhealth-JCAFB-2020v-13* (2020-07-11)
-----------------------------------------------------------------------------

    #. Acessar a *View* *Global Settings*:

        * Menu de acesso:

            * :bi:`Base` » :bi:`Global Settings` » :bi:`Global Settings`

        #. Configurar o parâmetro :bi:`Person` » :bi:`Reference Date`: **31/01/2020**

.. _Lista de Schedules jcafb_2021v_13_history_002 (1):

Lista de *Schedules* instalados (1) (2020-07-11)
------------------------------------------------

    * Lista de *Schedules* instalados:

        * :blue:`(Enabled - Sync)` res.users [Migration]

        * :blue:`(Enabled - Sync)` res.country (res.country)
        * :blue:`(Enabled - Sync)` res.country.state (res.country.state)
        * :blue:`(Enabled - Sync)` res.city (res.city)

        * :blue:`(Enabled - Sync)` res.users (res.users)

        * :blue:`(Enabled - Sync)` clv.file_system.directory (clv.file_system.directory)

        * :blue:`(Enabled - Sync)` clv.global_tag (clv.global_tag)

        * :blue:`(Enabled - Sync)` clv.phase (clv.phase)

        * :blue:`(Enabled - Sync)` hr.department (hr.department) [rec]
        * :blue:`(Enabled - Sync)` hr.department (hr.department)
        * :blue:`(Enabled - Sync)` hr.job (hr.job)
        * :blue:`(Enabled - Sync)` hr.employee (hr.employee) [rec]
        * :blue:`(Enabled - Sync)` hr.employee (hr.employee)
        * :blue:`(Enabled - Sync)` hr.employee.history (hr.employee.history)

        * :blue:`(Enabled - Sync)` clv.address.category (clv.address.category)
        * :blue:`(Enabled - Sync)` clv.address (clv.address)
        * :blue:`(Enabled - Sync)` clv.address.history (clv.address.history)

        * :blue:`(Enabled - Sync)` clv.address.aux (clv.address.aux)

        * :blue:`(Enabled - Sync)` clv.family.category (clv.family.category)
        * :blue:`(Enabled - Sync)` clv.family (clv.family)
        * :blue:`(Enabled - Sync)` clv.family.history (clv.family.history)

        * :blue:`(Enabled - Sync)` clv.person.category (clv.person.category)
        * :blue:`(Enabled - Sync)` clv.person.marker (clv.person.marker)
        * :blue:`(Enabled - Sync)` clv.person (clv.person)
        * :blue:`(Enabled - Sync)` clv.person.history (clv.person.history)

        * :blue:`(Enabled - Sync)` clv.person.aux (clv.person.aux)

        * :blue:`(Enabled - Sync)` clv.event (clv.event)
        * :blue:`(Enabled - Sync)` clv.event.attendee (clv.event.attendee)

        * :blue:`(Enabled - Sync)` clv.document.category (clv.document.category)
        * :blue:`(Enabled - Sync)` clv.document.type (clv.document.type)
        * :blue:`(Enabled - Sync)` clv.document (clv.document)
        * :blue:`(Enabled - Sync)` clv.document.item (clv.document.item)

        * :blue:`(Enabled - Sync)` clv.lab_test.unit (clv.lab_test.unit)
        * :blue:`(Enabled - Sync)` clv.lab_test.parasite (clv.lab_test.parasite)
        * :blue:`(Enabled - Sync)` clv.lab_test.crystal (clv.lab_test.crystal)
        * :blue:`(Enabled - Sync)` clv.lab_test.type (clv.lab_test.type)
        * :blue:`(Enabled - Sync)` clv.lab_test.request (clv.lab_test.request)
        * :blue:`(Enabled - Sync)` clv.lab_test.result (clv.lab_test.result)
        * :blue:`(Enabled - Sync)` clv.lab_test.report (clv.lab_test.report)
        * :blue:`(Enabled - Sync)` clv.lab_test.result (clv.lab_test.result) [2]
        * :blue:`(Enabled - Sync)` clv.lab_test.criterion (clv.lab_test.criterion)

        * :blue:`(Enabled - Sync)` survey.survey (survey.survey)
        * :blue:`(Enabled - Sync)` survey.question (survey.question)
        * :blue:`(Enabled - Sync)` survey.label (survey.label)
        * :blue:`(Enabled - Sync)` survey.user_input (survey.user_input)
        * :blue:`(Enabled - Sync)` clv.document (clv.document) [2]
        * :blue:`(Enabled - Sync)` survey.user_input_line (survey.user_input_line)

        * :blue:`(Enabled - Sync)` clv.partner_entity.street_pattern (clv.partner_entity.street_pattern)

        * :blue:`(Enabled - Sync)` clv.verification.marker (clv.verification.marker)

        * :blue:`(Enabled - Sync)` clv.set (clv.set)
        * :blue:`(Enabled - Sync)` clv.set.element (clv.set.element)

        * :blue:`(Enabled - Sync)` ir.model (ir.model)
        * :blue:`(Enabled - Sync)` ir.model.fields (ir.model.fields)

        * :blue:`(Enabled - Sync)` clv.model_export.template (clv.model_export.template)
        * :blue:`(Enabled - Sync)` clv.model_export.template.field (clv.model_export.template.field)
        * :blue:`(Enabled - Sync)` clv.model_export.template.document_item (clv.model_export.template.document_item)
        * :blue:`(Enabled - Sync)` clv.model_export.template.lab_test_criterion (clv.model_export.template.lab_test_criterion)
        * :blue:`(Enabled - Sync)` clv.model_export (clv.model_export)

        * :blue:`(Enabled - Sync)` clv.person_sel.age_group (clv.person_sel.age_group
        * :blue:`(Enabled - Sync)` clv.person_sel.district (clv.person_sel.district)
        * :blue:`(Enabled - Sync)` clv.person_sel.group (clv.person_sel.group)
        * :blue:`(Enabled - Sync)` clv.person_sel.summary (clv.person_sel.summary)

Executar o *External Sync Batch* "*Default Batch*" (1) (2020-07-11)
-------------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Configurar todos os :bi:`External Sync Schedules`:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit (2)`, todos os :bi:`External Sync Schedules`:

            * Menu de acesso:
                
                * :bi:`External Sync` » :bi:`Confituration` » :bi:`External Sync` » :bi:`Batch Members` » **Ação** » :bi:`External Sync Schedule Mass Edit (2)`

            * Parâmetros alterados:
                
                * *External Host*: "**https://192.168.25.188**"
                * *Max Task Registers*: "**250.000**"

    #. Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb21-vm** e executar o *Odoo* no modo manual:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            ssh tkl-odoo13-jcafb21-vm -l root

            /etc/init.d/odoo stop

            su odoo

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    #. [tkl-odoo13-jcafb21-vm] Executar o :bi:`External Sync Batch` "**Default Batch**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Executar a ação :bi:`External Sync Batch Exec` para o "**Default Batch**":

            * Menu de acesso:
                
                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Batches` » **Ação** » :bi:`External Sync Batch Exec`

            * :bi:`Execution time: 6:39:26.588`

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo padrão:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            ^C

            exit

            /etc/init.d/odoo start

Atualizar o "*Global Settings*" para a *CLVhealth-JCAFB-2021v-13* (2020-07-11)
------------------------------------------------------------------------------

    #. Acessar a *View* *Global Settings*:

        * Menu de acesso:

            * :bi:`Base` » :bi:`Global Settings` » :bi:`Global Settings`

        #. Configurar o parâmetro :bi:`Phase` » :bi:`Phase`: **JCAFB-2020**

Executar o *Verification Batch* "*Default Batch*" (2020-07-11)
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

            * :bi:`Execution time: 0:16:48.623`

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo padrão:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            ^C

            exit

            /etc/init.d/odoo start

Marcar o *Active Log* de todos os Objetos (2020-07-11)
------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Global Log Client Mass Edit` para todos os Objetos:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Global Log Clients*:

            * Menu de acesso:

                * :bi:`Base` » :bi:`Global Logs` » :bi:`Global Log Clients`

        #. Selecionar todos os :bi:`Global Log Clients` (**43**)

        #. Executar a Ação ":bi:`Global Log Client Mass Edit`":

            * Parâmetros utilizados:

                * *Active Log*: **Set** **marcado**

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

.. toctree::   :maxdepth: 2
