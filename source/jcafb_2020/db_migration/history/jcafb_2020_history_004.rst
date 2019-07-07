.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

===========================================================================================
[2019-07-06 (c)] - Migração do Banco de Dados - JCAFB-2020 - Servidor [tkl-odoo12-jcafb-vm]
===========================================================================================

Restaurar um backup do *CLVhealth-JCAFB-2020* no servidor "tkl-odoo12-jcafb-vm" (2019-07-06b)
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
            # gzip -d clvhealth_jcafb_2020_2019-07-06b.sql.gz

            dropdb -i clvhealth_jcafb_2020

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020
            psql -f clvhealth_jcafb_2020_2019-07-06b.sql -d clvhealth_jcafb_2020 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-07-06b.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-07-06b.tar.gz

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo desejado:

        ::

            # ***** tkl-odoo12-jcafb-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

Instalar o(s) módulo(s) [ver lista de módulos] (2019-07-06 (c))
---------------------------------------------------------------

    * Referência: :doc:`/setup/module_installation`.

    #. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, habilitando o(s) Módulo(s):

        * clv_survey
        * clv_survey_history
        * :red:`(Não instalado)` clv_survey_sync_jcafb

    #. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, habilitando o(s) Módulo(s):

        * clv_event
        * clv_event_history
        * clv_event_jcafb
        * :red:`(Não instalado)` clv_event_sync_jcafb

    #. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, habilitando o(s) Módulo(s):

        * clv_community
        * clv_community_jcafb

    #. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, habilitando o(s) Módulo(s):

        * clv_document
        * clv_document_history
        * clv_document_jcafb
        * :red:`(Não instalado)` clv_document_sync_jcafb

    #. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, habilitando o(s) Módulo(s):

        * clv_lab_test
        * clv_lab_test_history
        * clv_lab_test_jcafb
        * :red:`(Não instalado)` clv_lab_test_sync_jcafb

    #. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, habilitando o(s) Módulo(s):

        * clv_partner_entity
        * clv_partner_entity_l10n_br
        * clv_address
        * clv_address_history
        * clv_address_l10n_br
        * clv_address_jcafb
        * clv_address_history_jcafb,
        * clv_address_sync_jcafb
        * clv_address_history_sync_jcafb

    #. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, habilitando o(s) Módulo(s):

        * clv_family
        * clv_family_history
        * clv_family_l10n_br
        * clv_family_jcafb
        * clv_family_history_jcafb

    #. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, habilitando o(s) Módulo(s):

        * clv_person
        * clv_person_history
        * clv_person_l10n_br
        * clv_person_jcafb
        * clv_person_history_jcafb
        * clv_person_sync_jcafb
        * clv_person_history_sync_jcafb

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

.. _Lista de Schedules 20190706c:

Lista de *Schedules* instalados (2019-07-06 (c))
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

Executar o *External Sync Batch* "*Default Batch*" (2019-07-06 (c))
-------------------------------------------------------------------

    #. [tkl-odoo12-jcafb-vm] Configurar os :bi:`External Sync Schedules` novos:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit`, os :bi:`External Sync Schedules` novos:

            * Lista de *Schedules*:
                * :ref:`Lista de Schedules 20190706c`

            * Menu de acesso:
                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Schedules` » **Ação** » :bi:`External Sync Schedule Mass Edit`

            * Parâmetros alterados:
                * *External Host*: "**https://192.168.25.152**"
                * *Max Task Registers*: "**200.000**"

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
                * :ref:`Lista de Schedules 20190706c`

            * *Synchronization Log*:
                * :ref:`External Sync Batch - Default Batch - 20190706c`

    #. [tkl-odoo12-jcafb-vm] Configurar os :bi:`External Sync Schedules` novos:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit`, os :bi:`External Sync Schedules` novos:

            * Lista de *Schedules*:
            * *Members*:
                * :ref:`Lista de Schedules 20190706c`

            * Menu de acesso:
                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Schedules` » **Ação** » :bi:`External Sync Schedule Mass Edit`

            * Parâmetros alterados:
                * *Disable Identification*: "**marcado**"

    #. [tkl-odoo12-jcafb-vm] Executar o :bi:`External Sync Batch` "**Default Batch**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Executar a ação :bi:`External Sync Batch Exec` para o "**Default Batch**":

            * Menu de acesso:
                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Batches` » **Ação** » :bi:`External Sync Batch Exec`

            * *Members*:
                * :ref:`Lista de Schedules 20190706c`

            * *Synchronization Log*:
                * :ref:`External Sync Batch - Default Batch - 20190706d`

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo padrão:

        ::

            # ***** tkl-odoo12-jcafb-vm
            #

            ^C

            exit

            /etc/init.d/odoo start

Criar um backup do *CLVhealth-JCAFB-2020* (2019-07-06c)
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
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-07-06c.sql

            gzip clvhealth_jcafb_2020_2019-07-06c.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-07-06c.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-07-06c.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-07-06c.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_2019-07-06c.sql
        * /opt/odoo/clvhealth_jcafb_2020_2019-07-06c.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2019-07-06c.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-07-06c.tar.gz

.. index:: clvhealth_jcafb_2020_2019-07-06c.sql
.. index:: filestore_clvhealth_jcafb_2020_2019-07-06c
.. index:: clvsol_filestore_clvhealth_jcafb_2019-07-06c

.. toctree::
   :maxdepth: 2

   jcafb_2020_history_004_sync_log

