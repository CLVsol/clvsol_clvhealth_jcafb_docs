.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

=======================================================================================
[2019-07-27] - Migração do Banco de Dados - JCAFB-2020 - Servidor [tkl-odoo12-jcafb-vm]
=======================================================================================

Restaurar um backup do *CLVhealth-JCAFB-2020* no servidor "tkl-odoo12-jcafb-vm" (2019-07-27a)
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
            # gzip -d clvhealth_jcafb_2020_2019-07-27a.sql.gz

            dropdb -i clvhealth_jcafb_2020

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020
            psql -f clvhealth_jcafb_2020_2019-07-27a.sql -d clvhealth_jcafb_2020 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-07-27a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-07-27a.tar.gz

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo desejado:

        ::

            # ***** tkl-odoo12-jcafb-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

Executar o *External Sync Batch* "*Default Batch*" (2019-07-27 (a))
-------------------------------------------------------------------

    #. [tkl-odoo12-jcafb-vm] Configurar o :bi:`External Sync Schedule` "**survey.user_input_line (survey.user_input_line)**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit`, o :bi:`External Sync Schedule` "**survey.user_input_line (survey.user_input_line)**":

            * Lista de *Schedules*:
                * :ref:`Lista de Schedules  20190714b`

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
                * :ref:`Lista de Schedules 20190714b`

            * *Synchronization Log*:
                * :ref:`External Sync Batch - Default Batch - 20190727a`

    #. [tkl-odoo12-jcafb-vm] Configurar os :bi:`External Sync Schedules`:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit`, os :bi:`External Sync Schedules`:

            * Lista de *Schedules*:
            * *Members*:
                * :ref:`Lista de Schedules 20190714b`

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

Criar um backup do *CLVhealth-JCAFB-2020* (2019-07-28a)
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
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-07-28a.sql

            gzip clvhealth_jcafb_2020_2019-07-28a.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-07-28a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-07-28a.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-07-28a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_2019-07-28a.sql
        * /opt/odoo/clvhealth_jcafb_2020_2019-07-28a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2019-07-28a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-07-28a.tar.gz

.. index:: clvhealth_jcafb_2020_2019-07-28a.sql
.. index:: filestore_clvhealth_jcafb_2020_2019-07-28a
.. index:: clvsol_filestore_clvhealth_jcafb_2019-07-28a

.. toctree::
   :maxdepth: 2

   jcafb_2020_history_007_sync_log

