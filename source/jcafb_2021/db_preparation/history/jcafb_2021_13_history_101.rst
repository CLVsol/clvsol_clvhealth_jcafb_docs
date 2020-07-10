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
Preparação do Banco de Dados - JCAFB-2021v-13
=============================================

:red:`(Não Executado])` Restaurar um backup do banco de dados *CLVhealth-JCAFB-2021v-13* (2020-07-10b)
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
            # gzip -d clvhealth_jcafb_2021v_13_2020-07-10b.sql.gz

            dropdb -i clvhealth_jcafb_2021v_13

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2021v_13
            psql -f clvhealth_jcafb_2021v_13_2020-07-10b.sql -d clvhealth_jcafb_2021v_13 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2021v_13
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2021v_13_2020-07-10b.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021v_13_2020-07-10b.tar.gz

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

Excluir todas as Pessoas do Cadastro :bi:`Person (Aux)` (2020-07-11)
--------------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Excluir todas as Pessoas do Cadastro :bi:`Person (Aux)`:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Contatos*:

            * Menu de acesso:

                * **Contatos** » **Contatos**

        #. Ativar o filtro **Agrupar por** :bi:`Address Type`

        #. Selecionar todas as :bi:`Persons (Aux)` (**605**)

        #. Exercutar a Ação "**Excluir**":

            #. Utilize o botão :bi:`Ok` para executar a Ação.

Excluir todos os Endereços do Cadastro :bi:`Address (Aux)` (2020-07-11)
-----------------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Excluir todos os Endereços do Cadastro :bi:`Address (Aux)`:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Contatos*:

            * Menu de acesso:

                * **Contatos** » **Contatos**

        #. Ativar o filtro **Agrupar por** :bi:`Address Type`

        #. Selecionar todas os :bi:`Addresss (Aux)` (**202**)

        #. Exercutar a Ação "**Excluir**":

            #. Utilize o botão :bi:`Ok` para executar a Ação.

Executar o *Verification Batch* "*Default Batch*" (1) (2020-07-11)
------------------------------------------------------------------

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

            * :bi:`Execution time: 0:11:37.808`

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo13-jcafb21-vm** ao modo padrão:

        ::

            # ***** tkl-odoo13-jcafb21-vm
            #

            ^C

            exit

            /etc/init.d/odoo start

Criar um backup do banco de dados *CLVhealth-JCAFB-2021v-13* (2020-07-11a)
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
            pg_dump clvhealth_jcafb_2021v_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2021v_13_2020-07-11a.sql

            gzip clvhealth_jcafb_2021v_13_2020-07-11a.sql
            pg_dump clvhealth_jcafb_2021v_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2021v_13_2020-07-11a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2021v_13_2020-07-11a.tar.gz clvhealth_jcafb_2021v_13

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021v_13_2020-07-11a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2021v_13_2020-07-11a.sql
        * /opt/odoo/clvhealth_jcafb_2021v_13_2020-07-11a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2021v_13_2020-07-11a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021v_13_2020-07-11a.tar.gz

.. index:: clvhealth_jcafb_2021v_13_2020-07-11a.sql
.. index:: clvhealth_jcafb_2021v_13_2020-07-11a.sql.gz
.. index:: filestore_clvhealth_jcafb_2021v_13_2020-07-11a
.. index:: clvsol_filestore_clvhealth_jcafb_2021v_13_2020-07-11a

:red:`(Não Executado])` Restaurar um backup do banco de dados *CLVhealth-JCAFB-2021v-13* (2020-07-11a)
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
            # gzip -d clvhealth_jcafb_2021v_13_2020-07-11a.sql.gz

            dropdb -i clvhealth_jcafb_2021v_13

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2021v_13
            psql -f clvhealth_jcafb_2021v_13_2020-07-11a.sql -d clvhealth_jcafb_2021v_13 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2021v_13
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2021v_13_2020-07-11a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021v_13_2020-07-11a.tar.gz

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

