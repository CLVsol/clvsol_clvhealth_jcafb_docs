.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .blue {color:blue} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: blue
.. role:: bi

============================================
Preparação do Banco de Dados - JCAFB-2020-13
============================================

:red:`(Não Executado])` Restaurar um backup do banco de dados *CLVhealth-JCAFB-2020-13* (2020-07-10a)
-----------------------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_restore`.

    #. [tkl-odoo13-jcafb20-vm] Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb20-vm** e paralizar o *Odoo*:

        ::

            # ***** tkl-odoo13-jcafb20-vm
            #

            ssh tkl-odoo13-jcafb20-vm -l root

            /etc/init.d/odoo stop

            su odoo

    #. [tkl-odoo13-jcafb20-vm] Executar os comandos de restauração dos arquivos de backup:

        ::

            # ***** tkl-odoo13-jcafb20-vm
            #

            cd /opt/odoo
            # gzip -d clvhealth_jcafb_2020_13_2020-07-10a.sql.gz

            dropdb -i clvhealth_jcafb_2020_13

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020_13
            psql -f clvhealth_jcafb_2020_13_2020-07-10a.sql -d clvhealth_jcafb_2020_13 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020_13
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-07-10a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-10a.tar.gz

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb20-vm** ao modo desejado:

        ::

            # ***** tkl-odoo13-jcafb20-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    #. [tkl-odoo13-jcafb20-vm] Configurar o parâmetro "**web.base.url**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb20-vm <https://tkl-odoo13-jcafb20-vm>`_

        #. Acessar a *View* **Parâmetros do Sistema**:

            * Menu de acesso:
                
                * **Configurações** » **Técnico** » **Parâmetros** » **Parâmetros do Sistema**

        #. Pesquisar pelo registro com a **Chave** "**web.base.url**"

        #. Editar o registro apresentado (**Chave**: "**web.base.url**")

        #. Alterar o campo **Valor** para:

            * "**http://tkl-odoo13-jcafb20-vm**".

        #. Salvar o registro editado.

Atualizar os fontes do projeto (2020-07-16)
-------------------------------------------

    #. **Atualizar** os fontes do projeto

        ::

            ssh tkl-odoo13-jcafb20-vm -l odoo

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

Atualizar o(s) módulo(s) [clv_employee_jcafb] (2020-07-16)
----------------------------------------------------------

    #. [tkl-odoo13-jcafb20-vm] Lista de Módulos:

        * clv_employee_jcafb

    #. [tkl-odoo13-jcafb20-vm] **Executar** a atualização do(s) Módulo(s):

        #. Estabelecer uma sessão ssh (session 1) com o servidor **tkl-odoo13-jcafb20-vm** e executar o *Odoo* no modo manual:

            ::

                # ***** tkl-odoo13-jcafb20-vm (session 1)
                #

                ssh tkl-odoo13-jcafb20-vm -l root

                /etc/init.d/odoo stop

                su odoo
                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

        #. Estabelecer uma sessão ssh (session 2) com o servidor **tkl-odoo13-jcafb20-vm** e executar o **install.py**:

            ::

                # ***** tkl-odoo13-jcafb20-vm (session 2)
                #

                ssh tkl-odoo13-jcafb20-vm -l odoo

                cd /opt/odoo/clvsol_clvhealth_jcafb/project
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_employee_jcafb
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb20-vm** ao modo desejado:

            ::

                # ***** tkl-odoo13-jcafb20-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Renovar o *Token* de todos os Funcionários (2020-07-16)
-------------------------------------------------------

    #. [tkl-odoo13-jcafb20-vm] Executar a Ação :bi:`Employee Mass Edit` para todas os Funcionários:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb20-vm <https://tkl-odoo13-jcafb20-vm>`_

        #. Acessar a *View* *Funcionários*:

            * Menu de acesso:

                * :bi:`Funcionários` » :bi:`Funcionários`

        #. Selecionar todos os Funcionários (**248**)

        #. Exercutar a Ação ":bi:`Employee Mass Edit`":

            * Parâmetros utilizados:

                * *Token*: :bi:`Remove`

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

        #. Selecionar todos os Funcionários (**248**)

        #. Exercutar a Ação ":bi:`Employee Mass Edit`":

            * Parâmetros utilizados:

                * *Token*: :bi:`Set` "**/**"

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Redefinir a **Senha** de todos os Funcionários da **JCAFB-2020** (2020-07-16)
-----------------------------------------------------------------------------

    #. [tkl-odoo13-jcafb20-vm] Executar a Ação :bi:`Employee Mass Edit` para todas os Funcionários da **JCAFB-2020**:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb20-vm <https://tkl-odoo13-jcafb20-vm>`_

        #. Acessar a *View* *Funcionários*:

            * Menu de acesso:

                * :bi:`Funcionários` » :bi:`Funcionários`

        #. Selecionar todos os Funcionários da **JCAFB-2020** (**57**)

        #. Exercutar a Ação ":bi:`Employee Mass Edit`":

            * Parâmetros utilizados:

                * *Reset User Password*: :bi:`marcado`

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Redefinir a senha do usuário de referência da JCAFB-2020 (2020-07-16)
---------------------------------------------------------------------

    #. Redefinir a senha do usuário de referência:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb20-vm <https://tkl-odoo13-jcafb20-vm>`_

        #. Acessar a *View* *Users*:

            * Menu de acesso:

                * :bi:`Configurações` » :bi:`Utilizadores e Empresas` » :bi:`Usuários`

        #. Selecionar o usuário de referência.

        #. Exercutar a Ação "**Alterar Senha**":

            * Parâmetros:
                * Nova Senha: *******
            
            #. Utilize o botão "**Alterar Senha**" para executar a ação.

