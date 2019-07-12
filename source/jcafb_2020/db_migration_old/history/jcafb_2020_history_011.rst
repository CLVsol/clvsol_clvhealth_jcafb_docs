.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

=======================================================================================
[2019-07-10] - Migração do Banco de Dados - JCAFB-2020 - Servidor [tkl-odoo12-jcafb-vm]
=======================================================================================

Restaurar um backup do *CLVhealth-JCAFB-2020* no servidor "tkl-odoo12-jcafb-vm" (2019-07-08a)
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
            # gzip -d clvhealth_jcafb_2020_2019-07-08a.sql.gz

            dropdb -i clvhealth_jcafb_2020

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020
            psql -f clvhealth_jcafb_2020_2019-07-08a.sql -d clvhealth_jcafb_2020 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-07-08a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-07-08a.tar.gz

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo desejado:

        ::

            # ***** tkl-odoo12-jcafb-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

Instalar o(s) módulo(s) [clv_employee_jcafb] (2019-07-11)
---------------------------------------------------------

    * Referência: :doc:`/setup/module_installation`.

    #. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, **desabilitando** o(s) Módulo(s):

        * clv_employee_jcafb

    #. [tkl-odoo12-jcafb-vm] **Executar** a instalação do(s) Módulo(s) adicionado(s)/habilitado(s):

        #. Estabelecer uma sessão ssh (session 1) com o servidor **tkl-odoo12-jcafb-vm** e executar o *Odoo* no modo manual:

            ::

                # ***** tkl-odoo12-jcafb-vm (session 1)
                #

                ssh tkl-odoo12-jcafb-vm -l root

                /etc/init.d/odoo stop

                su odoo
                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

        #. Estabelecer uma sessão ssh (session 2) com o servidor **tkl-odoo12-jcafb-vm** e executar o **install.py**:

            ::

                # ***** tkl-odoo12-jcafb-vm (session 2)
                #

                ssh tkl-odoo12-jcafb-vm -l odoo

                cd /opt/odoo/clvsol_clvhealth_jcafb/project
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020"

            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo desejado:

            ::

                # ***** tkl-odoo12-jcafb-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Excluir todos os *Schedules* do *External Sync Batch* "*Default Batch*" (2019-07-08)
------------------------------------------------------------------------------------

    #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

    #. Excluir todos os *Members* do *External Sync Batch* "*Default Batch*" (**35** *Schedules*):

        * Menu de acesso:
            * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Batches` » :bi:`Default Batch`

            * Lista de *Schedules*:
                * :ref:`Lista de Schedules  20190708a`

Atualizar o(s) módulo(s): [clv_base_sync_jcafb, clv_employee_sync_jcafb] (2019-07-10)
-------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/module_update`.

    #. [tkl-odoo12-jcafb-vm] **Executar** a atualização do(s) Módulo(s): **clv_base_jcafb**

        #. Estabelecer uma sessão ssh (session 1) com o servidor **tkl-odoo12-jcafb-vm** e executar o *Odoo* no modo manual:

            ::

                # ***** tkl-odoo12-jcafb-vm (session 1)
                #

                ssh tkl-odoo12-jcafb-vm -l root

                /etc/init.d/odoo stop

                su odoo
                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

        #. Estabelecer uma sessão ssh (session 2) com o servidor **tkl-odoo12-jcafb-vm** e executar o **install.py**:

            ::

                # ***** tkl-odoo12-jcafb-vm (session 2)
                #

                ssh tkl-odoo12-jcafb-vm -l odoo

                cd /opt/odoo/clvsol_clvhealth_jcafb/project
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" -m clv_base_sync_jcafb
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" -m clv_global_tag_sync_jcafb
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" -m clv_phase_sync_jcafb
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" -m clv_employee_sync_jcafb
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" -m clv_address_sync_jcafb
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" -m clv_address_history_sync_jcafb
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" -m clv_person_sync_jcafb
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" -m clv_person_history_sync_jcafb
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" -m clv_survey_sync_jcafb
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" -m clv_event_sync_jcafb
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" -m clv_document_sync_jcafb
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" -m clv_lab_test_sync_jcafb
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" -m clv_mfile_sync_jcafb
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo padrão:

            ::

                # ***** tkl-odoo12-jcafb-vm (session 1)
                #

                ^C

                exit

                /etc/init.d/odoo start

.. _Lista de Schedules 20190710a:

Lista de *Schedules* instalados (2019-07-10 (a))
------------------------------------------------

    * Lista de *Schedules* instalados:
        * res.country (res.country)
        * res.country.state (res.country.state)
        * res.city (l10n_br_base.city)
        * :green:`(Novo)` res.users (res.users)
        * clv.global_tag (clv.global_tag)
        * clv.phase (clv.history_marker)
        * hr.department (hr.department)
        * hr.job (hr.job)
        * :green:`(Atualizado)` hr.employee (hr.employee)
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

Excluir todos os Funcionários exceto o **Administrador** (2019-07-10)
---------------------------------------------------------------------

    #. [tkl-odoo12-jcafb-vm] Excluir todos os Funcionários exceto o **Administrador**:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Excluir todos os Funcionários exceto o **Administrador** :red:`sem registro de Log` (**191** registros):

            * Menu de acesso:
                * :bi:`Funcionários` » :bi:`Employees` » :bi:`Employees`

    #. [tkl-odoo12-jcafb-vm] Excluir os *External Syncs* referentes ao *Model* "**hr.employee**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Excluir os :bi:`External Syncs` referentes ao *Model* "**hr.employee**" (**191** registros):

            * Menu de acesso:
                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Syncs`

Atualizar a lista de *Object Fields* do *Schedule* "**hr.employee (hr.employee)**" (2019-07-10)
-----------------------------------------------------------------------------------------------

    #. [tkl-odoo12-jcafb-vm] Atualizar a lista de *Object Fields* do *Schedule* "**hr.employee (hr.employee)**":

        :red:`(Implementar a descrição do procedimento)`

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

            * Adicionar os campos:
                * **work_email**
                * **user_id**

Executar o *External Sync Batch* "*Default Batch*" (2019-07-10 (a))
-------------------------------------------------------------------

    #. [tkl-odoo12-jcafb-vm] Configurar o :bi:`External Sync Schedule` "**res.users (res.users)**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit`, os :bi:`External Sync Schedule` "**res.users (res.users)**" e "**hr.employee (hr.employee)**":

            * Lista de *Schedules*:
                * :ref:`Lista de Schedules  20190710a`

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
                * :ref:`Lista de Schedules 20190710a`

            * *Synchronization Log*:
                * :ref:`External Sync Batch - Default Batch - 20190710a`

    #. [tkl-odoo12-jcafb-vm] Configurar os :bi:`External Sync Schedules`:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit`, os :bi:`External Sync Schedules`:

            * Lista de *Schedules*:
            * *Members*:
                * :ref:`Lista de Schedules 20190710a`

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

Criar um backup do *CLVhealth-JCAFB-2020* (2019-07-10a)
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
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-07-10a.sql

            gzip clvhealth_jcafb_2020_2019-07-10a.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-07-10a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-07-10a.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-07-10a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_2019-07-10a.sql
        * /opt/odoo/clvhealth_jcafb_2020_2019-07-10a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2019-07-10a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-07-10a.tar.gz

.. index:: clvhealth_jcafb_2020_2019-07-10a.sql
.. index:: filestore_clvhealth_jcafb_2020_2019-07-10a
.. index:: clvsol_filestore_clvhealth_jcafb_2019-07-10a

.. toctree::
   :maxdepth: 2

   jcafb_2020_history_011_sync_log

