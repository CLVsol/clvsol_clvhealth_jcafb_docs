.. raw:: html

    <style> .red {color:red} </style>

.. role:: red

.. index:: Backup do Banco de Dados (tkl-odoo12-jcafb-vm)

==============================================
Backup do Banco de Dados (tkl-odoo12-jcafb-vm)
==============================================

Glossário
---------
    .. glossary::

       tkl-odoo12-jcafb-vm
          Nome do Servidor Linux em que o *CLVhelth_JCAFB* está sendo executado.

       clvhealth_jcafb
          Nome do Banco de Dados do *CLVhelth_JCAFB*.

       timestamp
          *Time Stamp* de identificação da versão do backup dos dados.

Procedimento
------------

O Backup do Banco de Dados pode ser restaurado executando o procedimento :doc:`/setup/database_restore`.

#. [tkl-odoo12-jcafb-vm] Criar um backup do Banco de Dados "**clvhealth_jcafb**", executando:

    ::

        # ***** tkl-odoo12-jcafb-vm
        #

        ssh tkl-odoo12-jcafb-vm -l root

        /etc/init.d/odoo stop

        su odoo

    ::

        # ***** tkl-odoo12-jcafb-vm
        #
        # data_dir = /var/lib/odoo/.local/share/Odoo
        #

        cd /opt/odoo
        pg_dump clvhealth_jcafb -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_<time_stamp>.sql

        gzip clvhealth_jcafb_<time_stamp>.sql
        pg_dump clvhealth_jcafb -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_<time_stamp>.sql

        cd /var/lib/odoo/.local/share/Odoo/filestore
        tar -czvf /opt/odoo/filestore_clvhealth_jcafb_<time_stamp>.tar.gz clvhealth_jcafb

        cd /opt/odoo/clvsol_filestore
        tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_<time_stamp>.tar.gz clvhealth_jcafb

    ::

        # ***** tkl-odoo12-jcafb-vm
        #

        cd /opt/odoo
        /usr/bin/odoo -c /etc/odoo/odoo-man.conf

        ^C

        exit

        /etc/init.d/odoo start

    Criados os seguintes arquivos:
        * /opt/odoo/clvhealth_jcafb_<time_stamp>.sql
        * /opt/odoo/clvhealth_jcafb_<time_stamp>.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_<time_stamp>.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_<time_stamp>.tar.gz

.. toctree::
   :maxdepth: 2
   :caption: Contents:
