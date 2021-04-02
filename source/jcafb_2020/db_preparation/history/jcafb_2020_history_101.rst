.. raw:: html

    <style> .red {color:red} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: bi

=========================================================================================
[2019-07-22] - Preparação do Banco de Dados - JCAFB-2020 - Servidor [tkl-odoo12-jcafb-vm]
=========================================================================================

Restaurar um backup do *CLVhealth-JCAFB-2020* no servidor "tkl-odoo12-jcafb-vm" (2019-07-14b)
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
            # gzip -d clvhealth_jcafb_2020_2019-07-14b.sql.gz

            dropdb -i clvhealth_jcafb_2020

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020
            psql -f clvhealth_jcafb_2020_2019-07-14b.sql -d clvhealth_jcafb_2020 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-07-14b.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-07-14b.tar.gz

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo desejado:

        ::

            # ***** tkl-odoo12-jcafb-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

Atualizar o(s) módulo(s) [clv_employee] (2019-07-22]
----------------------------------------------------

    * Referência: :doc:`/setup/module_update`.


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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" - m clv_employee

            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo desejado:

            ::

                # ***** tkl-odoo12-jcafb-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Preparar as "*Phases*" para a JCAFB-2020 (2019-07-22)
-----------------------------------------------------

    #. Excluir as Fases **JCAFB-2019*** e **JCAFB-2019****:

        #. Acessar a *View* *Phases*:

            * Menu de acesso:
                * :bi:`Base` » :bi:`Configuration` » :bi:`Phases`

        #. Selecionar os registros referentes às Fases **JCAFB-2019*** e **JCAFB-2019****.

        #. Executar a Ação "**Excluir**":

    #. Incluir a nova Fase **JCAFB-2020**:

        #. Acessar a *View* *Phases*:

            * Menu de acesso:
                * :bi:`Base` » :bi:`Configuration` » :bi:`Phases`

        #. Incluir uma nova Fase:

            * Parâmetros editados:
                * *Phase*: **JCAFB-2020**

Preparar os "*Global Settings*" para a JCAFB-2020 (2019-07-22)
--------------------------------------------------------------

    #. Acessar a *View* *Global Settings*:

        * Menu de acesso:
            * :bi:`Base` » :bi:`Global Settings` » :bi:`Global Settings`

        #. Configurar o parâmetro :bi:`Phase` » :bi:`Phase`: **JCAFB-2020**

        #. Configurar o parâmetro :bi:`Person` » :bi:`Reference Date`: **31/01/2020**

Preparar os "*Employees*" para a JCAFB-2020 (2019-07-22)
--------------------------------------------------------

    #. Acessar a *View* *Funcionários*:

        * Menu de acesso:
            * :bi:`Funcionários` » :bi:`Employees` » :bi:`Employees`

        #. Configurar o parâmetro :bi:`Phase` como **JCAFB-2020** para todos os Employees da **JCAFB-2020**.

        #. Configurar o parâmetro **Cargo** para todos os Employees da **JCAFB-2020**.

        #. Remover o parâmetro :bi:`Department` de todos os Employees.

        #. Resetar a **Senha** de todos os Coordenadores novos da **JCAFB-2020**.

Redefinir a senha do usuário de referência da JCAFB-2020 (2019-07-22)
---------------------------------------------------------------------

    #. Redefinir a senha do usuário de referência:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Users*:

            * Menu de acesso:
                * :bi:`Configurações` » :bi:`Utilizadores e Empresas` » :bi:`Usuários`

        #. Selecionar o usuário de referência.

        #. Executar a Ação "**Alterar Senha**":

            * Parâmetros:
                * Nova Senha: *******
            
            #. Utilize o botão "**Alterar Senha**" para executar a ação.

Criar um backup do *CLVhealth-JCAFB-2020* (2019-07-22a)
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
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-07-22a.sql

            gzip clvhealth_jcafb_2020_2019-07-22a.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-07-22a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-07-22a.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-07-22a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_2019-07-22a.sql
        * /opt/odoo/clvhealth_jcafb_2020_2019-07-22a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2019-07-22a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-07-22a.tar.gz

.. index:: clvhealth_jcafb_2020_2019-07-22a.sql
.. index:: filestore_clvhealth_jcafb_2020_2019-07-22a
.. index:: clvsol_filestore_clvhealth_jcafb_2019-07-22a

.. toctree::
   :maxdepth: 2
