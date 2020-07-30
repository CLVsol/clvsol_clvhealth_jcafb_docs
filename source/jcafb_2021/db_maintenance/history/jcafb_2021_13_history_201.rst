.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .blue {color:blue} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: blue
.. role:: bi

=============================================
Manutenção do Banco de Dados - JCAFB-2021v-13
=============================================

[clvheatlh-jcafb-2021v-13-aws-tst] Restaurar um backup do banco de dados *CLVhealth-JCAFB-2021v-13* (2020-07-12b)
-----------------------------------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_restore`.

    #. [clvheatlh-jcafb-2021v-13-aws-tst] Estabelecer uma sessão ssh com o servidor **clvheatlh-jcafb-2021v-13-aws-tst** e paralizar o *Odoo*:

        ::

            # ***** clvheatlh-jcafb-2021v-13-aws-tst
            #

            ssh clvheatlh-jcafb-2021v-13-aws-tst -l root

            /etc/init.d/odoo stop

            su odoo

    #. [clvheatlh-jcafb-2021v-13-aws-tst] Executar os comandos de restauração dos arquivos de backup:

        ::

            # ***** clvheatlh-jcafb-2021v-13-aws-tst
            #

            cd /opt/odoo
            # gzip -d clvhealth_jcafb_2021v_13_2020-07-12b.sql.gz

            dropdb -i clvhealth_jcafb_2021v_13

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2021v_13
            psql -f clvhealth_jcafb_2021v_13_2020-07-12b.sql -d clvhealth_jcafb_2021v_13 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2021v_13
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2021v_13_2020-07-12b.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021v_13_2020-07-12b.tar.gz

    #. Retornar a execução do *Odoo* do servidor **clvheatlh-jcafb-2021v-13-aws-tst** ao modo desejado:

        ::

            # ***** clvheatlh-jcafb-2021v-13-aws-tst
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    #. [clvheatlh-jcafb-2021v-13-aws-tst] Configurar o parâmetro "**web.base.url**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `clvheatlh-jcafb-2021v-13-aws-tst <https://clvheatlh-jcafb-2021v-13-aws-tst>`_

        #. Acessar a *View* **Parâmetros do Sistema**:

            * Menu de acesso:
                
                * **Configurações** » **Técnico** » **Parâmetros** » **Parâmetros do Sistema**

        #. Pesquisar pelo registro com a **Chave** "**web.base.url**"

        #. Editar o registro apresentado (**Chave**: "**web.base.url**")

        #. Alterar o campo **Valor** para:

            * "**http://clvheatlh-jcafb-2021v-13-aws-tst.tklapp.com**".

        #. Salvar o registro editado.

Atualizar os fontes do projeto (2020-07-16)
-------------------------------------------

    #. **Atualizar** os fontes do projeto

        ::

            ssh clvheatlh-jcafb-2021v-13-aws-tst -l odoo

        ::

            /etc/init.d/odoo stop

        ::

            # ***** clvheatlh-jcafb-2020-aws-pro
            #

            cd /opt/odoo/clvsol_odoo_client
            git pull

            cd /opt/odoo/clvsol_clvhealth_jcafb
            git pull

            cd /opt/odoo/clvsol_l10n_brazil
            git pull

            cd /opt/odoo/clvsol_odoo_addons
            git pull

            cd /opt/odoo/clvsol_odoo_addons_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_l10n_br
            git pull

            cd /opt/odoo/clvsol_odoo_addons_l10n_br_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_history
            git pull

            cd /opt/odoo/clvsol_odoo_addons_history_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_verification
            git pull

            cd /opt/odoo/clvsol_odoo_addons_verification_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_summary
            git pull

            cd /opt/odoo/clvsol_odoo_addons_summary_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_export
            git pull

            cd /opt/odoo/clvsol_odoo_addons_export_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_report
            git pull

            cd /opt/odoo/clvsol_odoo_addons_report_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_process
            git pull

            cd /opt/odoo/clvsol_odoo_addons_process_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_sync
            git pull

            cd /opt/odoo/clvsol_odoo_addons_sync_jcafb
            git pull

        ::

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

[clvheatlh-jcafb-2021v-13-aws-tst] Restaurar um backup do banco de dados *CLVhealth-JCAFB-2021v-13* (2020-07-16a)
-----------------------------------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_restore`.

    #. [clvheatlh-jcafb-2021v-13-aws-tst] Estabelecer uma sessão ssh com o servidor **clvheatlh-jcafb-2021v-13-aws-tst** e paralizar o *Odoo*:

        ::

            # ***** clvheatlh-jcafb-2021v-13-aws-tst
            #

            ssh clvheatlh-jcafb-2021v-13-aws-tst -l root

            /etc/init.d/odoo stop

            su odoo

    #. [clvheatlh-jcafb-2021v-13-aws-tst] Executar os comandos de restauração dos arquivos de backup:

        ::

            # ***** clvheatlh-jcafb-2021v-13-aws-tst
            #

            cd /opt/odoo
            # gzip -d clvhealth_jcafb_2021v_13_2020-07-16a.sql.gz

            dropdb -i clvhealth_jcafb_2021v_13

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2021v_13
            psql -f clvhealth_jcafb_2021v_13_2020-07-16a.sql -d clvhealth_jcafb_2021v_13 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2021v_13
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2021v_13_2020-07-16a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021v_13_2020-07-16a.tar.gz

    #. Retornar a execução do *Odoo* do servidor **clvheatlh-jcafb-2021v-13-aws-tst** ao modo desejado:

        ::

            # ***** clvheatlh-jcafb-2021v-13-aws-tst
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    #. [clvheatlh-jcafb-2021v-13-aws-tst] Configurar o parâmetro "**web.base.url**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `clvheatlh-jcafb-2021v-13-aws-tst <https://clvheatlh-jcafb-2021v-13-aws-tst>`_

        #. Acessar a *View* **Parâmetros do Sistema**:

            * Menu de acesso:
                
                * **Configurações** » **Técnico** » **Parâmetros** » **Parâmetros do Sistema**

        #. Pesquisar pelo registro com a **Chave** "**web.base.url**"

        #. Editar o registro apresentado (**Chave**: "**web.base.url**")

        #. Alterar o campo **Valor** para:

            * "**http://clvheatlh-jcafb-2021v-13-aws-tst.tklapp.com**".

        #. Salvar o registro editado.

Atualizar os fontes do projeto (2020-07-19)
-------------------------------------------

    #. **Atualizar** os fontes do projeto

        ::

            ssh clvheatlh-jcafb-2021v-13-aws-tst -l odoo

        ::

            /etc/init.d/odoo stop

        ::

            # ***** clvheatlh-jcafb-2020-aws-pro
            #

            cd /opt/odoo/clvsol_odoo_client
            git pull

            cd /opt/odoo/clvsol_clvhealth_jcafb
            git pull

            cd /opt/odoo/clvsol_l10n_brazil
            git pull

            cd /opt/odoo/clvsol_odoo_addons
            git pull

            cd /opt/odoo/clvsol_odoo_addons_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_l10n_br
            git pull

            cd /opt/odoo/clvsol_odoo_addons_l10n_br_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_history
            git pull

            cd /opt/odoo/clvsol_odoo_addons_history_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_verification
            git pull

            cd /opt/odoo/clvsol_odoo_addons_verification_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_summary
            git pull

            cd /opt/odoo/clvsol_odoo_addons_summary_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_export
            git pull

            cd /opt/odoo/clvsol_odoo_addons_export_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_report
            git pull

            cd /opt/odoo/clvsol_odoo_addons_report_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_process
            git pull

            cd /opt/odoo/clvsol_odoo_addons_process_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_sync
            git pull

            cd /opt/odoo/clvsol_odoo_addons_sync_jcafb
            git pull

        ::

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

[clvheatlh-jcafb-2021v-13-aws-tst] Restaurar um backup do banco de dados *CLVhealth-JCAFB-2021v-13* (2020-07-19a)
-----------------------------------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_restore`.

    #. [clvheatlh-jcafb-2021v-13-aws-tst] Estabelecer uma sessão ssh com o servidor **clvheatlh-jcafb-2021v-13-aws-tst** e paralizar o *Odoo*:

        ::

            # ***** clvheatlh-jcafb-2021v-13-aws-tst
            #

            ssh clvheatlh-jcafb-2021v-13-aws-tst -l root

            /etc/init.d/odoo stop

            su odoo

    #. [clvheatlh-jcafb-2021v-13-aws-tst] Executar os comandos de restauração dos arquivos de backup:

        ::

            # ***** clvheatlh-jcafb-2021v-13-aws-tst
            #

            cd /opt/odoo
            gzip -d clvhealth_jcafb_2021v_13_2020-07-19a.sql.gz

            dropdb -i clvhealth_jcafb_2021v_13

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2021v_13
            psql -f clvhealth_jcafb_2021v_13_2020-07-19a.sql -d clvhealth_jcafb_2021v_13 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2021v_13
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2021v_13_2020-07-19a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021v_13_2020-07-19a.tar.gz

    #. Retornar a execução do *Odoo* do servidor **clvheatlh-jcafb-2021v-13-aws-tst** ao modo desejado:

        ::

            # ***** clvheatlh-jcafb-2021v-13-aws-tst
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    #. [clvheatlh-jcafb-2021v-13-aws-tst] Configurar o parâmetro "**web.base.url**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `clvheatlh-jcafb-2021v-13-aws-tst <https://clvheatlh-jcafb-2021v-13-aws-tst>`_

        #. Acessar a *View* **Parâmetros do Sistema**:

            * Menu de acesso:
                
                * **Configurações** » **Técnico** » **Parâmetros** » **Parâmetros do Sistema**

        #. Pesquisar pelo registro com a **Chave** "**web.base.url**"

        #. Editar o registro apresentado (**Chave**: "**web.base.url**")

        #. Alterar o campo **Valor** para:

            * "**http://clvheatlh-jcafb-2021v-13-aws-tst.tklapp.com**".

        #. Salvar o registro editado.

Atualizar os fontes do projeto (2020-07-21)
-------------------------------------------

    #. **Atualizar** os fontes do projeto

        ::

            ssh clvheatlh-jcafb-2021v-13-aws-tst -l odoo

        ::

            /etc/init.d/odoo stop

        ::

            # ***** clvheatlh-jcafb-2020-aws-pro
            #

            cd /opt/odoo/clvsol_odoo_client
            git pull

            cd /opt/odoo/clvsol_clvhealth_jcafb
            git pull

            cd /opt/odoo/clvsol_l10n_brazil
            git pull

            cd /opt/odoo/clvsol_odoo_addons
            git pull

            cd /opt/odoo/clvsol_odoo_addons_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_l10n_br
            git pull

            cd /opt/odoo/clvsol_odoo_addons_l10n_br_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_history
            git pull

            cd /opt/odoo/clvsol_odoo_addons_history_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_verification
            git pull

            cd /opt/odoo/clvsol_odoo_addons_verification_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_summary
            git pull

            cd /opt/odoo/clvsol_odoo_addons_summary_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_export
            git pull

            cd /opt/odoo/clvsol_odoo_addons_export_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_report
            git pull

            cd /opt/odoo/clvsol_odoo_addons_report_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_process
            git pull

            cd /opt/odoo/clvsol_odoo_addons_process_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_sync
            git pull

            cd /opt/odoo/clvsol_odoo_addons_sync_jcafb
            git pull

        ::

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

[clvheatlh-jcafb-2021v-13-aws-tst] Restaurar um backup do banco de dados *CLVhealth-JCAFB-2021v-13* (2020-07-20c)
-----------------------------------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_restore`.

    #. [clvheatlh-jcafb-2021v-13-aws-tst] Estabelecer uma sessão ssh com o servidor **clvheatlh-jcafb-2021v-13-aws-tst** e paralizar o *Odoo*:

        ::

            # ***** clvheatlh-jcafb-2021v-13-aws-tst
            #

            ssh clvheatlh-jcafb-2021v-13-aws-tst -l root

            /etc/init.d/odoo stop

            su odoo

    #. [clvheatlh-jcafb-2021v-13-aws-tst] Executar os comandos de restauração dos arquivos de backup:

        ::

            # ***** clvheatlh-jcafb-2021v-13-aws-tst
            #

            cd /opt/odoo
            gzip -d clvhealth_jcafb_2021v_13_2020-07-20c.sql.gz

            dropdb -i clvhealth_jcafb_2021v_13

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2021v_13
            psql -f clvhealth_jcafb_2021v_13_2020-07-20c.sql -d clvhealth_jcafb_2021v_13 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2021v_13
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2021v_13_2020-07-20c.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021v_13_2020-07-20c.tar.gz

    #. Retornar a execução do *Odoo* do servidor **clvheatlh-jcafb-2021v-13-aws-tst** ao modo desejado:

        ::

            # ***** clvheatlh-jcafb-2021v-13-aws-tst
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    #. [clvheatlh-jcafb-2021v-13-aws-tst] Configurar o parâmetro "**web.base.url**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `clvheatlh-jcafb-2021v-13-aws-tst <https://clvheatlh-jcafb-2021v-13-aws-tst>`_

        #. Acessar a *View* **Parâmetros do Sistema**:

            * Menu de acesso:
                
                * **Configurações** » **Técnico** » **Parâmetros** » **Parâmetros do Sistema**

        #. Pesquisar pelo registro com a **Chave** "**web.base.url**"

        #. Editar o registro apresentado (**Chave**: "**web.base.url**")

        #. Alterar o campo **Valor** para:

            * "**http://clvheatlh-jcafb-2021v-13-aws-tst.tklapp.com**".

        #. Salvar o registro editado.

Atualizar os fontes do projeto (2020-07-23)
-------------------------------------------

    #. **Atualizar** os fontes do projeto

        ::

            ssh clvheatlh-jcafb-2021v-13-aws-tst -l root

        ::

            /etc/init.d/odoo stop

            su odoo

        ::

            # ***** clvheatlh-jcafb-2020-aws-pro
            #

            cd /opt/odoo/clvsol_odoo_client
            git pull

            cd /opt/odoo/clvsol_clvhealth_jcafb
            git pull

            cd /opt/odoo/clvsol_l10n_brazil
            git pull

            cd /opt/odoo/clvsol_odoo_addons
            git pull

            cd /opt/odoo/clvsol_odoo_addons_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_l10n_br
            git pull

            cd /opt/odoo/clvsol_odoo_addons_l10n_br_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_history
            git pull

            cd /opt/odoo/clvsol_odoo_addons_history_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_verification
            git pull

            cd /opt/odoo/clvsol_odoo_addons_verification_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_summary
            git pull

            cd /opt/odoo/clvsol_odoo_addons_summary_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_export
            git pull

            cd /opt/odoo/clvsol_odoo_addons_export_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_report
            git pull

            cd /opt/odoo/clvsol_odoo_addons_report_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_process
            git pull

            cd /opt/odoo/clvsol_odoo_addons_process_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_sync
            git pull

            cd /opt/odoo/clvsol_odoo_addons_sync_jcafb
            git pull

        ::

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

[clvheatlh-jcafb-2021v-13-aws-tst] Restaurar um backup do banco de dados *CLVhealth-JCAFB-2021v-13* (2020-07-23a)
-----------------------------------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_restore`.

    #. [clvheatlh-jcafb-2021v-13-aws-tst] Estabelecer uma sessão ssh com o servidor **clvheatlh-jcafb-2021v-13-aws-tst** e paralizar o *Odoo*:

        ::

            # ***** clvheatlh-jcafb-2021v-13-aws-tst
            #

            ssh clvheatlh-jcafb-2021v-13-aws-tst -l root

            /etc/init.d/odoo stop

            su odoo

    #. [clvheatlh-jcafb-2021v-13-aws-tst] Executar os comandos de restauração dos arquivos de backup:

        ::

            # ***** clvheatlh-jcafb-2021v-13-aws-tst
            #

            cd /opt/odoo
            gzip -d clvhealth_jcafb_2021v_13_2020-07-23a.sql.gz

            dropdb -i clvhealth_jcafb_2021v_13

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2021v_13
            psql -f clvhealth_jcafb_2021v_13_2020-07-23a.sql -d clvhealth_jcafb_2021v_13 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2021v_13
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2021v_13_2020-07-23a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021v_13_2020-07-23a.tar.gz

    #. Retornar a execução do *Odoo* do servidor **clvheatlh-jcafb-2021v-13-aws-tst** ao modo desejado:

        ::

            # ***** clvheatlh-jcafb-2021v-13-aws-tst
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    #. [clvheatlh-jcafb-2021v-13-aws-tst] Configurar o parâmetro "**web.base.url**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `clvheatlh-jcafb-2021v-13-aws-tst <https://clvheatlh-jcafb-2021v-13-aws-tst>`_

        #. Acessar a *View* **Parâmetros do Sistema**:

            * Menu de acesso:
                
                * **Configurações** » **Técnico** » **Parâmetros** » **Parâmetros do Sistema**

        #. Pesquisar pelo registro com a **Chave** "**web.base.url**"

        #. Editar o registro apresentado (**Chave**: "**web.base.url**")

        #. Alterar o campo **Valor** para:

            * "**http://clvheatlh-jcafb-2021v-13-aws-tst.tklapp.com**".

        #. Salvar o registro editado.

