.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

============================
2020-01-(06-07) (JCAFB-2020)
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

.. index:: clvhealth_jcafb_2020_2020-01-06a.sql
.. index:: filestore_clvhealth_jcafb_2020_2020-01-06a
.. index:: clvsol_filestore_clvhealth_jcafb_2020-01-06a

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

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* **Parâmetros do Sistema**:

            * Menu de acesso:
                * **Configurações** » **Técnico** » **Parâmetros** » **Parâmetros do Sistema**

        #. Pesquisar pelo registro com a **Chave** "**web.base.url**";

        #. Editar o registro apresentado (**Chave**: "**web.base.url**")

        #. Alterar o campo **Valor** para:

            * "**http://clvheatlh-jcafb-2020-aws-tst.tklapp.com**".

        #. Salvar o registro editado.

.. toctree::
   :maxdepth: 2
