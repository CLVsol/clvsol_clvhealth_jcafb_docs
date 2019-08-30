.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

=========================================================================================
[2019-08-30] - Preparação do Banco de Dados - JCAFB-2020 - Servidor [tkl-odoo12-jcafb-vm]
=========================================================================================

Restaurar um backup do *CLVhealth-JCAFB-2020* no servidor "tkl-odoo12-jcafb-vm" (2019-08-30a)
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
            # gzip -d clvhealth_jcafb_2020_2019-08-30a.sql.gz

            dropdb -i clvhealth_jcafb_2020

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020
            psql -f clvhealth_jcafb_2020_2019-08-30a.sql -d clvhealth_jcafb_2020 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-08-30a.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-08-30a.tar.gz

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo desejado:

        ::

            # ***** tkl-odoo12-jcafb-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

Atualizar o(s) módulo(s) [clv_survey] (2019-08-30)
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

Atualizar o(s) módulo(s) [clv_lab_test, clv_person_jcafb, clv_person_aux_jcafb] (2019-08-30)
--------------------------------------------------------------------------------------------

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

Criar a Pesquisa "[TUR20]" (2019-08-30)
---------------------------------------

    * Referência: :doc:`/user_guide/survey/survey_duplicate`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Survey Duplicate` para a Pesquisa "**[TUR19]**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Lab Test Types*:

            * Menu de acesso:
                * **Pesquisas** » **Pesquisas**

        #. Abrir o Formulário da Pesquisa "**[TUR19]**".

        #. Exercutar a Ação ":bi:`Survey Duplicate`":

            * Parâmetros utilizados:
                * *New Survey Title*: **[TUR20]**
                * *New Survey Code*: **TUR20**
                * *New Survey Description*: **<p>JCAFB 2020 - Termo de Consentimento Livre e Esclarecido para Realização de Exame de Urina</p>**

            #. Utilize o botão :bi:`Duplicate` para executar a Ação.

        #. Abrir o Formulário da Pesqauisa "**[TUR20]**".

        #. Atualizar o campo ":bi:`Phase`": **JCAFB-2020**.

Criar a Pesquisa "[TPR20]" (2019-08-30)
---------------------------------------

    * Referência: :doc:`/user_guide/survey/survey_duplicate`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Survey Duplicate` para a Pesquisa "**[TPR19]**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Lab Test Types*:

            * Menu de acesso:
                * **Pesquisas** » **Pesquisas**

        #. Abrir o Formulário da Pesquisa "**[TPR19]**".

        #. Exercutar a Ação ":bi:`Survey Duplicate`":

            * Parâmetros utilizados:
                * *New Survey Title*: **[TPR20]**
                * *New Survey Code*: **TPR20**
                * *New Survey Description*: **<p>JCAFB 2020 - Termo de Consentimento Livre e Esclarecido para Realização de Exames Coproparasitológicos</p>**

            #. Utilize o botão :bi:`Duplicate` para executar a Ação.

        #. Abrir o Formulário da Pesqauisa "**[TPR20]**".

        #. Atualizar o campo ":bi:`Phase`": **JCAFB-2020**.

Criar a Pesquisa "[TID20]" (2019-08-30)
---------------------------------------

    * Referência: :doc:`/user_guide/survey/survey_duplicate`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Survey Duplicate` para a Pesquisa "**[TID19]**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Lab Test Types*:

            * Menu de acesso:
                * **Pesquisas** » **Pesquisas**

        #. Abrir o Formulário da Pesquisa "**[TID19]**".

        #. Exercutar a Ação ":bi:`Survey Duplicate`":

            * Parâmetros utilizados:
                * *New Survey Title*: **[TID20]**
                * *New Survey Code*: **TID20**
                * *New Survey Description*: **<p>JCAFB 2020 - Termo de Consentimento Livre e Esclarecido para Realização de Questionário Socioeconômico e de Exames de Urina e Coproparasitológico</p>**

            #. Utilize o botão :bi:`Duplicate` para executar a Ação.

        #. Abrir o Formulário da Pesqauisa "**[TID20]**".

        #. Atualizar o campo ":bi:`Phase`": **JCAFB-2020**.

Criar a Pesquisa "[TCR20]" (2019-08-30)
---------------------------------------

    * Referência: :doc:`/user_guide/survey/survey_duplicate`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Survey Duplicate` para a Pesquisa "**[TCR19]**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Lab Test Types*:

            * Menu de acesso:
                * **Pesquisas** » **Pesquisas**

        #. Abrir o Formulário da Pesquisa "**[TCR19]**".

        #. Exercutar a Ação ":bi:`Survey Duplicate`":

            * Parâmetros utilizados:
                * *New Survey Title*: **[TCR20]**
                * *New Survey Code*: **TCR20**
                * *New Survey Description*: **<p>JCAFB 2020 - Termo de Consentimento Livre e Esclarecido para Realização de Questionário Socioeconômico e de Exames Coproparasitológicos</p>**

            #. Utilize o botão :bi:`Duplicate` para executar a Ação.

        #. Abrir o Formulário da Pesqauisa "**[TCR20]**".

        #. Atualizar o campo ":bi:`Phase`": **JCAFB-2020**.

