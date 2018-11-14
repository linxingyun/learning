
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
    #       > iptables -t nat -A OUTPUT -p udp --dport 53 -j DNAT --to 23.226.230.72:5353
    #       > iptables -t nat -A OUTPUT -p tcp --dport 53 -j DNAT --to 23.226.230.72:5353


'''

<li> <a href="https://askubuntu.com/questions/150135/how-to-block-specific-domains-in-hosts-file/150180#150180"> dnsmasq - how to block specific domains in hosts file? </a> </li>

<li> <a href="https://stackoverflow.com/questions/20446930/how-to-put-wildcard-entry-into-etc-hosts"> How to put wildcard entry into /etc/hosts? </a> </li>
'''

    # /etc/hosts file doesn't support wild card entries (like: *.example.com).
    # You'll have to use other services like dnsmasq. To enable it in dnsmasq, just edit /etc/dnsmasq.conf and add the following line:
    # address=/example.com/127.0.0.1

'''

<ul>
