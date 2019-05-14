.. raw:: html

    <style> .red {color:red} </style>

.. role:: red

.. index:: Banco de Dados (Preparação)
.. index:: Preparação do Banco de Dados

============================
Preparação do Banco de Dados
============================

Glossário
---------
    .. glossary::

       odoo12-jcafb-server
          Nome do Servidor Linux em que o *CLVhelth_JCAFB* está sendo executado.

       clvhealth_jcafb_db
          Nome do Banco de Dados do *CLVhelth_JCAFB*.

.. _Preparação do Banco de Dados (Procedimento 1):

Procedimento 1
--------------

O **Procedimento 1** é utilizado por ocasição da criação de uma nova instância (**vazia**) do *CLVhealth-JCAFB*. Nenhum módulo será instalado nesta nova instância do *CLVhealth-JCAFB*

    #. [odoo12-jcafb-server] Criar, manualmente, o Banco de Dados **clvhealth_jcafb_db**:

        #. Estabelecer uma sessão ssh com o servidor **odoo12-jcafb-server** e executar o *Odoo* no modo manual:

            ::

                # ***** odoo12-jcafb-server
                #

                ssh odoo12-jcafb-server -l root

                /etc/init.d/odoo stop

                su odoo

                cd /opt/odoo
                /usr/bin/odoo -c /etc/odoo/odoo-man.conf

        #. Conectar-se, via *browser*, ao *Odoo* do servidor `odoo12-jcafb-server <https://odoo12-jcafb-server>`_

        #. Criar o Banco de Dados **clvhealth_jcafb_db**:

        	* Database Name: **clvhealth_jcafb_db**
        	* Email: **admin**
        	* Language: **Portuguese (BR)/ Português (BR)**
        	* Country: **Brazil**

        #. Retornar a execução do *Odoo* do servidor **odoo12-jcafb-server** ao modo padrão:

            ::

                # ***** odoo12-jcafb-server
                #

                ^C

                exit

                /etc/init.d/odoo start

    #. [odoo12-jcafb-server] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, desabilitando a instalação de todos os módulos do projeto.

    #. [odoo12-jcafb-server] Executar pela primeira vez o **install.py**:

        #. Estabelecer uma sessão ssh (session 1) com o servidor **odoo12-jcafb-server** e executar o *Odoo* no modo manual:

        ::

            # ***** odoo12-jcafb-server (session 1)
            #

            ssh odoo12-jcafb-server -l root

            /etc/init.d/odoo stop

            su odoo
            cd /opt/odoo
            /usr/bin/odoo -c /etc/odoo/odoo-man.conf

        #. Estabelecer uma sessão ssh (session 2) com o servidor **odoo12-jcafb-server** e executar o **install.py**:

            ::

                # ***** odoo12-jcafb-server (session 2)
                #

                ssh odoo12-jcafb-server -l odoo

                cd /opt/odoo/clvsol_clvhealth_jcafb/project
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_db"
            
        #. Retornar a execução do *Odoo* do servidor **odoo12-jcafb-server** ao modo padrão:

            ::

                # ***** odoo12-jcafb-server (session 1)
                #

                ^C

                exit

                /etc/init.d/odoo start

Procedimento 2
--------------

O **Procedimento 2** é utilizado por ocasição da criação de uma nova instância (**completa**) do *CLVhealth-JCAFB*. Todos os módulos do Projeto serão instalados nesta nova instância do *CLVhealth-JCAFB*

#. [odoo12-jcafb-server] Criar, manualmente, o banco de dados **clvhealth_jcafb_db**:

    ::

        # ***** odoo12-jcafb-server
        #

        ssh odoo12-jcafb-server -l root

        /etc/init.d/odoo stop

        su odoo

        cd /opt/odoo
        /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    #. Conectar-se, via *browser*, ao *Odoo* do servidor `odoo12-jcafb-server <https://odoo12-jcafb-server>`_

    #. Criar o banco de dados **clvhealth_jcafb_db**:

        * Database Name: **clvhealth_jcafb_db**
        * Email: **admin**
        * Language: **Portuguese (BR)/ Português (BR)**
        * Country: **Brazil**

    ::

        # ***** odoo12-jcafb-server
        #

        ^C

        exit

        /etc/init.d/odoo start

#. [odoo12-jcafb-server] Executar pela primeira vez o **install.py**:

    ::

        # ***** odoo12-jcafb-server (session 1)
        #

        ssh odoo12-jcafb-server -l root

        /etc/init.d/odoo stop

        su odoo
        cd /opt/odoo
        /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    ::

        # ***** odoo12-jcafb-server (session 2)
        #

        ssh odoo12-jcafb-server -l odoo

        cd /opt/odoo/clvsol_clvhealth_jcafb/project
        
        python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_db"
        
    ::

        # ***** odoo12-jcafb-server (session 1)
        #

        ^C

        exit

        /etc/init.d/odoo start

.. toctree::
   :maxdepth: 2
   :caption: Contents:
