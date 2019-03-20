
<ul>
<li> dnsmasq: failed to create listening socket for port 53: Address already in use </li>
'''

    # To tell what is using port 53, here are some general comments on finding what blocks your ports:
    # 1. list the IPv4 ports due to the -i4:
    > lsof -Pn +M -i4
    # 2. list the IPv6 ports:
    > lsof -Pn +M -i6
    # 3. using netstat:
    > netstat -utlnp


    # To change dnsmasq port?
    # 1. Usually every piece of DNS requester software expects to find the DNS service on port 53 of the nameserver. 
    #    If it is not there then DNS will not work.
    #         $ grep '\s53/' /etc/services 
                 domain          53/tcp                          # name-domain server
                 domain          53/udp
    #  
    # 2. If have to change the dnsmasq port, then there is a trick/tips for it:
    #
    #    1) change port in /etc/dnsmasq.conf (port=<other port here>) it's not advised unless you know what you're doing.
    #       dnsmasq is meant to be queried by other clients or the server itself and if it's not running on the common port 53 the DNS requests won't work.
    #
    #    2) In order to have the change port in 1) take effect, use iptables to to redirect port 53 to port 5353 (for instance):
    #       > iptables -t nat -A OUTPUT -p udp --dport 53 -j DNAT --to 127.0.0.1:5353
    #       > iptables -t nat -A OUTPUT -p tcp --dport 53 -j DNAT --to 127.0.0.1:5353


'''

<li> <a href="https://askubuntu.com/questions/150135/how-to-block-specific-domains-in-hosts-file/150180#150180"> dnsmasq - how to block specific domains in hosts file? </a> </li>

<li> <a href="https://stackoverflow.com/questions/20446930/how-to-put-wildcard-entry-into-etc-hosts"> How to put wildcard entry into /etc/hosts? </a> </li>
'''

    # /etc/hosts file doesn't support wild card entries (like: *.example.com).
    # You'll have to use other services like dnsmasq. To enable it in dnsmasq, just edit /etc/dnsmasq.conf and add the following line:
    # address=/example.com/127.0.0.1

'''

<li> dnsmasq: dns record clean/update script </li>

'''

     [dns@testhost ~]$ cat clean 
     #!/bin/sh
     ID=$1

     echo "password" | sudo -S pkill dnsmasq
     mv /home/dns/conf/$ID.conf /home/dns/deleted/
     echo "password" | sudo -S dnsmasq --log-facility=/var/log/dnsmasq/dnsmasq.log --log-queries -u root

'''

<li> Config dnsmasq as service </li>


'''

     #dnsmasq.service
     [Unit]
     Description=dnsmasq - A lightweight DHCP and caching DNS server
     
     [Service]
     Type=forking
     User=root
     Group=root
     ExecStartPre=/usr/sbin/dnsmasq --test
     ExecStart=/usr/sbin/dnsmasq2

     [Install]
     WantedBy=multi-user.target
     
'''

<li> <a href="https://www.linux.com/learn/intro-to-linux/2018/2/advanced-dnsmasq-tips-and-tricks">Advanced Dnsmasq Tips and Tricks</a> </li>

</ul>


<h3> Reference: </h3>
<ul>
    <li> iptable </li>
    <li>
        <ul>
            <li> <a href="https://my.oschina.net/javagg/blog/3239"> 终于搞点iptables端口映射了 </a> </li>
            <li> <a href="https://www.digitalocean.com/community/tutorials/how-to-list-and-delete-iptables-firewall-rules"> How To List and Delete Iptables Firewall Rules</a> </li>            
            <li> <a href="https://unix.stackexchange.com/questions/205867/viewing-all-iptables-rules"> Viewing all iptables rules </a> </li>
            <li> <a href="http://coolnull.com/3322.html"> iptables实现端口映射</a> </li>
        </ul>
    </li>
    
    <li> <a href="https://www.server-world.info/en/note?os=CentOS_7&p=dnsmasq"> Install Dnsmasq in CentOS </a> </li>
</ul>

