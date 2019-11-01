


openssl command:

openssl x509 -in portal.crt -text | less

openssl s_client -connect <domain_name>:443 -servername <SNI> -CAfile <ca-file>.pem



<h4> SSL concepts & practice </h4>
<ul>
  <li> <a href="https://www.codeproject.com/Articles/326574/An-Introduction-to-Mutual-SSL-Authentication">An Introduction to Mutual SSL Authentication</a> </li>
  
  <li> <a href="https://medium.com/@Jenananthan/nginx-mutual-ssl-one-way-ssl-with-multiple-clients-ae87b3de0935"> Nginx-Mutual SSL/One way SSL with multiple clients </a> </li>
  
  '''

     # mutual (2 way) ssl config
     server {
        listen 443;
        server_name nginx.mssl.com;
        ssl on;
        ssl_certificate /etc/nginx/ssl/nginx/nginx.crt;
        ssl_certificate_key /etc/nginx/ssl/nginx/nginx.key;
        ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
        #setting for mutual ssl with client
        ssl_client_certificate /etc/nginx/ssl/trust/client.crt;
        ssl_verify_client on;
        location / {
            root /usr/share/nginx/mssl;
            index index.html index.htm;
        }
     }
  
  
     # one way ssl config
     server {
        listen 443;
        server_name nginx.ssl.com;
        ssl on;
        ssl_certificate /etc/nginx/ssl/nginx/nginx.crt;
        ssl_certificate_key /etc/nginx/ssl/nginx/nginx.key;
        ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
        location / {
           root /usr/share/nginx/html;
           index index.html index.htm;
        }
     }
     
  '''
  
  
  
  
</ul>
