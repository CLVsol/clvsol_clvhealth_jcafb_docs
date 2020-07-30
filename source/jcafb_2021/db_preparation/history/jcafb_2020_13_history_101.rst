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

Atualizar os fontes do projeto (2020-07-16 (2))
-----------------------------------------------

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

Executar o *Verification Batch* "*Default Batch*" (2020-07-16)
--------------------------------------------------------------

    #. Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb20-vm** e executar o *Odoo* no modo manual:

        ::

            # ***** tkl-odoo13-jcafb20-vm
            #

            ssh tkl-odoo13-jcafb20-vm -l root

            /etc/init.d/odoo stop

            su odoo

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    #. [tkl-odoo13-jcafb20-vm] Executar o :bi:`Verification Batch` "**Default Batch**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb20-vm <https://tkl-odoo13-jcafb20-vm>`_

        #. Executar a ação :bi:`Verification Batch Exec` para o "**Default Batch**":

            * Menu de acesso:
                
                * :bi:`Verification` » :bi:`Verification` » :bi:`Verification` » :bi:`Batches` » **Ação** » :bi:`Verification Batch Exec`

            * :bi:`Execution time: 0:15:04.278`

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb20-vm** ao modo padrão:

        ::

            # ***** tkl-odoo13-jcafb20-vm
            #

            ^C

            exit

            /etc/init.d/odoo start

Criar um backup do banco de dados *CLVhealth-JCAFB-2020-13* (2020-07-16b)
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
            pg_dump clvhealth_jcafb_2020_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_13_2020-07-16b.sql

            gzip clvhealth_jcafb_2020_13_2020-07-16b.sql
            pg_dump clvhealth_jcafb_2020_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_13_2020-07-16b.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-07-16b.tar.gz clvhealth_jcafb_2020_13

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-16b.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_13_2020-07-16b.sql
        * /opt/odoo/clvhealth_jcafb_2020_13_2020-07-16b.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-07-16b.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-16b.tar.gz

.. index:: clvhealth_jcafb_2020_13_2020-07-16b.sql
.. index:: clvhealth_jcafb_2020_13_2020-07-16b.sql.gz
.. index:: filestore_clvhealth_jcafb_2020_13_2020-07-16b
.. index:: clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-16b

:red:`(Não Executado])` Restaurar um backup do banco de dados *CLVhealth-JCAFB-2020-13* (2020-07-16b)
-----------------------------------------------------------------------------------------------------

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
            # gzip -d clvhealth_jcafb_2020_13_2020-07-16b.sql.gz

            dropdb -i clvhealth_jcafb_2020_13

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020_13
            psql -f clvhealth_jcafb_2020_13_2020-07-16b.sql -d clvhealth_jcafb_2020_13 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020_13
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-07-16b.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-16b.tar.gz

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

Atualizar os fontes do projeto (2020-07-17)
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

Atualizar o(s) módulo(s) [ver lista] (2020-07-17)
-------------------------------------------------

    #. [tkl-odoo13-jcafb20-vm] Lista de Módulos:

        * clv_document
        * clv_partner_entity
        * clv_address
        * clv_family

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_document
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_partner_entity
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb20-vm** ao modo desejado:

            ::

                # ***** tkl-odoo13-jcafb20-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Ativar *Automatic Name* de todos os Endereços (2020-07-17)
----------------------------------------------------------

    #. [tkl-odoo13-jcafb20-vm] Executar a Ação :bi:`Address Mass Edit` para todas as Pessoas:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb20-vm <https://tkl-odoo13-jcafb20-vm>`_

        #. Acessar a *View* *Addresses*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Addresses`

        #. Selecionar todos os Endereços (**665**)

        #. Exercutar a Ação ":bi:`Address Mass Edit`":

            * Parâmetros utilizados:

                * *Automatic Name*: :bi:`Set` **marcado**

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Ativar *Automatic Name* de todas as Famílias (2020-07-17)
---------------------------------------------------------

    #. [tkl-odoo13-jcafb20-vm] Executar a Ação :bi:`Family Mass Edit` para todas as Famílias:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb20-vm <https://tkl-odoo13-jcafb20-vm>`_

        #. Acessar a *View* *Families*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Families`

        #. Selecionar todas as Famílias (**441**)

        #. Exercutar a Ação ":bi:`Family Mass Edit`":

            * Parâmetros utilizados:

                * *Automatic Name*: :bi:`Set` **marcado**

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Atualizar o *Entity Code* de todas as Pessoas (2020-07-17)
----------------------------------------------------------

    #. [tkl-odoo13-jcafb20-vm] Executar a Ação :bi:`Person Mass Edit` para todas as Pessoas:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb20-vm <https://tkl-odoo13-jcafb20-vm>`_

        #. Acessar a *View* *Persons*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Persons`

        #. Selecionar todas as Pessoas (**1540**)

        #. Exercutar a Ação ":bi:`Person Mass Edit`":

            * Parâmetros utilizados:

                * *Partner Entity Code*: **Set**

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Atualizar o *Entity Code* de todas as Famílias (2020-07-17)
-----------------------------------------------------------

    #. [tkl-odoo13-jcafb20-vm] Executar a Ação :bi:`Family Mass Edit` para todas as Famílias:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb20-vm <https://tkl-odoo13-jcafb20-vm>`_

        #. Acessar a *View* *Families*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Families`

        #. Selecionar todas as Famílias (**441**)

        #. Exercutar a Ação ":bi:`Family Mass Edit`":

            * Parâmetros utilizados:

                * *Partner Entity Code*: **Set**

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Atualizar o *Entity Code* de todas os Endereços (2020-07-17)
------------------------------------------------------------

    #. [tkl-odoo13-jcafb20-vm] Executar a Ação :bi:`Address Mass Edit` para todas os Endereços:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb20-vm <https://tkl-odoo13-jcafb20-vm>`_

        #. Acessar a *View* *Addresses*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Addresses`

        #. Selecionar todas os Endereços (**665**)

        #. Exercutar a Ação ":bi:`Address Mass Edit`":

            * Parâmetros utilizados:

                * *Partner Entity Code*: **Set**

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Atualizar o *Entity Code* de todas as Pessoas (Aux) (2020-07-17)
----------------------------------------------------------------

    #. [tkl-odoo13-jcafb20-vm] Executar a Ação :bi:`Person (Aux) Mass Edit` para todas as Pessoas (Aux):

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb20-vm <https://tkl-odoo13-jcafb20-vm>`_

        #. Acessar a *View* *Persons*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Auxiliary` » :bi:`Persons (Aux)`

        #. Selecionar todas as Pessoas (Aux) (**605**)

        #. Exercutar a Ação ":bi:`Person (Aux) Mass Edit`":

            * Parâmetros utilizados:

                * *Partner Entity Code*: **Set**

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Atualizar o *Entity Code* de todas os Endereços (Aux) (2020-07-17)
------------------------------------------------------------------

    #. [tkl-odoo13-jcafb20-vm] Executar a Ação :bi:`Address (Aux) Mass Edit` para todas os Endereços (Aux):

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb20-vm <https://tkl-odoo13-jcafb20-vm>`_

        #. Acessar a *View* *Addresses*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Addresses`

        #. Selecionar todas os Endereços (Aux) (**202**)

        #. Exercutar a Ação ":bi:`Address (Aux) Mass Edit`":

            * Parâmetros utilizados:

                * *Partner Entity Code*: **Set**

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Criar um backup do banco de dados *CLVhealth-JCAFB-2020-13* (2020-07-17a)
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
            pg_dump clvhealth_jcafb_2020_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_13_2020-07-17a.sql

            gzip clvhealth_jcafb_2020_13_2020-07-17a.sql
            pg_dump clvhealth_jcafb_2020_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_13_2020-07-17a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-07-17a.tar.gz clvhealth_jcafb_2020_13

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-17a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_13_2020-07-17a.sql
        * /opt/odoo/clvhealth_jcafb_2020_13_2020-07-17a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-07-17a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-17a.tar.gz

