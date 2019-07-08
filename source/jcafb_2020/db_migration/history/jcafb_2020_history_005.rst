.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

===========================================================================================
[2019-07-07 (a)] - Migração do Banco de Dados - JCAFB-2020 - Servidor [tkl-odoo12-jcafb-vm]
===========================================================================================

Restaurar um backup do *CLVhealth-JCAFB-2020* no servidor "tkl-odoo12-jcafb-vm" (2019-07-06c)
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
            # gzip -d clvhealth_jcafb_2020_2019-07-06c.sql.gz

            dropdb -i clvhealth_jcafb_2020

            createdb -O odoo -E UTF8 -T template0 clvhealth_jcafb_2020
            psql -f clvhealth_jcafb_2020_2019-07-06c.sql -d clvhealth_jcafb_2020 -U postgres -h localhost -p 5432 -q

            # mkdir /var/lib/odoo/.local/share/Odoo/filestore
            cd /var/lib/odoo/.local/share/Odoo/filestore
            rm -rf clvhealth_jcafb_2020
            tar -xzvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-07-06c.tar.gz

            # mkdir /opt/odoo/clvsol_filestore
            cd /opt/odoo/clvsol_filestore
            rm -rf clvhealth_jcafb
            tar -xzvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-07-06c.tar.gz

    #. Retornar a execução do *Odoo* do servidor **tkl-odoo12-jcafb-vm** ao modo desejado:

        ::

            # ***** tkl-odoo12-jcafb-vm
            #

            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

            ^C

            exit

            /etc/init.d/odoo start

Atualizar o *Contact Information* de todas as Pessoas
-----------------------------------------------------

    * Referência: :doc:`/user_guide/community/person/person_contact_info_updt`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação *Person Contact Information Update* para todas as Pessoas:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Persons*:

            * Menu de acesso:
                * *Community* > *Community* > *Persons*

        #. Selecionar todas as Pessoas (**1375**)

        #. Exercutar a Ação "**Person Contact Information Update**":

            * Parâmetros utilizados:
                * *Update Phone*: marcado
                * *Update Mobile*: marcado
                * *Update Email*: marcado

            #. Utilize o botão *Contact Information Update* para executar a Ação.

Criar a *Family* para cada Idosos e Criança da JCAFB-2019
---------------------------------------------------------

    * Referência: :doc:`/user_guide/community/person/person_associate_to_family`.

    #. [tkl-odoo12-jcafb-vm] Executar a Ação *Person Associate to Family* para cada Idosos e Criança da JCAFB-2019:

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

        #. Acessar a *View* *Persons*:

            * Menu de acesso:
                * *Community* > *Community* > *Persons*

        #. Selecionar todos os Idosos da JCAFB-2019 (**397**)

        #. Selecionar todas as Crianças da JCAFB-2019 (**195**)

        #. Exercutar a Ação "**Person Associate to Family**":

            * Parâmetros utilizados:
                * *Create new Family*: marcado
                * *Associate all Persons form Reference Address*: marcado

            #. Utilize o botão *Associate to Family* para executar a Ação.

Criar um backup do *CLVhealth-JCAFB-2020* (2019-07-07a)
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
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-07-07a.sql

            gzip clvhealth_jcafb_2020_2019-07-07a.sql
            pg_dump clvhealth_jcafb_2020 -Fp -U postgres -h localhost -p 5432 > clvhealth_jcafb_2020_2019-07-07a.sql

            cd /var/lib/odoo/.local/share/Odoo/filestore
            tar -czvf /opt/odoo/filestore_clvhealth_jcafb_2020_2019-07-07a.tar.gz clvhealth_jcafb_2020

            cd /opt/odoo/clvsol_filestore
            tar -czvf /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-07-07a.tar.gz clvhealth_jcafb

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
        * /opt/odoo/clvhealth_jcafb_2020_2019-07-07a.sql
        * /opt/odoo/clvhealth_jcafb_2020_2019-07-07a.sql.gz
        * /opt/odoo/filestore_clvhealth_jcafb_2020_2019-07-07a.tar.gz
        * /opt/odoo/clvsol_filestore_clvhealth_jcafb_2019-07-07a.tar.gz

.. index:: clvhealth_jcafb_2020_2019-07-07a.sql
.. index:: filestore_clvhealth_jcafb_2020_2019-07-07a
.. index:: clvsol_filestore_clvhealth_jcafb_2019-07-07a

.. toctree::
   :maxdepth: 2
