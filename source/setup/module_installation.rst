.. raw:: html

    <style> .red {color:red} </style>

.. role:: red

.. index:: Instalação de Modulo(s)

=======================
Instalação de Modulo(s)
=======================

Glossário
---------
    .. glossary::

       odoo12-jcafb-server
          Nome do Servidor Linux em que o *CLVhelth_JCAFB* está sendo executado.

       clvhealth_jcafb_db
          Nome do Banco de Dados do *CLVhelth_JCAFB*.

Procedimento
------------

O **Procedimento** é utilizado por ocasição da instalação de um ou mais Módulos do Odoo em uma instância do *CLVhealth-JCAFB*

#. [odoo12-jcafb-server] Editar o arquivo **/opt/odoo/clvsol_clvhealth_jcafb/project/install.py**, adicionando/habilitando o(s) Módulo(s) a serem instalados.

#. [odoo12-jcafb-server] **Executar** a instalação do(s) Módulo(s) adicionado(s)/habilitado(s):

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