.. index:: clvhealth_jcafb_2020_13_2020-07-17a.sql
.. index:: clvhealth_jcafb_2020_13_2020-07-17a.sql.gz
.. index:: filestore_clvhealth_jcafb_2020_13_2020-07-17a
.. index:: clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-17a

:red:`(Não Executado])` Restaurar um backup do banco de dados *CLVhealth-JCAFB-2020-13* (2020-07-17a)
-----------------------------------------------------------------------------------------------------

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
            # gzip -d clvhealth_jcafb_2020_13_2020-07-17a.sql.gz

            dropdb -i clvhealth_jcafb_2020_13

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020_13
            psql -f clvhealth_jcafb_2020_13_2020-07-17a.sql -d clvhealth_jcafb_2020_13 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020_13
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-07-17a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-17a.tar.gz

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

Atualizar o(s) módulo(s) [clv_address_aux] (2020-07-18)
-------------------------------------------------------

    #. [tkl-odoo13-jcafb20-vm] Lista de Módulos:

        * clv_address_aux

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_address_aux
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb20-vm** ao modo desejado:

            ::

                # ***** tkl-odoo13-jcafb20-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Ativar *Automatic Name* de todos os Endereços (Aux) (2020-07-18)
----------------------------------------------------------------

    #. [tkl-odoo13-jcafb20-vm] Executar a Ação :bi:`Address (Aux) Mass Edit` para todas as Pessoas:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb20-vm <https://tkl-odoo13-jcafb20-vm>`_

        #. Acessar a *View* *Addresses (Aux)*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Auxiliary` » :bi:`Addresses (Aux)`

        #. Selecionar todos os Endereços (Aux) (**202**)

        #. Exercutar a Ação ":bi:`Address (Aux) Mass Edit`":

            * Parâmetros utilizados:

                * *Automatic Name*: :bi:`Set` **marcado**

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Criar um backup do banco de dados *CLVhealth-JCAFB-2020-13* (2020-07-18a)
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
            pg_dump clvhealth_jcafb_2020_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_13_2020-07-18a.sql

            gzip clvhealth_jcafb_2020_13_2020-07-18a.sql
            pg_dump clvhealth_jcafb_2020_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_13_2020-07-18a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-07-18a.tar.gz clvhealth_jcafb_2020_13

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-18a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_13_2020-07-18a.sql
        * /opt/odoo/clvhealth_jcafb_2020_13_2020-07-18a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-07-18a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-18a.tar.gz

.. index:: clvhealth_jcafb_2020_13_2020-07-18a.sql
.. index:: clvhealth_jcafb_2020_13_2020-07-18a.sql.gz
.. index:: filestore_clvhealth_jcafb_2020_13_2020-07-18a
.. index:: clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-18a

:red:`(Não Executado])` Restaurar um backup do banco de dados *CLVhealth-JCAFB-2020-13* (2020-07-18a)
-----------------------------------------------------------------------------------------------------

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
            # gzip -d clvhealth_jcafb_2020_13_2020-07-18a.sql.gz

            dropdb -i clvhealth_jcafb_2020_13

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020_13
            psql -f clvhealth_jcafb_2020_13_2020-07-18a.sql -d clvhealth_jcafb_2020_13 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020_13
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-07-18a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-18a.tar.gz

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

Atualizar os fontes do projeto (2020-07-18)
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

Executar o *Verification Batch* "*Default Batch*" (2020-07-16)
--------------------------------------------------------------

    #. Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb20-vm** e executar o *Odoo* no modo manual:

        ::

            # ***** tkl-odoo13-jcafb20-vm
            #

            ssh tkl-odoo13-jcafb20-vm -l root

            /etc/init.d/odoo stop

            su odoo

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    #. [tkl-odoo13-jcafb20-vm] Executar o :bi:`Verification Batch` "**Default Batch**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb20-vm <https://tkl-odoo13-jcafb20-vm>`_

        #. Executar a ação :bi:`Verification Batch Exec` para o "**Default Batch**":

            * Menu de acesso:
                
                * :bi:`Verification` » :bi:`Verification` » :bi:`Verification` » :bi:`Batches` » **Ação** » :bi:`Verification Batch Exec`

            * :bi:`Execution time: 0:16:26.466`

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb20-vm** ao modo padrão:

        ::

            # ***** tkl-odoo13-jcafb20-vm
            #

            ^C

            exit

            /etc/init.d/odoo start

Criar um backup do banco de dados *CLVhealth-JCAFB-2020-13* (2020-07-19a)
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
            pg_dump clvhealth_jcafb_2020_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_13_2020-07-19a.sql

            gzip clvhealth_jcafb_2020_13_2020-07-19a.sql
            pg_dump clvhealth_jcafb_2020_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_13_2020-07-19a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-07-19a.tar.gz clvhealth_jcafb_2020_13

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-19a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_13_2020-07-19a.sql
        * /opt/odoo/clvhealth_jcafb_2020_13_2020-07-19a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-07-19a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-19a.tar.gz

.. index:: clvhealth_jcafb_2020_13_2020-07-19a.sql
.. index:: clvhealth_jcafb_2020_13_2020-07-19a.sql.gz
.. index:: filestore_clvhealth_jcafb_2020_13_2020-07-19a
.. index:: clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-19a

:red:`(Não Executado])` Restaurar um backup do banco de dados *CLVhealth-JCAFB-2020-13* (2020-07-19a)
-----------------------------------------------------------------------------------------------------

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
            # gzip -d clvhealth_jcafb_2020_13_2020-07-19a.sql.gz

            dropdb -i clvhealth_jcafb_2020_13

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020_13
            psql -f clvhealth_jcafb_2020_13_2020-07-19a.sql -d clvhealth_jcafb_2020_13 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020_13
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-07-19a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-19a.tar.gz

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

Atualizar os fontes do projeto (2020-07-20)
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

Atualizar o(s) módulo(s) [clv_person_aux_verification_jcafb] (2020-07-20)
-------------------------------------------------------------------------

    #. [tkl-odoo13-jcafb20-vm] Lista de Módulos:

        * clv_person_aux_verification_jcafb

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_person_aux_verification_jcafb
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb20-vm** ao modo desejado:

            ::

                # ***** tkl-odoo13-jcafb20-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Criar um backup do banco de dados *CLVhealth-JCAFB-2020-13* (2020-07-20a)
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
            pg_dump clvhealth_jcafb_2020_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_13_2020-07-20a.sql

            gzip clvhealth_jcafb_2020_13_2020-07-20a.sql
            pg_dump clvhealth_jcafb_2020_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_13_2020-07-20a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-07-20a.tar.gz clvhealth_jcafb_2020_13

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-20a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_13_2020-07-20a.sql
        * /opt/odoo/clvhealth_jcafb_2020_13_2020-07-20a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-07-20a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-20a.tar.gz

.. index:: clvhealth_jcafb_2020_13_2020-07-20a.sql
.. index:: clvhealth_jcafb_2020_13_2020-07-20a.sql.gz
.. index:: filestore_clvhealth_jcafb_2020_13_2020-07-20a
.. index:: clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-20a

:red:`(Não Executado])` Restaurar um backup do banco de dados *CLVhealth-JCAFB-2020-13* (2020-07-20a)
-----------------------------------------------------------------------------------------------------

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
            # gzip -d clvhealth_jcafb_2020_13_2020-07-20a.sql.gz

            dropdb -i clvhealth_jcafb_2020_13

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020_13
            psql -f clvhealth_jcafb_2020_13_2020-07-20a.sql -d clvhealth_jcafb_2020_13 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020_13
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-07-20a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-20a.tar.gz

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

Atualizar os fontes do projeto (2020-07-21)
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

Atualizar o(s) módulo(s) [clv_survey] (2020-07-21)
--------------------------------------------------

    #. [tkl-odoo13-jcafb20-vm] Lista de Módulos:

        * clv_survey

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_survey
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb20-vm** ao modo desejado:

            ::

                # ***** tkl-odoo13-jcafb20-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Criar um backup do banco de dados *CLVhealth-JCAFB-2020-13* (2020-07-21a)
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
            pg_dump clvhealth_jcafb_2020_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_13_2020-07-21a.sql

            gzip clvhealth_jcafb_2020_13_2020-07-21a.sql
            pg_dump clvhealth_jcafb_2020_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_13_2020-07-21a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-07-21a.tar.gz clvhealth_jcafb_2020_13

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-21a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_13_2020-07-21a.sql
        * /opt/odoo/clvhealth_jcafb_2020_13_2020-07-21a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-07-21a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-21a.tar.gz

.. index:: clvhealth_jcafb_2020_13_2020-07-21a.sql
.. index:: clvhealth_jcafb_2020_13_2020-07-21a.sql.gz
.. index:: filestore_clvhealth_jcafb_2020_13_2020-07-21a
.. index:: clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-21a

:red:`(Não Executado])` Restaurar um backup do banco de dados *CLVhealth-JCAFB-2020-13* (2020-07-21a)
-----------------------------------------------------------------------------------------------------

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
            # gzip -d clvhealth_jcafb_2020_13_2020-07-21a.sql.gz

            dropdb -i clvhealth_jcafb_2020_13

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020_13
            psql -f clvhealth_jcafb_2020_13_2020-07-21a.sql -d clvhealth_jcafb_2020_13 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020_13
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-07-21a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-21a.tar.gz

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

Atualizar os fontes do projeto (2020-07-22)
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

Atualizar o(s) módulo(s) [clv_survey] (2020-07-22)
--------------------------------------------------

    #. [tkl-odoo13-jcafb20-vm] Lista de Módulos:

        * clv_survey

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_survey
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb20-vm** ao modo desejado:

            ::

                # ***** tkl-odoo13-jcafb20-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Criar um backup do banco de dados *CLVhealth-JCAFB-2020-13* (2020-07-22a)
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
            pg_dump clvhealth_jcafb_2020_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_13_2020-07-22a.sql

            gzip clvhealth_jcafb_2020_13_2020-07-22a.sql
            pg_dump clvhealth_jcafb_2020_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_13_2020-07-22a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-07-22a.tar.gz clvhealth_jcafb_2020_13

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-22a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_13_2020-07-22a.sql
        * /opt/odoo/clvhealth_jcafb_2020_13_2020-07-22a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-07-22a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-22a.tar.gz

.. index:: clvhealth_jcafb_2020_13_2020-07-22a.sql
.. index:: clvhealth_jcafb_2020_13_2020-07-22a.sql.gz
.. index:: filestore_clvhealth_jcafb_2020_13_2020-07-22a
.. index:: clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-22a

:red:`(Não Executado])` Restaurar um backup do banco de dados *CLVhealth-JCAFB-2020-13* (2020-07-22a)
-----------------------------------------------------------------------------------------------------

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
            # gzip -d clvhealth_jcafb_2020_13_2020-07-22a.sql.gz

            dropdb -i clvhealth_jcafb_2020_13

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020_13
            psql -f clvhealth_jcafb_2020_13_2020-07-22a.sql -d clvhealth_jcafb_2020_13 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020_13
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-07-22a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-22a.tar.gz

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

Atualizar o(s) módulo(s) [clv_document_sync_jcafb] (2020-07-23)
---------------------------------------------------------------

    #. [tkl-odoo13-jcafb20-vm] Lista de Módulos:

        * clv_document_sync_jcafb

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_document_sync_jcafb
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb20-vm** ao modo desejado:

            ::

                # ***** tkl-odoo13-jcafb20-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Atualizar os fontes do projeto (2020-07-23)
-------------------------------------------

    #. **Atualizar** os fontes do projeto

        ::

            ssh tkl-odoo13-jcafb20-vm -l root

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

