.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

============================
2020-01-(16-25) (JCAFB-2020)
============================

Criar um backup do *CLVhealth-JCAFB-2020* (2020-01-16a)
-------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_backup`.

    #. [clvheatlh-jcafb-2020-vm-pro] Estabelecer uma sessão ssh com o servidor **clvheatlh-jcafb-2020-vm-pro** e paralizar o *Odoo*:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #

            ssh clvheatlh-jcafb-2020-vm-pro -l root

            /etc/init.d/odoo stop

            su odoo

    #. [clvheatlh-jcafb-2020-vm-pro] Executar os comandos de criação dos arquivos de backup:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #
            # data_dir = /var/lib/odoo/.local/share/Odoo
            #

            cd /opt/odoo
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2020-01-16a.sql

            gzip clvhealth_jcafb_2020_2020-01-16a.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2020-01-16a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-16a.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-16a.tar.gz clvhealth_jcafb

    #. Retornar a execução do *Odoo* do servidor **clvheatlh-jcafb-2020-vm-pro** ao modo desejado:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    Criados os seguintes arquivos:
        * /opt/odoo/clvhealth_jcafb_2020_2020-01-16a.sql
        * /opt/odoo/clvhealth_jcafb_2020_2020-01-16a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-16a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-16a.tar.gz

Criar um backup do *CLVhealth-JCAFB-2020* (2020-01-16b)
-------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_backup`.

    #. [clvheatlh-jcafb-2020-vm-pro] Estabelecer uma sessão ssh com o servidor **clvheatlh-jcafb-2020-vm-pro** e paralizar o *Odoo*:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #

            ssh clvheatlh-jcafb-2020-vm-pro -l root

            /etc/init.d/odoo stop

            su odoo

    #. [clvheatlh-jcafb-2020-vm-pro] Executar os comandos de criação dos arquivos de backup:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #
            # data_dir = /var/lib/odoo/.local/share/Odoo
            #

            cd /opt/odoo
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2020-01-16b.sql

            gzip clvhealth_jcafb_2020_2020-01-16b.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2020-01-16b.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-16b.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-16b.tar.gz clvhealth_jcafb

    #. Retornar a execução do *Odoo* do servidor **clvheatlh-jcafb-2020-vm-pro** ao modo desejado:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    Criados os seguintes arquivos:
        * /opt/odoo/clvhealth_jcafb_2020_2020-01-16b.sql
        * /opt/odoo/clvhealth_jcafb_2020_2020-01-16b.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-16b.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-16b.tar.gz

