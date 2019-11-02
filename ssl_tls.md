


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
  
  <li> <a href="https://gist.github.com/linxingyun/30ee0b6d3a07576a151300e724f7277c"> Mutual SSL in NGINX </a> </li>
  
  
  <li> <a href="https://venilnoronha.io/a-step-by-step-guide-to-mtls-in-go">A step by step guide to mTLS (Mutual SSL) in Go </a> </li>
  
  '''
     // server.go
     package main

      import (
        "crypto/tls"
        "crypto/x509"
        "io"
        "io/ioutil"
        "log"
        "net/http"
      )

      func helloHandler(w http.ResponseWriter, r *http.Request) {
        // Write "Hello, world!" to the response body
        io.WriteString(w, "Hello, world!\n")
      }

      func main() {
        // Set up a /hello resource handler
        http.HandleFunc("/hello", helloHandler)

        // Create a CA certificate pool and add cert.pem to it
        caCert, err := ioutil.ReadFile("cert.pem")
        if err != nil {
          log.Fatal(err)
        }
        caCertPool := x509.NewCertPool()
        caCertPool.AppendCertsFromPEM(caCert)

        // Create the TLS Config with the CA pool and enable Client certificate validation
        tlsConfig := &tls.Config{
          ClientCAs: caCertPool,
          ClientAuth: tls.RequireAndVerifyClientCert,
        }
        tlsConfig.BuildNameToCertificate()

        // Create a Server instance to listen on port 8443 with the TLS config
        server := &http.Server{
          Addr:      ":8443",
          TLSConfig: tlsConfig,
        }

        // Listen to HTTPS connections with the server certificate and wait
        log.Fatal(server.ListenAndServeTLS("cert.pem", "key.pem"))
      }
      
      
      # client.go
      package main

      import (
        "crypto/tls"
        "crypto/x509"
        "fmt"
        "io/ioutil"
        "log"
        "net/http"
      )

      func main() {
        // Read the key pair to create certificate
        cert, err := tls.LoadX509KeyPair("cert.pem", "key.pem")
        if err != nil {
          log.Fatal(err)
        }

        // Create a CA certificate pool and add cert.pem to it
        caCert, err := ioutil.ReadFile("cert.pem")
        if err != nil {
          log.Fatal(err)
        }
        caCertPool := x509.NewCertPool()
        caCertPool.AppendCertsFromPEM(caCert)

        // Create a HTTPS client and supply the created CA pool and certificate
        client := &http.Client{
          Transport: &http.Transport{
            TLSClientConfig: &tls.Config{
              RootCAs: caCertPool,
              Certificates: []tls.Certificate{cert},
            },
          },
        }

        // Request /hello via the created HTTPS client over port 8443 via GET
        r, err := client.Get("https://localhost:8443/hello")
        if err != nil {
          log.Fatal(err)
        }

        // Read the response body
        defer r.Body.Close()
        body, err := ioutil.ReadAll(r.Body)
        if err != nil {
          log.Fatal(err)
        }

        // Print the response body to stdout
        fmt.Printf("%s\n", body)
      }
      
  '''
  
  
</ul>
