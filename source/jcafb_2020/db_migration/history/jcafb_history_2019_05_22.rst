.. raw:: html

    <style> .red {color:red} </style>

.. role:: red

=================
2019-05-(22 a 29)
=================

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

Instalar o(s) módulo(s) [contacts, base_address_city, hr, survey]
-----------------------------------------------------------------

    * Referência: :doc:`/setup/module_installation`.

    #. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, habilitando o(s) Módulo(s):

        * contacts
        * base_address_city
        * hr
        * survey

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

Instalar o(s) módulo(s) [l10n_br_base, l10n_br_zip, l10n_br_zip_correios]
-------------------------------------------------------------------------

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

Instalar o(s) módulo(s) [clv_base, clv_base_jcafb]
--------------------------------------------------

    * Referência: :doc:`/setup/module_installation`.

    #. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, habilitando o(s) Módulo(s):

        * clv_base
        * clv_base_jcafb

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

Instalar o(s) módulo(s) [clv_file_system, clv_file_system_jcafb, clv_global_log, clv_global_log_jcafb, clv_external_sync, clv_external_sync_jcafb, clv_base_sync_jcafb]
------------------------------------------------------------------------------------------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/module_installation`.

    #. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, habilitando o(s) Módulo(s):

        * clv_file_system
        * clv_file_system_jcafb
        * clv_global_log
        * clv_global_log_jcafb
        * clv_external_sync
        * clv_external_sync_jcafb
        * clv_base_sync_jcafb

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

Instalar o(s) módulo(s) [clv_global_tag, clv_global_tag_jcafb, clv_global_tag_sync_jcafb, clv_phase, clv_phase_jcafb, clv_phase_sync_jcafb]
---------------------------------------------------------------------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/module_installation`.

    #. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, habilitando o(s) Módulo(s):

        * clv_global_tag
        * clv_global_tag_jcafb
        * clv_global_tag_sync_jcafb
        * clv_phase
        * clv_phase_jcafb
        * clv_phase_sync_jcafb

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

Instalar o(s) módulo(s) [clv_employee, clv_employee_history, clv_employee_sync_jcafb]
-------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/module_installation`.

    #. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, habilitando o(s) Módulo(s):

        * clv_employee
        * clv_employee_history
        * clv_employee_sync_jcafb

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

Instalar o(s) módulo(s) [clv_survey, clv_survey_history, clv_survey_sync_jcafb]
-------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/module_installation`.

    #. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, habilitando o(s) Módulo(s):

        * clv_survey
        * clv_survey_history
        * clv_survey_sync_jcafb

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

Instalar o(s) módulo(s) [clv_event, clv_event_history, clv_event_jcafb, clv_event_sync_jcafb, clv_community, clv_community_jcafb, clv_document, clv_document_history, clv_document_jcafb, clv_document_sync_jcafb]
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/module_installation`.

    #. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, habilitando o(s) Módulo(s):

        * clv_event
        * clv_event_history
        * clv_event_jcafb
        * clv_event_sync_jcafb
        * clv_community
        * clv_community_jcafb
        * clv_document
        * clv_document_history
        * clv_document_jcafb
        * clv_document_sync_jcafb

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

Instalar o(s) módulo(s) [clv_mfile, clv_mfile_history, clv_mfile_jcafb, clv_mfile_sync_jcafb]
---------------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/module_installation`.

    #. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, habilitando o(s) Módulo(s):

        * clv_mfile
        * clv_mfile_history
        * clv_mfile_jcafb
        * clv_mfile_sync_jcafb

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

Instalar o(s) módulo(s) [clv_lab_test, clv_lab_test_history, clv_mfile_jcafb, clv_lab_test_sync_jcafb]
------------------------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/module_installation`.

    #. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, habilitando o(s) Módulo(s):

        * clv_lab_test
        * clv_lab_test_history
        * clv_lab_test_jcafb
        * clv_lab_test_sync_jcafb

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

Instalar o(s) módulo(s) [clv_partner_entity, clv_partner_entity_l10n_br, clv_address, clv_address_history, clv_address_l10n_br, clv_address_jcafb, clv_address_history_jcafb, clv_address_sync_jcafb, clv_address_history_sync_jcafb]
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/module_installation`.

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

Instalar o(s) módulo(s) [clv_family, clv_family_history, clv_family_l10n_br, clv_family_jcafb, clv_family_history_jcafb]
-------------------------------------------------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/module_installation`.

    #. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, habilitando o(s) Módulo(s):

        * clv_family
        * clv_family_history
        * clv_family_l10n_br
        * clv_family_jcafb
        * clv_family_history_jcafb

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

Instalar o(s) módulo(s) [clv_person, clv_person_history, clv_person_l10n_br, clv_person_jcafb, clv_person_history_jcafb, clv_person_sync_jcafb, clv_person_history_sync_jcafb]
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/module_installation`.

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
            
Criar o *External Sync Host* "https://192.168.25.152"
-----------------------------------------------------

    #. [tkl-odoo12-jcafb-vm] Criar, manualmente, o *External Sync Host* **https://192.168.25.152**:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Criar o *External Sync Host* **https://192.168.25.152**:

            * Menu de acesso:
                * *External Sync* > *Configuration* > *Hosts* > Criar

            * Parâmetros utilizados:
                * External Host Name: "**https://192.168.25.152**"
                * External Database Name: "**clvhealth_jcafb_2019**"
                * External User: "**data.admin**"
                * External User Password: "*******"

Executar o *External Sync Batch* "*Default Batch*"
--------------------------------------------------

    #. [tkl-odoo12-jcafb-vm] Configurar os *External Sync Schedules* disponíveis:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Configurar, com a ajuda do *wizzard* *External Sync Schedule Mass Edit*, os *External Sync Schedules* disponíveis:

            * Lista de *Schedules*:
                * res.country (res.country)
                * res.country.state (res.country.state)
                * res.city (l10n_br_base.city)
                * clv.global_tag (clv.global_tag)
                * clv.phase (clv.history_marker)
                * hr.department (hr.department)
                * hr.job (hr.job)
                * hr.employee (hr.employee)
                * survey.stage (survey.stage)
                * survey.survey (survey.survey)
                * survey.page (survey.page)
                * survey.question (survey.question)
                * survey.question (survey.question)
                * survey.user_input (survey.user_input)
                * survey.user_input_line (survey.user_input_line)
                * clv.event (clv.event)
                * clv.event.attendee (clv.event.attendee)
                * clv.document.category (clv.document.category)
                * clv.document.type (clv.document.type)
                * clv.document (clv.document)
                * clv.document.item (clv.document.item)
                * clv.mfile (clv.mfile)
                * clv.lab_test.unit (clv.lab_test.unit)
                * clv.lab_test.type (clv.lab_test.type)
                * clv.lab_test.request (clv.lab_test.request)
                * clv.lab_test.result (clv.lab_test.result)
                * clv.lab_test.report (clv.lab_test.report)
                * clv.lab_test.criterion (clv.lab_test.criterion)
                * clv.address.category (clv.address.category)
                * clv.address (clv.address)
                * clv.address.history (clv.address.history)
                * clv.person.category (clv.person.category)
                * clv.person.marker (clv.person.marker)
                * clv.person (clv.person)
                * clv.person.history (clv.person.history)

            * Menu de acesso:
                * *External Sync* > *External Sync* > *External Sync* > *Schedules* > Ação > *External Sync Schedule Mass Edit*

            * Parâmetros alterados:
                * External Host: "**https://192.168.25.152**"
                * Max Task Registers: "**200.000**"

    #. Estabelecer uma sessão ssh com o servidor **tkl-odoo12-jcafb-vm** e executar o *Odoo* no modo manual:

        ::

            # ***** tkl-odoo12-jcafb-vm
            #

            ssh tkl-odoo12-jcafb-vm -l root

            /etc/init.d/odoo stop

            su odoo

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    #. [tkl-odoo12-jcafb-vm] Executar o *External Sync Batch* "**Default Batch**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Executar o *wizzard* *External Sync Batch Exec* para o "**Default Batch**":

            * Menu de acesso:
                * *External Sync* > *External Sync* > *External Sync* > *Batches* > Ação > *External Sync Batch Exec*

            * *Members*:
                * res.country (res.country)
                * res.country.state (res.country.state)
                * res.city (l10n_br_base.city)
                * clv.global_tag (clv.global_tag)
                * clv.phase (clv.history_marker)
                * hr.department (hr.department)
                * hr.job (hr.job)
                * hr.employee (hr.employee)
                * survey.stage (survey.stage)
                * survey.survey (survey.survey)
                * survey.page (survey.page)
                * survey.question (survey.question)
                * survey.question (survey.question)
                * survey.user_input (survey.user_input)
                * survey.user_input_line (survey.user_input_line)
                * clv.event (clv.event)
                * clv.event.attendee (clv.event.attendee)
                * clv.document.category (clv.document.category)
                * clv.document.type (clv.document.type)
                * clv.document (clv.document)
                * clv.document.item (clv.document.item)
                * clv.mfile (clv.mfile)
                * clv.lab_test.unit (clv.lab_test.unit)
                * clv.lab_test.type (clv.lab_test.type)
                * clv.lab_test.request (clv.lab_test.request)
                * clv.lab_test.result (clv.lab_test.result)
                * clv.lab_test.report (clv.lab_test.report)
                * clv.lab_test.criterion (clv.lab_test.criterion)
                * clv.address.category (clv.address.category)
                * clv.address (clv.address)
                * clv.address.history (clv.address.history)
                * clv.person.category (clv.person.category)
                * clv.person.marker (clv.person.marker)
                * clv.person (clv.person)
                * clv.person.history (clv.person.history)

            * *Synchronization Logs*:
                .. * :doc:`/jcafb_2020/db_migration/history/jcafb_history_2019_05_22_sync_log`

                .. toctree::
                   :maxdepth: 2

                   jcafb_history_2019_05_22_sync_log

    #. [tkl-odoo12-jcafb-vm] Configurar os *External Sync Schedules* disponíveis:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Configurar, com a ajuda do *wizzard* *External Sync Schedule Mass Edit*, os *External Sync Schedules* disponíveis:

            * Lista de *Schedules*:
            * *Members*:
                * res.country (res.country)
                * res.country.state (res.country.state)
                * res.city (l10n_br_base.city)
                * clv.global_tag (clv.global_tag)
                * clv.phase (clv.history_marker)
                * hr.department (hr.department)
                * hr.job (hr.job)
                * hr.employee (hr.employee)
                * survey.stage (survey.stage)
                * survey.survey (survey.survey)
                * survey.page (survey.page)
                * survey.question (survey.question)
                * survey.question (survey.question)
                * survey.user_input (survey.user_input)
                * survey.user_input_line (survey.user_input_line)
                * clv.event (clv.event)
                * clv.event.attendee (clv.event.attendee)
                * clv.document.category (clv.document.category)
                * clv.document.type (clv.document.type)
                * clv.document (clv.document)
                * clv.document.item (clv.document.item)
                * clv.mfile (clv.mfile)
                * clv.lab_test.unit (clv.lab_test.unit)
                * clv.lab_test.type (clv.lab_test.type)
                * clv.lab_test.request (clv.lab_test.request)
                * clv.lab_test.result (clv.lab_test.result)
                * clv.lab_test.report (clv.lab_test.report)
                * clv.lab_test.criterion (clv.lab_test.criterion)
                * clv.address.category (clv.address.category)
                * clv.address (clv.address)
                * clv.address.history (clv.address.history)
                * clv.person.category (clv.person.category)
                * clv.person.marker (clv.person.marker)
                * clv.person (clv.person)
                * clv.person.history (clv.person.history)

            * Menu de acesso:
                * *External Sync* > *External Sync* > *External Sync* > *Schedules* > Ação > *External Sync Schedule Mass Edit*

            * Parâmetros alterados:
                * Disable Identification: "**marcado**"

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo padrão:

        ::

            # ***** tkl-odoo12-jcafb-vm
            #

            ^C

            exit

            /etc/init.d/odoo start

Criar um backup do *CLVhealth-JCAFB-2020* (2019-05-29a)
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
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-05-29a.sql

            gzip clvhealth_jcafb_2020_2019-05-29a.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-05-29a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-05-29a.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-05-29a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_2019-05-29a.sql
        * /opt/odoo/clvhealth_jcafb_2020_2019-05-29a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2019-05-29a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-05-29a.tar.gz

.. index:: clvhealth_jcafb_2020_2019-05-29a.sql
.. index:: filestore_clvhealth_jcafb_2020_2019-05-29a
.. index:: clvsol_filestore_clvhealth_jcafb_2019-05-29a
