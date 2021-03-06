.. raw:: html

    <style> .red {color:red} </style>
    <style> .green {color:green} </style>
    <style> .bi {font-weight: bold; font-style: italic} </style>

.. role:: red
.. role:: green
.. role:: bi

.. index:: Criação de um Servidor de Produção na AWS do CLVhealth-JCAFB (Turnkey Linux AWS)

================================================================================
Criação de um Servidor de Produção na AWS do *CLVhealth-JCAFB* (*Turnkey Linux*)
================================================================================

This project will help you create a server to host the **Odoo 12 (JCAFB)** solution, based on an `Odoo <https://www.odoo.com/>`_  appliance, using the Amazon Web Services (AWS) EC2 infrastructure.

    * Based on `Odoo - From ERP to CRM, eCommerce to CMS <https://www.turnkeylinux.org/odoo>`_ 

Glossary
--------
..
    .. glossary::

       `clvheatlh-jcafb-2020-aws-pro <https://clvheatlh-jcafb-2020-aws-pro>`_
          Name of the Turnkey Linux Server.

       `clvsol_odoo_addons (12.0) <https://github.com/CLVsol/clvsol_odoo_addons/tree/12.0>`_
          CLVsol Odoo Addons.

       `clvsol_odoo_addons_l10n_br (12.0) <https://github.com/CLVsol/clvsol_odoo_addons_l10n_br/tree/12.0>`_
          CLVsol Odoo Addons - Brazilian Localization.

       `clvsol_odoo_addons_jcafb (12.0) <https://github.com/CLVsol/clvsol_odoo_addons_jcafb/tree/12.0>`_
          CLVsol Odoo Addons - JCAFB customizations.

       `clvsol_clvhealth_jcafb (12.0) <https://github.com/CLVsol/clvsol_clvhealth_jcafb/tree/12.0>`_
          Implemantation of CLVhealth-JCAFB, the CLVsol Health Management solution for JCAFB.

       `clvsol_odoo_client <https://github.com/CLVsol/clvsol_odoo_client>`_
          CLVsol Odoo Client.

       `OCA/l10n-brazil (12.0) <https://github.com/OCA/l10n-brazil/tree/12.0>`_
          Este projeto contêm os principais módulos da localização brasileira do Odoo.

       `AWS <https://aws.amazon.com/>`_
          Amazon Web Services

       `TurnKey Hub <https://hub.turnkeylinux.org/>`_
          The Hub powers TurnKey GNU/Linux

Server preparation
------------------

    #. Create, via TrunKey Hub, a new Key Pair:

        * Region: **Sao Paulo (South America)**
        * Key pair name: **clvheatlh-jcafb-2020-aws-pro**
        * Private Key File: **clvheatlh-jcafb-2020-aws-pro.pem**

    #. Create, via TrunKey Hub, a new Elastic IP:

        * Region: **Sao Paulo (South America)**
        * Label: **clvheatlh-jcafb-2020-aws-pro**

    #. Create, via TrunKey Hub, the Amazon EC2 instance tk-postgres-aws:

        * Basics:

            * TurnKey Appliance: **Odoo**
            * Hostname: **clvheatlh-jcafb-2020-aws-pro**

        * Instance:

            * Region: **Sao Paulo (South America)**
            * Size: **T2.Micro ($0.027/hour)**

        * Root account:

            * Root password: "*******"
            * SSH key-pair: **clvheatlh-jcafb-2020-aws-pro**

        * Application settings:

            * PostgreSQL postgres password: "*******"
            * Odoo admin password: "*******"

        * Advanced configuration:

            * Root file system size (GB): **16**
            * Availability Zone: **Automatic**
            * Install Security Updates: **Enabled**
            * Configure Security Alerts: **Enabled**
            * Auto-associate Elastic IP: **Automatic**

    Security Group: **turnkey-odoo-4c23** (Inbound)::

        Port (Service)   Source
        -------------------------------------
        N/A(PING)        0.0.0.0/0
        22(SSH)          0.0.0.0/0
        80(HTTP)         0.0.0.0/0
        443(HTTPS)       0.0.0.0/0
        12320(Web Shell) 0.0.0.0/0  (enabled)
        12321(Webmin)    0.0.0.0/0  (enabled)
        12322(Adminer)   0.0.0.0/0  (enabled)

