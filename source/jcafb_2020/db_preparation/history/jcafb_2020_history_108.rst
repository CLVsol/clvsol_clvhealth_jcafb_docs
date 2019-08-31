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

Restaurar um backup do *CLVhealth-JCAFB-2020* no servidor "tkl-odoo12-jcafb-vm" (2019-08-31b)
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
            # gzip -d clvhealth_jcafb_2020_2019-08-31b.sql.gz

            dropdb -i clvhealth_jcafb_2020

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020
            psql -f clvhealth_jcafb_2020_2019-08-31b.sql -d clvhealth_jcafb_2020 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-08-31b.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-08-31b.tar.gz

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo desejado:

        ::

            # ***** tkl-odoo12-jcafb-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

Alterar o Questionário "[QSF20]" (2019-08-31)
---------------------------------------------

    * Referência: :doc:`/user_guide/survey/survey_code_renew`.

    #. [tkl-odoo12-jcafb-vm] Alterar o Questionário "[QSF20]" conforme sugestões da Coordenação da JCAFB-2020:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Lab Test Types*:

            * Menu de acesso:
                * **Pesquisas** » **Pesquisas**

        #. Abrir o Formulário da Pesquisa "**[QSF20]**".

        #. Aplicar as alterações sugeridas pela Coordenação da JCAFB-2020.

        #. Exercutar a Ação ":bi:`Survey Code Renew`":

            #. Utilize o botão :bi:`Code Renew` para executar a Ação.

Alterar o Questionário "[QSI20]" (2019-08-31)
---------------------------------------------

    * Referência: :doc:`/user_guide/survey/survey_code_renew`.

    #. [tkl-odoo12-jcafb-vm] Alterar o Questionário "[QSI20]" conforme sugestões da Coordenação da JCAFB-2020:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Lab Test Types*:

            * Menu de acesso:
                * **Pesquisas** » **Pesquisas**

        #. Abrir o Formulário da Pesquisa "**[QSI20]**".

        #. Aplicar as alterações sugeridas pela Coordenação da JCAFB-2020.

        #. Exercutar a Ação ":bi:`Survey Code Renew`":

            #. Utilize o botão :bi:`Code Renew` para executar a Ação.

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
                * *File Name*: **<code>_nnn.nnn-dd_<file_format>.xls**
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
                * *File Name*: **<code>_nnn.nnn-dd_<file_format>.xls**
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
                * *File Name*: **<code>_nnn.nnn-dd_<file_format>.xls**
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
                * *File Name*: **<code>_nnn.nnn-dd_<file_format>.xls**
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
                * *File Name*: **<code>_nnn.nnn-dd_<file_format>.xls**
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
                * *File Name*: **<code>_nnn.nnn-dd_<file_format>.xls**
                * *Password*: *******
                * *File Format*: **Draft**

            #. Utilize o botão :bi:`Export XLS` para executar a Ação.

Criar um backup do *CLVhealth-JCAFB-2020* (2019-08-31c)
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
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-08-31c.sql

            gzip clvhealth_jcafb_2020_2019-08-31c.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-08-31c.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-08-31c.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-08-31c.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_2019-08-31c.sql
        * /opt/odoo/clvhealth_jcafb_2020_2019-08-31c.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2019-08-31c.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-08-31c.tar.gz

.. index:: clvhealth_jcafb_2020_2019-08-31c.sql
.. index:: filestore_clvhealth_jcafb_2020_2019-08-31c
.. index:: clvsol_filestore_clvhealth_jcafb_2019-08-31c

.. toctree::
   :maxdepth: 2
