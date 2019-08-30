.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

=========================================================================================
[2019-08-31] - Preparação do Banco de Dados - JCAFB-2020 - Servidor [tkl-odoo12-jcafb-vm]
=========================================================================================

Restaurar um backup do *CLVhealth-JCAFB-2020* no servidor "tkl-odoo12-jcafb-vm" (2019-08-30b)
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
            # gzip -d clvhealth_jcafb_2020_2019-08-30b.sql.gz

            dropdb -i clvhealth_jcafb_2020

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020
            psql -f clvhealth_jcafb_2020_2019-08-30b.sql -d clvhealth_jcafb_2020 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-08-30b.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-08-30b.tar.gz

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo desejado:

        ::

            # ***** tkl-odoo12-jcafb-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

Atualizar o(s) módulo(s) [clv_survey] (2019-08-31)
--------------------------------------------------

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" - m clv_survey
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo desejado:

            ::

                # ***** tkl-odoo12-jcafb-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Exportar o Questionário "[QSI20]" (2019-08-31)
----------------------------------------------

    * Referência: :doc:`/user_guide/survey/survey_export_xls`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Survey Export XLS` para a Pesquisa "**[QSI20]**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Lab Test Types*:

            * Menu de acesso:
                * **Pesquisas** » **Pesquisas**

        #. Abrir o Formulário da Pesquisa "**[QSI20]**".

        #. Exercutar a Ação ":bi:`Survey Export XLS`":

            * Parâmetros utilizados:
                * *Directory Path*: **/opt/odoo/clvsol_filestore/clvhealth_jcafb/survey_files/templates**
                * *File Name*: **<code>_nnn.nnn-dd.xls**
                * *Password*: *******
                * *File Format*: **Draft**

            #. Utilize o botão :bi:`Export XLS` para executar a Ação.

Exportar o Questionário "[QSC20]" (2019-08-31)
----------------------------------------------

    * Referência: :doc:`/user_guide/survey/survey_export_xls`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Survey Export XLS` para a Pesquisa "**[QSC20]**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Lab Test Types*:

            * Menu de acesso:
                * **Pesquisas** » **Pesquisas**

        #. Abrir o Formulário da Pesquisa "**[QSC20]**".

        #. Exercutar a Ação ":bi:`Survey Export XLS`":

            * Parâmetros utilizados:
                * *Directory Path*: **/opt/odoo/clvsol_filestore/clvhealth_jcafb/survey_files/templates**
                * *File Name*: **<code>_nnn.nnn-dd.xls**
                * *Password*: *******
                * *File Format*: **Draft**

            #. Utilize o botão :bi:`Export XLS` para executar a Ação.

Exportar o Questionário "[QSF20]" (2019-08-31)
----------------------------------------------

    * Referência: :doc:`/user_guide/survey/survey_export_xls`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Survey Export XLS` para a Pesquisa "**[QSF20]**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Lab Test Types*:

            * Menu de acesso:
                * **Pesquisas** » **Pesquisas**

        #. Abrir o Formulário da Pesquisa "**[QSF20]**".

        #. Exercutar a Ação ":bi:`Survey Export XLS`":

            * Parâmetros utilizados:
                * *Directory Path*: **/opt/odoo/clvsol_filestore/clvhealth_jcafb/survey_files/templates**
                * *File Name*: **<code>_nnn.nnn-dd.xls**
                * *Password*: *******
                * *File Format*: **Draft**

            #. Utilize o botão :bi:`Export XLS` para executar a Ação.

Exportar o Questionário "[QMD20]" (2019-08-31)
----------------------------------------------

    * Referência: :doc:`/user_guide/survey/survey_export_xls`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Survey Export XLS` para a Pesquisa "**[QMD20]**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Lab Test Types*:

            * Menu de acesso:
                * **Pesquisas** » **Pesquisas**

        #. Abrir o Formulário da Pesquisa "**[QMD20]**".

        #. Exercutar a Ação ":bi:`Survey Export XLS`":

            * Parâmetros utilizados:
                * *Directory Path*: **/opt/odoo/clvsol_filestore/clvhealth_jcafb/survey_files/templates**
                * *File Name*: **<code>_nnn.nnn-dd.xls**
                * *Password*: *******
                * *File Format*: **Draft**

            #. Utilize o botão :bi:`Export XLS` para executar a Ação.

Exportar o Questionário "[QDH20]" (2019-08-31)
----------------------------------------------

    * Referência: :doc:`/user_guide/survey/survey_export_xls`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Survey Export XLS` para a Pesquisa "**[QDH20]**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Lab Test Types*:

            * Menu de acesso:
                * **Pesquisas** » **Pesquisas**

        #. Abrir o Formulário da Pesquisa "**[QDH20]**".

        #. Exercutar a Ação ":bi:`Survey Export XLS`":

            * Parâmetros utilizados:
                * *Directory Path*: **/opt/odoo/clvsol_filestore/clvhealth_jcafb/survey_files/templates**
                * *File Name*: **<code>_nnn.nnn-dd.xls**
                * *Password*: *******
                * *File Format*: **Draft**

            #. Utilize o botão :bi:`Export XLS` para executar a Ação.

Exportar o Questionário "[QAN20]" (2019-08-31)
----------------------------------------------

    * Referência: :doc:`/user_guide/survey/survey_export_xls`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Survey Export XLS` para a Pesquisa "**[QAN20]**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Lab Test Types*:

            * Menu de acesso:
                * **Pesquisas** » **Pesquisas**

        #. Abrir o Formulário da Pesquisa "**[QAN20]**".

        #. Exercutar a Ação ":bi:`Survey Export XLS`":

            * Parâmetros utilizados:
                * *Directory Path*: **/opt/odoo/clvsol_filestore/clvhealth_jcafb/survey_files/templates**
                * *File Name*: **<code>_nnn.nnn-dd.xls**
                * *Password*: *******
                * *File Format*: **Draft**

            #. Utilize o botão :bi:`Export XLS` para executar a Ação.

.. toctree::
   :maxdepth: 2
