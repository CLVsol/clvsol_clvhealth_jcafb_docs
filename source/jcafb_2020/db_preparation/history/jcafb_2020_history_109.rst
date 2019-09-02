.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

=========================================================================================
[2019-09-01] - Preparação do Banco de Dados - JCAFB-2020 - Servidor [tkl-odoo12-jcafb-vm]
=========================================================================================

Restaurar um backup do *CLVhealth-JCAFB-2020* no servidor "tkl-odoo12-jcafb-vm" (2019-08-31c)
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
            # gzip -d clvhealth_jcafb_2020_2019-08-31c.sql.gz

            dropdb -i clvhealth_jcafb_2020

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020
            psql -f clvhealth_jcafb_2020_2019-08-31c.sql -d clvhealth_jcafb_2020 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-08-31c.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-08-31c.tar.gz

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo desejado:

        ::

            # ***** tkl-odoo12-jcafb-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

Atualizar o(s) módulo(s) [clv_person_jcafb, clv_person_aux_jcafb] (2019-09-01)
------------------------------------------------------------------------------

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" - m clv_person_jcafb
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" - m clv_person_aux_jcafb
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo desejado:

            ::

                # ***** tkl-odoo12-jcafb-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Atualizar o(s) módulo(s) [clv_document, clv_person_jcafb, clv_person_aux_jcafb] (2019-09-01)
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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_2020" - m clv_document
            
        #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo desejado:

            ::

                # ***** tkl-odoo12-jcafb-vm (session 1)
                #

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

                ^C

                exit

                /etc/init.d/odoo start

Criar o *Document Type* "[QAN20]" (2019-09-01)
----------------------------------------------

    * Referência: :doc:`/user_guide/base/document/document_type_duplicate`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Document Type Duplicate` para o *Document Type* "**[TUR19]**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Document Types*:

            * Menu de acesso:
                * **Base** » **Configuration** » **Document** » **Types**

        #. Abrir o Formulário do *Document Type* "**[QAN19]**".

        #. Exercutar a Ação ":bi:`Document Type Duplicate`":

            * Parâmetros utilizados:
                * *New Document Type*: **QAN20**
                * *New Document Type Code*: **QAN20**
                * *New Document Type Description*: **JCAFB 2020 - Questionário para detecção de Anemia**

            #. Utilize o botão :bi:`Duplicate` para executar a Ação.

        #. Abrir o Formulário do Document "**QAN20**".

        #. Atualizar o campo ":bi:`Phase`": **JCAFB-2020**.

Criar o *Document Type* "[QDH20]" (2019-09-01)
----------------------------------------------

    * Referência: :doc:`/user_guide/base/document/document_type_duplicate`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Document Type Duplicate` para o *Document Type* "**[TUR19]**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Document Types*:

            * Menu de acesso:
                * **Base** » **Configuration** » **Document** » **Types**

        #. Abrir o Formulário do *Document Type* "**[QDH19]**".

        #. Exercutar a Ação ":bi:`Document Type Duplicate`":

            * Parâmetros utilizados:
                * *New Document Type*: **QDH20**
                * *New Document Type Code*: **QDH20**
                * *New Document Type Description*: **JCAFB 2020 - Questionário - Diabetes, Hipertensão Arterial e Hipercolesterolemia**

            #. Utilize o botão :bi:`Duplicate` para executar a Ação.

        #. Abrir o Formulário do Document "**QDH20**".

        #. Atualizar o campo ":bi:`Phase`": **JCAFB-2020**.

Criar o *Document Type* "[QMD20]" (2019-09-01)
----------------------------------------------

    * Referência: :doc:`/user_guide/base/document/document_type_duplicate`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Document Type Duplicate` para o *Document Type* "**[TUR19]**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Document Types*:

            * Menu de acesso:
                * **Base** » **Configuration** » **Document** » **Types**

        #. Abrir o Formulário do *Document Type* "**[QMD19]**".

        #. Exercutar a Ação ":bi:`Document Type Duplicate`":

            * Parâmetros utilizados:
                * *New Document Type*: **QMD20**
                * *New Document Type Code*: **QMD20**
                * *New Document Type Description*: **JCAFB 2020 - Questionário - Medicamentos**

            #. Utilize o botão :bi:`Duplicate` para executar a Ação.

        #. Abrir o Formulário do Document "**QMD20**".

        #. Atualizar o campo ":bi:`Phase`": **JCAFB-2020**.

Criar o *Document Type* "[QSC20]" (2019-09-01)
----------------------------------------------

    * Referência: :doc:`/user_guide/base/document/document_type_duplicate`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Document Type Duplicate` para o *Document Type* "**[TUR19]**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Document Types*:

            * Menu de acesso:
                * **Base** » **Configuration** » **Document** » **Types**

        #. Abrir o Formulário do *Document Type* "**[QSC19]**".

        #. Exercutar a Ação ":bi:`Document Type Duplicate`":

            * Parâmetros utilizados:
                * *New Document Type*: **QSC20**
                * *New Document Type Code*: **QSC20**
                * *New Document Type Description*: **JCAFB 2020 - Questionário Socioeconômico Individual (Crianças)**

            #. Utilize o botão :bi:`Duplicate` para executar a Ação.

        #. Abrir o Formulário do Document "**QSC20**".

        #. Atualizar o campo ":bi:`Phase`": **JCAFB-2020**.

