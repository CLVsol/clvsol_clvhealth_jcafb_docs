.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

===========================================================================
Migração do Banco de Dados - JCAFB-2021 - Servidor [tkl-odoo-160-buster-vm]
===========================================================================

Inicializar o conteúdo do diretório **clvsol_filestore/clvhealth_jcafb** (2020-06-02)
-------------------------------------------------------------------------------------

	#. [tkl-odoo-160-buster-vm] Criar, manualmente, os diretórios:

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

	#. Copiar, manualmente, a partir do servidor **tkl-odoo12-jcafb-vm** para o servidor **tkl-odoo-160-buster-vm**, o conteúdo dos diretórios listados anteriormente.

		* "tkl-odoo12-jcafb-vm:/opt/odoo/clvsol_filestore/clvhealth_jcafb" **->** "tkl-odoo-160-buster-vm:/opt/odoo/clvsol_filestore/clvhealth_jcafb"

.. index:: clvsol_filestore
.. index:: clvsol_filestore/clvhealth_jcafb
.. index:: clvsol_filestore/clvhealth_jcafb/export_files
.. index:: clvsol_filestore/clvhealth_jcafb/lab_test_files
.. index:: clvsol_filestore/clvhealth_jcafb/summary_files
.. index:: clvsol_filestore/clvhealth_jcafb/survey_files

Criar uma nova instância do *CLVhealth-JCAFB-2021* (2020-06-02)
------------------------------------------------------------------

    #. [tkl-odoo-160-buster-vm] Estabelecer uma sessão ssh (session 1) com o servidor **tkl-odoo-160-buster-vm** e paralizar o *Odoo*:

        ::

            # ***** tkl-odoo-160-buster-vm
            #

            ssh tkl-odoo-160-buster-vm -l root

            /etc/init.d/odoo stop

            su odoo

    #. [tkl-odoo-160-buster-vm] Excluir a instância do *CLVhealth-JCAFB-2021* existente:

        ::

            # ***** tkl-odoo-160-buster-vm
            #

            cd /opt/odoo
            dropdb -i clvhealth_jcafb_2021

            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2021

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo-160-buster-vm** ao modo manual:

        ::

            # ***** tkl-odoo-160-buster-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    #. Estabelecer uma sessão ssh (session 2) com o servidor **tkl-odoo-160-buster-vm** e executar o **install.py**:

        ::

            # ***** tkl-odoo-160-buster-vm (session 2)
            #

            ssh tkl-odoo-160-buster-vm -l odoo

            cd /opt/odoo/clvsol_clvhealth_jcafb/project
            
            python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021"
            # Execution time: 0:08:22.364

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo-160-buster-vm** ao modo desejado:

        ::

            # ***** tkl-odoo-160-buster-vm (session 1)
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

Migrar os Usuários de **clvhealth_jcafb_2020** para **clvhealth_jcafb_2021** (2020-06-02)
-----------------------------------------------------------------------------------------

    #. Estabelecer uma sessão ssh com o servidor **tkl-odoo-160-buster-vm** e executar o **res_users_migration.py**, acessando o servidor **tkl-odoo-160-buster-vm** [base de dados **clvhealth_jcafb_2020**]:

        ::

            # ***** tkl-odoo-160-buster-vm (session 2)
            #

            ssh tkl-odoo-160-buster-vm -l odoo

            cd /opt/odoo/clvsol_clvhealth_jcafb/project
            
            python3 res_users_migration.py --rserver "https://192.168.25.183" --radmin_pw "***" --rdb "clvhealth_jcafb_2020" --lserver "https://192.168.25.192" --ladmin_pw "***" --ldb "clvhealth_jcafb_2021"
            # Execution time: 0:01:10.814

    * Os "passwords" não foram migrados.
        
Criar o *External Sync Host* "https://192.168.25.183" (2020-06-02)
------------------------------------------------------------------

    #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo-160-buster-vm <https://tkl-odoo-160-buster-vm>`_

    #. Criar o *External Sync Host* **https://192.168.25.183**:

        * Menu de acesso:
            
            * *External Sync* > *Configuration* > *Hosts* > Criar

        * Parâmetros utilizados:
            
            * External Host Name: "**https://192.168.25.183**"
            * External Database Name: "**clvhealth_jcafb_2020**"
            * External User: "**admin**"
            * External User Password: "*******"

.. toctree::
   :maxdepth: 2
