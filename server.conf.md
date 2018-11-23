
<h2> DNS server (dnsmasq) config </h2>
dnsmasq - A lightweight DHCP and caching DNS server.
<ul>
  <li> <a href="https://wiki.debian.org/HowTo/dnsmasq"> How To dnsmasq </a> </li>
  <li> <a href="https://www.linux.com/learn/intro-to-linux/2018/2/advanced-dnsmasq-tips-and-tricks">Advanced Dnsmasq Tips and Tricks</a> </li>
</ul>

'''

    # Enable dnsmasq automatically adding new DNS record without restart:
    
    # Add following options in dnsmasq config file (etc/dnsmasq.conf):
    # DNSMASQ can discover the dynamically added new DNS record file in the specified directory.
    hostsdir=/home/centos/hostconf
    expand-hosts
    # If startup log inform you there is permmison issue (like below) on the path as specified for hostdir,
    # then you need to startup the dnsmasq with specifying the user. 
      dnsmasq[30622]: bad dynamic directory /home/centos/hostconf/: Permission denied

    # Then, we can create the new DNS record file in the mannually or programmly 
       # file tst1.conf:
       192.168.1.12  tst1.dnsexample.com

    # Command to startup dnsmasq with log information:
    > sudo dnsmasq --log-facility=/var/log/dnsmasq/dnsmasq.log --log-queries -u root


'''



<h2>Nginx config</h2>
<ul> 
  <li> <a href="http://www.udpwork.com/item/12552.html"> 配置Nginx代理</a> </li>
  <li> <a href="https://regex101.com/"> Regular expression test </a> </li>
  <li> <a href="https://docs.microsoft.com/en-us/dotnet/standard/base-types/regular-expression-language-quick-reference">Regular Expression Language - Quick Reference</a></li>
  
  <li> <a href="http://nginx.org/en/docs/http/load_balancing.html">Using nginx as HTTP load balancer</a> </li>
</ul>

<h3> redirect, reverse proxy setting with internal DNS server </h3>
'''
       
       location ~ ^/vms/(.*)$ {
            set $domain_prefix $1;
            return 301 $scheme://$domain_prefix.<host-name>/;
        }
       
       location / {
            resolver 10.102.138.71 ipv6=off;
            proxy_set_header Host $http_host;
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header X-Forwarded-Proto $scheme;
            #proxy_pass http://unix:/home/centos/myprj/myproject.sock;
            proxy_pass https://$host;
        }
        
'''

<h3> <a href="https://serverfault.com/questions/832790/sticky-sessions-with-nginx-proxy">sticky-sessions-with-nginx-proxy </a></h3>
'''

    My server was behind AWS load balancing, so I needed to pass the correct headers to upstream so it would always reflect the client IP. The following configuration fixed my issue (see the commented line):
    
    upstream my_app {
    ip_hash;
    server 111.11.11.11:3001 weight=100 max_fails=5 fail_timeout=300;
    server 222.22.22.22:3002 weight=100 max_fails=5 fail_timeout=300;
    keepalive 8;
    }

    server {
      server_name my-app.com;

      location / {
          proxy_set_header Upgrade $http_upgrade;
          proxy_set_header Connection "upgrade";

          proxy_set_header X-Real_IP $remote_addr;
          proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
          proxy_set_header Host $http_host;
          proxy_set_header X-NginX-Proxy true;

          # This is necessary to pass the correct IP to be hashed
          real_ip_header X-Real-IP;

          proxy_pass http://my_app/;
          proxy_redirect off;
      }
    }

'''


