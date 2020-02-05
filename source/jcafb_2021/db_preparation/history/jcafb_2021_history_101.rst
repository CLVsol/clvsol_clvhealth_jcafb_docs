.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

=============================================================
[2020-02-(05-06)] - Preparação do Banco de Dados - JCAFB-2021
=============================================================

Restaurar um backup do *CLVhealth-JCAFB-2020* no servidor "tkl-odoo12-jcafb-ng-vm" (2020-01-25a)
------------------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_restore`.

    #. [tkl-odoo12-jcafb-ng-vm] Estabelecer uma sessão ssh com o servidor **tkl-odoo12-jcafb-ng-vm** e paralizar o *Odoo*:

        ::

            # ***** tkl-odoo12-jcafb-ng-vm
            #

            ssh tkl-odoo12-jcafb-ng-vm -l root

            /etc/init.d/odoo stop

            su odoo

    #. [tkl-odoo12-jcafb-ng-vm] Executar os comandos de restauração dos arquivos de backup:

        ::

            # ***** tkl-odoo12-jcafb-ng-vm
            #

            cd /opt/odoo
            # gzip -d clvhealth_jcafb_2020_2020-01-25a.sql.gz

            dropdb -i clvhealth_jcafb_2020

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020
            psql -f clvhealth_jcafb_2020_2020-01-25a.sql -d clvhealth_jcafb_2020 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_2020-01-25a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020-01-25a.tar.gz

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-ng-vm** ao modo desejado:

        ::

            # ***** tkl-odoo12-jcafb-ng-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    :red:`(WARNING clvhealth_jcafb_2020 odoo.modules.graph: module l10n_br_zip_correios: not installable, skipped)`

    #. :red:`(Não Executado)` [tkl-odoo12-jcafb-ng-vm] Configurar o parâmetro "**web.base.url**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-ng-vm <https://tkl-odoo12-jcafb-ng-vm>`_

        #. Acessar a *View* **Parâmetros do Sistema**:

            * Menu de acesso:
                * **Configurações** » **Técnico** » **Parâmetros** » **Parâmetros do Sistema**

        #. Pesquisar pelo registro com a **Chave** "**web.base.url**";

        #. Editar o registro apresentado (**Chave**: "**web.base.url**")

        #. Alterar o campo **Valor** para:

            * "**http://tkl-odoo12-jcafb-ng-vm**".

        #. Salvar o registro editado.

Atualizar o(s) módulo(s) [l10n_br_base] (2020-02-05)
----------------------------------------------------

    * Referência: :doc:`/setup/module_update`.


    #. [tkl-odoo12-jcafb-ng-vm] Lista de Módulos:

        * l10n_br_base

    #. [tkl-odoo12-jcafb-ng-vm] **Executar** a atualização do(s) Módulo(s):

        #. Estabelecer uma sessão ssh (session 1) com o servidor **tkl-odoo12-jcafb-ng-vm** e executar o *Odoo* no modo manual:

            ::

                # ***** tkl-odoo12-jcafb-ng-vm (session 1)
                #

                ssh tkl-odoo12-jcafb-ng-vm -l root

                /etc/init.d/odoo stop

                su odoo
                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

        #. Estabelecer uma sessão ssh (session 2) com o servidor **tkl-odoo12-jcafb-ng-vm** e executar o **install.py**:

            ::

                # ***** tkl-odoo12-jcafb-ng-vm (session 2)
                #

                ssh tkl-odoo12-jcafb-ng-vm -l odoo

                cd /opt/odoo/clvsol_clvhealth_jcafb/project
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" - m l10n_br_base
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-ng-vm** ao modo desejado:

            ::

                # ***** tkl-odoo12-jcafb-ng-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

.. toctree::
   :maxdepth: 2
