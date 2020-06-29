.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

==========================================
Migração do Banco de Dados - JCAFB-2021-13
==========================================

Inicializar o conteúdo do diretório **clvsol_filestore/clvhealth_jcafb** [tkl-odoo13-jcafb21-vm] (2020-06-21)
-------------------------------------------------------------------------------------------------------------

	#. [tkl-odoo13-jcafb21-vm] Criar, manualmente, os diretórios:

		* /opt/odoo/**clvsol_filestore**

		* /opt/odoo/clvsol_filestore/**clvhealth_jcafb**

		* /opt/odoo/clvsol_filestore/clvhealth_jcafb/**export_files**

		* /opt/odoo/clvsol_filestore/clvhealth_jcafb/export_files/**csv**

		* /opt/odoo/clvsol_filestore/clvhealth_jcafb/export_files/**sqlite**

		* /opt/odoo/clvsol_filestore/clvhealth_jcafb/export_files/**xls**

		* /opt/odoo/clvsol_filestore/clvhealth_jcafb/**lab_test_files**

		* /opt/odoo/clvsol_filestore/clvhealth_jcafb/lab_test_files/**reports**

		* /opt/odoo/clvsol_filestore/clvhealth_jcafb/lab_test_files/reports/**templates**

		* /opt/odoo/clvsol_filestore/clvhealth_jcafb/lab_test_files/reports/**xls**

		* /opt/odoo/clvsol_filestore/clvhealth_jcafb/lab_test_files/**results**

		* /opt/odoo/clvsol_filestore/clvhealth_jcafb/lab_test_files/results/**templates**

		* /opt/odoo/clvsol_filestore/clvhealth_jcafb/lab_test_files/results/**xls**

		* /opt/odoo/clvsol_filestore/clvhealth_jcafb/**summary_files**

		* /opt/odoo/clvsol_filestore/clvhealth_jcafb/**survey_files**

		* /opt/odoo/clvsol_filestore/clvhealth_jcafb/survey_files/**templates**

	#. Copiar, manualmente, a partir do servidor **tkl-odoo13-jcafb21-vm** para o servidor **tkl-odoo13-jcafb21-vm**, o conteúdo dos diretórios listados anteriormente.

		* "tkl-odoo13-jcafb21-vm:/opt/odoo/clvsol_filestore/clvhealth_jcafb" **->** "tkl-odoo13-jcafb21-vm:/opt/odoo/clvsol_filestore/clvhealth_jcafb"

.. index:: clvsol_filestore
.. index:: clvsol_filestore/clvhealth_jcafb
.. index:: clvsol_filestore/clvhealth_jcafb/export_files
.. index:: clvsol_filestore/clvhealth_jcafb/lab_test_files
.. index:: clvsol_filestore/clvhealth_jcafb/summary_files
.. index:: clvsol_filestore/clvhealth_jcafb/survey_files

Criar uma nova instância do *CLVhealth-JCAFB-2021-13* (2020-06-23)
------------------------------------------------------------------

	* **Execution time: 0:08:48.580**

    #. [tkl-odoo13-jcafb21-vm] Estabelecer uma sessão ssh (session 1) com o servidor **tkl-odoo13-jcafb21-vm** e paralizar o *Odoo*:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            ssh tkl-odoo13-jcafb21-vm -l root

            /etc/init.d/odoo stop

            su odoo

    #. [tkl-odoo13-jcafb21-vm] Excluir a instância do *CLVhealth-JCAFB-2021-13* existente:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            cd /opt/odoo
            dropdb -i clvhealth_jcafb_2021_13

            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2021_13

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo manual:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    #. Estabelecer uma sessão ssh (session 2) com o servidor **tkl-odoo13-jcafb21-vm** e executar o **install.py**:

        ::

            # ***** tkl-odoo13-jcafb21-vm (session 2)
            #

            ssh tkl-odoo13-jcafb21-vm -l odoo

            cd /opt/odoo/clvsol_clvhealth_jcafb/project
            
            python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2021_13"
            # Execution time: 0:08:22.364

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo desejado:

        ::

            # ***** tkl-odoo13-jcafb21-vm (session 1)
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

Criar o *External Sync Host* "https://192.168.25.188" (2020-06-23)
------------------------------------------------------------------

    #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

    #. Criar o *External Sync Host* **https://192.168.25.188**:

        * Menu de acesso:
            
            * *External Sync* > *Configuration* > *Hosts* > Criar

        * Parâmetros utilizados:
            
            * External Host Name: "**https://192.168.25.188**"
            * External Database Name: "**clvhealth_jcafb_2020_13**"
            * External User: "**admin**"
            * External User Password: "*******"

Criar um backup do banco de dados *CLVhealth-JCAFB-2021-13* (2020-06-24a)
-------------------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb21-vm** e paralizar o *Odoo*:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            ssh tkl-odoo13-jcafb21-vm -l root

            /etc/init.d/odoo stop

            su odoo

    #. [tkl-odoo13-jcafb21-vm] Executar os comandos de criação dos arquivos de backup:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #
            # data_dir = /var/lib/odoo/.local/share/Odoo
            #

            cd /opt/odoo
            pg_dump clvhealth_jcafb_2021_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2021_13_2020-06-24a.sql

            gzip clvhealth_jcafb_2021_13_2020-06-24a.sql
            pg_dump clvhealth_jcafb_2021_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2021_13_2020-06-24a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2021_13_2020-06-24a.tar.gz clvhealth_jcafb_2021_13

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021_13_2020-06-24a.tar.gz clvhealth_jcafb

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo desejado:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    Criados os seguintes arquivos:
        * /opt/odoo/clvhealth_jcafb_2021_13_2020-06-24a.sql
        * /opt/odoo/clvhealth_jcafb_2021_13_2020-06-24a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2021_13_2020-06-24a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021_13_2020-06-24a.tar.gz

.. index:: clvhealth_jcafb_2021_13_2020-06-24a.sql
.. index:: clvhealth_jcafb_2021_13_2020-06-24a.sql.gz
.. index:: filestore_clvhealth_jcafb_2021_13_2020-06-24a
.. index:: clvsol_filestore_clvhealth_jcafb_2021_13_2020-06-24a

:red:`(Não Executado])` Restaurar um backup do banco de dados *CLVhealth-JCAFB-2021-13* (2020-06-24a)
-----------------------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_restore`.

    #. [tkl-odoo13-jcafb21-vm] Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb21-vm** e paralizar o *Odoo*:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            ssh tkl-odoo13-jcafb21-vm -l root

            /etc/init.d/odoo stop

            su odoo

    #. [tkl-odoo13-jcafb21-vm] Executar os comandos de restauração dos arquivos de backup:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            cd /opt/odoo
            # gzip -d clvhealth_jcafb_2021_13_2020-06-24a.sql.gz

            dropdb -i clvhealth_jcafb_2021_13

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2021_13
            psql -f clvhealth_jcafb_2021_13_2020-06-24a.sql -d clvhealth_jcafb_2021_13 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2021_13
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2021_13_2020-06-24a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021_13_2020-06-24a.tar.gz

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo desejado:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    #. [tkl-odoo13-jcafb21-vm] Configurar o parâmetro "**web.base.url**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* **Parâmetros do Sistema**:

            * Menu de acesso:
                
                * **Configurações** » **Técnico** » **Parâmetros** » **Parâmetros do Sistema**

        #. Pesquisar pelo registro com a **Chave** "**web.base.url**"

        #. Editar o registro apresentado (**Chave**: "**web.base.url**")

        #. Alterar o campo **Valor** para:

            * "**http://tkl-odoo13-jcafb21-vm**".

        #. Salvar o registro editado.

Executar o *External Sync Batch* "*Default Batch*" (1) (2020-06-22)
-------------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Configurar todos os :bi:`External Sync Schedules`:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit (2)`, todos os :bi:`External Sync Schedules`:

            * Menu de acesso:
                
                * :bi:`External Sync` » :bi:`Confituration` » :bi:`External Sync` » :bi:`Batch Members` » **Ação** » :bi:`External Sync Schedule Mass Edit (2)`

            * Parâmetros alterados:
                
                * *External Host*: "**https://192.168.25.188**"
                * *Max Task Registers*: "**250.000**"
                * *Disable Inclusion*: "**marcado**"
                * *Disable Sync*: "**marcado**"

    #. Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb21-vm** e executar o *Odoo* no modo manual:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            ssh tkl-odoo13-jcafb21-vm -l root

            /etc/init.d/odoo stop

            su odoo

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    #. [tkl-odoo13-jcafb21-vm] Executar o :bi:`External Sync Batch` "**Default Batch**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Executar a ação :bi:`External Sync Batch Exec` para o "**Default Batch**":

            * Menu de acesso:
                
                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Batches` » **Ação** » :bi:`External Sync Batch Exec`

            * :bi:`Execution time: 0:10:47.361`

    #. [tkl-odoo13-jcafb21-vm] Configurar os :bi:`External Sync Schedules` :green:`(Enabled)`:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit (2)`, todos os :bi:`External Sync Schedules`:

            * Menu de acesso:
                
                * :bi:`External Sync` » :bi:`Confituration` » :bi:`External Sync` » :bi:`Batch Members` » **Ação** » :bi:`External Sync Schedule Mass Edit (2)`

            * Parâmetros alterados:
                
                * *Disable Identification*: "**marcado**"

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo padrão:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            ^C

            exit

            /etc/init.d/odoo start

Executar o *External Sync Batch* "*Default Batch*" (2) (2020-06-22)
-------------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Configurar todos os :bi:`External Sync Schedules`:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit (2)`, os :bi:`External Sync Schedules` cujos "Methods* seja "**_res_users_migration**"" :

            * Menu de acesso:
                
                * :bi:`External Sync` » :bi:`Confituration` » :bi:`External Sync` » :bi:`Batch Members` » **Ação** » :bi:`External Sync Schedule Mass Edit (2)`

            * Parâmetros alterados:
                
                * *Disable Inclusion*: "**desmarcado**"
                * *Disable Sync*: "**desmarcado**"

    #. Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb21-vm** e executar o *Odoo* no modo manual:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            ssh tkl-odoo13-jcafb21-vm -l root

            /etc/init.d/odoo stop

            su odoo

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    #. [tkl-odoo13-jcafb21-vm] Executar o :bi:`External Sync Batch` "**Default Batch**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Executar a ação :bi:`External Sync Batch Exec` para o "**Default Batch**":

            * Menu de acesso:
                
                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Batches` » **Ação** » :bi:`External Sync Batch Exec`

            * :bi:`Execution time: 0:00:20.528`

    #. [tkl-odoo13-jcafb21-vm] Configurar os :bi:`External Sync Schedules` :green:`(Enabled)`:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit (2)`, os :bi:`External Sync Schedules` cujos "Methods* seja "**_res_users_migration**"" :

            * Menu de acesso:
                
                * :bi:`External Sync` » :bi:`Confituration` » :bi:`External Sync` » :bi:`Batch Members` » **Ação** » :bi:`External Sync Schedule Mass Edit (2)`

            * Parâmetros alterados:
                
                * *Disable Inclusion*: "**marcado**"
                * *Disable Sync*: "**marcado**"

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo padrão:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            ^C

            exit

            /etc/init.d/odoo start

Criar um backup do banco de dados *CLVhealth-JCAFB-2021-13* (2020-06-22b)
-------------------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb21-vm** e paralizar o *Odoo*:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            ssh tkl-odoo13-jcafb21-vm -l root

            /etc/init.d/odoo stop

            su odoo

    #. [tkl-odoo13-jcafb21-vm] Executar os comandos de criação dos arquivos de backup:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #
            # data_dir = /var/lib/odoo/.local/share/Odoo
            #

            cd /opt/odoo
            pg_dump clvhealth_jcafb_2021_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2021_13_2020-06-22b.sql

            gzip clvhealth_jcafb_2021_13_2020-06-22b.sql
            pg_dump clvhealth_jcafb_2021_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2021_13_2020-06-22b.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2021_13_2020-06-22b.tar.gz clvhealth_jcafb_2021_13

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021_13_2020-06-22b.tar.gz clvhealth_jcafb

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo desejado:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    Criados os seguintes arquivos:
        * /opt/odoo/clvhealth_jcafb_2021_13_2020-06-22b.sql
        * /opt/odoo/clvhealth_jcafb_2021_13_2020-06-22b.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2021_13_2020-06-22b.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021_13_2020-06-22b.tar.gz

.. index:: clvhealth_jcafb_2021_13_2020-06-22b.sql
.. index:: clvhealth_jcafb_2021_13_2020-06-22b.sql.gz
.. index:: filestore_clvhealth_jcafb_2021_13_2020-06-22b
.. index:: clvsol_filestore_clvhealth_jcafb_2021_13_2020-06-22b

:red:`(Não Executado])` Restaurar um backup do banco de dados *CLVhealth-JCAFB-2021-13* (2020-06-22b)
-----------------------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_restore`.

    #. [tkl-odoo13-jcafb21-vm] Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb21-vm** e paralizar o *Odoo*:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            ssh tkl-odoo13-jcafb21-vm -l root

            /etc/init.d/odoo stop

            su odoo

    #. [tkl-odoo13-jcafb21-vm] Executar os comandos de restauração dos arquivos de backup:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            cd /opt/odoo
            # gzip -d clvhealth_jcafb_2021_13_2020-06-22b.sql.gz

            dropdb -i clvhealth_jcafb_2021_13

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2021_13
            psql -f clvhealth_jcafb_2021_13_2020-06-22b.sql -d clvhealth_jcafb_2021_13 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2021_13
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2021_13_2020-06-22b.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021_13_2020-06-22b.tar.gz

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo desejado:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    #. [tkl-odoo13-jcafb21-vm] Configurar o parâmetro "**web.base.url**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* **Parâmetros do Sistema**:

            * Menu de acesso:
                
                * **Configurações** » **Técnico** » **Parâmetros** » **Parâmetros do Sistema**

        #. Pesquisar pelo registro com a **Chave** "**web.base.url**"

        #. Editar o registro apresentado (**Chave**: "**web.base.url**")

        #. Alterar o campo **Valor** para:

            * "**http://tkl-odoo13-jcafb21-vm**".

        #. Salvar o registro editado.

Executar o *External Sync Batch* "*Default Batch*" (3) (2020-06-22)
-------------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Configurar todos os :bi:`External Sync Schedules`:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit (2)`, os :bi:`External Sync Schedules` cujos "Methods* seja "**_object_external_recognize**"" :

            * Menu de acesso:
                
                * :bi:`External Sync` » :bi:`Confituration` » :bi:`External Sync` » :bi:`Batch Members` » **Ação** » :bi:`External Sync Schedule Mass Edit (2)`

            * Parâmetros alterados:
                
                * *Disable Inclusion*: "**desmarcado**"
                * *Disable Sync*: "**desmarcado**"

    #. Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb21-vm** e executar o *Odoo* no modo manual:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            ssh tkl-odoo13-jcafb21-vm -l root

            /etc/init.d/odoo stop

            su odoo

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    #. [tkl-odoo13-jcafb21-vm] Executar o :bi:`External Sync Batch` "**Default Batch**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Executar a ação :bi:`External Sync Batch Exec` para o "**Default Batch**":

            * Menu de acesso:
                
                * :bi:`External Sync` » :bi:`External Sync` » :bi:`External Sync` » :bi:`Batches` » **Ação** » :bi:`External Sync Batch Exec`

            * :bi:`Execution time: 0:17:57.029`

    #. [tkl-odoo13-jcafb21-vm] Configurar os :bi:`External Sync Schedules` :green:`(Enabled)`:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Configurar, com a ajuda da ação :bi:`External Sync Schedule Mass Edit (2)`, os :bi:`External Sync Schedules` cujos "Methods* seja "**_object_external_recognize**"" :

            * Menu de acesso:
                
                * :bi:`External Sync` » :bi:`Confituration` » :bi:`External Sync` » :bi:`Batch Members` » **Ação** » :bi:`External Sync Schedule Mass Edit (2)`

            * Parâmetros alterados:
                
                * *Disable Inclusion*: "**marcado**"
                * *Disable Sync*: "**marcado**"

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo padrão:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            ^C

            exit

            /etc/init.d/odoo start

.. toctree::   :maxdepth: 2