Atualizar o(s) módulo(s) [clv_survey, clv_document] (2020-07-23)
----------------------------------------------------------------

    #. [tkl-odoo13-jcafb20-vm] Lista de Módulos:

        * clv_survey
        * clv_document

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_survey
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_document
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb20-vm** ao modo desejado:

            ::

                # ***** tkl-odoo13-jcafb20-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Criar um backup do banco de dados *CLVhealth-JCAFB-2020-13* (2020-07-23a)
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
            pg_dump clvhealth_jcafb_2020_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_13_2020-07-23a.sql

            gzip clvhealth_jcafb_2020_13_2020-07-23a.sql
            pg_dump clvhealth_jcafb_2020_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_13_2020-07-23a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-07-23a.tar.gz clvhealth_jcafb_2020_13

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-23a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_13_2020-07-23a.sql
        * /opt/odoo/clvhealth_jcafb_2020_13_2020-07-23a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-07-23a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-23a.tar.gz

.. index:: clvhealth_jcafb_2020_13_2020-07-23a.sql
.. index:: clvhealth_jcafb_2020_13_2020-07-23a.sql.gz
.. index:: filestore_clvhealth_jcafb_2020_13_2020-07-23a
.. index:: clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-23a

:red:`(Não Executado])` Restaurar um backup do banco de dados *CLVhealth-JCAFB-2020-13* (2020-07-23a)
-----------------------------------------------------------------------------------------------------

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
            # gzip -d clvhealth_jcafb_2020_13_2020-07-23a.sql.gz

            dropdb -i clvhealth_jcafb_2020_13

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020_13
            psql -f clvhealth_jcafb_2020_13_2020-07-23a.sql -d clvhealth_jcafb_2020_13 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020_13
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-07-23a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-23a.tar.gz

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

Atualizar os fontes do projeto (2020-07-28)
-------------------------------------------

    #. **Atualizar** os fontes do projeto

        ::

            ssh tkl-odoo13-jcafb20-vm -l root

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

Atualizar o(s) módulo(s) [clv_survey] (2020-07-28)
--------------------------------------------------

    #. [tkl-odoo13-jcafb20-vm] Lista de Módulos:

        * clv_survey

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_survey
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb20-vm** ao modo desejado:

            ::

                # ***** tkl-odoo13-jcafb20-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Criar um backup do banco de dados *CLVhealth-JCAFB-2020-13* (2020-07-28a)
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
            pg_dump clvhealth_jcafb_2020_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_13_2020-07-28a.sql

            gzip clvhealth_jcafb_2020_13_2020-07-28a.sql
            pg_dump clvhealth_jcafb_2020_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_13_2020-07-28a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-07-28a.tar.gz clvhealth_jcafb_2020_13

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-28a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_13_2020-07-28a.sql
        * /opt/odoo/clvhealth_jcafb_2020_13_2020-07-28a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-07-28a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-28a.tar.gz

.. index:: clvhealth_jcafb_2020_13_2020-07-28a.sql
.. index:: clvhealth_jcafb_2020_13_2020-07-28a.sql.gz
.. index:: filestore_clvhealth_jcafb_2020_13_2020-07-28a
.. index:: clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-28a

:red:`(Não Executado])` Restaurar um backup do banco de dados *CLVhealth-JCAFB-2020-13* (2020-07-28a)
-----------------------------------------------------------------------------------------------------

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
            # gzip -d clvhealth_jcafb_2020_13_2020-07-28a.sql.gz

            dropdb -i clvhealth_jcafb_2020_13

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020_13
            psql -f clvhealth_jcafb_2020_13_2020-07-28a.sql -d clvhealth_jcafb_2020_13 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020_13
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-07-28a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-28a.tar.gz

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

Atualizar os fontes do projeto (2020-07-30)
-------------------------------------------

    #. **Atualizar** os fontes do projeto

        ::

            ssh tkl-odoo13-jcafb20-vm -l root

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