Criar a Pesquisa "[TDH20]" (2019-08-30)
---------------------------------------

    * Referência: :doc:`/user_guide/survey/survey_duplicate`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Survey Duplicate` para a Pesquisa "**[TDH19]**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Lab Test Types*:

            * Menu de acesso:
                * **Pesquisas** » **Pesquisas**

        #. Abrir o Formulário da Pesquisa "**[TDH19]**".

        #. Exercutar a Ação ":bi:`Survey Duplicate`":

            * Parâmetros utilizados:
                * *New Survey Title*: **[TDH20]**
                * *New Survey Code*: **TDH20**
                * *New Survey Description*: **<p>JCAFB 2020 - Termo de Consentimento para a Campanha de Detecão de Diabetes, Hipertensão Arterial e Hipercolesterolemia</p>**

            #. Utilize o botão :bi:`Duplicate` para executar a Ação.

        #. Abrir o Formulário da Pesqauisa "**[TDH20]**".

        #. Atualizar o campo ":bi:`Phase`": **JCAFB-2020**.

Criar a Pesquisa "[TAN20]" (2019-08-30)
---------------------------------------

    * Referência: :doc:`/user_guide/survey/survey_duplicate`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Survey Duplicate` para a Pesquisa "**[TAN19]**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Lab Test Types*:

            * Menu de acesso:
                * **Pesquisas** » **Pesquisas**

        #. Abrir o Formulário da Pesquisa "**[TAN19]**".

        #. Exercutar a Ação ":bi:`Survey Duplicate`":

            * Parâmetros utilizados:
                * *New Survey Title*: **[TAN20]**
                * *New Survey Code*: **TAN20**
                * *New Survey Description*: **<p>JCAFB 2020 - Termo de Consentimento para a Campanha de Detecção de Anemia</p>**

            #. Utilize o botão :bi:`Duplicate` para executar a Ação.

        #. Abrir o Formulário da Pesqauisa "**[TAN20]**".

        #. Atualizar o campo ":bi:`Phase`": **JCAFB-2020**.

Criar a Pesquisa "[QSI20]" (2019-08-30)
---------------------------------------

    * Referência: :doc:`/user_guide/survey/survey_duplicate`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Survey Duplicate` para a Pesquisa "**[QSI19]**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Lab Test Types*:

            * Menu de acesso:
                * **Pesquisas** » **Pesquisas**

        #. Abrir o Formulário da Pesquisa "**[QSI19]**".

        #. Exercutar a Ação ":bi:`Survey Duplicate`":

            * Parâmetros utilizados:
                * *New Survey Title*: **[QSI20]**
                * *New Survey Code*: **QSI20**
                * *New Survey Description*: **<p>JCAFB 2020 - Questionário Socioeconômico Individual (Idosos)</p>**

            #. Utilize o botão :bi:`Duplicate` para executar a Ação.

        #. Abrir o Formulário da Pesqauisa "**[QSI20]**".

        #. Atualizar o campo ":bi:`Phase`": **JCAFB-2020**.

Criar a Pesquisa "[QSC20]" (2019-08-30)
---------------------------------------

    * Referência: :doc:`/user_guide/survey/survey_duplicate`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Survey Duplicate` para a Pesquisa "**[QSC19]**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Lab Test Types*:

            * Menu de acesso:
                * **Pesquisas** » **Pesquisas**

        #. Abrir o Formulário da Pesquisa "**[QSC19]**".

        #. Exercutar a Ação ":bi:`Survey Duplicate`":

            * Parâmetros utilizados:
                * *New Survey Title*: **[QSC20]**
                * *New Survey Code*: **QSC20**
                * *New Survey Description*: **<p>JCAFB 2020 - Questionário Socioeconômico Individual (Crianças)</p>**

            #. Utilize o botão :bi:`Duplicate` para executar a Ação.

        #. Abrir o Formulário da Pesqauisa "**[QSC20]**".

        #. Atualizar o campo ":bi:`Phase`": **JCAFB-2020**.

