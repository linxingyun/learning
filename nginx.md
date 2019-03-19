

<h3> logrotate configuration </h3>
<ul>
  <li><a href="https://linoxide.com/linux-how-to/install-logrotate-configure-nginx-log-rotation/">How to Install Logrotate and Configure Nginx Log Rotation</a></li>
<li><a href="https://www.keycdn.com/support/nginx-error-log">Configuring the Nginx Error Log and Access Log</a></li>
<li><a href="https://docs.nginx.com/nginx/admin-guide/monitoring/logging/">Configuring Logging</a></li>
<li><a href="https://www.jianshu.com/p/1001b9d75e03">CentOS 7下使用Logrotate管理日志</a></li>
<li><a href="https://www.digitalocean.com/community/tutorials/how-to-configure-logging-and-log-rotation-in-nginx-on-an-ubuntu-vps">How To Configure Logging and Log Rotation in Nginx on an Ubuntu VPS</a> </li>
  <li> <a href="https://linux.cn/article-4126-1.html">Linux日志文件总管——logrotate</a></li>
  
  <li> <a href="https://stackoverflow.com/questions/20162176/centos-linux-setting-logrotate-to-maximum-file-size-for-all-logs">Centos/Linux setting logrotate to maximum file size for all logs</a></li>
  
  <li> <a href="https://serversforhackers.com/c/redirect-http-to-https-nginx"> Redirect HTTP to HTTPS in Nginx </a> </li>
  
  '''
  
     server {
        listen 80 default_server;
        server_name _;
        return 301 https://$host$request_uri;
     }
  
  '''
  
</ul>


'''

    /var/log/celery/*.log {
        weekly
        missingok
        rotate 52
        compress
        delaycompress
        notifempty
        copytruncate
    }
    
    /var/log/cloud/*.log {
        daily
        size 1k
        rotate 10
        copytruncate
        compress
        dateext
        notifempty
        missingok
    }

    
'''

<h3> log analysis </h3>
<ul>
  <li><a href="https://pawelurbanek.com/elk-nginx-logs-setup">Setup ELK for NGINX logs with Elasticsearch, Logstash, and Kibana</a> </li>
</ul>
