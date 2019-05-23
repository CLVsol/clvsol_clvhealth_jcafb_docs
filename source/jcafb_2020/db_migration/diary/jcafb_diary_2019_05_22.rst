.. raw:: html

    <style> .red {color:red} </style>

.. role:: red

===============
2019-05-(22-23)
===============

Restaurar um backup do *CLVhealth-JCAFB-2020* (2019-05-21a)
-----------------------------------------------------------

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
	        # gzip -d clvhealth_jcafb_2020_2019-05-21a.sql.gz

	        dropdb -i clvhealth_jcafb_2020

	        createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020
	        psql -f clvhealth_jcafb_2020_2019-05-21a.sql -d clvhealth_jcafb_2020 -U postgres -h localhost -p 5432 -q

	        # mkdir /var/lib/odoo/.local/share/Odoo/filestore
	        cd /var/lib/odoo/.local/share/Odoo/filestore
	        rm -rf clvhealth_jcafb_2020
	        tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-05-21a.tar.gz

	        # mkdir /opt/odoo/clvsol_filestore
	        cd /opt/odoo/clvsol_filestore
	        rm -rf clvhealth_jcafb
	        tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-05-21a.tar.gz

	#. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo desejado:

	    ::

	        # ***** tkl-odoo12-jcafb-vm
	        #

	        cd /opt/odoo
	        /usr/bin/odoo -c /etc/odoo/odoo-man.conf

	        ^C

	        exit

	        /etc/init.d/odoo start

Instalar o módulo "contacts"
----------------------------

	* Referência: :doc:`/setup/module_installation`.

    #. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, habilitando o(s) Módulo(s):

    	* contacts

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

Migrar os Usuários do *CLVhealth-JCAFB-2019* para o *CLVhealth-JCAFB-2020*
--------------------------------------------------------------------------

	    #. Estabelecer uma sessão ssh com o servidor **tkl-odoo12-jcafb-vm** e executar o **res_users_migration.py**, acessando o servidor **tkl-odoo10-jcafb-vm** [base de dados **clvhealth_jcafb_2019**]:

		    ::

		        # ***** tkl-odoo12-jcafb-vm (session 2)
		        #

		        ssh tkl-odoo12-jcafb-vm -l odoo

		        cd /opt/odoo/clvsol_clvhealth_jcafb/project
		        
		        python3 res_users_migration.py --rserver "https://192.168.25.152" --radmin_pw "***" --rdb "clvhealth_jcafb_2019" --lserver "https://192.168.25.183" --ladmin_pw "***" --ldb "clvhealth_jcafb_2020"
	        
Criar um backup do *CLVhealth-JCAFB-2020* (2019-05-23a)
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
	        pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-05-23a.sql

	        gzip clvhealth_jcafb_2020_2019-05-23a.sql
	        pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > <clvhealth_jcafb_2020_2019-05-23a.sql

	        cd /var/lib/odoo/.local/share/Odoo/filestore
	        tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-05-23a.tar.gz clvhealth_jcafb_2020

	        cd /opt/odoo/clvsol_filestore
	        tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-05-23a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_2019-05-23a.sql
        * /opt/odoo/clvhealth_jcafb_2020_2019-05-23a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2019-05-23a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-05-23a.tar.gz

.. index:: clvhealth_jcafb_2020_2019-05-23a.sql
.. index:: filestore_clvhealth_jcafb_2020_2019-05-23a
.. index:: clvsol_filestore_clvhealth_jcafb_2019-05-23a