Criar um backup do banco de dados *CLVhealth-JCAFB-2020-13* (2020-07-16a)
-------------------------------------------------------------------------

    #. [tkl-odoo13-jcafb20-vm] Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb20-vm** e paralizar o *Odoo*:

        ::

            # ***** tkl-odoo13-jcafb20-vm
            #

            ssh tkl-odoo13-jcafb20-vm -l root

            /etc/init.d/odoo stop

            su odoo

    #. [tkl-odoo13-jcafb20-vm] Executar os comandos de criação dos arquivos de backup:

        ::

            # ***** tkl-odoo13-jcafb20-vm
            #
            # data_dir = /var/lib/odoo/.local/share/Odoo
            #

            cd /opt/odoo
            pg_dump clvhealth_jcafb_2020_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_13_2020-07-16a.sql

            gzip clvhealth_jcafb_2020_13_2020-07-16a.sql
            pg_dump clvhealth_jcafb_2020_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_13_2020-07-16a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-07-16a.tar.gz clvhealth_jcafb_2020_13

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-16a.tar.gz clvhealth_jcafb

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb20-vm** ao modo desejado:

        ::

            # ***** tkl-odoo13-jcafb20-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    Criados os seguintes arquivos:
        * /opt/odoo/clvhealth_jcafb_2020_13_2020-07-16a.sql
        * /opt/odoo/clvhealth_jcafb_2020_13_2020-07-16a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-07-16a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-16a.tar.gz

.. index:: clvhealth_jcafb_2020_13_2020-07-16a.sql
.. index:: clvhealth_jcafb_2020_13_2020-07-16a.sql.gz
.. index:: filestore_clvhealth_jcafb_2020_13_2020-07-16a
.. index:: clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-16a

:red:`(Não Executado])` Restaurar um backup do banco de dados *CLVhealth-JCAFB-2020-13* (2020-07-16a)
-----------------------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_restore`.

    #. [tkl-odoo13-jcafb20-vm] Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb20-vm** e paralizar o *Odoo*:

        ::

            # ***** tkl-odoo13-jcafb20-vm
            #

            ssh tkl-odoo13-jcafb20-vm -l root

            /etc/init.d/odoo stop

            su odoo

    #. [tkl-odoo13-jcafb20-vm] Executar os comandos de restauração dos arquivos de backup:

        ::

            # ***** tkl-odoo13-jcafb20-vm
            #

            cd /opt/odoo
            # gzip -d clvhealth_jcafb_2020_13_2020-07-16a.sql.gz

            dropdb -i clvhealth_jcafb_2020_13

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020_13
            psql -f clvhealth_jcafb_2020_13_2020-07-16a.sql -d clvhealth_jcafb_2020_13 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020_13
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-07-16a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-16a.tar.gz

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb20-vm** ao modo desejado:

        ::

            # ***** tkl-odoo13-jcafb20-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    #. [tkl-odoo13-jcafb20-vm] Configurar o parâmetro "**web.base.url**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb20-vm <https://tkl-odoo13-jcafb20-vm>`_

        #. Acessar a *View* **Parâmetros do Sistema**:

            * Menu de acesso:
                
                * **Configurações** » **Técnico** » **Parâmetros** » **Parâmetros do Sistema**

        #. Pesquisar pelo registro com a **Chave** "**web.base.url**"

        #. Editar o registro apresentado (**Chave**: "**web.base.url**")

        #. Alterar o campo **Valor** para:

            * "**http://tkl-odoo13-jcafb20-vm**".

        #. Salvar o registro editado.

.. toctree::   :maxdepth: 2
