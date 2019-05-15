.. raw:: html

    <style> .red {color:red} </style>

.. role:: red

===============
2019-05-(14-15)
===============

Inicializar o conteúdo do **clvsol_filestore/clvhealth_jcafb**
--------------------------------------------------------------

Criar uma nova instância (**vazia**) do *CLVhealth-JCAFB-2020*
--------------------------------------------------------------

	* Nenhum módulo será instalado nesta nova instância do *CLVhealth-JCAFB*

	* Referência: "Preparação do Banco de Dados", :ref:`Preparação do Banco de Dados (Procedimento 1)`.

	#. [tkl-odoo12-jcafb-vm] Criar, manualmente, o Banco de Dados **clvhealth_jcafb_2020**:

	    #. Estabelecer uma sessão ssh com o servidor **tkl-odoo12-jcafb-vm** e executar o *Odoo* no modo manual:

	    	::

		        # ***** tkl-odoo12-jcafb-vm
		        #

		        ssh tkl-odoo12-jcafb-vm -l root

		        /etc/init.d/odoo stop

		        su odoo

		        cd /opt/odoo
		        /usr/bin/odoo -c /etc/odoo/odoo-man.conf

	    #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

	    #. Criar o Banco de Dados **clvhealth_jcafb_2020**:

	    	* Database Name: **clvhealth_jcafb_2020**
	    	* Email: **admin**
	    	* Language: **Portuguese (BR)/ Português (BR)**
	    	* Country: **Brazil**

	    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo padrão:

		    ::

		        # ***** tkl-odoo12-jcafb-vm
		        #

		        ^C

		        exit

		        /etc/init.d/odoo start

	#. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, desabilitando a instalação de todos os módulos do projeto.

	#. [tkl-odoo12-jcafb-vm] Executar pela primeira vez o **install.py**:

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
	        
	    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo padrão:

		    ::

		        # ***** tkl-odoo12-jcafb-vm (session 1)
		        #

		        ^C

		        exit

		        /etc/init.d/odoo start

Criar um backup do *CLVhealth-JCAFB-2020* (2019-05-15a)
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
	        pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-05-15a.sql

	        gzip clvhealth_jcafb_2020_2019-05-15a.sql
	        pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > <clvhealth_jcafb_2020_2019-05-15a.sql

	        cd /var/lib/odoo/.local/share/Odoo/filestore
	        tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-05-15a.tar.gz clvhealth_jcafb_2020

	        cd /opt/odoo/clvsol_filestore
	        tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-05-15a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_2019-05-15a.sql
        * /opt/odoo/clvhealth_jcafb_2020_2019-05-15a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2019-05-15atar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-05-15a.tar.gz

Restaurar um backup do *CLVhealth-JCAFB-2020* (2019-05-15a)
-----------------------------------------------------------

Migrar os Usuários do *CLVhealth-JCAFB-2020* para o *CLVhealth-JCAFB-2020*
--------------------------------------------------------------------------

Criar um backup do *CLVhealth-JCAFB-2020* (2019-05-15b)
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
	        pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-05-15b.sql

	        gzip clvhealth_jcafb_2020_2019-05-15b.sql
	        pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > <clvhealth_jcafb_2020_2019-05-15b.sql

	        cd /var/lib/odoo/.local/share/Odoo/filestore
	        tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-05-15b.tar.gz clvhealth_jcafb_2020

	        cd /opt/odoo/clvsol_filestore
	        tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-05-15b.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_2019-05-15b.sql
        * /opt/odoo/clvhealth_jcafb_2020_2019-05-15b.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2019-05-15btar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-05-15b.tar.gz
