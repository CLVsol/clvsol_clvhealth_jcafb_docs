.. raw:: html

    <style> .red {color:red} </style>

.. role:: red

============================
2019-10-(01-07) (JCAFB-2020)
============================

Criar um backup do *CLVhealth-JCAFB-2020* (2019-10-01a)
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
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-10-01a.sql

            gzip clvhealth_jcafb_2020_2019-10-01a.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-10-01a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-10-01a.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-10-01a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_2019-10-01a.sql
        * /opt/odoo/clvhealth_jcafb_2020_2019-10-01a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2019-10-01a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-10-01a.tar.gz

.. index:: clvhealth_jcafb_2020_2019-10-01a.sql
.. index:: filestore_clvhealth_jcafb_2020_2019-10-01a
.. index:: clvsol_filestore_clvhealth_jcafb_2019-10-01a

Restaurar um backup do *CLVhealth-JCAFB-2020* [clvheatlh-jcafb-2020-aws-pro] (2019-10-01b)
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
            gzip -d clvhealth_jcafb_2020_2019-10-01b.sql.gz

            dropdb -i clvhealth_jcafb_2020

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020
            psql -f clvhealth_jcafb_2020_2019-10-01b.sql -d clvhealth_jcafb_2020 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-10-01b.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-10-01b.tar.gz

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

Criar um backup do *CLVhealth-JCAFB-2020* (2019-10-03a)
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
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-10-03a.sql

            gzip clvhealth_jcafb_2020_2019-10-03a.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-10-03a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-10-03a.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-10-03a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_2019-10-03a.sql
        * /opt/odoo/clvhealth_jcafb_2020_2019-10-03a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2019-10-03a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-10-03a.tar.gz

.. index:: clvhealth_jcafb_2020_2019-10-03a.sql
.. index:: filestore_clvhealth_jcafb_2020_2019-10-03a
.. index:: clvsol_filestore_clvhealth_jcafb_2019-10-03a

Criar um backup do *CLVhealth-JCAFB-2020* (2019-10-04a)
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
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-10-04a.sql

            gzip clvhealth_jcafb_2020_2019-10-04a.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-10-04a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-10-04a.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-10-04a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_2019-10-04a.sql
        * /opt/odoo/clvhealth_jcafb_2020_2019-10-04a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2019-10-04a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-10-04a.tar.gz

.. index:: clvhealth_jcafb_2020_2019-10-04a.sql
.. index:: filestore_clvhealth_jcafb_2020_2019-10-04a
.. index:: clvsol_filestore_clvhealth_jcafb_2019-10-04a

Criar um backup do *CLVhealth-JCAFB-2020* (2019-10-07a)
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
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-10-07a.sql

            gzip clvhealth_jcafb_2020_2019-10-07a.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-10-07a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-10-07a.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-10-07a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_2019-10-07a.sql
        * /opt/odoo/clvhealth_jcafb_2020_2019-10-07a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2019-10-07a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-10-07a.tar.gz

.. index:: clvhealth_jcafb_2020_2019-10-07a.sql
.. index:: filestore_clvhealth_jcafb_2020_2019-10-07a
.. index:: clvsol_filestore_clvhealth_jcafb_2019-10-07a

:red:`(Não Executado)` Restaurar um backup do *CLVhealth-JCAFB-2020* [clvheatlh-jcafb-2020-aws-tst] (2019-10-01b)
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
            gzip -d clvhealth_jcafb_2020_2019-10-01b.sql.gz

            dropdb -i clvhealth_jcafb_2020

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020
            psql -f clvhealth_jcafb_2020_2019-10-01b.sql -d clvhealth_jcafb_2020 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-10-01b.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-10-01b.tar.gz

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