#. Upgrade the software:

    ::

        ssh clvheatlh-jcafb-2020-aws-pro -l root

    ::

        apt-get update
        apt-get -y upgrade
        apt-get autoremove

#. Update host name, executing the following commands:

    ::

        HOSTNAME=clvheatlh-jcafb-2020-aws-pro
        echo "$HOSTNAME" > /etc/hostname
        sed -i "s|127.0.1.1 \(.*\)|127.0.1.1 $HOSTNAME|" /etc/hosts
        /etc/init.d/hostname.sh start

#. Change the timezone, executing the following command and picking out the time zone from a list:

    ::

        dpkg-reconfigure tzdata

    * Geographic area: **America**
    * Time Zone: **Sao Paulo**

#. Set the time and date manually, executing the following command:

    ::

        date -set="STRING"

    * STRING: **19 JUL 2018 15:06:00**

#. Enable **Connecting through SSH tunnel**:

    * `Solving SSH “channel 3: open failed: administratively prohibited” error when tunnelling <https://blog.mypapit.net/2012/06/solving-ssh-channel-3-open-failed-administratively-prohibited-error-when-tunnelling.html>`_ 
    * `Secure TCP/IP Connections with SSH Tunnels <https://www.postgresql.org/docs/9.1/static/ssh-tunnels.html>`_ 
    * `Using an SSH Tunnel <http://confluence.dbvis.com/display/UG91/Using+an+SSH+Tunnel>`_ 

    #. Edit the file "**/etc/ssh/sshd_config**" (as root):

        ::

            AllowTcpForwarding no

        ::

            AllowTcpForwarding yes

    #. To restart the SSH service, use the following commands (as root):

        ::

            ssh clvheatlh-jcafb-2020-aws-pro -l root

        ::

            service sshd restart

    #. To  establish a secure tunnel from the remote computer, use one the following commands (change the local port (5432) and the remote port (33335) appropriately):

        ::

            ssh -v -L 33335:localhost:5432 root@clvheatlh-jcafb-2020-aws-pro

        ::

            ssh -L 33335:localhost:5432 root@clvheatlh-jcafb-2020-aws-pro

        ::

            ssh -v -L 33335:127.0.0.1:5432 root@clvheatlh-jcafb-2020-aws-pro

        ::

            ssh -L 33335:127.0.0.1:5432 root@clvheatlh-jcafb-2020-aws-pro

Development (1)
---------------

#. Notes on the installation:

    #. Installation: **/usr/lib/python3/dist-packages/odoo**

    #. Configuration File: **/etc/odoo/odoo.conf**

    #. Init file: **/etc/init.d/odoo**

    #. DAEMON: **/usr/bin/odoo**

    #. LOGFILE: **/var/log/odoo/odoo-server.log**

#. To stop and start the Odoo server, use the following commands (as root):

    ::

        ssh clvheatlh-jcafb-2020-aws-pro -l root

    ::

        /etc/init.d/odoo stop

        /etc/init.d/odoo start

#. Delete the 'odoo' database, using the following procedure:

    #. Open a web browser and type in the odoo URL, in my case: http://clvheatlh-jcafb-2020-aws-pro.

    #. Click on 'Manage Databases'.

    #. Clik on 'Delete' (Delete the 'odoo' database).

#. To set **odoo** user password (Linux), use the following commands (as root):

    ::

        passwd odoo


#. Edit the file "**/etc/password**":

    ::

        odoo:x:112:118::/var/lib/odoo:/bin/false

    ::

        odoo:x:112:118::/var/lib/odoo:/bin/bash

#. Copy file "**/etc/odoo/odoo.conf**" into "**/etc/odoo/odoo-man.conf**". Edit the file "**/etc/odoo/odoo-man.conf**":

    ::

            logfile = /var/log/odoo/odoo-server.log

    ::

            # logfile = /var/log/odoo/odoo-server.log
            logfile = False

#. Setup the file "**/etc/odoo/odoo-man.conf**" (Group: odoo[118] Owner: odoo[112]) permissions, using the following commands (as root):

    ::

        ssh clvheatlh-jcafb-2020-aws-pro -l root

    ::

        chown -R odoo:odoo /etc/odoo/odoo-man.conf


