.. raw:: html

    <style> .red {color:red} </style>

.. role:: red

.. index:: Backup do CLVhealth-JCAFB

===========================
Backup do *CLVhealth-JCAFB*
===========================

Glossário
---------
..
    .. glossary::

       odoo12-jcafb-server
          Nome do Servidor Linux em que o *CLVhelth-JCAFB* está sendo executado.

       clvhealth_jcafb_db
          Nome do Banco de Dados do *CLVhelth-JCAFB*.

       timestamp
          *Time Stamp* de identificação da versão do backup dos dados.

Procedimento
------------

O Backup do Banco de Dados pode ser restaurado executando o procedimento :doc:`/setup/clvhealth_jcafb_restore`.

    #. [tkl-odoo12-jcafb-vm] Estabelecer uma sessão ssh com o servidor **tkl-odoo12-jcafb-vm** e paralizar o *Odoo*:

        ::

            # ***** odoo12-jcafb-server
            #

            ssh odoo12-jcafb-server -l root

            /etc/init.d/odoo stop

            su odoo

    #. [tkl-odoo12-jcafb-vm] Executar os comandos de criação dos arquivos de backup:

        ::

            # ***** odoo12-jcafb-server
            #
            # data_dir = /var/lib/odoo/.local/share/Odoo
            #

            cd /opt/odoo
            pg_dump <clvhealth_jcafb_db> -Fp -U postgres -h localhost -p 5432 > <clvhealth_jcafb_db>_<time_stamp>.sql

            gzip <clvhealth_jcafb_db>_<time_stamp>.sql
            pg_dump <clvhealth_jcafb_db> -Fp -U postgres -h localhost -p 5432 > <clvhealth_jcafb_db>_<time_stamp>.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_<clvhealth_jcafb_db>_<time_stamp>.tar.gz <clvhealth_jcafb_db>

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_<time_stamp>.tar.gz clvhealth_jcafb

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo desejado:

        ::

            # ***** odoo12-jcafb-server
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    Criados os seguintes arquivos:
        * /opt/odoo/<clvhealth_jcafb_db>_<time_stamp>.sql
        * /opt/odoo/<clvhealth_jcafb_db>_<time_stamp>.sql.gz
        * /opt/odoo/filestore_<clvhealth_jcafb_db>_<time_stamp>.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_<time_stamp>.tar.gz

.. toctree::
   :maxdepth: 2
   :caption: Contents:
