***Vprofile Project***

requirements-
    mysql container
            create database accounts;
            grant all privileges on accounts. * To 'admin' @ '%' identified by 'admin123';
            FLUSH privileges;
        # git clone -b local-setup https://github.com/devopshydclub/vprofile-project.git
        # cd vprofile-project
        # mysql -u root -p admin123 accounts < src/main/resources/db_backup.sql
        # confirm data is available using show tables in accounts db

    memcached container

    Rabbitmq container
        # echo "[{rabbit, [{loopback_users, []}]}]." >/etc/rabbitmq/rabbitmq.config
        # rabbitmqctl add_user fox fox123
        # rabbitmqctl set_user_tags fox administrator
    
    tomcat container
        
    nginx container
        # create a loadbalancer
            vim /etc/nginx/sites-available/vprof && /etc/nginx/sites-enabled/vprof
                
                    upstream vprof {
                        server app01:8080;
                        server app02:8080;
                    }
                    server {
                        listen 80;
                    location / {
                        proxy_pass http://vprof;
                    }
                    }



make the properties change based on your infra/configs (src/main/resources/application.properties)

login - admin_vp/admin_vp



netstat -antp  : to see open ports and pid on the machine (be a sudo user)
ps -ef : to see the running processes (can grep using pid with netstat)
ss -tnlp : to see the open ports on the running machine
nmap <host> : to see and scan the open ports, can use to identify firewall related issues
dig <dns name>/ nslookup <dns name> : to see dns resolution from your computer is working fine
route -n : to show the gateways and interface
arp : to view or add the content to kernel's arp table. can identify mac address of ip address/hosts
mtr: similiar as tracert, but live
telnet <ip> <port> : to check connection between networks