Criar o *Document Type* "[QSF20]" (2019-09-01)
----------------------------------------------

    * Referência: :doc:`/user_guide/base/document/document_type_duplicate`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Document Type Duplicate` para o *Document Type* "**[TUR19]**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Document Types*:

            * Menu de acesso:
                * **Base** » **Configuration** » **Document** » **Types**

        #. Abrir o Formulário do *Document Type* "**[QSF19]**".

        #. Exercutar a Ação ":bi:`Document Type Duplicate`":

            * Parâmetros utilizados:
                * *New Document Type*: **QSF20**
                * *New Document Type Code*: **QSF20**
                * *New Document Type Description*: **JCAFB 2020 - Questionário Socioeconômico Familiar (Crianças e Idosos)**

            #. Utilize o botão :bi:`Duplicate` para executar a Ação.

        #. Abrir o Formulário do Document "**QSF20**".

        #. Atualizar o campo ":bi:`Phase`": **JCAFB-2020**.

Criar o *Document Type* "[QSI20]" (2019-09-01)
----------------------------------------------

    * Referência: :doc:`/user_guide/base/document/document_type_duplicate`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Document Type Duplicate` para o *Document Type* "**[TUR19]**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Document Types*:

            * Menu de acesso:
                * **Base** » **Configuration** » **Document** » **Types**

        #. Abrir o Formulário do *Document Type* "**[QSI19]**".

        #. Exercutar a Ação ":bi:`Document Type Duplicate`":

            * Parâmetros utilizados:
                * *New Document Type*: **QSI20**
                * *New Document Type Code*: **QSI20**
                * *New Document Type Description*: **JCAFB 2020 - Questionário Socioeconômico Individual (Idosos)**

            #. Utilize o botão :bi:`Duplicate` para executar a Ação.

        #. Abrir o Formulário do Document "**QSI20**".

        #. Atualizar o campo ":bi:`Phase`": **JCAFB-2020**.

Criar o *Document Type* "[TAN20]" (2019-09-01)
----------------------------------------------

    * Referência: :doc:`/user_guide/base/document/document_type_duplicate`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Document Type Duplicate` para o *Document Type* "**[TUR19]**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Document Types*:

            * Menu de acesso:
                * **Base** » **Configuration** » **Document** » **Types**

        #. Abrir o Formulário do *Document Type* "**[TAN19]**".

        #. Exercutar a Ação ":bi:`Document Type Duplicate`":

            * Parâmetros utilizados:
                * *New Document Type*: **TAN20**
                * *New Document Type Code*: **TAN20**
                * *New Document Type Description*: **JCAFB 2020 - Termo de Consentimento para a Campanha de Detecção de Anemia**

            #. Utilize o botão :bi:`Duplicate` para executar a Ação.

        #. Abrir o Formulário do Document "**TAN20**".

        #. Atualizar o campo ":bi:`Phase`": **JCAFB-2020**.

Criar o *Document Type* "[TCR20]" (2019-09-01)
----------------------------------------------

    * Referência: :doc:`/user_guide/base/document/document_type_duplicate`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Document Type Duplicate` para o *Document Type* "**[TUR19]**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Document Types*:

            * Menu de acesso:
                * **Base** » **Configuration** » **Document** » **Types**

        #. Abrir o Formulário do *Document Type* "**[TCR19]**".

        #. Exercutar a Ação ":bi:`Document Type Duplicate`":

            * Parâmetros utilizados:
                * *New Document Type*: **TCR20**
                * *New Document Type Code*: **TCR20**
                * *New Document Type Description*: **JCAFB 2020 - Termo de Consentimento Livre e Esclarecido para Realização de Questionário Socioeconômico e de Exames Coproparasitológicos**

            #. Utilize o botão :bi:`Duplicate` para executar a Ação.

        #. Abrir o Formulário do Document "**TCR20**".

        #. Atualizar o campo ":bi:`Phase`": **JCAFB-2020**.

Criar o *Document Type* "[TDH20]" (2019-09-01)
----------------------------------------------

    * Referência: :doc:`/user_guide/base/document/document_type_duplicate`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Document Type Duplicate` para o *Document Type* "**[TUR19]**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Document Types*:

            * Menu de acesso:
                * **Base** » **Configuration** » **Document** » **Types**

        #. Abrir o Formulário do *Document Type* "**[TDH19]**".

        #. Exercutar a Ação ":bi:`Document Type Duplicate`":

            * Parâmetros utilizados:
                * *New Document Type*: **TDH20**
                * *New Document Type Code*: **TDH20**
                * *New Document Type Description*: **JCAFB 2020 - JCAFB 2020 - Termo de Consentimento para a Campanha de Detecão de Diabetes, Hipertensão Arterial e Hipercolesterolemia**

            #. Utilize o botão :bi:`Duplicate` para executar a Ação.

        #. Abrir o Formulário do Document "**TDH20**".

        #. Atualizar o campo ":bi:`Phase`": **JCAFB-2020**.

Criar o *Document Type* "[TID20]" (2019-09-01)
----------------------------------------------

    * Referência: :doc:`/user_guide/base/document/document_type_duplicate`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação :bi:`Document Type Duplicate` para o *Document Type* "**[TUR19]**":

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Document Types*:

            * Menu de acesso:
                * **Base** » **Configuration** » **Document** » **Types**

        #. Abrir o Formulário do *Document Type* "**[TID19]**".

        #. Exercutar a Ação ":bi:`Document Type Duplicate`":

            * Parâmetros utilizados:
                * *New Document Type*: **TID20**
                * *New Document Type Code*: **TID20**
                * *New Document Type Description*: **JCAFB 2020 - Termo de Consentimento Livre e Esclarecido para Realização de Questionário Socioeconômico e de Exames de Urina e Coproparasitológico**

            #. Utilize o botão :bi:`Duplicate` para executar a Ação.

        #. Abrir o Formulário do Document "**TID20**".

        #. Atualizar o campo ":bi:`Phase`": **JCAFB-2020**.

.. toctree::
   :maxdepth: 2
