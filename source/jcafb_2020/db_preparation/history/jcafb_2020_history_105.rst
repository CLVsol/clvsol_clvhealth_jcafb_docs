.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

=========================================================================================
[2019-08-20] - Preparação do Banco de Dados - JCAFB-2020 - Servidor [tkl-odoo12-jcafb-vm]
=========================================================================================

Restaurar um backup do *CLVhealth-JCAFB-2020* no servidor "tkl-odoo12-jcafb-vm" (2019-08-19a)
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
            # gzip -d clvhealth_jcafb_2020_2019-08-06a.sql.gz

            dropdb -i clvhealth_jcafb_2020

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020
            psql -f clvhealth_jcafb_2020_2019-08-06a.sql -d clvhealth_jcafb_2020 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-08-06a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-08-06a.tar.gz

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo desejado:

        ::

            # ***** tkl-odoo12-jcafb-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

Atualizar o(s) módulo(s) [clv_address_history, clv_family, clv_family_jcafb, clv_family_history, clv_family_history, clv_person_history_jcafb] (2019-08-19)
-----------------------------------------------------------------------------------------------------------------------------------------------------------

    * Referência: :doc:`/setup/module_update`.


    #. [tkl-odoo12-jcafb-vm] **Executar** a atualização do(s) Módulo(s):

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" - m clv_address_history
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" - m clv_family
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" - m clv_family_history
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" - m clv_person_history

            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo desejado:

            ::

                # ***** tkl-odoo12-jcafb-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Atualizar o *Person History* de todas as Pessoas (a) (2019-08-20)
-----------------------------------------------------------------

    * Referência: :doc:`/user_guide/community/person/person_person_history_updt`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Person History Update` para todas as Pessoas:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Persons*:

            * Menu de acesso:
                * :bi:`Community` » :bi:`Community` » :bi:`Persons`

        #. Selecionar todas as Pessoas (**1375**)

        #. Exercutar a Ação ":bi:`Person History Update`":

            * Parâmetros utilizados:
                * *Sign out date*: **01/07/2019**
                * *Sign in date*: **01/11/2018**

            #. Utilize o botão :bi:`Person History Update` para executar a Ação.

Remover a Fase de todas as Pessoas (2019-08-20)
-----------------------------------------------

    * Referência: :doc:`/user_guide/community/person/person_mass_edit`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Person Mass Edit` para todas as Pessoas:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Persons*:

            * Menu de acesso:
                * :bi:`Community` » :bi:`Community` » :bi:`Persons`

        #. Selecionar todas as Pessoas (**1375**)

        #. Exercutar a Ação ":bi:`Person Mass Edit`":

            * Parâmetros utilizados:
                * *Phase*: :bi:`Remove`

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Atualizar o *Person History* de todas as Pessoas (b) (2019-08-20)
-----------------------------------------------------------------

    * Referência: :doc:`/user_guide/community/person/person_person_history_updt`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Person History Update` para todas as Pessoas:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Persons*:

            * Menu de acesso:
                * :bi:`Community` » :bi:`Community` » :bi:`Persons`

        #. Selecionar todas as Pessoas (**1375**)

        #. Exercutar a Ação ":bi:`Person History Update`":

            * Parâmetros utilizados:
                * *Sign out date*: **01/07/2019**
                * *Sign in date*: **01/11/2018**

            #. Utilize o botão :bi:`Person History Update` para executar a Ação.

Atualizar o *Address History* de todos os Endereços (a) (2019-08-20)
--------------------------------------------------------------------

    * Referência: :doc:`/user_guide/community/address/address_address_history_updt`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Address History Update` para todos os Endereços:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Addresss*:

            * Menu de acesso:
                * :bi:`Community` » :bi:`Community` » :bi:`Addresss`

        #. Selecionar todos os Endereços (**575**)

        #. Exercutar a Ação ":bi:`Address History Update`":

            * Parâmetros utilizados:
                * *Sign out date*: **01/07/2019**
                * *Sign in date*: **01/11/2018**

            #. Utilize o botão :bi:`Address History Update` para executar a Ação.

Remover a Fase de todos os Endereços (2019-08-20)
-------------------------------------------------

    * Referência: :doc:`/user_guide/community/address/address_mass_edit`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Address Mass Edit` para todas as Pessoas:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Addresses*:

            * Menu de acesso:
                * :bi:`Community` » :bi:`Community` » :bi:`Addresses`

        #. Selecionar todas as Pessoas (**575**)

        #. Exercutar a Ação ":bi:`Address Mass Edit`":

            * Parâmetros utilizados:
                * *Phase*: :bi:`Remove`

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Atualizar o *Address History* de todos os Endereços (b) (2019-08-20)
--------------------------------------------------------------------

    * Referência: :doc:`/user_guide/community/address/address_address_history_updt`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Address History Update` para todos os Endereços:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Addresss*:

            * Menu de acesso:
                * :bi:`Community` » :bi:`Community` » :bi:`Addresss`

        #. Selecionar todos os Endereços (**575**)

        #. Exercutar a Ação ":bi:`Address History Update`":

            * Parâmetros utilizados:
                * *Sign out date*: **01/07/2019**
                * *Sign in date*: **01/11/2018**

            #. Utilize o botão :bi:`Address History Update` para executar a Ação.

Atualizar o *Family History* de todas as Famílias (a) (2019-08-20)
------------------------------------------------------------------

    * Referência: :doc:`/user_guide/community/family/family_family_history_updt`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Family History Update` para todas as Famílias:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Families*:

            * Menu de acesso:
                * :bi:`Community` » :bi:`Community` » :bi:`Families`

        #. Selecionar todas as Famílias (**373**)

        #. Exercutar a Ação ":bi:`Family History Update`":

            * Parâmetros utilizados:
                * *Sign out date*: **01/07/2019**
                * *Sign in date*: **01/11/2018**

            #. Utilize o botão :bi:`Family History Update` para executar a Ação.

Remover a Fase de todas as Famílias (2019-08-20)
------------------------------------------------

    * Referência: :doc:`/user_guide/community/family/family_mass_edit`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Family Mass Edit` para todas as Famílias:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Families*:

            * Menu de acesso:
                * :bi:`Community` » :bi:`Community` » :bi:`Families`

        #. Selecionar todas as Famílias (**373**)

        #. Exercutar a Ação ":bi:`Family Mass Edit`":

            * Parâmetros utilizados:
                * *Phase*: :bi:`Remove`

            #. Utilize o botão :bi:`Mass Edit` para executar a Ação.

Atualizar o *Family History* de todas as Famílias (b) (2019-08-20)
------------------------------------------------------------------

    * Referência: :doc:`/user_guide/community/family/family_family_history_updt`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Family History Update` para todas as Famílias:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Families*:

            * Menu de acesso:
                * :bi:`Community` » :bi:`Community` » :bi:`Families`

        #. Selecionar todas as Famílias (**373**)

        #. Exercutar a Ação ":bi:`Family History Update`":

            * Parâmetros utilizados:
                * *Sign out date*: **01/07/2019**
                * *Sign in date*: **01/11/2018**

            #. Utilize o botão :bi:`Family History Update` para executar a Ação.

Criar um backup do *CLVhealth-JCAFB-2020* (2019-08-20a)
-------------------------------------------------------

    * Referência: :doc:`/setup/clvhealth_jcafb_backup`.

    #. [tkl-odoo12-jcafb-vm] Estabelecer uma sessão ssh com o servidor **tkl-odoo12-jcafb-vm** e paralizar o *Odoo*:

        ::

            # ***** tkl-odoo12-jcafb-vm
            #

            ssh tkl-odoo12-jcafb-vm -l root

            /etc/init.d/odoo stop

            su odoo

    #. [tkl-odoo12-jcafb-vm] Executar os comandos de criação dos arquivos de backup:

        ::

            # ***** tkl-odoo12-jcafb-vm
            #
            # data_dir = /var/lib/odoo/.local/share/Odoo
            #

            cd /opt/odoo
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-08-20a.sql

            gzip clvhealth_jcafb_2020_2019-08-20a.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-08-20a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-08-20a.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-08-20a.tar.gz clvhealth_jcafb

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo desejado:

        ::

            # ***** tkl-odoo12-jcafb-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

    Criados os seguintes arquivos:
        * /opt/odoo/clvhealth_jcafb_2020_2019-08-20a.sql
        * /opt/odoo/clvhealth_jcafb_2020_2019-08-20a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2019-08-20a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-08-20a.tar.gz

.. index:: clvhealth_jcafb_2020_2019-08-20a.sql
.. index:: filestore_clvhealth_jcafb_2020_2019-08-20a
.. index:: clvsol_filestore_clvhealth_jcafb_2019-08-20a
