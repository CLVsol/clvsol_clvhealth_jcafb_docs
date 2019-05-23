.. raw:: html

    <style> .red {color:red} </style>

.. role:: red

==========
2019-05-24
==========

Restaurar um backup do *CLVhealth-JCAFB-2020* (2019-05-23a)
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
	        # gzip -d clvhealth_jcafb_2020_2019-05-23a.sql.gz

	        dropdb -i clvhealth_jcafb_2020

	        createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020
	        psql -f clvhealth_jcafb_2020_2019-05-23a.sql -d clvhealth_jcafb_2020 -U postgres -h localhost -p 5432 -q

	        # mkdir /var/lib/odoo/.local/share/Odoo/filestore
	        cd /var/lib/odoo/.local/share/Odoo/filestore
	        rm -rf clvhealth_jcafb_2020
	        tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-05-23a.tar.gz

	        # mkdir /opt/odoo/clvsol_filestore
	        cd /opt/odoo/clvsol_filestore
	        rm -rf clvhealth_jcafb
	        tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-05-23a.tar.gz

	#. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo desejado:

	    ::

	        # ***** tkl-odoo12-jcafb-vm
	        #

	        cd /opt/odoo
	        /usr/bin/odoo -c /etc/odoo/odoo-man.conf

	        ^C

	        exit

	        /etc/init.d/odoo start

Instalar os módulos "l10n_br_base", "l10n_br_zip" e "l10n_br_zip_correios"
--------------------------------------------------------------------------

	* Referência: :doc:`/setup/module_installation`.

    #. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, habilitando o(s) Módulo(s):

    	* l10n_br_base
    	* l10n_br_zip
    	* l10n_br_zip_correios

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