Criar a Pesquisa "[QSF20]" (2019-08-30)
---------------------------------------

    * Referência: :doc:`/user_guide/survey/survey_duplicate`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Survey Duplicate` para a Pesquisa "**[QSF19]**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Lab Test Types*:

            * Menu de acesso:
                * **Pesquisas** » **Pesquisas**

        #. Abrir o Formulário da Pesquisa "**[QSF19]**".

        #. Exercutar a Ação ":bi:`Survey Duplicate`":

            * Parâmetros utilizados:
                * *New Survey Title*: **[QSF20]**
                * *New Survey Code*: **QSF20**
                * *New Survey Description*: **<p>JCAFB 2020 - Questionário Socioeconômico Familiar (Crianças e Idosos)</p>**

            #. Utilize o botão :bi:`Duplicate` para executar a Ação.

        #. Abrir o Formulário da Pesqauisa "**[QSF20]**".

        #. Atualizar o campo ":bi:`Phase`": **JCAFB-2020**.

Criar a Pesquisa "[QMD20]" (2019-08-30)
---------------------------------------

    * Referência: :doc:`/user_guide/survey/survey_duplicate`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Survey Duplicate` para a Pesquisa "**[QMD19]**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Lab Test Types*:

            * Menu de acesso:
                * **Pesquisas** » **Pesquisas**

        #. Abrir o Formulário da Pesquisa "**[QMD19]**".

        #. Exercutar a Ação ":bi:`Survey Duplicate`":

            * Parâmetros utilizados:
                * *New Survey Title*: **[QMD20]**
                * *New Survey Code*: **QMD20**
                * *New Survey Description*: **<p>JCAFB 2020 - Questionário - Medicamentos</p>**

            #. Utilize o botão :bi:`Duplicate` para executar a Ação.

        #. Abrir o Formulário da Pesqauisa "**[QMD20]**".

        #. Atualizar o campo ":bi:`Phase`": **JCAFB-2020**.

Criar a Pesquisa "[QDH20]" (2019-08-30)
---------------------------------------

    * Referência: :doc:`/user_guide/survey/survey_duplicate`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Survey Duplicate` para a Pesquisa "**[QDH19]**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Lab Test Types*:

            * Menu de acesso:
                * **Pesquisas** » **Pesquisas**

        #. Abrir o Formulário da Pesquisa "**[QDH19]**".

        #. Exercutar a Ação ":bi:`Survey Duplicate`":

            * Parâmetros utilizados:
                * *New Survey Title*: **[QDH20]**
                * *New Survey Code*: **QDH20**
                * *New Survey Description*: **<p>JCAFB 2020 - Questionário - Diabetes, Hipertensão Arterial e Hipercolesterolemia</p>**

            #. Utilize o botão :bi:`Duplicate` para executar a Ação.

        #. Abrir o Formulário da Pesqauisa "**[QDH20]**".

        #. Atualizar o campo ":bi:`Phase`": **JCAFB-2020**.

Criar a Pesquisa "[QAN20]" (2019-08-30)
---------------------------------------

    * Referência: :doc:`/user_guide/survey/survey_duplicate`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Survey Duplicate` para a Pesquisa "**[QAN19]**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Lab Test Types*:

            * Menu de acesso:
                * **Pesquisas** » **Pesquisas**

        #. Abrir o Formulário da Pesquisa "**[QAN19]**".

        #. Exercutar a Ação ":bi:`Survey Duplicate`":

            * Parâmetros utilizados:
                * *New Survey Title*: **[QAN20]**
                * *New Survey Code*: **QAN20**
                * *New Survey Description*: **<p>JCAFB 2020 - Questionário para detecção de Anemia</p>**

            #. Utilize o botão :bi:`Duplicate` para executar a Ação.

        #. Abrir o Formulário da Pesqauisa "**[QAN20]**".

        #. Atualizar o campo ":bi:`Phase`": **JCAFB-2020**.

Criar um backup do *CLVhealth-JCAFB-2020* (2019-08-30b)
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
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-08-30b.sql

            gzip clvhealth_jcafb_2020_2019-08-30b.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-08-30b.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-08-30b.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-08-30b.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_2019-08-30b.sql
        * /opt/odoo/clvhealth_jcafb_2020_2019-08-30b.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2019-08-30b.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-08-30b.tar.gz

.. index:: clvhealth_jcafb_2020_2019-08-30b.sql
.. index:: filestore_clvhealth_jcafb_2020_2019-08-30b
.. index:: clvsol_filestore_clvhealth_jcafb_2019-08-30b

.. toctree::
   :maxdepth: 2
