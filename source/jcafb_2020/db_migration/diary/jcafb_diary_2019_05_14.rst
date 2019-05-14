.. raw:: html

    <style> .red {color:red} </style>

.. role:: red

============================
2019-05-(14-15) (JCAFB-2020)
============================

Criar uma nova instância (**vazia**) do *CLVhealth-JCAFB*
---------------------------------------------------------

	* Nenhum módulo será instalado nesta nova instância do *CLVhealth-JCAFB*

	* Referência: "Preparação do Banco de Dados", :ref:`Preparação do Banco de Dados (Procedimento 1)`.

	#. [tkl-odoo12-jcafb-vm] Criar, manualmente, o Banco de Dados **clvhealth_jcafb_db**:

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

	    #. Criar o Banco de Dados **clvhealth_jcafb_db**:

	    	* Database Name: **clvhealth_jcafb_db**
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
		        
		        python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_db"
	        
	    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo padrão:

		    ::

		        # ***** tkl-odoo12-jcafb-vm (session 1)
		        #

		        ^C

		        exit

		        /etc/init.d/odoo start
