.. raw:: html

    <style> .red {color:red} </style>

.. role:: red

.. index:: Atualização de Modulo(s)

========================
Atualização de Modulo(s)
========================

Glossário
---------
..
    .. glossary::

       odoo12-jcafb-server
          Nome do Servidor Linux em que o *CLVhelth_JCAFB* está sendo executado.

       clvhealth_jcafb_db
          Nome do Banco de Dados do *CLVhelth_JCAFB*.

Procedimento
------------

O **Procedimento** é utilizado por ocasição da atualização de um ou mais Módulos do Odoo em uma instância do *CLVhealth-JCAFB*

    #. [odoo12-jcafb-server] **Executar** a atualização do(s) Módulo(s): **module_1_name**, **module_2_name**

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
                
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_db" -m module_1_name
                python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb_db" -m module_2_name

            
        #. Retornar a execução do *Odoo* do servidor **odoo12-jcafb-server** ao modo padrão:

            ::

                # ***** odoo12-jcafb-server (session 1)
                #

                ^C

                exit

                /etc/init.d/odoo start

.. toctree::
   :maxdepth: 2
   :caption: Contents:
