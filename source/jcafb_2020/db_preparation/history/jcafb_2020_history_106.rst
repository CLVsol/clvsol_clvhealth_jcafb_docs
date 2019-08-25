.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

=========================================================================================
[2019-08-24] - Preparação do Banco de Dados - JCAFB-2020 - Servidor [tkl-odoo12-jcafb-vm]
=========================================================================================

Restaurar um backup do *CLVhealth-JCAFB-2020* no servidor "tkl-odoo12-jcafb-vm" (2019-08-20a)
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
            # gzip -d clvhealth_jcafb_2020_2019-08-20a.sql.gz

            dropdb -i clvhealth_jcafb_2020

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020
            psql -f clvhealth_jcafb_2020_2019-08-20a.sql -d clvhealth_jcafb_2020 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-08-20a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-08-20a.tar.gz

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo desejado:

        ::

            # ***** tkl-odoo12-jcafb-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

Atualizar o(s) módulo(s) [clv_lab_test, clv_lab_test_jcafb] (2019-08-24)
------------------------------------------------------------------------

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" - m clv_lab_test
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo desejado:

            ::

                # ***** tkl-odoo12-jcafb-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Criar o *Lab Test Type* "JCAFB 2020 - Exames - Detecção de Anemia" (2019-08-20)
-------------------------------------------------------------------------------

    * Referência: :doc:`/user_guide/health/lab_test_type_duplicate`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Lab Test Type Duplicate` para o :bi:`Lab Test Type` "**JCAFB 2019 - Exames - Detecção de Anemia**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Lab Test Types*:

            * Menu de acesso:
                * :bi:`Health` » :bi:`Configuration` » :bi:`Lab Test Types`

        #. Abrir o Formulário do *Lab Test Type* "JCAFB 2019 - Exames - Detecção de Anemia".

        #. Exercutar a Ação ":bi:`Lab Test Type Duplicate`":

            * Parâmetros utilizados:
                * *New Lab Test Type*: **JCAFB 2020 - Exames - Detecção de Anemia**
                * *New Lab Test Type Code*: **EAN20**

            #. Utilize o botão :bi:`Duplicate` para executar a Ação.

        #. Abrir o Formulário do *Lab Test Type* "JCAFB 2020 - Exames - Detecção de Anemia".

        #. Atualizar o campo ":bi:`Pahse`": **JCAFB-2020**.

Criar o *Lab Test Type* "JCAFB 2020 - Exames - Diabetes, Hipertensão Arterial e Hipercolesterolemia" (2019-08-20)
-----------------------------------------------------------------------------------------------------------------

    * Referência: :doc:`/user_guide/health/lab_test_type_duplicate`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Lab Test Type Duplicate` para o :bi:`Lab Test Type` "**JCAFB 2019 - Exames - Diabetes, Hipertensão Arterial e Hipercolesterolemia**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Lab Test Types*:

            * Menu de acesso:
                * :bi:`Health` » :bi:`Configuration` » :bi:`Lab Test Types`

        #. Abrir o Formulário do *Lab Test Type* "JCAFB 2019 - Exames - Diabetes, Hipertensão Arterial e Hipercolesterolemia".

        #. Exercutar a Ação ":bi:`Lab Test Type Duplicate`":

            * Parâmetros utilizados:
                * *New Lab Test Type*: **JCAFB 2020 - Exames - Diabetes, Hipertensão Arterial e Hipercolesterolemia**
                * *New Lab Test Type Code*: **EDH20**

            #. Utilize o botão :bi:`Duplicate` para executar a Ação.

        #. Abrir o Formulário do *Lab Test Type* "JCAFB 2020 - Exames - Diabetes, Hipertensão Arterial e Hipercolesterolemia".

        #. Atualizar o campo ":bi:`Pahse`": **JCAFB-2020**.

Criar o *Lab Test Type* "JCAFB 2020 - Laboratório - Parasitologia" (2019-08-20)
-------------------------------------------------------------------------------

    * Referência: :doc:`/user_guide/health/lab_test_type_duplicate`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Lab Test Type Duplicate` para o :bi:`Lab Test Type` "**JCAFB 2019 - Laboratório - Parasitologia**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Lab Test Types*:

            * Menu de acesso:
                * :bi:`Health` » :bi:`Configuration` » :bi:`Lab Test Types`

        #. Abrir o Formulário do *Lab Test Type* "JCAFB 2019 - Laboratório - Parasitologia".

        #. Exercutar a Ação ":bi:`Lab Test Type Duplicate`":

            * Parâmetros utilizados:
                * *New Lab Test Type*: **JCAFB 2020 - Laboratório - Parasitologia**
                * *New Lab Test Type Code*: **ECP20**

            #. Utilize o botão :bi:`Duplicate` para executar a Ação.

        #. Abrir o Formulário do *Lab Test Type* "JCAFB 2020 - Laboratório - Parasitologia".

        #. Atualizar o campo ":bi:`Pahse`": **JCAFB-2020**.

Criar o *Lab Test Type* "JCAFB 2020 - Laboratório - Pesquisa de Enterobius vermicularis" (2019-08-20)
-----------------------------------------------------------------------------------------------------

    * Referência: :doc:`/user_guide/health/lab_test_type_duplicate`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Lab Test Type Duplicate` para o :bi:`Lab Test Type` "**JCAFB 2019 - Laboratório - Pesquisa de Enterobius vermicularis**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Lab Test Types*:

            * Menu de acesso:
                * :bi:`Health` » :bi:`Configuration` » :bi:`Lab Test Types`

        #. Abrir o Formulário do *Lab Test Type* "JCAFB 2019 - Laboratório - Pesquisa de Enterobius vermicularis".

        #. Exercutar a Ação ":bi:`Lab Test Type Duplicate`":

            * Parâmetros utilizados:
                * *New Lab Test Type*: **JCAFB 2020 - Laboratório - Pesquisa de Enterobius vermicularis**
                * *New Lab Test Type Code*: **EEV20**

            #. Utilize o botão :bi:`Duplicate` para executar a Ação.

        #. Abrir o Formulário do *Lab Test Type* "JCAFB 2020 - Laboratório - Pesquisa de Enterobius vermicularis".

        #. Atualizar o campo ":bi:`Pahse`": **JCAFB-2020**.

Criar o *Lab Test Type* "JCAFB 2020 - Laboratório - Urinálise" (2019-08-20)
---------------------------------------------------------------------------

    * Referência: :doc:`/user_guide/health/lab_test_type_duplicate`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Lab Test Type Duplicate` para o :bi:`Lab Test Type` "**JCAFB 2019 - Laboratório - Urinálise**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Lab Test Types*:

            * Menu de acesso:
                * :bi:`Health` » :bi:`Configuration` » :bi:`Lab Test Types`

        #. Abrir o Formulário do *Lab Test Type* "JCAFB 2019 - Laboratório - Urinálise".

        #. Exercutar a Ação ":bi:`Lab Test Type Duplicate`":

            * Parâmetros utilizados:
                * *New Lab Test Type*: **JCAFB 2020 - Laboratório - Urinálise**
                * *New Lab Test Type Code*: **EUR20**

            #. Utilize o botão :bi:`Duplicate` para executar a Ação.

        #. Abrir o Formulário do *Lab Test Type* "JCAFB 2020 - Laboratório - Urinálise".

        #. Atualizar o campo ":bi:`Pahse`": **JCAFB-2020**.

.. toctree::
   :maxdepth: 2
