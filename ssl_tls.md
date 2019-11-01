


openssl command:

openssl x509 -in portal.crt -text | less

openssl s_client -connect <domain_name>:443 -servername <SNI> -CAfile <ca-file>.pem



<h4> SSL concepts & practice </h4>
<ul>
  <li> <a href="https://www.codeproject.com/Articles/326574/An-Introduction-to-Mutual-SSL-Authentication">An Introduction to Mutual SSL Authentication</a> </li>
  
  <li> <a href="https://medium.com/@Jenananthan/nginx-mutual-ssl-one-way-ssl-with-multiple-clients-ae87b3de0935"> Nginx-Mutual SSL/One way SSL with multiple clients </a> </li>
</ul>