Criar um backup do *CLVhealth-JCAFB-2020* (2020-01-17a)
-------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_backup`.

    #. [clvheatlh-jcafb-2020-vm-pro] Estabelecer uma sessão ssh com o servidor **clvheatlh-jcafb-2020-vm-pro** e paralizar o *Odoo*:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #

            ssh clvheatlh-jcafb-2020-vm-pro -l root

            /etc/init.d/odoo stop

            su odoo

    #. [clvheatlh-jcafb-2020-vm-pro] Executar os comandos de criação dos arquivos de backup:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #
            # data_dir = /var/lib/odoo/.local/share/Odoo
            #

            cd /opt/odoo
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2020-01-17a.sql

            gzip clvhealth_jcafb_2020_2020-01-17a.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2020-01-17a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-17a.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-17a.tar.gz clvhealth_jcafb

    #. Retornar a execução do *Odoo* do servidor **clvheatlh-jcafb-2020-vm-pro** ao modo desejado:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    Criados os seguintes arquivos:
        * /opt/odoo/clvhealth_jcafb_2020_2020-01-17a.sql
        * /opt/odoo/clvhealth_jcafb_2020_2020-01-17a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-17a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-17a.tar.gz

Atualizar os fontes do projeto (2020-01-18)
-------------------------------------------

    #. [clvheatlh-jcafb-2020-vm-pro] Estabelecer uma sessão ssh com o servidor **clvheatlh-jcafb-2020-vm-pro** e paralizar o *Odoo*:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #

            ssh clvheatlh-jcafb-2020-vm-pro -l root

            /etc/init.d/odoo stop

            su odoo

    #. [clvheatlh-jcafb-2020-vm-pro] **Atualizar** os fontes do projeto

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #

            cd /opt/odoo/clvsol_clvhealth_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons
            git pull

            cd /opt/odoo/clvsol_odoo_addons_l10n_br
            git pull

            cd /opt/odoo/clvsol_odoo_addons_jcafb
            git pull

    #. Retornar a execução do *Odoo* do servidor **clvheatlh-jcafb-2020-vm-pro** ao modo desejado:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

Atualizar o(s) módulo(s) [clv_processing, clv_processing_jcafb] (2020-01-18)
----------------------------------------------------------------------------

    * Referência: :doc:`/setup/module_update`.


    #. [clvheatlh-jcafb-2020-vm-pro] Lista de Módulos:

        * clv_processing
        * clv_processing_jcafb

    #. [clvheatlh-jcafb-2020-vm-pro] **Executar** a atualização do(s) Módulo(s):

        #. Estabelecer uma sessão ssh (session 1) com o servidor **clvheatlh-jcafb-2020-vm-pro** e executar o *Odoo* no modo manual:

            ::

                # ***** clvheatlh-jcafb-2020-vm-pro (session 1)
                #

                ssh clvheatlh-jcafb-2020-vm-pro -l root

                /etc/init.d/odoo stop

                su odoo
                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

        #. Estabelecer uma sessão ssh (session 2) com o servidor **clvheatlh-jcafb-2020-vm-pro** e executar o **install.py**:

            ::

                # ***** clvheatlh-jcafb-2020-vm-pro (session 2)
                #

                ssh clvheatlh-jcafb-2020-vm-pro -l odoo

                cd /opt/odoo/clvsol_clvhealth_jcafb/project
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" - m clv_processing
            
        #. Retornar a execução do *Odoo* do servidor **clvheatlh-jcafb-2020-vm-pro** ao modo desejado:

            ::

                # ***** clvheatlh-jcafb-2020-vm-pro (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Atualizar o(s) módulo(s) [clv_survey_jcafb_2020] (2020-01-18)
-------------------------------------------------------------

    * Referência: :doc:`/setup/module_update`.


    #. [clvheatlh-jcafb-2020-vm-pro] Lista de Módulos:

        * clv_survey_jcafb_2020

    #. [clvheatlh-jcafb-2020-vm-pro] **Executar** a atualização do(s) Módulo(s):

        #. Estabelecer uma sessão ssh (session 1) com o servidor **clvheatlh-jcafb-2020-vm-pro** e executar o *Odoo* no modo manual:

            ::

                # ***** clvheatlh-jcafb-2020-vm-pro (session 1)
                #

                ssh clvheatlh-jcafb-2020-vm-pro -l root

                /etc/init.d/odoo stop

                su odoo
                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

        #. Estabelecer uma sessão ssh (session 2) com o servidor **clvheatlh-jcafb-2020-vm-pro** e executar o **install.py**:

            ::

                # ***** clvheatlh-jcafb-2020-vm-pro (session 2)
                #

                ssh clvheatlh-jcafb-2020-vm-pro -l odoo

                cd /opt/odoo/clvsol_clvhealth_jcafb/project
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" - m clv_survey_jcafb_2020
            
        #. Retornar a execução do *Odoo* do servidor **clvheatlh-jcafb-2020-vm-pro** ao modo desejado:

            ::

                # ***** clvheatlh-jcafb-2020-vm-pro (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Criar um backup do *CLVhealth-JCAFB-2020* (2020-01-18a)
-------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_backup`.

    #. [clvheatlh-jcafb-2020-vm-pro] Estabelecer uma sessão ssh com o servidor **clvheatlh-jcafb-2020-vm-pro** e paralizar o *Odoo*:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #

            ssh clvheatlh-jcafb-2020-vm-pro -l root

            /etc/init.d/odoo stop

            su odoo

    #. [clvheatlh-jcafb-2020-vm-pro] Executar os comandos de criação dos arquivos de backup:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #
            # data_dir = /var/lib/odoo/.local/share/Odoo
            #

            cd /opt/odoo
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2020-01-18a.sql

            gzip clvhealth_jcafb_2020_2020-01-18a.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2020-01-18a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-18a.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-18a.tar.gz clvhealth_jcafb

    #. Retornar a execução do *Odoo* do servidor **clvheatlh-jcafb-2020-vm-pro** ao modo desejado:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    Criados os seguintes arquivos:
        * /opt/odoo/clvhealth_jcafb_2020_2020-01-18a.sql
        * /opt/odoo/clvhealth_jcafb_2020_2020-01-18a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-18a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-18a.tar.gz

Criar um backup do *CLVhealth-JCAFB-2020* (2020-01-18b)
-------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_backup`.

    #. [clvheatlh-jcafb-2020-vm-pro] Estabelecer uma sessão ssh com o servidor **clvheatlh-jcafb-2020-vm-pro** e paralizar o *Odoo*:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #

            ssh clvheatlh-jcafb-2020-vm-pro -l root

            /etc/init.d/odoo stop

            su odoo

    #. [clvheatlh-jcafb-2020-vm-pro] Executar os comandos de criação dos arquivos de backup:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #
            # data_dir = /var/lib/odoo/.local/share/Odoo
            #

            cd /opt/odoo
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2020-01-18b.sql

            gzip clvhealth_jcafb_2020_2020-01-18b.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2020-01-18b.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-18b.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-18b.tar.gz clvhealth_jcafb

    #. Retornar a execução do *Odoo* do servidor **clvheatlh-jcafb-2020-vm-pro** ao modo desejado:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    Criados os seguintes arquivos:
        * /opt/odoo/clvhealth_jcafb_2020_2020-01-18b.sql
        * /opt/odoo/clvhealth_jcafb_2020_2020-01-18b.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-18b.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-18b.tar.gz

Criar um backup do *CLVhealth-JCAFB-2020* (2020-01-19a)
-------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_backup`.

    #. [clvheatlh-jcafb-2020-vm-pro] Estabelecer uma sessão ssh com o servidor **clvheatlh-jcafb-2020-vm-pro** e paralizar o *Odoo*:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #

            ssh clvheatlh-jcafb-2020-vm-pro -l root

            /etc/init.d/odoo stop

            su odoo

    #. [clvheatlh-jcafb-2020-vm-pro] Executar os comandos de criação dos arquivos de backup:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #
            # data_dir = /var/lib/odoo/.local/share/Odoo
            #

            cd /opt/odoo
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2020-01-19a.sql

            gzip clvhealth_jcafb_2020_2020-01-19a.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2020-01-19a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-19a.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-19a.tar.gz clvhealth_jcafb

    #. Retornar a execução do *Odoo* do servidor **clvheatlh-jcafb-2020-vm-pro** ao modo desejado:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    Criados os seguintes arquivos:
        * /opt/odoo/clvhealth_jcafb_2020_2020-01-19a.sql
        * /opt/odoo/clvhealth_jcafb_2020_2020-01-19a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-19a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-19a.tar.gz

Criar um backup do *CLVhealth-JCAFB-2020* (2020-01-20a)
-------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_backup`.

    #. [clvheatlh-jcafb-2020-vm-pro] Estabelecer uma sessão ssh com o servidor **clvheatlh-jcafb-2020-vm-pro** e paralizar o *Odoo*:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #

            ssh clvheatlh-jcafb-2020-vm-pro -l root

            /etc/init.d/odoo stop

            su odoo

    #. [clvheatlh-jcafb-2020-vm-pro] Executar os comandos de criação dos arquivos de backup:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #
            # data_dir = /var/lib/odoo/.local/share/Odoo
            #

            cd /opt/odoo
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2020-01-20a.sql

            gzip clvhealth_jcafb_2020_2020-01-20a.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2020-01-20a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-20a.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-20a.tar.gz clvhealth_jcafb

    #. Retornar a execução do *Odoo* do servidor **clvheatlh-jcafb-2020-vm-pro** ao modo desejado:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    Criados os seguintes arquivos:
        * /opt/odoo/clvhealth_jcafb_2020_2020-01-20a.sql
        * /opt/odoo/clvhealth_jcafb_2020_2020-01-20a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-20a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-20a.tar.gz

Atualizar os fontes do projeto (2020-01-21)
-------------------------------------------

    #. [clvheatlh-jcafb-2020-vm-pro] Estabelecer uma sessão ssh com o servidor **clvheatlh-jcafb-2020-vm-pro** e paralizar o *Odoo*:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #

            ssh clvheatlh-jcafb-2020-vm-pro -l root

            /etc/init.d/odoo stop

            su odoo

    #. [clvheatlh-jcafb-2020-vm-pro] **Atualizar** os fontes do projeto

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #

            cd /opt/odoo/clvsol_clvhealth_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons
            git pull

            cd /opt/odoo/clvsol_odoo_addons_l10n_br
            git pull

            cd /opt/odoo/clvsol_odoo_addons_jcafb
            git pull

    #. Retornar a execução do *Odoo* do servidor **clvheatlh-jcafb-2020-vm-pro** ao modo desejado:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

Atualizar o(s) módulo(s) [clv_summary_jcafb] (2020-01-21)
---------------------------------------------------------

    * Referência: :doc:`/setup/module_update`.


    #. [clvheatlh-jcafb-2020-vm-pro] Lista de Módulos:

        * clv_summary_jcafb

    #. [clvheatlh-jcafb-2020-vm-pro] **Executar** a atualização do(s) Módulo(s):

        #. Estabelecer uma sessão ssh (session 1) com o servidor **clvheatlh-jcafb-2020-vm-pro** e executar o *Odoo* no modo manual:

            ::

                # ***** clvheatlh-jcafb-2020-vm-pro (session 1)
                #

                ssh clvheatlh-jcafb-2020-vm-pro -l root

                /etc/init.d/odoo stop

                su odoo
                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

        #. Estabelecer uma sessão ssh (session 2) com o servidor **clvheatlh-jcafb-2020-vm-pro** e executar o **install.py**:

            ::

                # ***** clvheatlh-jcafb-2020-vm-pro (session 2)
                #

                ssh clvheatlh-jcafb-2020-vm-pro -l odoo

                cd /opt/odoo/clvsol_clvhealth_jcafb/project
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" - m clv_summary_jcafb
            
        #. Retornar a execução do *Odoo* do servidor **clvheatlh-jcafb-2020-vm-pro** ao modo desejado:

            ::

                # ***** clvheatlh-jcafb-2020-vm-pro (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Criar um backup do *CLVhealth-JCAFB-2020* (2020-01-21a)
-------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_backup`.

    #. [clvheatlh-jcafb-2020-vm-pro] Estabelecer uma sessão ssh com o servidor **clvheatlh-jcafb-2020-vm-pro** e paralizar o *Odoo*:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #

            ssh clvheatlh-jcafb-2020-vm-pro -l root

            /etc/init.d/odoo stop

            su odoo

    #. [clvheatlh-jcafb-2020-vm-pro] Executar os comandos de criação dos arquivos de backup:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #
            # data_dir = /var/lib/odoo/.local/share/Odoo
            #

            cd /opt/odoo
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2020-01-21a.sql

            gzip clvhealth_jcafb_2020_2020-01-21a.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2020-01-21a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-21a.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-21a.tar.gz clvhealth_jcafb

    #. Retornar a execução do *Odoo* do servidor **clvheatlh-jcafb-2020-vm-pro** ao modo desejado:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    Criados os seguintes arquivos:
        * /opt/odoo/clvhealth_jcafb_2020_2020-01-21a.sql
        * /opt/odoo/clvhealth_jcafb_2020_2020-01-21a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-21a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-21a.tar.gz

Atualizar os fontes do projeto (2020-01-22)
-------------------------------------------

    #. [clvheatlh-jcafb-2020-vm-pro] Estabelecer uma sessão ssh com o servidor **clvheatlh-jcafb-2020-vm-pro** e paralizar o *Odoo*:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #

            ssh clvheatlh-jcafb-2020-vm-pro -l root

            /etc/init.d/odoo stop

            su odoo

    #. [clvheatlh-jcafb-2020-vm-pro] **Atualizar** os fontes do projeto

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #

            cd /opt/odoo/clvsol_clvhealth_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons
            git pull

            cd /opt/odoo/clvsol_odoo_addons_l10n_br
            git pull

            cd /opt/odoo/clvsol_odoo_addons_jcafb
            git pull

    #. Retornar a execução do *Odoo* do servidor **clvheatlh-jcafb-2020-vm-pro** ao modo desejado:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

Criar um backup do *CLVhealth-JCAFB-2020* (2020-01-22a)
-------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_backup`.

    #. [clvheatlh-jcafb-2020-vm-pro] Estabelecer uma sessão ssh com o servidor **clvheatlh-jcafb-2020-vm-pro** e paralizar o *Odoo*:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #

            ssh clvheatlh-jcafb-2020-vm-pro -l root

            /etc/init.d/odoo stop

            su odoo

    #. [clvheatlh-jcafb-2020-vm-pro] Executar os comandos de criação dos arquivos de backup:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #
            # data_dir = /var/lib/odoo/.local/share/Odoo
            #

            cd /opt/odoo
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2020-01-22a.sql

            gzip clvhealth_jcafb_2020_2020-01-22a.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2020-01-22a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-22a.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-22a.tar.gz clvhealth_jcafb

    #. Retornar a execução do *Odoo* do servidor **clvheatlh-jcafb-2020-vm-pro** ao modo desejado:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    Criados os seguintes arquivos:
        * /opt/odoo/clvhealth_jcafb_2020_2020-01-22a.sql
        * /opt/odoo/clvhealth_jcafb_2020_2020-01-22a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-22a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-22a.tar.gz

Criar um backup do *CLVhealth-JCAFB-2020* (2020-01-23a)
-------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_backup`.

    #. [clvheatlh-jcafb-2020-vm-pro] Estabelecer uma sessão ssh com o servidor **clvheatlh-jcafb-2020-vm-pro** e paralizar o *Odoo*:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #

            ssh clvheatlh-jcafb-2020-vm-pro -l root

            /etc/init.d/odoo stop

            su odoo

    #. [clvheatlh-jcafb-2020-vm-pro] Executar os comandos de criação dos arquivos de backup:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #
            # data_dir = /var/lib/odoo/.local/share/Odoo
            #

            cd /opt/odoo
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2020-01-23a.sql

            gzip clvhealth_jcafb_2020_2020-01-23a.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2020-01-23a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-23a.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-23a.tar.gz clvhealth_jcafb

    #. Retornar a execução do *Odoo* do servidor **clvheatlh-jcafb-2020-vm-pro** ao modo desejado:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    Criados os seguintes arquivos:
        * /opt/odoo/clvhealth_jcafb_2020_2020-01-23a.sql
        * /opt/odoo/clvhealth_jcafb_2020_2020-01-23a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-23a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-23a.tar.gz

Atualizar os fontes do projeto (2020-01-23)
-------------------------------------------

    #. [clvheatlh-jcafb-2020-vm-pro] Estabelecer uma sessão ssh com o servidor **clvheatlh-jcafb-2020-vm-pro** e paralizar o *Odoo*:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #

            ssh clvheatlh-jcafb-2020-vm-pro -l root

            /etc/init.d/odoo stop

            su odoo

    #. [clvheatlh-jcafb-2020-vm-pro] **Atualizar** os fontes do projeto

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #

            cd /opt/odoo/clvsol_clvhealth_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons
            git pull

            cd /opt/odoo/clvsol_odoo_addons_l10n_br
            git pull

            cd /opt/odoo/clvsol_odoo_addons_jcafb
            git pull

    #. Retornar a execução do *Odoo* do servidor **clvheatlh-jcafb-2020-vm-pro** ao modo desejado:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

