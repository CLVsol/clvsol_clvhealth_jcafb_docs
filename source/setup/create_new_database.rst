.. raw:: html

    <style> .red {color:red} </style>

.. role:: red

===================
Create new database
===================

#. [tkl-odoo12-jcafb-vm] Criar, manualmente, o banco de dados "**clvhealth_jcafb**":

    ::

        # ***** tkl-odoo12-jcafb-vm
        #

        ssh tkl-odoo12-jcafb-vm -l root

        /etc/init.d/odoo stop

        su odoo

        cd /opt/odoo
        /usr/bin/odoo -c /etc/odoo/odoo-man.conf

    #. Conectar-se, via *browser*, ao *Odoo* do servidor `tkl-odoo12-jcafb-vm <https://tkl-odoo12-jcafb-vm>`_

    #. Criar o banco de dados "**clvhealth_jcafb**":

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

.. toctree::
   :maxdepth: 2
   :caption: Contents:
