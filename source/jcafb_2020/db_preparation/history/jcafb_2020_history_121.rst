.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

==============================================================================================
[2019-12-(02-04)] - Preparação do Banco de Dados - JCAFB-2020 - Servidor [tkl-odoo12-jcafb-vm]
==============================================================================================

Restaurar um backup do *CLVhealth-JCAFB-2020* no servidor "tkl-odoo12-jcafb-vm" (2019-11-30a)
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
            # gzip -d clvhealth_jcafb_2020_2019-11-30a.sql.gz

            dropdb -i clvhealth_jcafb_2020

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020
            psql -f clvhealth_jcafb_2020_2019-11-30a.sql -d clvhealth_jcafb_2020 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-11-30a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-11-30a.tar.gz

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo desejado:

        ::

            # ***** tkl-odoo12-jcafb-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

Criar um backup do *CLVhealth-JCAFB-2020* (2019-12-03a)
-------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_backup`.

    #. [clvheatlh-jcafb-2020-aws-pro] Estabelecer uma sessão ssh com o servidor **clvheatlh-jcafb-2020-aws-pro** e paralizar o *Odoo*:

        ::

            # ***** clvheatlh-jcafb-2020-aws-pro
            #

            ssh clvheatlh-jcafb-2020-aws-pro -l root

            /etc/init.d/odoo stop

            su odoo

    #. [clvheatlh-jcafb-2020-aws-pro] Executar os comandos de criação dos arquivos de backup:

        ::

            # ***** clvheatlh-jcafb-2020-aws-pro
            #
            # data_dir = /var/lib/odoo/.local/share/Odoo
            #

            cd /opt/odoo
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-12-03a.sql

            gzip clvhealth_jcafb_2020_2019-12-03a.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-12-03a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-12-03a.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-12-03a.tar.gz clvhealth_jcafb

    #. Retornar a execução do *Odoo* do servidor **clvheatlh-jcafb-2020-aws-pro** ao modo desejado:

        ::

            # ***** clvheatlh-jcafb-2020-aws-pro
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    Criados os seguintes arquivos:
        * /opt/odoo/clvhealth_jcafb_2020_2019-12-03a.sql
        * /opt/odoo/clvhealth_jcafb_2020_2019-12-03a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2019-12-03a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-12-03a.tar.gz

Restaurar um backup do *CLVhealth-JCAFB-2020* no servidor "tkl-odoo12-jcafb-vm" (2019-12-03a)
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
            # gzip -d clvhealth_jcafb_2020_2019-12-03a.sql.gz

            dropdb -i clvhealth_jcafb_2020

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020
            psql -f clvhealth_jcafb_2020_2019-12-03a.sql -d clvhealth_jcafb_2020 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-12-03a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-12-03a.tar.gz

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo desejado:

        ::

            # ***** tkl-odoo12-jcafb-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

Atualizar o(s) módulo(s) [clv_lab_test_jcafb_2020] (2019-12-04)
---------------------------------------------------------------

    * Referência: :doc:`/setup/module_update`.


    #. [tkl-odoo12-jcafb-vm] Lista de Módulos:

        * clv_lab_test_jcafb_2020

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" - m clv_lab_test_jcafb_2020
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo desejado:

            ::

                # ***** tkl-odoo12-jcafb-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Criar um backup do *CLVhealth-JCAFB-2020* (2019-12-04a)
-------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_backup`.

    #. [clvheatlh-jcafb-2020-aws-pro] Estabelecer uma sessão ssh com o servidor **clvheatlh-jcafb-2020-aws-pro** e paralizar o *Odoo*:

        ::

            # ***** clvheatlh-jcafb-2020-aws-pro
            #

            ssh clvheatlh-jcafb-2020-aws-pro -l root

            /etc/init.d/odoo stop

            su odoo

    #. [clvheatlh-jcafb-2020-aws-pro] Executar os comandos de criação dos arquivos de backup:

        ::

            # ***** clvheatlh-jcafb-2020-aws-pro
            #
            # data_dir = /var/lib/odoo/.local/share/Odoo
            #

            cd /opt/odoo
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-12-04a.sql

            gzip clvhealth_jcafb_2020_2019-12-04a.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-12-04a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-12-04a.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-12-04a.tar.gz clvhealth_jcafb

    #. Retornar a execução do *Odoo* do servidor **clvheatlh-jcafb-2020-aws-pro** ao modo desejado:

        ::

            # ***** clvheatlh-jcafb-2020-aws-pro
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    Criados os seguintes arquivos:
        * /opt/odoo/clvhealth_jcafb_2020_2019-12-04a.sql
        * /opt/odoo/clvhealth_jcafb_2020_2019-12-04a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2019-12-04a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-12-04a.tar.gz

.. index:: clvhealth_jcafb_2020_2019-12-04a.sql
.. index:: filestore_clvhealth_jcafb_2020_2019-12-04a
.. index:: clvsol_filestore_clvhealth_jcafb_2019-12-04a

:red:`(Não Executado)` Configurar as permissões do usuário de referência da JCAFB-2020 (2019-10-25)
---------------------------------------------------------------------------------------------------

    #. Configurar as permissões do usuário de referência:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Users*:

            * Menu de acesso:
                * :bi:`Configurações` » :bi:`Utilizadores e Empresas` » :bi:`Usuários`

        #. Selecionar o usuário de referência.

        #. Configurar as permissões:

            * *Address*: :bi:`User (Address)`
            * *Address (Aux)*: :bi:`Manager (Address (Aux))`
            * Administração:  
            * *Community*: :bi:`User (Community)`
            * *Event*: :bi:`User (Event)`
            * :green:`(Novo)` *Export*: :bi:`User (Export)`
            * *External Sync*: :bi:`User (External Sync)`
            * *Family*: :bi:`User (Family)`
            * *Family (Aux)*: :bi:`Manager (Family (Aux))`
            * *File System User*: :bi:`(File System)`
            * *Funcionários*: :bi:`Oficial`
            * *Global Tag*: :bi:`User (Global Tag)`
            * *Media File*: :bi:`User (Media File)`
            * *Aux*: :bi:`User (Aux)`
            * *Person*: :bi:`User (Person)`
            * *Person (Aux)*: :bi:`Manager (Person (Aux))`
            * *Pesquisa*: :bi:`Utilizador`
            * *Phase*: :bi:`User (Phase)`
            * :green:`(Novo)` *Processing*: :bi:`User (Processing)`
            * :green:`(Novo)` *Report*: :bi:`User (Report)`
            * *Set*: :bi:`User (Set)`
            * *Survey*: :bi:`User (Survey)`
            * :green:`(Novo)` *Verification*: :bi:`User (Verification)`
            *
            * *Lab Test*:
                * :bi:`User (Lab Test) ​`
            *
            * *Base*:
                * :bi:`Annotation User (Base)`,
                * :bi:`Log User (Base)`,
                * :bi:`Register User (Base)`,
                * :bi:`User (Base)`,
                * :bi:`Super User (Base)`,
                * :bi:`Manager (Base)` ​
            *
            * *Document*:
                * :bi:`User (Document)` ​
            
:red:`(Não Executado)` Atualizar as permissões de todos os Usuários da JCAFB-2020 (2019-10-25)
----------------------------------------------------------------------------------------------

    * Referência: :doc:`/user_guide/employee/employee_user_groups_updt`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação *Employee User Groups Update* para os *Employees* da JCAFB-2020:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Employees*:

            * Menu de acesso:
                * *Funcionários* » *Employees* » *Employees*

        #. Selecionar os *Employees* da JCAFB-2020 (**18**)

        #. Exercutar a Ação "**Employee User Groups Update**":

            #. Selecionar o :bi:`Reference Employee`: Usuário de referência (selecionado no ítem anterior).

            #. Selecionar o parâmetro :bi:`Access Rights:` » :bi:`Set`.

            #. Precionar o botão :bi:`Get Reference Employee Access Rights`.

            #. Utilize o botão :bi:`Update` para executar a Ação.

.. toctree::
   :maxdepth: 2