#. To stop and start the Odoo server, use the following commands (as root):

    ::

        ssh clvheatlh-jcafb-2020-aws-pro -l root

    ::

        /etc/init.d/odoo stop

        /etc/init.d/odoo start

    ::

        su odoo
        /usr/bin/odoo -c /etc/odoo/odoo-man.conf

#. To create the **/opt/odoo** directory, use the following commands (as root):

    ::

        ssh clvheatlh-jcafb-2020-aws-pro -l root

    ::

        mkdir /opt/odoo

        chown -R odoo:odoo /opt/odoo

#. To configure **Git**, use the following commands (as root):

    ::

        ssh clvheatlh-jcafb-2020-aws-pro -l root

    ::

        cd /opt/odoo
        su odoo

        git config --global user.email "carlos.vercelino@clvsol.com"
        git config --global user.name "Carlos Eduardo Vercelino - CLVsol"

        git config --global alias.lg "log --oneline --all --graph --decorate"

        git config --list

        exit

#. To install erppeek (for python 3.5), use the following commands (as root):

    ::

        pip3 install erppeek

#. To install xlrd 1.0.0, execute the following commands (as root):

    ::

        pip3 install xlrd
        pip3 install xlwt
        pip3 install xlutils

#. :red:`(Não Executado)` To install odoolib (for python 3.5), use the following commands (as root):

    ::

        pip3 install odoo-client-lib

Replace the Odoo installation (Odoo 12.0)
-----------------------------------------

#. To replace the Odoo installation (Odoo 12.0), use the following commands (as root):

    ::

        ssh clvheatlh-jcafb-2020-aws-pro -l root

    ::

        /etc/init.d/odoo stop

    ::

        wget -O - https://nightly.odoo.com/odoo.key | apt-key add -
        echo "deb http://nightly.odoo.com/12.0/nightly/deb/ ./" >> /etc/apt/sources.list.d/odoo.list

        apt-get update

        apt-get install odoo

#. To stop and start the Odoo server, use the following commands (as root):

    ::

        ssh clvheatlh-jcafb-2020-aws-pro -l root

    ::

        /etc/init.d/odoo stop

        /etc/init.d/odoo start

    ::

        su odoo
        /usr/bin/odoo -c /etc/odoo/odoo-man.conf

#. Install **basic dependencies** needed by Odoo, using the following commands (as root):

    * Extracted from LOGFILE: **/var/log/odoo/odoo-server.log**:

        ::

            2019-05-03 13:24:09,170 3050 WARNING ? odoo.addons.base.models.res_currency: The num2words python library is not installed, amount-to-text features won't be fully available. 

    ::

        ssh clvheatlh-jcafb-2020-aws-pro -l root

    ::

        apt-get update
        apt-get -y upgrade
        apt autoremove

    ::

        pip3 install num2words

    ::

        /etc/init.d/odoo stop

        /etc/init.d/odoo start

#. Configure Odoo Server :bi:`timeouts`

    #. Edit the files "**/etc/odoo/odoo.conf**" and "**/etc/odoo/odoo-man.conf**" (as odoo):

        * `Command-line interface: odoo-bin <https://www.odoo.com/documentation/12.0/reference/cmdline.html>`_
        * `Difference between CPU time and wall time <https://service.futurequest.net/index.php?/Knowledgebase/Article/View/407/0/difference-between-cpu-time-and-wall-time>`_

        ::

            limit_time_cpu = 60

            limit_time_real = 120

        ::

            # limit_time_cpu = 60
            limit_time_cpu = 36000
            # limit_time_real = 120
            limit_time_real = 72000

#. Configure Odoo Server :bi:`workers`

    #. Edit the files "**/etc/odoo/odoo.conf**" and "**/etc/odoo/odoo-man.conf**" (as odoo):

        * `Sample odoo.conf file  <https://gist.github.com/Guidoom/d5db0a76ce669b139271a528a8a2a27f>`_
        * `How to Speed up Odoo <https://www.rosehosting.com/blog/how-to-speed-up-odoo/>`_
        * `What is a “worker” in Odoo? <https://stackoverflow.com/questions/35918633/what-is-a-worker-in-odoo>`_

        ::

            workers = 1

        ::

            # workers = 1
            workers = 5

        ::

            workers = 1
            # workers = 5

#. :red:`(Não Executado)` Configure Odoo Server :bi:`data_dir`

    #. Edit the files "**/etc/odoo/odoo.conf**" and "**/etc/odoo/odoo-man.conf**" (as odoo):

        * `Filestore and Session Physical Location – Odoo/OpenERP  <https://www.technaureus.com/filestore-and-session-physical-location/>`_
        * `Odoo 12 Development Cookbook <https://books.google.com.br/books?id=KfeVDwAAQBAJ&pg=PA75&lpg=PA75&dq=odoo+data_dir&source=bl&ots=I1OW2GaxYr&sig=ACfU3U0gBkE_N64J6HcHFP337yJTHA8PYA&hl=pt-BR&sa=X&ved=2ahUKEwi_uv7ihrXjAhV4D7kGHfaIAKMQ6AEwBXoECAgQAQ#v=onepage&q=odoo%20data_dir&f=false>`_

        ::

            data_dir = /var/lib/odoo/.local/share/Odoo

        ::

            # data_dir = /var/lib/odoo/.local/share/Odoo
            data_dir = /var/lib/odoo/.local/share/Odoo

Installation of project modules
-------------------------------

#. `clvsol_odoo_addons (12.0) <https://github.com/CLVsol/clvsol_odoo_addons/tree/12.0>`_

    #. To install "**clvsol_odoo_addons**", use the following commands (as odoo):

        ::

            ssh clvheatlh-jcafb-2020-aws-pro -l odoo

        ::

            cd /opt/odoo
            git clone https://github.com/CLVsol/clvsol_odoo_addons --branch 12.0
            cd /opt/odoo/clvsol_odoo_addons
            git branch -a

    #. Edit the files "**/etc/odoo/odoo.conf**" and "**/etc/odoo/odoo-man.conf**" (as odoo):

        ::

                addons_path = /usr/lib/python3/dist-packages/odoo/addons,...

        ::

                # addons_path = /usr/lib/python3/dist-packages/odoo/addons,...
                addons_path = /usr/lib/python3/dist-packages/odoo/addons,...,/opt/odoo/clvsol_odoo_addons

#. `clvsol_odoo_addons_l10n_br (12.0) <https://github.com/CLVsol/clvsol_odoo_addons_l10n_br/tree/12.0>`_

    #. To install "**clvsol_odoo_addons_l10n_br**", use the following commands (as odoo):

        ::

            ssh clvheatlh-jcafb-2020-aws-pro -l odoo

        ::

            cd /opt/odoo
            git clone https://github.com/CLVsol/clvsol_odoo_addons_l10n_br --branch 12.0
            cd /opt/odoo/clvsol_odoo_addons_l10n_br
            git branch -a

    #. Edit the files "**/etc/odoo/odoo.conf**" and "**/etc/odoo/odoo-man.conf**" (as odoo):

        ::

                addons_path = /usr/lib/python3/dist-packages/odoo/addons,...

        ::

                # addons_path = /usr/lib/python3/dist-packages/odoo/addons,...
                addons_path = /usr/lib/python3/dist-packages/odoo/addons,...,/opt/odoo/clvsol_odoo_addons_l10n_br

#. `clvsol_odoo_addons_jcafb (12.0) <https://github.com/CLVsol/clvsol_odoo_addons_jcafb/tree/12.0>`_

    #. To install "**clvsol_odoo_addons_jcafb**", use the following commands (as odoo):

        ::

            ssh clvheatlh-jcafb-2020-aws-pro -l odoo

        ::

            cd /opt/odoo
            git clone https://github.com/CLVsol/clvsol_odoo_addons_jcafb --branch 12.0
            cd /opt/odoo/clvsol_odoo_addons_jcafb
            git branch -a

    #. Edit the files "**/etc/odoo/odoo.conf**" and "**/etc/odoo/odoo-man.conf**" (as odoo):

        ::

                addons_path = /usr/lib/python3/dist-packages/odoo/addons,...

        ::

                # addons_path = /usr/lib/python3/dist-packages/odoo/addons,...
                addons_path = /usr/lib/python3/dist-packages/odoo/addons,...,/opt/odoo/clvsol_odoo_addons_jcafb

