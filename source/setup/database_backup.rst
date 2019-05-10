.. raw:: html

    <style> .red {color:red} </style>

.. role:: red

===============
Database backup
===============

#. [tkl-odoo12-dev-vm] Criar um backup do banco de dados "**clvhealth_jcafb**", executando:

    ::

        # ***** tkl-odoo12-dev-vm
        #

        ssh tkl-odoo12-dev-vm -l root

        /etc/init.d/odoo stop

        su odoo

    ::

        # ***** tkl-odoo12-dev-vm
        #
        # data_dir = /var/lib/odoo/.local/share/Odoo
        #

        cd /opt/odoo
        pg_dump clvhealth_jcafb -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2019-05-15a.sql

        gzip clvhealth_jcafb_2019-05-15a.sql
        pg_dump clvhealth_jcafb -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2019-05-15a.sql

        cd /var/lib/odoo/.local/share/Odoo/filestore
        tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2019-05-15a.tar.gz clvhealth_jcafb

        cd /opt/odoo/clvsol_filestore
        tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-05-15a.tar.gz clvhealth_jcafb

    ::

        # ***** tkl-odoo12-dev-vm
        #

        cd /opt/odoo
        /usr/bin/odoo -c /etc/odoo/odoo-man.conf

        ^C

        exit

        /etc/init.d/odoo start

    Criados os seguintes arquivos:
        * /opt/odoo/clvhealth_jcafb_2019-05-15a.sql
        * /opt/odoo/clvhealth_jcafb_2019-05-15a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2019-05-15a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-05-15a.tar.gz

.. toctree::
   :maxdepth: 2
   :caption: Contents:
