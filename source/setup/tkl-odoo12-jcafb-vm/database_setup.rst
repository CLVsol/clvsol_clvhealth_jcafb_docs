.. raw:: html

    <style> .red {color:red} </style>

.. role:: red

.. index:: Preparação do Banco de Dados (tkl-odoo12-jcafb-vm)

==================================================
Preparação do Banco de Dados (tkl-odoo12-jcafb-vm)
==================================================

Glossário
---------
    .. glossary::

       tkl-odoo12-jcafb-vm
          Nome do Servidor Linux em que o *CLVhelth_JCAFB* está sendo executado.

       clvhealth_jcafb
          Nome do Banco de Dados do *CLVhelth_JCAFB*.

Procedimento 1
--------------

O **Procedimento 1** é utilizado por ocasição da criação de uma nova instância (**vazia**) do *CLVhealth-JCAFB*. Nenhum módulo será instalado nesta nova instância do *CLVhealth-JCAFB*

#. [tkl-odoo12-jcafb-vm] Criar, manualmente, o Banco de Dados **clvhealth_jcafb**:

    ::

        # ***** tkl-odoo12-jcafb-vm
        #

        ssh tkl-odoo12-jcafb-vm -l root

        /etc/init.d/odoo stop

        su odoo

        cd /opt/odoo
        /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

    #. Criar o Banco de Dados **clvhealth_jcafb**:

    	* Database Name: **clvhealth_jcafb**
    	* Email: **admin**
    	* Language: **Portuguese (BR)/ Português (BR)**
    	* Country: **Brazil**

    ::

        # ***** tkl-odoo12-jcafb-vm
        #

        ^C

        exit

        /etc/init.d/odoo start

#. [tkl-odoo12-jcafb-vm] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, desabilitando a instalação de todos os módulos do projeto.

#. [tkl-odoo12-jcafb-vm] Executar pela primeira vez o **install.py**:

    ::

        # ***** tkl-odoo12-jcafb-vm (session 1)
        #

        ssh tkl-odoo12-jcafb-vm -l root

        /etc/init.d/odoo stop

        su odoo
        cd /opt/odoo
        /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    ::

        # ***** tkl-odoo12-jcafb-vm (session 2)
        #

        ssh tkl-odoo12-jcafb-vm -l odoo

        cd /opt/odoo/clvsol_clvhealth_jcafb/project
        
        python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb"
        
    ::

        # ***** tkl-odoo12-jcafb-vm (session 1)
        #

        ^C

        exit

        /etc/init.d/odoo start

Procedimento 2
--------------

O **Procedimento 2** é utilizado por ocasição da criação de uma nova instância (**completa**) do *CLVhealth-JCAFB*. Todos os módulos do Projeto serão instalados nesta nova instância do *CLVhealth-JCAFB*

#. [tkl-odoo12-jcafb-vm] Criar, manualmente, o banco de dados **clvhealth_jcafb**:

    ::

        # ***** tkl-odoo12-jcafb-vm
        #

        ssh tkl-odoo12-jcafb-vm -l root

        /etc/init.d/odoo stop

        su odoo

        cd /opt/odoo
        /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

    #. Criar o banco de dados **clvhealth_jcafb**:

        * Database Name: **clvhealth_jcafb**
        * Email: **admin**
        * Language: **Portuguese (BR)/ Português (BR)**
        * Country: **Brazil**

    ::

        # ***** tkl-odoo12-jcafb-vm
        #

        ^C

        exit

        /etc/init.d/odoo start

#. [tkl-odoo12-jcafb-vm] Executar pela primeira vez o **install.py**:

    ::

        # ***** tkl-odoo12-jcafb-vm (session 1)
        #

        ssh tkl-odoo12-jcafb-vm -l root

        /etc/init.d/odoo stop

        su odoo
        cd /opt/odoo
        /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    ::

        # ***** tkl-odoo12-jcafb-vm (session 2)
        #

        ssh tkl-odoo12-jcafb-vm -l odoo

        cd /opt/odoo/clvsol_clvhealth_jcafb/project
        
        python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb"
        
    ::

        # ***** tkl-odoo12-jcafb-vm (session 1)
        #

        ^C

        exit

        /etc/init.d/odoo start

.. toctree::
   :maxdepth: 2
   :caption: Contents:
