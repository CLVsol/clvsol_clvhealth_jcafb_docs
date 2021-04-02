.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

==============================================================================================
[2019-10-(09-13)] - Preparação do Banco de Dados - JCAFB-2020 - Servidor [tkl-odoo12-jcafb-vm]
==============================================================================================

Restaurar um backup do *CLVhealth-JCAFB-2020* no servidor "tkl-odoo12-jcafb-vm" (2019-10-09a)
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
            # gzip -d clvhealth_jcafb_2020_2019-10-09a.sql.gz

            dropdb -i clvhealth_jcafb_2020

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020
            psql -f clvhealth_jcafb_2020_2019-10-09a.sql -d clvhealth_jcafb_2020 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-10-09a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-10-09a.tar.gz

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo desejado:

        ::

            # ***** tkl-odoo12-jcafb-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

Desabilitar a instalação do(s) módulo(s) [verification, export, processing, report] (2019-10-09)
------------------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/module_installation`.

    #. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, **desabilitando** o(s) Módulo(s):

        * clv_verification
        * clv_verification_jcafb
        * clv_address_verification_jcafb
        * clv_family_verification_jcafb
        * clv_person_verification_jcafb
        * clv_address_aux_verification_jcafb
        * clv_family_aux_verification_jcafb
        * clv_person_aux_verification_jcafb

    #. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, **desabilitando** o(s) Módulo(s):

        * clv_export
        * clv_document_export
        * clv_lab_test_export
        * clv_person_export
        * clv_export_jcafb
        * clv_document_export_jcafb
        * clv_lab_test_export_jcafb
        * clv_person_export_jcafb

    #. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, **desabilitando** o(s) Módulo(s):

        * clv_processing
        * clv_processing_jcafb

    #. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, **desabilitando** o(s) Módulo(s):

        * clv_report
        * clv_report_jcafb

Atualizar o(s) módulo(s) [ver lista] (2019-10-09)
-------------------------------------------------

    * Referência: :doc:`/setup/module_update`.


    #. [tkl-odoo12-jcafb-vm] Lista de Módulos:

        * clv_partner_entity
        * clv_address
        * clv_address_aux
        * clv_family
        * clv_family_aux
        * clv_person
        * clv_person_aux

    #. [tkl-odoo12-jcafb-vm] **Executar** a atualização do(s) Módulo(s):

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" - m clv_partner_entity
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo desejado:

            ::

                # ***** tkl-odoo12-jcafb-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Criar um backup do *CLVhealth-JCAFB-2020* (2019-10-09b)
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
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-10-09b.sql

            gzip clvhealth_jcafb_2020_2019-10-09b.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-10-09b.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-10-09b.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-10-09b.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_2019-10-09b.sql
        * /opt/odoo/clvhealth_jcafb_2020_2019-10-09b.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2019-10-09b.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-10-09b.tar.gz

.. index:: clvhealth_jcafb_2020_2019-10-09b.sql
.. index:: filestore_clvhealth_jcafb_2020_2019-10-09b
.. index:: clvsol_filestore_clvhealth_jcafb_2019-10-09b

Restaurar um backup do *CLVhealth-JCAFB-2020* no servidor "tkl-odoo12-jcafb-vm" (2019-10-09b)
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
            # gzip -d clvhealth_jcafb_2020_2019-10-09b.sql.gz

            dropdb -i clvhealth_jcafb_2020

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020
            psql -f clvhealth_jcafb_2020_2019-10-09b.sql -d clvhealth_jcafb_2020 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-10-09b.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-10-09b.tar.gz

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo desejado:

        ::

            # ***** tkl-odoo12-jcafb-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

Desabilitar a instalação do(s) módulo(s) [verification, export, processing, report] (2019-10-11)
------------------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/module_installation`.

    #. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, **desabilitando** o(s) Módulo(s):

        * clv_verification
        * clv_verification_jcafb
        * clv_address_verification_jcafb
        * clv_family_verification_jcafb
        * clv_person_verification_jcafb
        * clv_address_aux_verification_jcafb
        * clv_family_aux_verification_jcafb
        * clv_person_aux_verification_jcafb

    #. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, **desabilitando** o(s) Módulo(s):

        * clv_export
        * clv_document_export
        * clv_lab_test_export
        * clv_person_export
        * clv_export_jcafb
        * clv_document_export_jcafb
        * clv_lab_test_export_jcafb
        * clv_person_export_jcafb

    #. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, **desabilitando** o(s) Módulo(s):

        * clv_processing
        * clv_processing_jcafb

    #. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, **desabilitando** o(s) Módulo(s):

        * clv_report
        * clv_report_jcafb

Atualizar o(s) módulo(s) [clv_person, clv_person_aux] (2019-10-11)
------------------------------------------------------------------

    * Referência: :doc:`/setup/module_update`.


    #. [tkl-odoo12-jcafb-vm] Lista de Módulos:

        * clv_person
        * clv_person_aux

    #. [tkl-odoo12-jcafb-vm] **Executar** a atualização do(s) Módulo(s):

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" - m clv_person
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo desejado:

            ::

                # ***** tkl-odoo12-jcafb-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Instalar o(s) módulo(s) [verification] (2019-10-11)
---------------------------------------------------

    * Referência: :doc:`/setup/module_installation`.

    #. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, **habilitando** o(s) Módulo(s):

        * clv_verification
        * clv_verification_jcafb
        * clv_address_verification_jcafb
        * clv_family_verification_jcafb
        * clv_person_verification_jcafb
        * clv_address_aux_verification_jcafb
        * clv_family_aux_verification_jcafb
        * clv_person_aux_verification_jcafb

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

Executar o processo de verificação para todas as Pessoas (Aux) (2019-10-11)
---------------------------------------------------------------------------

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Person (Aux) Verification Execute` para todas as Pessoas:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Persons (Aux)*:

            * Menu de acesso:
                * :bi:`Community` » :bi:`Community` » :bi:`Persons (Aux)`

        #. Selecionar todas as Pessoas (Aux) (**1344**)

        #. Executar a Ação ":bi:`Person (Aux) Verification Execute`":

            #. Utilize o botão :bi:`Person (Aux) Verification Execute` para executar a Ação.

Criar um backup do *CLVhealth-JCAFB-2020* (2019-10-11a)
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
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-10-11a.sql

            gzip clvhealth_jcafb_2020_2019-10-11a.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-10-11a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-10-11a.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-10-11a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_2019-10-11a.sql
        * /opt/odoo/clvhealth_jcafb_2020_2019-10-11a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2019-10-11a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-10-11a.tar.gz

.. index:: clvhealth_jcafb_2020_2019-10-11a.sql
.. index:: filestore_clvhealth_jcafb_2020_2019-10-11a
.. index:: clvsol_filestore_clvhealth_jcafb_2019-10-11a

Criar o *Verification Marker* "**a Verificar [1]"**" (2019-10-11)
-----------------------------------------------------------------

    #. Acessar a *View* *Person Markers*:

        * Menu de acesso:
            
            * :bi:`Verification` » :bi:`Configuration` » :bi:`Verification` » :bi:`Markers`

        * Parâmetros:

            * *Name*: **a Verificar [1]"**
            * *Description*:

Criar o *Verification Marker* "**a Verificar [2]"**" (2019-10-11)
-----------------------------------------------------------------

    #. Acessar a *View* *Person Markers*:

        * Menu de acesso:
            
            * :bi:`Verification` » :bi:`Configuration` » :bi:`Verification` » :bi:`Markers`

        * Parâmetros:

            * *Name*: **a Verificar [2]"**
            * *Description*:

Criar o *Verification Marker* "**a Verificar [3]"**" (2019-10-11)
-----------------------------------------------------------------

    #. Acessar a *View* *Person Markers*:

        * Menu de acesso:
            
            * :bi:`Verification` » :bi:`Configuration` » :bi:`Verification` » :bi:`Markers`

        * Parâmetros:

            * *Name*: **a Verificar [3]"**
            * *Description*:

Criar o *Verification Marker* "**a Verificar [4]"**" (2019-10-11)
-----------------------------------------------------------------

    #. Acessar a *View* *Person Markers*:

        * Menu de acesso:
            
            * :bi:`Verification` » :bi:`Configuration` » :bi:`Verification` » :bi:`Markers`

        * Parâmetros:

            * *Name*: **a Verificar [4]"**
            * *Description*:

Criar o *Verification Marker* "**a Verificar [5]"**" (2019-10-11)
-----------------------------------------------------------------

    #. Acessar a *View* *Person Markers*:

        * Menu de acesso:
            
            * :bi:`Verification` » :bi:`Configuration` » :bi:`Verification` » :bi:`Markers`

        * Parâmetros:

            * *Name*: **a Verificar [5]"**
            * *Description*:

Criar um backup do *CLVhealth-JCAFB-2020* (2019-10-11b)
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
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-10-11b.sql

            gzip clvhealth_jcafb_2020_2019-10-11b.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-10-11b.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-10-11b.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-10-11b.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_2019-10-11b.sql
        * /opt/odoo/clvhealth_jcafb_2020_2019-10-11b.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2019-10-11b.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-10-11b.tar.gz

.. index:: clvhealth_jcafb_2020_2019-10-11b.sql
.. index:: filestore_clvhealth_jcafb_2020_2019-10-11b
.. index:: clvsol_filestore_clvhealth_jcafb_2019-10-11b

Restaurar um backup do *CLVhealth-JCAFB-2020* no servidor "tkl-odoo12-jcafb-vm" (2019-10-11b)
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
            # gzip -d clvhealth_jcafb_2020_2019-10-11b.sql.gz

            dropdb -i clvhealth_jcafb_2020

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020
            psql -f clvhealth_jcafb_2020_2019-10-11b.sql -d clvhealth_jcafb_2020 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-10-11b.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-10-11b.tar.gz

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo desejado:

        ::

            # ***** tkl-odoo12-jcafb-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

Criar o *Verification Marker* "**Person [Confirmar Cadastro]**" (2019-10-11)
----------------------------------------------------------------------------

    #. Acessar a *View* *Person Markers*:

        * Menu de acesso:
            
            * :bi:`Verification` » :bi:`Configuration` » :bi:`Verification` » :bi:`Markers`

        * Parâmetros:

            * *Name*: **Person [Confirmar Cadastro]**
            * *Description*:

Criar o *Verification Marker* "**Person [Atualizar Cadastro]**" (2019-10-11)
----------------------------------------------------------------------------

    #. Acessar a *View* *Person Markers*:

        * Menu de acesso:
            
            * :bi:`Verification` » :bi:`Configuration` » :bi:`Verification` » :bi:`Markers`

        * Parâmetros:

            * *Name*: **Person [Atualizar Cadastro]**
            * *Description*:

Criar o *Verification Marker* "**Person [Incluir no Cadastro]**" (2019-10-11)
-----------------------------------------------------------------------------

    #. Acessar a *View* *Person Markers*:

        * Menu de acesso:
            
            * :bi:`Verification` » :bi:`Configuration` » :bi:`Verification` » :bi:`Markers`

        * Parâmetros:

            * *Name*: **Person [Incluir no Cadastro]**
            * *Description*:

Criar um backup do *CLVhealth-JCAFB-2020* (2019-10-11c)
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
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-10-11c.sql

            gzip clvhealth_jcafb_2020_2019-10-11c.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-10-11c.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-10-11c.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-10-11c.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_2019-10-11c.sql
        * /opt/odoo/clvhealth_jcafb_2020_2019-10-11c.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2019-10-11c.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-10-11c.tar.gz

.. index:: clvhealth_jcafb_2020_2019-10-11c.sql
.. index:: filestore_clvhealth_jcafb_2020_2019-10-11c
.. index:: clvsol_filestore_clvhealth_jcafb_2019-10-11c

Executar o processo de verificação para todas as Pessoas (2019-10-12)
---------------------------------------------------------------------

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Person Verification Execute` para todas as Pessoas:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Persons*:

            * Menu de acesso:
                * :bi:`Community` » :bi:`Community` » :bi:`Persons`

        #. Selecionar todas as Pessoas (**1375**)

        #. Executar a Ação ":bi:`Person Verification Execute`":

            #. Utilize o botão :bi:`Person Verification Execute` para executar a Ação.

Executar o processo de verificação para todas as Famílias (2019-10-12)
----------------------------------------------------------------------

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Family Verification Execute` para todas as Pessoas:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Families*:

            * Menu de acesso:
                * :bi:`Community` » :bi:`Community` » :bi:`Families`

        #. Selecionar todas as Pessoas (**373**)

        #. Executar a Ação ":bi:`Family Verification Execute`":

            #. Utilize o botão :bi:`Family Verification Execute` para executar a Ação.

Executar o processo de verificação para todos os Endereços (2019-10-12)
-----------------------------------------------------------------------

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Address Verification Execute` para todas as Pessoas:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Addresses*:

            * Menu de acesso:
                * :bi:`Community` » :bi:`Community` » :bi:`Addresses`

        #. Selecionar todas as Pessoas (**575**)

        #. Executar a Ação ":bi:`Address Verification Execute`":

            #. Utilize o botão :bi:`Address Verification Execute` para executar a Ação.

Executar o processo de verificação para todas as Famílias (Aux) (2019-10-12)
----------------------------------------------------------------------------

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Family (Aux) Verification Execute` para todas as Pessoas:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Families (Aux)*:

            * Menu de acesso:
                * :bi:`Community` » :bi:`Community` » :bi:`Families (Aux)`

        #. Selecionar todas as Famílias (Aux) (**261**)

        #. Executar a Ação ":bi:`Family (Aux) Verification Execute`":

            #. Utilize o botão :bi:`Family (Aux) Verification Execute` para executar a Ação.

Executar o processo de verificação para todos os Endereços (Aux) (2019-10-12)
-----------------------------------------------------------------------------

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Address (Aux) Verification Execute` para todas as Pessoas:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Addresses (Aux)*:

            * Menu de acesso:
                * :bi:`Community` » :bi:`Community` » :bi:`Addresses (Aux)`

        #. Selecionar todas os Endereços (Aux) (**429**)

        #. Executar a Ação ":bi:`Address (Aux) Verification Execute`":

            #. Utilize o botão :bi:`Address (Aux) Verification Execute` para executar a Ação.