Atualizar os fontes do projeto (2020-01-24)
-------------------------------------------

    #. [clvheatlh-jcafb-2020-vm-pro] Estabelecer uma sessão ssh com o servidor **clvheatlh-jcafb-2020-vm-pro** e paralizar o *Odoo*:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #

            ssh clvheatlh-jcafb-2020-vm-pro -l root

            /etc/init.d/odoo stop

            su odoo

    #. [clvheatlh-jcafb-2020-vm-pro] **Atualizar** os fontes do projeto

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #

            cd /opt/odoo/clvsol_clvhealth_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons
            git pull

            cd /opt/odoo/clvsol_odoo_addons_l10n_br
            git pull

            cd /opt/odoo/clvsol_odoo_addons_jcafb
            git pull

    #. Retornar a execução do *Odoo* do servidor **clvheatlh-jcafb-2020-vm-pro** ao modo desejado:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

Criar um backup do *CLVhealth-JCAFB-2020* (2020-01-24a)
-------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_backup`.

    #. [clvheatlh-jcafb-2020-vm-pro] Estabelecer uma sessão ssh com o servidor **clvheatlh-jcafb-2020-vm-pro** e paralizar o *Odoo*:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #

            ssh clvheatlh-jcafb-2020-vm-pro -l root

            /etc/init.d/odoo stop

            su odoo

    #. [clvheatlh-jcafb-2020-vm-pro] Executar os comandos de criação dos arquivos de backup:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #
            # data_dir = /var/lib/odoo/.local/share/Odoo
            #

            cd /opt/odoo
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2020-01-24a.sql

            gzip clvhealth_jcafb_2020_2020-01-24a.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2020-01-24a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-24a.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-24a.tar.gz clvhealth_jcafb

    #. Retornar a execução do *Odoo* do servidor **clvheatlh-jcafb-2020-vm-pro** ao modo desejado:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    Criados os seguintes arquivos:
        * /opt/odoo/clvhealth_jcafb_2020_2020-01-24a.sql
        * /opt/odoo/clvhealth_jcafb_2020_2020-01-24a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-24a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-24a.tar.gz

Criar um backup do *CLVhealth-JCAFB-2020* (2020-01-25a)
-------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_backup`.

    #. [clvheatlh-jcafb-2020-vm-pro] Estabelecer uma sessão ssh com o servidor **clvheatlh-jcafb-2020-vm-pro** e paralizar o *Odoo*:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #

            ssh clvheatlh-jcafb-2020-vm-pro -l root

            /etc/init.d/odoo stop

            su odoo

    #. [clvheatlh-jcafb-2020-vm-pro] Executar os comandos de criação dos arquivos de backup:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #
            # data_dir = /var/lib/odoo/.local/share/Odoo
            #

            cd /opt/odoo
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2020-01-25a.sql

            gzip clvhealth_jcafb_2020_2020-01-25a.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2020-01-25a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-25a.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-25a.tar.gz clvhealth_jcafb

    #. Retornar a execução do *Odoo* do servidor **clvheatlh-jcafb-2020-vm-pro** ao modo desejado:

        ::

            # ***** clvheatlh-jcafb-2020-vm-pro
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    Criados os seguintes arquivos:
        * /opt/odoo/clvhealth_jcafb_2020_2020-01-25a.sql
        * /opt/odoo/clvhealth_jcafb_2020_2020-01-25a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-25a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-25a.tar.gz

Restaurar um backup do *CLVhealth-JCAFB-2020* [clvheatlh-jcafb-2020-aws-pro] (2020-01-25a)
------------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_restore`.

    #. [clvheatlh-jcafb-2020-aws-pro] Estabelecer uma sessão ssh com o servidor **clvheatlh-jcafb-2020-aws-pro** e paralizar o *Odoo*:

        ::

            # ***** clvheatlh-jcafb-2020-aws-pro
            #

            ssh clvheatlh-jcafb-2020-aws-pro -l root

            /etc/init.d/odoo stop

            su odoo

    #. [clvheatlh-jcafb-2020-aws-pro] Executar os comandos de restauração dos arquivos de backup:

        ::

            # ***** clvheatlh-jcafb-2020-aws-pro
            #

            cd /opt/odoo
            gzip -d clvhealth_jcafb_2020_2020-01-25a.sql.gz

            dropdb -i clvhealth_jcafb_2020

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020
            psql -f clvhealth_jcafb_2020_2020-01-25a.sql -d clvhealth_jcafb_2020 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-25a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-25a.tar.gz

    #. [clvheatlh-jcafb-2020-aws-pro] **Atualizar** os fontes do projeto

        ::

            # ***** clvheatlh-jcafb-2020-aws-pro
            #

            cd /opt/odoo/clvsol_clvhealth_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons
            git pull

            cd /opt/odoo/clvsol_odoo_addons_l10n_br
            git pull

            cd /opt/odoo/clvsol_odoo_addons_jcafb
            git pull

    #. Retornar a execução do *Odoo* do servidor **clvheatlh-jcafb-2020-aws-pro** ao modo desejado:

        ::

            # ***** clvheatlh-jcafb-2020-aws-pro
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    #. [clvheatlh-jcafb-2020-aws-pro] Configurar o parâmetro "**web.base.url**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `clvheatlh-jcafb-2020-aws-pro <https://clvheatlh-jcafb-2020-aws-pro.tklapp.com/>`_

        #. Acessar a *View* **Parâmetros do Sistema**:

            * Menu de acesso:
                * **Configurações** » **Técnico** » **Parâmetros** » **Parâmetros do Sistema**

        #. Pesquisar pelo registro com a **Chave** "**web.base.url**";

        #. Editar o registro apresentado (**Chave**: "**web.base.url**")

        #. Alterar o campo **Valor** para:

            * "**clvheatlh-jcafb-2020-aws-pro.tklapp.com**".

        #. Salvar o registro editado.

Restaurar um backup do *CLVhealth-JCAFB-2020* [clvheatlh-jcafb-2020-aws-tst] (2020-01-25a)
------------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_restore`.

    #. [clvheatlh-jcafb-2020-aws-tst] Estabelecer uma sessão ssh com o servidor **clvheatlh-jcafb-2020-aws-tst** e paralizar o *Odoo*:

        ::

            # ***** clvheatlh-jcafb-2020-aws-tst
            #

            ssh clvheatlh-jcafb-2020-aws-tst -l root

            /etc/init.d/odoo stop

            su odoo

    #. [clvheatlh-jcafb-2020-aws-tst] Executar os comandos de restauração dos arquivos de backup:

        ::

            # ***** clvheatlh-jcafb-2020-aws-tst
            #

            cd /opt/odoo
            gzip -d clvhealth_jcafb_2020_2020-01-25a.sql.gz

            dropdb -i clvhealth_jcafb_2020

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020
            psql -f clvhealth_jcafb_2020_2020-01-25a.sql -d clvhealth_jcafb_2020 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-25a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-25a.tar.gz

    #. [clvheatlh-jcafb-2020-aws-tst] **Atualizar** os fontes do projeto

        ::

            # ***** clvheatlh-jcafb-2020-aws-tst
            #

            cd /opt/odoo/clvsol_clvhealth_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons
            git pull

            cd /opt/odoo/clvsol_odoo_addons_l10n_br
            git pull

            cd /opt/odoo/clvsol_odoo_addons_jcafb
            git pull

    #. Retornar a execução do *Odoo* do servidor **clvheatlh-jcafb-2020-aws-tst** ao modo desejado:

        ::

            # ***** clvheatlh-jcafb-2020-aws-tst
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    #. [clvheatlh-jcafb-2020-aws-tst] Configurar o parâmetro "**web.base.url**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `clvheatlh-jcafb-2020-aws-tst <https://clvheatlh-jcafb-2020-aws-tst.tklapp.com/>`_

        #. Acessar a *View* **Parâmetros do Sistema**:

            * Menu de acesso:
                * **Configurações** » **Técnico** » **Parâmetros** » **Parâmetros do Sistema**

        #. Pesquisar pelo registro com a **Chave** "**web.base.url**";

        #. Editar o registro apresentado (**Chave**: "**web.base.url**")

        #. Alterar o campo **Valor** para:

            * "**clvheatlh-jcafb-2020-aws-tst.tklapp.com**".

        #. Salvar o registro editado.

.. toctree::
   :maxdepth: 2
