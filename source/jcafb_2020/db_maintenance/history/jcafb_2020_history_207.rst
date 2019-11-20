.. raw:: html

    <style> .red {color:red} </style>

.. role:: red

============================
2019-11-(04-20) (JCAFB-2020)
============================

Restaurar um backup do *CLVhealth-JCAFB-2020* [clvheatlh-jcafb-2020-aws-pro] (2019-11-03a)
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
            gzip -d clvhealth_jcafb_2020_2019-11-03a.sql.gz

            dropdb -i clvhealth_jcafb_2020

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020
            psql -f clvhealth_jcafb_2020_2019-11-03a.sql -d clvhealth_jcafb_2020 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-11-03a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-11-03a.tar.gz

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

Criar um backup do *CLVhealth-JCAFB-2020* (2019-11-04a)
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
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-11-04a.sql

            gzip clvhealth_jcafb_2020_2019-11-04a.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-11-04a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-11-04a.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-11-04a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_2019-11-04a.sql
        * /opt/odoo/clvhealth_jcafb_2020_2019-11-04a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2019-11-04a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-11-04a.tar.gz

Restaurar um backup do *CLVhealth-JCAFB-2020* [clvheatlh-jcafb-2020-aws-pro] (2019-11-05a)
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
            gzip -d clvhealth_jcafb_2020_2019-11-05a.sql.gz

            dropdb -i clvhealth_jcafb_2020

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020
            psql -f clvhealth_jcafb_2020_2019-11-05a.sql -d clvhealth_jcafb_2020 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-11-05a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-11-05a.tar.gz

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

Criar um backup do *CLVhealth-JCAFB-2020* (2019-11-05b)
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
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-11-05b.sql

            gzip clvhealth_jcafb_2020_2019-11-05b.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-11-05b.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-11-05b.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-11-05b.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_2019-11-05b.sql
        * /opt/odoo/clvhealth_jcafb_2020_2019-11-05b.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2019-11-05b.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-11-05b.tar.gz

Restaurar um backup do *CLVhealth-JCAFB-2020* [clvheatlh-jcafb-2020-aws-pro] (2019-11-11b)
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
            gzip -d clvhealth_jcafb_2020_2019-11-11b.sql.gz

            dropdb -i clvhealth_jcafb_2020

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020
            psql -f clvhealth_jcafb_2020_2019-11-11b.sql -d clvhealth_jcafb_2020 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-11-11b.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-11-11b.tar.gz

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

Criar um backup do *CLVhealth-JCAFB-2020* (2019-11-18a)
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
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-11-18a.sql

            gzip clvhealth_jcafb_2020_2019-11-18a.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-11-18a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-11-18a.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-11-18a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_2019-11-18a.sql
        * /opt/odoo/clvhealth_jcafb_2020_2019-11-18a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2019-11-18a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-11-18a.tar.gz

Criar um backup do *CLVhealth-JCAFB-2020* (2019-11-19a)
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
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-11-19a.sql

            gzip clvhealth_jcafb_2020_2019-11-19a.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-11-19a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-11-19a.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-11-19a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_2019-11-19a.sql
        * /opt/odoo/clvhealth_jcafb_2020_2019-11-19a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2019-11-19a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-11-19a.tar.gz

Criar um backup do *CLVhealth-JCAFB-2020* (2019-11-19b)
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
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-11-19b.sql

            gzip clvhealth_jcafb_2020_2019-11-19b.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-11-19b.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-11-19b.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-11-19b.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_2019-11-19b.sql
        * /opt/odoo/clvhealth_jcafb_2020_2019-11-19b.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2019-11-19b.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-11-19b.tar.gz

Restaurar um backup do *CLVhealth-JCAFB-2020* [clvheatlh-jcafb-2020-aws-pro] (2019-11-19c)
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
            gzip -d clvhealth_jcafb_2020_2019-11-19c.sql.gz

            dropdb -i clvhealth_jcafb_2020

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020
            psql -f clvhealth_jcafb_2020_2019-11-19c.sql -d clvhealth_jcafb_2020 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-11-19c.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-11-19c.tar.gz

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

:red:`(Não Executado)` Restaurar um backup do *CLVhealth-JCAFB-2020* [clvheatlh-jcafb-2020-aws-tst] (2019-11-03a)
-----------------------------------------------------------------------------------------------------------------

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
            gzip -d clvhealth_jcafb_2020_2019-11-03a.sql.gz

            dropdb -i clvhealth_jcafb_2020

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020
            psql -f clvhealth_jcafb_2020_2019-11-03a.sql -d clvhealth_jcafb_2020 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-11-03a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-11-03a.tar.gz

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
