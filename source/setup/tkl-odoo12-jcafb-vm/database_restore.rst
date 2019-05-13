.. raw:: html

    <style> .red {color:red} </style>

.. role:: red

.. index:: Restauração do Banco de dados (tkl-odoo12-jcafb-vm)

===================================================
Restauração do Banco de dados (tkl-odoo12-jcafb-vm)
===================================================

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

Este procedimento deve ser usado quando o backup do banco de dados tiver sido executado usando o procedimento :doc:`/setup/database_backup`.

#. [tkl-odoo12-jcafb-vm] Restaurar o backup dos dados de "**clvhealth_jcafb**", executando:

    ::

        # ***** tkl-odoo12-jcafb-vm
        #

        ssh tkl-odoo12-jcafb-vm -l root

        /etc/init.d/odoo stop

        su odoo

    ::

        # ***** tkl-odoo12-jcafb-vm
        #

        cd /opt/odoo
        # gzip -d clvhealth_jcafb_<time_stamp>.sql.gz

        dropdb -i clvhealth_jcafb

        createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb
        psql -f clvhealth_jcafb_<time_stamp>.sql -d clvhealth_jcafb -U postgres -h localhost -p 5432 -q

        # mkdir /var/lib/odoo/.local/share/Odoo/filestore
        cd /var/lib/odoo/.local/share/Odoo/filestore
        rm -rf clvhealth_jcafb
        tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_<time_stamp>.tar.gz

        # mkdir /opt/odoo/clvsol_filestore
        cd /opt/odoo/clvsol_filestore
        rm -rf clvhealth_jcafb
        tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_<time_stamp>.tar.gz

        cd /opt/odoo
        /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    ::

        # ***** tkl-odoo12-jcafb-vm
        #

        ^C

        exit

        /etc/init.d/odoo start

.. toctree::
   :maxdepth: 2
   :caption: Contents:
