.. raw:: html

    <style> .red {color:red} </style>

.. role:: red

=======================
2019-09-30 (JCAFB-2020)
=======================

Criar um backup do *CLVhealth-JCAFB-2020* (2019-09-30a)
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
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-09-30a.sql

            gzip clvhealth_jcafb_2020_2019-09-30a.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-09-30a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-09-30a.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-09-30a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_2019-09-30a.sql
        * /opt/odoo/clvhealth_jcafb_2020_2019-09-30a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2019-09-30a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-09-30a.tar.gz

.. index:: clvhealth_jcafb_2020_2019-09-30a.sql
.. index:: filestore_clvhealth_jcafb_2020_2019-09-30a
.. index:: clvsol_filestore_clvhealth_jcafb_2019-09-30a
