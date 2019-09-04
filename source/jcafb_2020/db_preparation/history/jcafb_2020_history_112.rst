.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

=========================================================================================
[2019-09-05] - Preparação do Banco de Dados - JCAFB-2020 - Servidor [tkl-odoo12-jcafb-vm]
=========================================================================================

Restaurar um backup do *CLVhealth-JCAFB-2020* no servidor "tkl-odoo12-jcafb-vm" (2019-09-04a)
---------------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_restore`.

    #. [tkl-odoo12-jcafb-vm] Estabelecer uma sessão ssh com o servidor **tkl-odoo12-jcafb-vm** e paralizar o *Odoo*:

        ::

            # ***** tkl-odoo12-jcafb-vm
            #

            ssh tkl-odoo12-jcafb-vm -l root

            /etc/init.d/odoo stop

            su odoo

    #. [tkl-odoo12-jcafb-vm] Executar os comandos de restauração dos arquivos de backup:

        ::

            # ***** tkl-odoo12-jcafb-vm
            #

            cd /opt/odoo
            # gzip -d clvhealth_jcafb_2020_2019-09-04a.sql.gz

            dropdb -i clvhealth_jcafb_2020

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020
            psql -f clvhealth_jcafb_2020_2019-09-04a.sql -d clvhealth_jcafb_2020 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-09-04a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-09-04a.tar.gz

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo desejado:

        ::

            # ***** tkl-odoo12-jcafb-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

:red:`(Não Executado)` Desabilitar a instalação do(s) módulo(s) [export, verification, processing, report] (2019-08-11)
-----------------------------------------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/module_installation`.

    #. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, **desabilitando** o(s) Módulo(s):

        * clv_export
        * clv_document_export
        * clv_lab_test_export
        * clv_person_export
        * clv_export_jcafb
        * clv_document_export_jcafb
        * clv_lab_test_export_jcafb
        * clv_person_export_jcafb

    #. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, **desabilitando** o(s) Módulo(s):

        * clv_verification
        * clv_verification_jcafb
        * clv_person_verification_jcafb

    #. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, **desabilitando** o(s) Módulo(s):

        * clv_processing
        * clv_processing_jcafb

    #. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, **desabilitando** o(s) Módulo(s):

        * clv_report
        * clv_report_jcafb

:red:`(Não Executado)` Instalar o(s) módulo(s) [export, verification, processing, report] (2019-07-29)
------------------------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/module_installation`.

    #. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, **habilitando** o(s) Módulo(s):

        * clv_export
        * clv_document_export
        * clv_lab_test_export
        * clv_person_export
        * clv_export_jcafb
        * clv_document_export_jcafb
        * clv_lab_test_export_jcafb
        * clv_person_export_jcafb

    #. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, **habilitando** o(s) Módulo(s):

        * clv_verification
        * clv_verification_jcafb
        * clv_person_verification_jcafb

    #. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, **habilitando** o(s) Módulo(s):

        * clv_processing
        * clv_processing_jcafb

    #. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, **habilitando** o(s) Módulo(s):

        * clv_report
        * clv_report_jcafb

    #. [tkl-odoo12-jcafb-vm] **Executar** a instalação do(s) Módulo(s) adicionado(s)/habilitado(s):

        #. Estabelecer uma sessão ssh (session 1) com o servidor **tkl-odoo12-jcafb-vm** e executar o *Odoo* no modo manual:

            ::

                # ***** tkl-odoo12-jcafb-vm (session 1)
                #

                ssh tkl-odoo12-jcafb-vm -l root

                /etc/init.d/odoo stop

                su odoo
                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

        #. Estabelecer uma sessão ssh (session 2) com o servidor **tkl-odoo12-jcafb-vm** e executar o **install.py**:

            ::

                # ***** tkl-odoo12-jcafb-vm (session 2)
                #

                ssh tkl-odoo12-jcafb-vm -l odoo

                cd /opt/odoo/clvsol_clvhealth_jcafb/project
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020"

            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo desejado:

            ::

                # ***** tkl-odoo12-jcafb-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

:red:`(Não Executado)` Configurar as permissões do usuário de referência da JCAFB-2020 (2019-08-11)
---------------------------------------------------------------------------------------------------

    #. Configurar as permissões do usuário de referência:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Users*:

            * Menu de acesso:
                * :bi:`Configurações` » :bi:`Utilizadores e Empresas` » :bi:`Usuários`

        #. Selecionar o usuário de referência.

        #. Configurar as permissões:

            * *Address*: :bi:`User (Address)`
            * *Address (Aux)*: :bi:`Manager (Address (Aux))`
            * Administração:  
            * *Community*: :bi:`User (Community)`
            * *Event*: :bi:`User (Event)`
            * :green:`(Novo)` *Export*: :bi:`User (Export)`
            * *External Sync*: :bi:`User (External Sync)`
            * *Family*: :bi:`User (Family)`
            * *Family (Aux)*: :bi:`Manager (Family (Aux))`
            * *File System User*: :bi:`(File System)`
            * *Funcionários*: :bi:`Oficial`
            * *Global Tag*: :bi:`User (Global Tag)`
            * *Media File*: :bi:`User (Media File)`
            * *Aux*: :bi:`User (Aux)`
            * *Person*: :bi:`User (Person)`
            * *Person (Aux)*: :bi:`Manager (Person (Aux))`
            * *Pesquisa*: :bi:`Utilizador`
            * *Phase*: :bi:`User (Phase)`
            * :green:`(Novo)` *Processing*: :bi:`User (Processing)`
            * :green:`(Novo)` *Report*: :bi:`User (Report)`
            * *Set*: :bi:`User (Set)`
            * *Survey*: :bi:`User (Survey)`
            * :green:`(Novo)` *Verification*: :bi:`User (Verification)`
            *
            * *Lab Test*:
                * :bi:`User (Lab Test) ​`
            *
            * *Base*:
                * :bi:`Annotation User (Base)`,
                * :bi:`Log User (Base)`,
                * :bi:`Register User (Base)`,
                * :bi:`User (Base)`,
                * :bi:`Super User (Base)`,
                * :bi:`Manager (Base)` ​
            *
            * *Document*:
                * :bi:`User (Document)` ​
            
:red:`(Não Executado)` Atualizar as permissões de todos os Usuários da JCAFB-2020 (2019-08-11)
----------------------------------------------------------------------------------------------

    * Referência: :doc:`/user_guide/employee/employee_user_groups_updt`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação *Employee User Groups Update* para os *Employees* da JCAFB-2020:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Employees*:

            * Menu de acesso:
                * *Funcionários* » *Employees* » *Employees*

        #. Selecionar os *Employees* da JCAFB-2020 (**18**)

        #. Exercutar a Ação "**Employee User Groups Update**":

            #. Selecionar o :bi:`Reference Employee`: Usuário de referência (selecionado no ítem anterior).

            #. Selecionar o parâmetro :bi:`Access Rights:` » :bi:`Set`.

            #. Precionar o botão :bi:`Get Reference Employee Access Rights`.

            #. Utilize o botão :bi:`Update` para executar a Ação.

.. toctree::
   :maxdepth: 2
