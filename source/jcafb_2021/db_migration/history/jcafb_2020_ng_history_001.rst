.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

==================================================================================================
[2020-03-(05-08)] - Migração do Banco de Dados - JCAFB-2020-NG - Servidor [tkl-odoo12-jcafb-ng-vm]
==================================================================================================

Inicializar o conteúdo do diretório **clvsol_filestore/clvhealth_jcafb**
------------------------------------------------------------------------

	#. [tkl-odoo12-jcafb-ng-vm] Criar, manualmente, os diretórios:

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

	#. Copiar, manualmente, a partir do servidor **tkl-odoo12-jcafb-ng-vm** para o servidor **tkl-odoo12-jcafb-ng-vm**, o conteúdo dos diretórios listados anteriormente.

		* "tkl-odoo12-jcafb-ng-vm:/opt/odoo/clvsol_filestore/clvhealth_jcafb" **->** "tkl-odoo12-jcafb-ng-vm:/opt/odoo/clvsol_filestore/clvhealth_jcafb"

.. index:: clvsol_filestore
.. index:: clvsol_filestore/clvhealth_jcafb
.. index:: clvsol_filestore/clvhealth_jcafb/export_files
.. index:: clvsol_filestore/clvhealth_jcafb/lab_test_files
.. index:: clvsol_filestore/clvhealth_jcafb/summary_files
.. index:: clvsol_filestore/clvhealth_jcafb/survey_files

Atualizar o Odoo (2020-03-05)
-----------------------------

	#. [tkl-odoo12-jcafb-ng-vm] Upgrade the server software:

	    ::

	        ssh tkl-odoo12-jcafb-ng-vm -l root

	    ::

	        apt-get update
	        apt-get -y upgrade

	    ::

	        exit

Atualizar o `OCA/l10n-brazil <https://github.com/OCA/l10n-brazil>`_ (2020-03-05)
--------------------------------------------------------------------------------

	#. [tkl-odoo12-jcafb-ng-vm] To install "**OCA/l10n-brazil**", use the following commands (as odoo):

	    ::

	        ssh tkl-odoo12-jcafb-ng-vm -l odoo

	    ::

	        cd /opt/odoo/oca_l10n-brazil
	        git pull

	    ::

	        exit

Criar uma nova instância do *CLVhealth-JCAFB-2020-NG* (2020-03-07)
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
            dropdb -i clvhealth_jcafb_2020-ng

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
        
    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-ng-vm** ao modo desejado:

        ::

            # ***** tkl-odoo12-jcafb-ng-vm (session 1)
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

Criar um backup do banco de dados *CLVhealth-JCAFB-2020_NG* (2020-03-07a)
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
	        pg_dump clvhealth_jcafb_2020_ng -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_ng_2020-03-07a.sql

	        gzip clvhealth_jcafb_2020_ng_2020-03-07a.sql
	        pg_dump clvhealth_jcafb_2020_ng -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_ng_2020-03-07a.sql

	        cd /var/lib/odoo/.local/share/Odoo/filestore
	        tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-03-07a.tar.gz clvhealth_jcafb_2020_ng

	        cd /opt/odoo/clvsol_filestore
	        tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-03-07a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_ng_2020-03-07a.sql
        * /opt/odoo/clvhealth_jcafb_2020_ng_2020-03-07a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-03-07a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-03-07a.tar.gz

.. index:: clvhealth_jcafb_2020_ng_2020-03-07a.sql
.. index:: filestore_clvhealth_jcafb_2020_ng_2020-03-07a
.. index:: clvsol_filestore_clvhealth_jcafb_2020_ng_2020-03-07a

Restaurar um backup do banco de dados *CLVhealth-JCAFB-2020-NG* (2020-03-07a)
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
            # gzip -d clvhealth_jcafb_2020_ng_2020-03-07a.sql.gz

            dropdb -i clvhealth_jcafb_2020_ng

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020_ng
            psql -f clvhealth_jcafb_2020_ng_2020-03-07a.sql -d clvhealth_jcafb_2020_ng -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020_ng
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-03-07a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-03-07a.tar.gz

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