Atualizar o *Employee History* de todos os Funcionários (1) (2020-07-11)
------------------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Employee History Update` para todos os Funcionários:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Employees*:

            * Menu de acesso:

                * **Funcionários** » :bi:`Employees` » :bi:`Employees`

        #. Selecionar todos os Funcionários (**248**)

        #. Exercutar a Ação ":bi:`Employee History Update`":

            * Parâmetros utilizados:

                * *Sign out date*: **01/03/2020**
                * *Sign in date*: **01/11/2019**

            #. Utilize o botão :bi:`Employee History Update` para executar a Ação.

Remover a Fase de todos os Funcionários (2020-07-11)
----------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Employee Mass Edit` para todos os Funcionários:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Employees*:

            * Menu de acesso:

                * **Funcionários** » :bi:`Employees` » :bi:`Employees`

        #. Selecionar todos os Funcionários (**248**)

        #. Exercutar a Ação ":bi:`Employee Mass Edit`":

            * Parâmetros utilizados:

                * *Phase*: :bi:`Remove`

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Atualizar o *Employee History* de todos os Funcionários (2) (2020-07-11)
------------------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Employee History Update` para todos os Funcionários:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Employees*:

            * Menu de acesso:

                * **Funcionários** » :bi:`Employees` » :bi:`Employees`

        #. Selecionar todos os Funcionários (**248**)

        #. Exercutar a Ação ":bi:`Employee History Update`":

            * Parâmetros utilizados:

                * *Sign out date*: **01/03/2020**
                * *Sign in date*: **01/11/2019**

            #. Utilize o botão :bi:`Employee History Update` para executar a Ação.

Remover a Fase de todas as Pessoas (2020-07-11)
-----------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Person Mass Edit` para todas as Pessoas:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Persons*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Persons`

        #. Selecionar todas as Pessoas (**1540**)

        #. Exercutar a Ação ":bi:`Person Mass Edit`":

            * Parâmetros utilizados:

                * *Phase*: :bi:`Remove`

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Atualizar o *Person History* de todas as Pessoas (2020-07-11)
-------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Person History Update` para todas as Pessoas:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Persons*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Persons`

        #. Selecionar todas as Pessoas (**1540**)

        #. Exercutar a Ação ":bi:`Person History Update`":

            * Parâmetros utilizados:

                * *Sign out date*: **01/03/2020**
                * *Sign in date*: **01/11/2019**

            #. Utilize o botão :bi:`Person History Update` para executar a Ação.

Renovar o *Random ID* de todas as Pessoas (2020-07-11)
------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Person Mass Edit` para todas as Pessoas:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Persons*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Persons`

        #. Selecionar todas as Pessoas (**1540**)

        #. Exercutar a Ação ":bi:`Person Mass Edit`":

            * Parâmetros utilizados:

                * *Random ID*: "**/**"

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Remover a Fase de todas as Famílias (2020-07-11)
------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Family Mass Edit` para todas as Famílias:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Families*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Families`

        #. Selecionar todas as Famílias (**441**)

        #. Exercutar a Ação ":bi:`Family Mass Edit`":

            * Parâmetros utilizados:

                * *Phase*: :bi:`Remove`

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Atualizar o *Family History* de todas as Famílias (2020-07-11)
--------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Family History Update` para todas as Famílias:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Families*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Families`

        #. Selecionar todas as Famílias (**441**)

        #. Exercutar a Ação ":bi:`Family History Update`":

            * Parâmetros utilizados:

                * *Sign out date*: **01/03/2020**
                * *Sign in date*: **01/11/2019**

            #. Utilize o botão :bi:`Family History Update` para executar a Ação.

Remover a Fase de todos os Endereços (2020-07-11)
-------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Address Mass Edit` para todas as Pessoas:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Addresses*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Addresses`

        #. Selecionar todas as Pessoas (**665**)

        #. Exercutar a Ação ":bi:`Address Mass Edit`":

            * Parâmetros utilizados:

                * *Phase*: :bi:`Remove`

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Atualizar o *Address History* de todos os Endereços (2020-07-11)
----------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Address History Update` para todos os Endereços:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Addresss*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Addresss`

        #. Selecionar todos os Endereços (**665**)

        #. Exercutar a Ação ":bi:`Address History Update`":

            * Parâmetros utilizados:

                * *Sign out date*: **01/03/2020**
                * *Sign in date*: **01/11/2019**

            #. Utilize o botão :bi:`Address History Update` para executar a Ação.

Remover o *Responsible Empĺoyee* de todos os Endereços (2020-07-11)
-------------------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Address Mass Edit` para todas as Pessoas:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Addresses*:

            * Menu de acesso:

                * :bi:`Community` » :bi:`Community` » :bi:`Addresses`

        #. Selecionar todas as Pessoas (**665**)

        #. Exercutar a Ação ":bi:`Address Mass Edit`":

            * Parâmetros utilizados:

                * *Responsible Empĺoyee*: :bi:`Remove`

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Criar um backup do banco de dados *CLVhealth-JCAFB-2021v-13* (2020-07-11b)
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
            pg_dump clvhealth_jcafb_2021v_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2021v_13_2020-07-11b.sql

            gzip clvhealth_jcafb_2021v_13_2020-07-11b.sql
            pg_dump clvhealth_jcafb_2021v_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2021v_13_2020-07-11b.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2021v_13_2020-07-11b.tar.gz clvhealth_jcafb_2021v_13

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021v_13_2020-07-11b.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2021v_13_2020-07-11b.sql
        * /opt/odoo/clvhealth_jcafb_2021v_13_2020-07-11b.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2021v_13_2020-07-11b.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021v_13_2020-07-11b.tar.gz