Atualizar os fontes do projeto (2020-07-30)
-------------------------------------------

    #. **Atualizar** os fontes do projeto

        ::

            ssh clvheatlh-jcafb-2021v-13-aws-tst -l root

        ::

            /etc/init.d/odoo stop

            su odoo

        ::

            # ***** clvheatlh-jcafb-2020-aws-pro
            #

            cd /opt/odoo/clvsol_odoo_client
            git pull

            cd /opt/odoo/clvsol_clvhealth_jcafb
            git pull

            cd /opt/odoo/clvsol_l10n_brazil
            git pull

            cd /opt/odoo/clvsol_odoo_addons
            git pull

            cd /opt/odoo/clvsol_odoo_addons_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_l10n_br
            git pull

            cd /opt/odoo/clvsol_odoo_addons_l10n_br_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_history
            git pull

            cd /opt/odoo/clvsol_odoo_addons_history_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_verification
            git pull

            cd /opt/odoo/clvsol_odoo_addons_verification_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_summary
            git pull

            cd /opt/odoo/clvsol_odoo_addons_summary_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_export
            git pull

            cd /opt/odoo/clvsol_odoo_addons_export_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_report
            git pull

            cd /opt/odoo/clvsol_odoo_addons_report_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_process
            git pull

            cd /opt/odoo/clvsol_odoo_addons_process_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_sync
            git pull

            cd /opt/odoo/clvsol_odoo_addons_sync_jcafb
            git pull

        ::

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

[clvheatlh-jcafb-2021v-13-aws-tst] Restaurar um backup do banco de dados *CLVhealth-JCAFB-2021v-13* (2020-07-29b)
-----------------------------------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_restore`.

    #. [clvheatlh-jcafb-2021v-13-aws-tst] Estabelecer uma sessão ssh com o servidor **clvheatlh-jcafb-2021v-13-aws-tst** e paralizar o *Odoo*:

        ::

            # ***** clvheatlh-jcafb-2021v-13-aws-tst
            #

            ssh clvheatlh-jcafb-2021v-13-aws-tst -l root

            /etc/init.d/odoo stop

            su odoo

    #. [clvheatlh-jcafb-2021v-13-aws-tst] Executar os comandos de restauração dos arquivos de backup:

        ::

            # ***** clvheatlh-jcafb-2021v-13-aws-tst
            #

            cd /opt/odoo
            gzip -d clvhealth_jcafb_2021v_13_2020-07-29b.sql.gz

            dropdb -i clvhealth_jcafb_2021v_13

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2021v_13
            psql -f clvhealth_jcafb_2021v_13_2020-07-29b.sql -d clvhealth_jcafb_2021v_13 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2021v_13
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2021v_13_2020-07-29b.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021v_13_2020-07-29b.tar.gz

    #. Retornar a execução do *Odoo* do servidor **clvheatlh-jcafb-2021v-13-aws-tst** ao modo desejado:

        ::

            # ***** clvheatlh-jcafb-2021v-13-aws-tst
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    #. [clvheatlh-jcafb-2021v-13-aws-tst] Configurar o parâmetro "**web.base.url**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `clvheatlh-jcafb-2021v-13-aws-tst <https://clvheatlh-jcafb-2021v-13-aws-tst>`_

        #. Acessar a *View* **Parâmetros do Sistema**:

            * Menu de acesso:
                
                * **Configurações** » **Técnico** » **Parâmetros** » **Parâmetros do Sistema**

        #. Pesquisar pelo registro com a **Chave** "**web.base.url**"

        #. Editar o registro apresentado (**Chave**: "**web.base.url**")

        #. Alterar o campo **Valor** para:

            * "**http://clvheatlh-jcafb-2021v-13-aws-tst.tklapp.com**".

        #. Salvar o registro editado.

Atualizar os fontes do projeto (2020-07-30)
-------------------------------------------

    #. **Atualizar** os fontes do projeto

        ::

            ssh clvheatlh-jcafb-2021v-13-aws-tst -l root

        ::

            /etc/init.d/odoo stop

            su odoo

        ::

            # ***** clvheatlh-jcafb-2020-aws-pro
            #

            cd /opt/odoo/clvsol_odoo_client
            git pull

            cd /opt/odoo/clvsol_clvhealth_jcafb
            git pull

            cd /opt/odoo/clvsol_l10n_brazil
            git pull

            cd /opt/odoo/clvsol_odoo_addons
            git pull

            cd /opt/odoo/clvsol_odoo_addons_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_l10n_br
            git pull

            cd /opt/odoo/clvsol_odoo_addons_l10n_br_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_history
            git pull

            cd /opt/odoo/clvsol_odoo_addons_history_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_verification
            git pull

            cd /opt/odoo/clvsol_odoo_addons_verification_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_summary
            git pull

            cd /opt/odoo/clvsol_odoo_addons_summary_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_export
            git pull

            cd /opt/odoo/clvsol_odoo_addons_export_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_report
            git pull

            cd /opt/odoo/clvsol_odoo_addons_report_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_process
            git pull

            cd /opt/odoo/clvsol_odoo_addons_process_jcafb
            git pull

            cd /opt/odoo/clvsol_odoo_addons_sync
            git pull

            cd /opt/odoo/clvsol_odoo_addons_sync_jcafb
            git pull

        ::

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

[clvheatlh-jcafb-2021v-13-aws-tst] Restaurar um backup do banco de dados *CLVhealth-JCAFB-2021v-13* (2020-07-30a)
-----------------------------------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_restore`.

    #. [clvheatlh-jcafb-2021v-13-aws-tst] Estabelecer uma sessão ssh com o servidor **clvheatlh-jcafb-2021v-13-aws-tst** e paralizar o *Odoo*:

        ::

            # ***** clvheatlh-jcafb-2021v-13-aws-tst
            #

            ssh clvheatlh-jcafb-2021v-13-aws-tst -l root

            /etc/init.d/odoo stop

            su odoo

    #. [clvheatlh-jcafb-2021v-13-aws-tst] Executar os comandos de restauração dos arquivos de backup:

        ::

            # ***** clvheatlh-jcafb-2021v-13-aws-tst
            #

            cd /opt/odoo
            gzip -d clvhealth_jcafb_2021v_13_2020-07-30a.sql.gz

            dropdb -i clvhealth_jcafb_2021v_13

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2021v_13
            psql -f clvhealth_jcafb_2021v_13_2020-07-30a.sql -d clvhealth_jcafb_2021v_13 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2021v_13
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2021v_13_2020-07-30a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021v_13_2020-07-30a.tar.gz

    #. Retornar a execução do *Odoo* do servidor **clvheatlh-jcafb-2021v-13-aws-tst** ao modo desejado:

        ::

            # ***** clvheatlh-jcafb-2021v-13-aws-tst
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    #. [clvheatlh-jcafb-2021v-13-aws-tst] Configurar o parâmetro "**web.base.url**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `clvheatlh-jcafb-2021v-13-aws-tst <https://clvheatlh-jcafb-2021v-13-aws-tst>`_

        #. Acessar a *View* **Parâmetros do Sistema**:

            * Menu de acesso:
                
                * **Configurações** » **Técnico** » **Parâmetros** » **Parâmetros do Sistema**

        #. Pesquisar pelo registro com a **Chave** "**web.base.url**"

        #. Editar o registro apresentado (**Chave**: "**web.base.url**")

        #. Alterar o campo **Valor** para:

            * "**http://clvheatlh-jcafb-2021v-13-aws-tst.tklapp.com**".

        #. Salvar o registro editado.

.. toctree::   :maxdepth: 2
