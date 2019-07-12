.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

===========================================================================================
[2019-07-08 (a)] - Migração do Banco de Dados - JCAFB-2020 - Servidor [tkl-odoo12-jcafb-vm]
===========================================================================================

Restaurar um backup do *CLVhealth-JCAFB-2020* no servidor "tkl-odoo12-jcafb-vm" (2019-07-07e)
---------------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_restore`.

    #. [tkl-odoo12-jcafb-vm] Estabelecer uma sessão ssh com o servidor **tkl-odoo12-jcafb-vm** e paralizar o *Odoo*:

        ::

            # ***** tkl-odoo12-jcafb-vm
            #

            ssh tkl-odoo12-jcafb-vm -l root

            /etc/init.d/odoo stop

            su odoo

    #. [tkl-odoo12-jcafb-vm] Executar os comandos de restauração dos arquivos de backup:

        ::

            # ***** tkl-odoo12-jcafb-vm
            #

            cd /opt/odoo
            # gzip -d clvhealth_jcafb_2020_2019-07-07e.sql.gz

            dropdb -i clvhealth_jcafb_2020

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020
            psql -f clvhealth_jcafb_2020_2019-07-07e.sql -d clvhealth_jcafb_2020 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-07-07e.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-07-07e.tar.gz

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo desejado:

        ::

            # ***** tkl-odoo12-jcafb-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

Executar o *External Sync Batch* "*Default Batch*" (2019-07-08 (a))
-------------------------------------------------------------------

    #. [tkl-odoo12-jcafb-vm] Configurar o :bi:`External Sync Schedule` "**clv.lab_test.criterion (clv.lab_test.criterion)**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit`, o :bi:`External Sync Schedule` "**clv.lab_test.criterion (clv.lab_test.criterion)**":

            * Lista de *Schedules*:
                * :ref:`Lista de Schedules  20190707b`

            * Menu de acesso:
                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Schedules` » **Ação** » :bi:`External Sync Schedule Mass Edit`

            * Parâmetros alterados:
                * *External Host*: "**https://192.168.25.152**"
                * *Max Task Registers*: "**200.000**"
                * *Disable Identification*: "**desmarcado**"

    #. Estabelecer uma sessão ssh com o servidor **tkl-odoo12-jcafb-vm** e executar o *Odoo* no modo manual:

        ::

            # ***** tkl-odoo12-jcafb-vm
            #

            ssh tkl-odoo12-jcafb-vm -l root

            /etc/init.d/odoo stop

            su odoo

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    #. [tkl-odoo12-jcafb-vm] Executar o :bi:`External Sync Batch` "**Default Batch**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Executar a ação :bi:`External Sync Batch Exec` para o "**Default Batch**":

            * Menu de acesso:
                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Batches` » **Ação** » :bi:`External Sync Batch Exec`

            * *Members*:
                * :ref:`Lista de Schedules 20190707b`

            * *Synchronization Log*:
                * :ref:`External Sync Batch - Default Batch - 20190708a`

    #. [tkl-odoo12-jcafb-vm] Configurar os :bi:`External Sync Schedules`:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit`, os :bi:`External Sync Schedules`:

            * Lista de *Schedules*:
            * *Members*:
                * :ref:`Lista de Schedules 20190707b`

            * Menu de acesso:
                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Schedules` » **Ação** » :bi:`External Sync Schedule Mass Edit`

            * Parâmetros alterados:
                * *Disable Identification*: "**marcado**"

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo padrão:

        ::

            # ***** tkl-odoo12-jcafb-vm
            #                * *Disable Identification*: "**marcado**"


            ^C

            exit

            /etc/init.d/odoo start

.. _Lista de Schedules 20190708a:

Lista de *Schedules* instalados (2019-07-08 (a))
------------------------------------------------

    * Lista de *Schedules* instalados:
        * res.country (res.country)
        * res.country.state (res.country.state)
        * res.city (l10n_br_base.city)
        * clv.global_tag (clv.global_tag)
        * clv.phase (clv.history_marker)
        * hr.department (hr.department)
        * hr.job (hr.job)
        * hr.employee (hr.employee)
        * clv.address.category (clv.address.category)
        * clv.address (clv.address)
        * clv.address.history (clv.address.history)
        * clv.person.category (clv.person.category)
        * clv.person.marker (clv.person.marker)
        * clv.person (clv.person)
        * clv.person.history (clv.person.history)

        * survey.stage (survey.stage)
        * survey.survey (survey.survey)
        * survey.page (survey.page)
        * survey.question (survey.question)
        * survey.question (survey.question)
        * survey.user_input (survey.user_input)
        * survey.user_input_line (survey.user_input_line)

        * clv.event (clv.event)
        * clv.event.attendee (clv.event.attendee)

        * clv.document.category (clv.document.category)
        * clv.document.type (clv.document.type)
        * clv.document (clv.document)
        * clv.document.item (clv.document.item)

        * clv.lab_test.unit (clv.lab_test.unit)
        * clv.lab_test.type (clv.lab_test.type)
        * clv.lab_test.request (clv.lab_test.request)
        * clv.lab_test.result (clv.lab_test.result)
        * clv.lab_test.report (clv.lab_test.report)
        * clv.lab_test.criterion (clv.lab_test.criterion)

        * clv.mfile (clv.mfile)

Criar um backup do *CLVhealth-JCAFB-2020* (2019-07-08a)
-------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_backup`.

    #. [tkl-odoo12-jcafb-vm] Estabelecer uma sessão ssh com o servidor **tkl-odoo12-jcafb-vm** e paralizar o *Odoo*:

        ::

            # ***** tkl-odoo12-jcafb-vm
            #

            ssh tkl-odoo12-jcafb-vm -l root

            /etc/init.d/odoo stop

            su odoo

    #. [tkl-odoo12-jcafb-vm] Executar os comandos de criação dos arquivos de backup:

        ::

            # ***** tkl-odoo12-jcafb-vm
            #
            # data_dir = /var/lib/odoo/.local/share/Odoo
            #

            cd /opt/odoo
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-07-08a.sql

            gzip clvhealth_jcafb_2020_2019-07-08a.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-07-08a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-07-08a.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-07-08a.tar.gz clvhealth_jcafb

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo desejado:

        ::

            # ***** tkl-odoo12-jcafb-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    Criados os seguintes arquivos:
        * /opt/odoo/clvhealth_jcafb_2020_2019-07-08a.sql
        * /opt/odoo/clvhealth_jcafb_2020_2019-07-08a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2019-07-08a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-07-08a.tar.gz

.. index:: clvhealth_jcafb_2020_2019-07-08a.sql
.. index:: filestore_clvhealth_jcafb_2020_2019-07-08a
.. index:: clvsol_filestore_clvhealth_jcafb_2019-07-08a

.. toctree::
   :maxdepth: 2

   jcafb_2020_history_010_sync_log