.. index:: clvhealth_jcafb_2021v_13_2020-07-11b.sql
.. index:: clvhealth_jcafb_2021v_13_2020-07-11b.sql.gz
.. index:: filestore_clvhealth_jcafb_2021v_13_2020-07-11b
.. index:: clvsol_filestore_clvhealth_jcafb_2021v_13_2020-07-11b

Restaurar um backup do banco de dados *CLVhealth-JCAFB-2021v-13* (2020-07-11b)
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
            # gzip -d clvhealth_jcafb_2021v_13_2020-07-11b.sql.gz

            dropdb -i clvhealth_jcafb_2021v_13

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2021v_13
            psql -f clvhealth_jcafb_2021v_13_2020-07-11b.sql -d clvhealth_jcafb_2021v_13 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2021v_13
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2021v_13_2020-07-11b.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021v_13_2020-07-11b.tar.gz

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

Marcar o *Active Log* de todos os Objetos (2020-07-09)
------------------------------------------------------

    #. [tkl-odoo13-jcafb21-vm] Executar a Ação :bi:`Global Log Client Mass Edit` para todos os Objetos:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo13-jcafb21-vm <https://tkl-odoo13-jcafb21-vm>`_

        #. Acessar a *View* *Global Log Clients*:

            * Menu de acesso:

                * :bi:`Base` » :bi:`Global Logs` » :bi:`Global Log Clients`

        #. Selecionar todos os :bi:`Global Log Clients` (**43**)

        #. Exercutar a Ação ":bi:`Global Log Client Mass Edit`":

            * Parâmetros utilizados:

                * *Active Log*: **Set** **marcado**

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Criar um backup do banco de dados *CLVhealth-JCAFB-2021v-13* (2020-07-09a)
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
            pg_dump clvhealth_jcafb_2021v_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2021v_13_2020-07-09a.sql

            gzip clvhealth_jcafb_2021v_13_2020-07-09a.sql
            pg_dump clvhealth_jcafb_2021v_13 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2021v_13_2020-07-09a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2021v_13_2020-07-09a.tar.gz clvhealth_jcafb_2021v_13

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021v_13_2020-07-09a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2021v_13_2020-07-09a.sql
        * /opt/odoo/clvhealth_jcafb_2021v_13_2020-07-09a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2021v_13_2020-07-09a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021v_13_2020-07-09a.tar.gz

.. index:: clvhealth_jcafb_2021v_13_2020-07-09a.sql
.. index:: clvhealth_jcafb_2021v_13_2020-07-09a.sql.gz
.. index:: filestore_clvhealth_jcafb_2021v_13_2020-07-09a
.. index:: clvsol_filestore_clvhealth_jcafb_2021v_13_2020-07-09a

:red:`(Não Executado])` Restaurar um backup do banco de dados *CLVhealth-JCAFB-2021v-13* (2020-07-09a)
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
            # gzip -d clvhealth_jcafb_2021v_13_2020-07-09a.sql.gz

            dropdb -i clvhealth_jcafb_2021v_13

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2021v_13
            psql -f clvhealth_jcafb_2021v_13_2020-07-09a.sql -d clvhealth_jcafb_2021v_13 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2021v_13
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2021v_13_2020-07-09a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2021v_13_2020-07-09a.tar.gz

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

Adicionar a nova *Phase* (JCAFB-2021v) para a *CLVhealth-JCAFB-2021v-13* (2020-07-10)
-------------------------------------------------------------------------------------

    #. Incluir a nova Fase **JCAFB-2021v**:

        #. Acessar a *View* *Phases*:

            * Menu de acesso:
                * :bi:`Base` » :bi:`Configuration` » :bi:`Phases`

        #. Incluir uma nova Fase:

            * Parâmetros editados:

                * *Phase*: "**JCAFB-2021v**"
                * *Description*: "**Jornada Virtual simulando uma quinta visita virtual à cidade de Fernão - SP**"

Atualizar o "*Global Settings*" para a *CLVhealth-JCAFB-2021v-13* (2020-07-10)
------------------------------------------------------------------------------

    #. Acessar a *View* *Global Settings*:

        * Menu de acesso:

            * :bi:`Base` » :bi:`Global Settings` » :bi:`Global Settings`

        #. Configurar o parâmetro :bi:`Phase` » :bi:`Phase`: **JCAFB-2021v**

.. toctree::   :maxdepth: 2
