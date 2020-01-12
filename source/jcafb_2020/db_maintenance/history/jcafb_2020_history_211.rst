.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

============================
2020-01-(06-12) (JCAFB-2020)
============================

Criar um backup do *CLVhealth-JCAFB-2020* (2020-01-06a)
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
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2020-01-06a.sql

            gzip clvhealth_jcafb_2020_2020-01-06a.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2020-01-06a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-06a.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-06a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_2020-01-06a.sql
        * /opt/odoo/clvhealth_jcafb_2020_2020-01-06a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-06a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-06a.tar.gz

Restaurar um backup do *CLVhealth-JCAFB-2020* [clvheatlh-jcafb-2020-aws-tst] (2020-01-06a)
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
            gzip -d clvhealth_jcafb_2020_2020-01-06a.sql.gz

            dropdb -i clvhealth_jcafb_2020

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020
            psql -f clvhealth_jcafb_2020_2020-01-06a.sql -d clvhealth_jcafb_2020 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-06a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-06a.tar.gz

    #. [clvheatlh-jcafb-2020-aws-tst] **Atualizar** os fontes do tstjeto

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

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `clvheatlh-jcafb-2020-vm-pro <https://clvheatlh-jcafb-2020-vm-pro>`_

        #. Acessar a *View* **Parâmetros do Sistema**:

            * Menu de acesso:
                * **Configurações** » **Técnico** » **Parâmetros** » **Parâmetros do Sistema**

        #. Pesquisar pelo registro com a **Chave** "**web.base.url**";

        #. Editar o registro apresentado (**Chave**: "**web.base.url**")

        #. Alterar o campo **Valor** para:

            * "**http://clvheatlh-jcafb-2020-aws-tst.tklapp.com**".

        #. Salvar o registro editado.

Criar um backup do *CLVhealth-JCAFB-2020* (2020-01-09a)
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
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2020-01-09a.sql

            gzip clvhealth_jcafb_2020_2020-01-09a.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2020-01-09a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-09a.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-09a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_2020-01-09a.sql
        * /opt/odoo/clvhealth_jcafb_2020_2020-01-09a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-09a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-09a.tar.gz

Criar um backup do *CLVhealth-JCAFB-2020* (2020-01-09b)
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
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2020-01-09b.sql

            gzip clvhealth_jcafb_2020_2020-01-09b.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2020-01-09b.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-09b.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-09b.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_2020-01-09b.sql
        * /opt/odoo/clvhealth_jcafb_2020_2020-01-09b.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-09b.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-09b.tar.gz

Atualizar os fontes do projeto (2020-01-09)
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

Atualizar o(s) módulo(s) [clv_event, clv_event_jcafb] (2020-01-09)
------------------------------------------------------------------

    * Referência: :doc:`/setup/module_update`.


    #. [clvheatlh-jcafb-2020-vm-pro] Lista de Módulos:

        * clv_event
        * clv_event_jcafb

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" - m clv_event
            
        #. Retornar a execução do *Odoo* do servidor **clvheatlh-jcafb-2020-vm-pro** ao modo desejado:

            ::

                # ***** clvheatlh-jcafb-2020-vm-pro (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Criar um backup do *CLVhealth-JCAFB-2020* (2020-01-09c)
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
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2020-01-09c.sql

            gzip clvhealth_jcafb_2020_2020-01-09c.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2020-01-09c.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-09c.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-09c.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_2020-01-09c.sql
        * /opt/odoo/clvhealth_jcafb_2020_2020-01-09c.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-09c.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-09c.tar.gz

Restaurar um backup do *CLVhealth-JCAFB-2020* [clvheatlh-jcafb-2020-aws-tst] (2020-01-09c)
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
            gzip -d clvhealth_jcafb_2020_2020-01-09c.sql.gz

            dropdb -i clvhealth_jcafb_2020

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020
            psql -f clvhealth_jcafb_2020_2020-01-09c.sql -d clvhealth_jcafb_2020 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-09c.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-09c.tar.gz

    #. [clvheatlh-jcafb-2020-aws-tst] **Atualizar** os fontes do tstjeto

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

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `clvheatlh-jcafb-2020-vm-pro <https://clvheatlh-jcafb-2020-vm-pro>`_

        #. Acessar a *View* **Parâmetros do Sistema**:

            * Menu de acesso:
                * **Configurações** » **Técnico** » **Parâmetros** » **Parâmetros do Sistema**

        #. Pesquisar pelo registro com a **Chave** "**web.base.url**";

        #. Editar o registro apresentado (**Chave**: "**web.base.url**")

        #. Alterar o campo **Valor** para:

            * "**http://clvheatlh-jcafb-2020-aws-tst.tklapp.com**".

        #. Salvar o registro editado.

Criar um backup do *CLVhealth-JCAFB-2020* (2020-01-11a)
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
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2020-01-11a.sql

            gzip clvhealth_jcafb_2020_2020-01-11a.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2020-01-11a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-11a.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-11a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_2020-01-11a.sql
        * /opt/odoo/clvhealth_jcafb_2020_2020-01-11a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-11a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-11a.tar.gz

Atualizar os fontes do projeto (2020-01-12)
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

Atualizar o(s) módulo(s) [clv_person_aux_jcafb] (2020-01-12)
------------------------------------------------------------

    * Referência: :doc:`/setup/module_update`.


    #. [clvheatlh-jcafb-2020-vm-pro] Lista de Módulos:

        * clv_person_aux_jcafb

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" - m clv_person_aux_jcafb
            
        #. Retornar a execução do *Odoo* do servidor **clvheatlh-jcafb-2020-vm-pro** ao modo desejado:

            ::

                # ***** clvheatlh-jcafb-2020-vm-pro (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Criar um backup do *CLVhealth-JCAFB-2020* (2020-01-12a)
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
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2020-01-12a.sql

            gzip clvhealth_jcafb_2020_2020-01-12a.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2020-01-12a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-12a.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-12a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_2020-01-12a.sql
        * /opt/odoo/clvhealth_jcafb_2020_2020-01-12a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-12a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-12a.tar.gz

.. index:: clvhealth_jcafb_2020_2020-01-12a.sql
.. index:: filestore_clvhealth_jcafb_2020_2020-01-12a
.. index:: clvsol_filestore_clvhealth_jcafb_2020-01-12a

.. toctree::
   :maxdepth: 2
