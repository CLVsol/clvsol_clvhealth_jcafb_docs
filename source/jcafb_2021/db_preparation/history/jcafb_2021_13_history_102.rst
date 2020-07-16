.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .blue {color:blue} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: blue
.. role:: bi

=================================================
Preparação do Banco de Dados (2) - JCAFB-2021v-13
=================================================

Restaurar um backup do banco de dados *CLVhealth-JCAFB-2021v-13* (2020-07-15a)
------------------------------------------------------------------------------

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
            # gzip -d clvhealth_jcafb_2021v_13_2020-07-15a.sql.gz

            dropdb -i clvhealth_jcafb_2021v_13

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2021v_13
            psql -f clvhealth_jcafb_2021v_13_2020-07-15a.sql -d clvhealth_jcafb_2021v_13 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2021v_13
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2021v_13_2020-07-15a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021v_13_2020-07-15a.tar.gz

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

Executar o *Verification Batch* "*Default Batch*" (2020-07-16)
--------------------------------------------------------------

    #. Estabelecer uma sessão ssh com o servidor **tkl-odoo13-jcafb21-vm** e executar o *Odoo* no modo manual:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            ssh tkl-odoo13-jcafb21-vm -l root

            /etc/init.d/odoo stop

            su odoo

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    #. [tkl-odoo13-jcafb21-vm] Executar o :bi:`Verification Batch` "**Default Batch**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Executar a ação :bi:`Verification Batch Exec` para o "**Default Batch**":

            * Menu de acesso:
                
                * :bi:`Verification` » :bi:`Verification` » :bi:`Verification` » :bi:`Batches` » **Ação** » :bi:`Verification Batch Exec`

            * :bi:`Execution time: 0:10:21.496`

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo padrão:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            ^C

            exit

            /etc/init.d/odoo start

Configurar as permissões do usuário de referência da JCAFB-2021v (2020-07-16)
-----------------------------------------------------------------------------

    #. Configurar as permissões do usuário de referência:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Users*:

            * Menu de acesso:

                * :bi:`Configurações` » :bi:`Utilizadores e Empresas` » :bi:`Usuários`

        #. Selecionar o usuário de referência.

        #. Configurar as permissões:

            * Recursos Humanos
            
                * Funcionários: **Administrador**

            * Marketing

                * Questionário: **Administrador**

            * Outro

                * *Address (Aux)*: :bi:`Manager (Address (Aux))`
                * *Address*: :bi:`Manager (Address)`
                * *Aux*: :bi:`Manager (Aux)`
                * *Community*: :bi:`Manager (Community)`
                * *Event*: :bi:`Manager (Event)`
                * *Export*: :bi:`Manager (Export)`
                * *External Sync*:
                * *Family*: :bi:`Manager (Family)`
                * *File System*: :bi:`Manager (File System)`
                * *Global Tag*: :bi:`Manager (Global Tag)`
                * *Person (Aux)*: :bi:`Manager (Person (Aux))`
                * *Person Selection*:
                * *Person*: :bi:`Manager (Person)`
                * *Phase*: :bi:`User (Phase)`
                * *Processing*:
                * *Report*:
                * *Set*: :bi:`Manager (Set)`
                * *Summary*: :bi:`Manager (Summary)`
                * *Survey*:  :bi:`Manager (Survey)`
                * *Verification*: :bi:`Manager (Verification)`

            * *Base*:

                * :bi:`Annotation User (Base)`,
                * :bi:`Log User (Base)`,
                * :bi:`Manager (Base)` ​
                * :bi:`Register User (Base)`,
                * :bi:`Super User (Base)`,
                * :bi:`User (Base)`,

            * *Document*:

                * :bi:`Manager (Document)` ​
                * :bi:`User (Document)` ​
            
            * *Lab Test*:

                * :bi:`Manager (Lab Test)`
                * :bi:`User (Lab Test)`

            * Ferramentas Extras:

                * **Criação de Contato**

Atualizar as permissões de todos os Usuários da JCAFB-2021v (2020-07-16)
------------------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação *Employee User Groups Update* para os *Employees* da JCAFB-2021v:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Employees*:

            * Menu de acesso:

                * *Funcionários* » *Employees* » *Employees*

        #. Selecionar os *Employees* da JCAFB-2021v (**28**)

        #. Exercutar a Ação "**Employee User Groups Update**":

            #. Selecionar o :bi:`Reference Employee`: Usuário de referência (selecionado no ítem anterior).

            #. Selecionar o parâmetro :bi:`Access Rights:` » :bi:`Set`.

            #. Precionar o botão :bi:`Get Reference Employee Access Rights`.

            #. Utilize o botão :bi:`Update` para executar a Ação.

Criar um backup do banco de dados *CLVhealth-JCAFB-2021v-13* (2020-07-16a)
--------------------------------------------------------------------------

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
            pg_dump clvhealth_jcafb_2021v_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2021v_13_2020-07-16a.sql

            gzip clvhealth_jcafb_2021v_13_2020-07-16a.sql
            pg_dump clvhealth_jcafb_2021v_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2021v_13_2020-07-16a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2021v_13_2020-07-16a.tar.gz clvhealth_jcafb_2021v_13

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021v_13_2020-07-16a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2021v_13_2020-07-16a.sql
        * /opt/odoo/clvhealth_jcafb_2021v_13_2020-07-16a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2021v_13_2020-07-16a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021v_13_2020-07-16a.tar.gz

.. index:: clvhealth_jcafb_2021v_13_2020-07-16a.sql
.. index:: clvhealth_jcafb_2021v_13_2020-07-16a.sql.gz
.. index:: filestore_clvhealth_jcafb_2021v_13_2020-07-16a
.. index:: clvsol_filestore_clvhealth_jcafb_2021v_13_2020-07-16a

:red:`(Não Executado])` Restaurar um backup do banco de dados *CLVhealth-JCAFB-2021v-13* (2020-07-16a)
------------------------------------------------------------------------------------------------------

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

.. toctree::   :maxdepth: 2
