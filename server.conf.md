
<h2>Nginx config</h2>
<ul> 
  <li> <a href="http://www.udpwork.com/item/12552.html"> 配置Nginx代理</a> </li>
  <li> <a href="https://regex101.com/"> Regular expression test </a> </li>
  <li> <a href="https://docs.microsoft.com/en-us/dotnet/standard/base-types/regular-expression-language-quick-reference">Regular Expression Language - Quick Reference</a></li>
</ul>


<h2> DNS config </h2>
<ul>
  <li> <a href="https://wiki.debian.org/HowTo/dnsmasq"> How To dnsmasq </a> </li>
</ul>

<h3> DNS redirect, reverse proxy setting </h3>
'''
       
       location ~ ^/instances/(.*)$ {
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