#. `clvsol_clvhealth_jcafb (12.0) <https://github.com/CLVsol/clvsol_clvhealth_jcafb/tree/12.0>`_

    #. To install "**clvsol_clvhealth_jcafb**", use the following commands (as odoo):

        ::

            ssh clvheatlh-jcafb-2020-aws-pro -l odoo

        ::

            cd /opt/odoo
            git clone https://github.com/CLVsol/clvsol_clvhealth_jcafb --branch 12.0
            cd /opt/odoo/clvsol_clvhealth_jcafb
            git branch -a

#. `clvsol_odoo_client <https://github.com/CLVsol/clvsol_odoo_client>`_

    #. To install "**clvsol_odoo_client**", use the following commands (as odoo):

        ::

            ssh clvheatlh-jcafb-2020-aws-pro -l odoo

        ::

            cd /opt/odoo
            git clone https://github.com/CLVsol/clvsol_odoo_client
            cd /opt/odoo/clvsol_odoo_client
            git branch -a


    #. To create a symbolic link "odoo_client", use the following commands (as **root**):

        ::

            ssh clvheatlh-jcafb-2020-aws-pro -l root

        ::

            cd /opt/odoo/clvsol_clvhealth_jcafb/project
            ln -s /opt/odoo/clvsol_odoo_client odoo_client 

        * SymLink <https://wiki.debian.org/SymLink>`_

Installation of external modules
--------------------------------

#. `OCA/l10n-brazil <https://github.com/OCA/l10n-brazil>`_

    #. To install "**OCA/l10n-brazil**", use the following commands (as odoo):

        ::

            ssh clvheatlh-jcafb-2020-aws-pro -l odoo

        ::

            cd /opt/odoo
            git clone https://github.com/OCA/l10n-brazil oca_l10n-brazil --branch 12.0 --depth=1
            cd /opt/odoo/oca_l10n-brazil
            git branch -a

    #. To install "`node-less <https://github.com/odoo/odoo/issues/16463>`_", use the following commands (as root):

        ::

            ssh clvheatlh-jcafb-2020-aws-pro -l root

        ::

            apt-get install node-less

    #. To install "`suds-py3 <https://stackoverflow.com/questions/46043345/how-use-suds-client-library-in-python-3-6-2>`_", use the following commands (as root):

        ::

            ssh clvheatlh-jcafb-2020-aws-pro -l root

        ::

            pip3 install suds-py3

    #. Edit the files "**/etc/odoo/odoo.conf**" and "**/etc/odoo/odoo-man.conf**" (as odoo):

        ::

                addons_path = /usr/lib/python3/dist-packages/odoo/addons,...

        ::

                # addons_path = /usr/lib/python3/dist-packages/odoo/addons,...
                addons_path = /usr/lib/python3/dist-packages/odoo/addons,...,/opt/odoo/oca_l10n-brazil

Remote access to the server
---------------------------

#. To access remotly the server, use the following commands (as **root**):

    ::

        ssh clvheatlh-jcafb-2020-aws-pro -l root

    ::

        /etc/init.d/odoo stop

        /etc/init.d/odoo start

    ::

        su odoo
        /usr/bin/odoo -c /etc/odoo/odoo-man.conf

#. To access remotly the server, use the following commands (as **odoo**) for **JCAFB**:

    ::

        ssh clvheatlh-jcafb-2020-aws-pro -l odoo

    ::

        cd /opt/odoo/clvsol_clvhealth_jcafb/project
        python3 install.py --super_user_pw "***" --admin_user_pw "***" --data_admin_user_pw "***" --db "clvhealth_jcafb"

        dropdb -i clvhealth_jcafb

References
----------

#. Installing Odoo (12)

 * `Odoo Nightly builds <https://nightly.odoo.com/>`_ 
 * `Installing Odoo (12) <https://www.odoo.com/documentation/12.0/setup/install.html>`_ 
 * `How to install Odoo 12 on Debian 9 <https://www.rosehosting.com/blog/how-to-install-odoo-12-on-debian-9/>`_ 
 * `How to deploy Odoo 12 on Ubuntu 18.04 <https://linuxize.com/post/how-to-deploy-odoo-12-on-ubuntu-18-04/>`_ 