Executar o processo de verificação para todas as Pessoas (Aux) (2019-10-12)
---------------------------------------------------------------------------

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Person (Aux) Verification Execute` para todas as Pessoas:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Persons (Aux)*:

            * Menu de acesso:
                * :bi:`Community` » :bi:`Community` » :bi:`Persons (Aux)`

        #. Selecionar todas as Pessoas (Aux) (**1344**)

        #. Executar a Ação ":bi:`Person (Aux) Verification Execute`":

            #. Utilize o botão :bi:`Person (Aux) Verification Execute` para executar a Ação.

Criar um backup do *CLVhealth-JCAFB-2020* (2019-10-12a)
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
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-10-12a.sql

            gzip clvhealth_jcafb_2020_2019-10-12a.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-10-12a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-10-12a.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-10-12a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_2019-10-12a.sql
        * /opt/odoo/clvhealth_jcafb_2020_2019-10-12a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2019-10-12a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-10-12a.tar.gz

.. index:: clvhealth_jcafb_2020_2019-10-12a.sql
.. index:: filestore_clvhealth_jcafb_2020_2019-10-12a
.. index:: clvsol_filestore_clvhealth_jcafb_2019-10-12a

Restaurar um backup do *CLVhealth-JCAFB-2020* no servidor "tkl-odoo12-jcafb-vm" (2019-10-12a)
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
            # gzip -d clvhealth_jcafb_2020_2019-10-12a.sql.gz

            dropdb -i clvhealth_jcafb_2020

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020
            psql -f clvhealth_jcafb_2020_2019-10-12a.sql -d clvhealth_jcafb_2020 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-10-12a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-10-12a.tar.gz

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo desejado:

        ::

            # ***** tkl-odoo12-jcafb-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

Criar o *Verification Marker* "**Address (Aux) [Verificar Contact Information]**" (2019-10-12)
----------------------------------------------------------------------------------------------

    #. Acessar a *View* *Person Markers*:

        * Menu de acesso:
            
            * :bi:`Verification` » :bi:`Configuration` » :bi:`Verification` » :bi:`Markers`

        * Parâmetros:

            * *Name*: **Address (Aux) [Verificar Contact Information]**
            * *Description*:

Criar o *Verification Marker* "**Address [Confirmar Cadastro]**" (2019-10-12)
-----------------------------------------------------------------------------

    #. Acessar a *View* *Address Markers*:

        * Menu de acesso:
            
            * :bi:`Verification` » :bi:`Configuration` » :bi:`Verification` » :bi:`Markers`

        * Parâmetros:

            * *Name*: **Address [Confirmar Cadastro]**
            * *Description*:

Criar o *Verification Marker* "**Address [Atualizar Cadastro]**" (2019-10-12)
-----------------------------------------------------------------------------

    #. Acessar a *View* *Address Markers*:

        * Menu de acesso:
            
            * :bi:`Verification` » :bi:`Configuration` » :bi:`Verification` » :bi:`Markers`

        * Parâmetros:

            * *Name*: **Address [Atualizar Cadastro]**
            * *Description*:

Criar o *Verification Marker* "**Address [Incluir no Cadastro]**" (2019-10-12)
------------------------------------------------------------------------------

    #. Acessar a *View* *Address Markers*:

        * Menu de acesso:
            
            * :bi:`Verification` » :bi:`Configuration` » :bi:`Verification` » :bi:`Markers`

        * Parâmetros:

            * *Name*: **Address [Incluir no Cadastro]**
            * *Description*:

Criar o *Verification Marker* "**Address [Fora da Comunidade]**" (2019-10-12)
-----------------------------------------------------------------------------

    #. Acessar a *View* *Address Markers*:

        * Menu de acesso:
            
            * :bi:`Verification` » :bi:`Configuration` » :bi:`Verification` » :bi:`Markers`

        * Parâmetros:

            * *Name*: **Address [Fora da Comunidade]**
            * *Description*:

Criar o *Verification Marker* "**Address [Desconhecido]**" (2019-10-12)
-----------------------------------------------------------------------------

    #. Acessar a *View* *Address Markers*:

        * Menu de acesso:
            
            * :bi:`Verification` » :bi:`Configuration` » :bi:`Verification` » :bi:`Markers`

        * Parâmetros:

            * *Name*: **Address [Desconhecido]**
            * *Description*:

Criar um backup do *CLVhealth-JCAFB-2020* (2019-10-12b)
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
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-10-12b.sql

            gzip clvhealth_jcafb_2020_2019-10-12b.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-10-12b.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-10-12b.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-10-12b.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_2019-10-12b.sql
        * /opt/odoo/clvhealth_jcafb_2020_2019-10-12b.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2019-10-12b.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-10-12b.tar.gz

.. index:: clvhealth_jcafb_2020_2019-10-12b.sql
.. index:: filestore_clvhealth_jcafb_2020_2019-10-12b
.. index:: clvsol_filestore_clvhealth_jcafb_2019-10-12b

Criar um backup do *CLVhealth-JCAFB-2020* (2019-10-12c)
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
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-10-12c.sql

            gzip clvhealth_jcafb_2020_2019-10-12c.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-10-12c.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-10-12c.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-10-12c.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_2019-10-12c.sql
        * /opt/odoo/clvhealth_jcafb_2020_2019-10-12c.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2019-10-12c.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-10-12c.tar.gz

.. index:: clvhealth_jcafb_2020_2019-10-12c.sql
.. index:: filestore_clvhealth_jcafb_2020_2019-10-12c
.. index:: clvsol_filestore_clvhealth_jcafb_2019-10-12c

Restaurar um backup do *CLVhealth-JCAFB-2020* no servidor "tkl-odoo12-jcafb-vm" (2019-10-12c)
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
            # gzip -d clvhealth_jcafb_2020_2019-10-12c.sql.gz

            dropdb -i clvhealth_jcafb_2020

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020
            psql -f clvhealth_jcafb_2020_2019-10-12c.sql -d clvhealth_jcafb_2020 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-10-12c.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-10-12c.tar.gz

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo desejado:

        ::

            # ***** tkl-odoo12-jcafb-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

Atualizar o(s) módulo(s) [clv_partner_entity, clv_address_aux_verification_jcafb] (2019-10-13)
----------------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/module_update`.


    #. [tkl-odoo12-jcafb-vm] Lista de Módulos:

        * clv_partner_entity
        * clv_address_aux_verification_jcafb

    #. [tkl-odoo12-jcafb-vm] **Executar** a atualização do(s) Módulo(s):

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" - m clv_partner_entity
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo desejado:

            ::

                # ***** tkl-odoo12-jcafb-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Criar um backup do *CLVhealth-JCAFB-2020* (2019-10-13a)
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
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-10-13a.sql

            gzip clvhealth_jcafb_2020_2019-10-13a.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-10-13a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-10-13a.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-10-13a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_2019-10-13a.sql
        * /opt/odoo/clvhealth_jcafb_2020_2019-10-13a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2019-10-13a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-10-13a.tar.gz

.. index:: clvhealth_jcafb_2020_2019-10-13a.sql
.. index:: filestore_clvhealth_jcafb_2020_2019-10-13a
.. index:: clvsol_filestore_clvhealth_jcafb_2019-10-13a

.. toctree::
   :maxdepth: 2
