


openssl command:

openssl x509 -in portal.crt -text | less

openssl s_client -connect <domain_name>:443 -servername <SNI> -CAfile <ca-file>.pem



