.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

============================
2020-01-(16-17) (JCAFB-2020)
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

.. index:: clvhealth_jcafb_2020_2020-01-16b.sql
.. index:: filestore_clvhealth_jcafb_2020_2020-01-16b
.. index:: clvsol_filestore_clvhealth_jcafb_2020-01-16b

.. toctree::
   :maxdepth: 2