Migrar os Usuários de **clvhealth_jcafb_2020** para **clvhealth_jcafb_2020_ng** (2020-03-08)
--------------------------------------------------------------------------------------------

    #. Estabelecer uma sessão ssh com o servidor **tkl-odoo12-jcafb-ng-vm** e executar o **res_users_migration.py**, acessando o servidor **tkl-odoo12-jcafb-ng-vm** [base de dados **clvhealth_jcafb_2020**]:

        ::

            # ***** tkl-odoo12-jcafb-ng-vm (session 2)
            #

            ssh tkl-odoo12-jcafb-ng-vm -l odoo

            cd /opt/odoo/clvsol_clvhealth_jcafb/project
            
            python3 res_users_migration.py --rserver "https://192.168.25.183" --radmin_pw "***" --rdb "clvhealth_jcafb_2020" --lserver "https://192.168.25.186" --ladmin_pw "***" --ldb "clvhealth_jcafb_2020_ng"

     #. Os "passwords" não foram migrados.
        
Criar o *External Sync Host* "https://192.168.25.183" (2020-03-08)
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

Instalar o(s) módulo(s) [ver lista] (2020-03-08)
------------------------------------------------

    * Referência: :doc:`/setup/module_installation`.

    #. [tkl-odoo12-jcafb-ng-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, **habilitando** o(s) Módulo(s):

        * clv_base_sync_jcafb
        * clv_global_tag_sync_jcafb
        * clv_phase_sync_jcafb
        * clv_employee_sync_jcafb
        * clv_employee_history_sync_jcafb
        * clv_address_sync_jcafb
        * clv_address_history_sync_jcafb

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

            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-ng-vm** ao modo desejado:

            ::

                # ***** tkl-odoo12-jcafb-ng-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

.. _Lista de Schedules 20200308:

Lista de *Schedules* instalados (2020-03-08)
--------------------------------------------

    * Lista de *Schedules* instalados:

        * :green:`(Novo)` res.country (res.country)
        * :green:`(Novo)` res.country.state (res.country.state)
        * :green:`(Novo)` res.city (res.city)

        * :green:`(Novo)` res.users (res.users)

        * :green:`(Novo)` clv.global_tag (clv.global_tag)

        * :green:`(Novo)` clv.phase (clv.phase)

        * :green:`(Novo)` hr.department (hr.department)
        * :green:`(Novo)` hr.job (hr.job)
        * :green:`(Novo)` hr.employee (hr.employee)
        * :green:`(Novo)` hr.employee.history (hr.employee.history)

        * :green:`(Novo)` clv.address.category (clv.address.category)
        * :green:`(Novo)` clv.address (clv.address)
        * :green:`(Novo)` clv.address.history (clv.address.history)

Executar o *External Sync Batch* "*Default Batch*" (2020-03-08)
---------------------------------------------------------------

    #. [tkl-odoo12-jcafb-ng-vm] Configurar os :bi:`External Sync Schedules` :green:`Novos`:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-ng-vm <https://tkl-odoo12-jcafb-ng-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit`, os :bi:`External Sync Schedules` :green:`Novos`:

            * Lista de *Schedules*:
                
                * :ref:`Lista de Schedules 20200308`

            * Menu de acesso:
                
                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Schedules` » **Ação** » :bi:`External Sync Schedule Mass Edit`

            * Parâmetros alterados:
                
                * *External Host*: "**https://192.168.25.183**"
                * *Max Task Registers*: "**10.000**"

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
                
                * :ref:`Lista de Schedules 20200308`

            * *Synchronization Log*:
                
                * :ref:`External Sync Batch - Default Batch - 20200308`

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-ng-vm** ao modo padrão:

        ::

            # ***** tkl-odoo12-jcafb-ng-vm
            #

            ^C

            exit

            /etc/init.d/odoo start

Criar um backup do banco de dados *CLVhealth-JCAFB-2020_NG* (2020-03-08a)
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
	        pg_dump clvhealth_jcafb_2020_ng -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_ng_2020-03-08a.sql

	        gzip clvhealth_jcafb_2020_ng_2020-03-08a.sql
	        pg_dump clvhealth_jcafb_2020_ng -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_ng_2020-03-08a.sql

	        cd /var/lib/odoo/.local/share/Odoo/filestore
	        tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-03-08a.tar.gz clvhealth_jcafb_2020_ng

	        cd /opt/odoo/clvsol_filestore
	        tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-03-08a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_ng_2020-03-08a.sql
        * /opt/odoo/clvhealth_jcafb_2020_ng_2020-03-08a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_ng_2020-03-08a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng_2020-03-08a.tar.gz

.. index:: clvhealth_jcafb_2020_ng_2020-03-08a.sql
.. index:: filestore_clvhealth_jcafb_2020_ng_2020-03-08a
.. index:: clvsol_filestore_clvhealth_jcafb_2020_ng_2020-03-08a

.. toctree::
   :maxdepth: 2

   jcafb_2020_ng_history_001_sync_log
