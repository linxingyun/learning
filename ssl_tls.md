


openssl command:

openssl x509 -in portal.crt -text | less

openssl s_client -connect <domain_name>:443 -servername <SNI> -CAfile <ca-file>.pem



<h4> SSL concepts </h4>
<ul>
  <li> <a href="https://www.codeproject.com/Articles/326574/An-Introduction-to-Mutual-SSL-Authentication">An Introduction to Mutual SSL Authentication</a> </li>
</ul>