Atualizar o(s) módulo(s) [ver lista] (2020-07-30)
-------------------------------------------------

    #. [tkl-odoo13-jcafb20-vm] Lista de Módulos:

        * clv_person_history_jcafb
        * clv_family_jcafb
        * clv_family_history_jcafb
        * clv_address_jcafb
        * clv_address_history_jcafb

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_person_history_jcafb
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_family_jcafb
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_address_jcafb
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb20-vm** ao modo desejado:

            ::

                # ***** tkl-odoo13-jcafb20-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Criar um backup do banco de dados *CLVhealth-JCAFB-2020-13* (2020-07-30a)
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
            pg_dump clvhealth_jcafb_2020_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_13_2020-07-30a.sql

            gzip clvhealth_jcafb_2020_13_2020-07-30a.sql
            pg_dump clvhealth_jcafb_2020_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_13_2020-07-30a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-07-30a.tar.gz clvhealth_jcafb_2020_13

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-30a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_13_2020-07-30a.sql
        * /opt/odoo/clvhealth_jcafb_2020_13_2020-07-30a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-07-30a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-30a.tar.gz

.. index:: clvhealth_jcafb_2020_13_2020-07-30a.sql
.. index:: clvhealth_jcafb_2020_13_2020-07-30a.sql.gz
.. index:: filestore_clvhealth_jcafb_2020_13_2020-07-30a
.. index:: clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-30a

:red:`(Não Executado])` Restaurar um backup do banco de dados *CLVhealth-JCAFB-2020-13* (2020-07-30a)
-----------------------------------------------------------------------------------------------------

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
            # gzip -d clvhealth_jcafb_2020_13_2020-07-30a.sql.gz

            dropdb -i clvhealth_jcafb_2020_13

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020_13
            psql -f clvhealth_jcafb_2020_13_2020-07-30a.sql -d clvhealth_jcafb_2020_13 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020_13
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-07-30a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-30a.tar.gz

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

Atualizar os fontes do projeto (2020-07-30)
-------------------------------------------

    #. **Atualizar** os fontes do projeto

        ::

            ssh tkl-odoo13-jcafb20-vm -l root

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

Atualizar o(s) módulo(s) [ver lista] (2020-07-30)
-------------------------------------------------

    #. [tkl-odoo13-jcafb20-vm] Lista de Módulos:

        * clv_document
        * clv_document_jcafb

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021v_13" - m clv_document
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb20-vm** ao modo desejado:

            ::

                # ***** tkl-odoo13-jcafb20-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Criar um backup do banco de dados *CLVhealth-JCAFB-2020-13* (2020-07-30b)
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
            pg_dump clvhealth_jcafb_2020_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_13_2020-07-30b.sql

            gzip clvhealth_jcafb_2020_13_2020-07-30b.sql
            pg_dump clvhealth_jcafb_2020_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_13_2020-07-30b.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-07-30b.tar.gz clvhealth_jcafb_2020_13

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-30b.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_13_2020-07-30b.sql
        * /opt/odoo/clvhealth_jcafb_2020_13_2020-07-30b.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-07-30b.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-30b.tar.gz

.. index:: clvhealth_jcafb_2020_13_2020-07-30b.sql
.. index:: clvhealth_jcafb_2020_13_2020-07-30b.sql.gz
.. index:: filestore_clvhealth_jcafb_2020_13_2020-07-30b
.. index:: clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-30b

:red:`(Não Executado])` Restaurar um backup do banco de dados *CLVhealth-JCAFB-2020-13* (2020-07-30b)
-----------------------------------------------------------------------------------------------------

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
            # gzip -d clvhealth_jcafb_2020_13_2020-07-30b.sql.gz

            dropdb -i clvhealth_jcafb_2020_13

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020_13
            psql -f clvhealth_jcafb_2020_13_2020-07-30b.sql -d clvhealth_jcafb_2020_13 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020_13
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_13_2020-07-30b.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2020_13_2020-07-30b.tar.gz

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
