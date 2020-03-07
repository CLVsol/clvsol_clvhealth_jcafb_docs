.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

==================================================================================================
[2020-03-(05-07)] - Migração do Banco de Dados - JCAFB-2020-NG - Servidor [tkl-odoo12-jcafb-ng-vm]
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

	#. Copiar, manualmente, a partir do servidor **tkl-odoo12-jcafb-vm** para o servidor **tkl-odoo12-jcafb-ng-vm**, o conteúdo dos diretórios listados anteriormente.

		* "tkl-odoo12-jcafb-vm:/opt/odoo/clvsol_filestore/clvhealth_jcafb" **->** "tkl-odoo12-jcafb-ng-vm:/opt/odoo/clvsol_filestore/clvhealth_jcafb"

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

Criar um backup do *CLVhealth-JCAFB-2020_NG* (2020-03-07a)
----------------------------------------------------------

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
	        tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng-03-05a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_ng-03-05a.tar.gz

.. index:: clvhealth_jcafb_2020_ng_2020-03-07a.sql
.. index:: filestore_clvhealth_jcafb_2020_ng_2020-03-07a
.. index:: clvsol_filestore_clvhealth_jcafb_2020_ng-03-05a
