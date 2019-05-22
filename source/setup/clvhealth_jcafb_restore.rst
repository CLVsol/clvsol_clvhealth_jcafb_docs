.. raw:: html

    <style> .red {color:red} </style>

.. role:: red

.. index:: Restauração do CLVhealth-JCAFB

================================
Restauração do *CLVhealth-JCAFB*
================================

Glossário
---------
    .. glossary::

       odoo12-jcafb-server
          Nome do Servidor Linux em que o *CLVhelth_JCAFB* está sendo executado.

       clvhealth_jcafb_db
          Nome do Banco de Dados do *CLVhelth_JCAFB*.

       timestamp
          *Time Stamp* de identificação da versão do backup dos dados.

Procedimento
------------

Este procedimento deve ser usado quando o backup do banco de dados tiver sido executado usando o procedimento :doc:`/setup/clvhealth_jcafb_backup`.

    #. [odoo12-jcafb-server] Estabelecer uma sessão ssh com o servidor **tkl-odoo12-jcafb-vm** e paralizar o *Odoo*:

        ::

            # ***** odoo12-jcafb-server
            #

            ssh odoo12-jcafb-server -l root

            /etc/init.d/odoo stop

            su odoo

    #. [odoo12-jcafb-server] Executar os comandos de restauração dos arquivos de backup:

        ::

            # ***** odoo12-jcafb-server
            #

            cd /opt/odoo
            # gzip -d <clvhealth_jcafb_db>_<time_stamp>.sql.gz

            dropdb -i <clvhealth_jcafb_db>

            createdb -O odoo -E UTF8 -T template0 <clvhealth_jcafb_db>
            psql -f <clvhealth_jcafb_db>_<time_stamp>.sql -d <clvhealth_jcafb_db> -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf <clvhealth_jcafb_db>
            tar -xzvf /opt/odoo/filestore_<clvhealth_jcafb_db>_<time_stamp>.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_<time_stamp>.tar.gz

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo desejado:

        ::

            # ***** odoo12-jcafb-server
            #

            ^C

            exit

            /etc/init.d/odoo start

.. toctree::
   :maxdepth: 2
   :caption: Contents:
