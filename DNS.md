
<ul>
<li> <a href="https://en.wikipedia.org/wiki/Comparison_of_DNS_server_software">Comparison of DNS server software</a> </li>

<li> <a href="https://doc.powerdns.com/md/httpapi/README/"> PowerDNS REST API</a> </li>
<li> <a href="https://n40lab.wordpress.com/2015/05/16/centos-7-using-the-powerdns-web-api-to-add-and-edit-records/"> CENTOS 7 – USING THE POWERDNS WEB API TO ADD AND EDIT RECORDS </a></li>
<li> <a href="https://pypi.org/project/python-powerdns/"> python-powerdns 0.2.1 </a> </li>
</ul>


<h4> PowerDNS vs Bind9 </h4>
Advantage of PowerDNS:
<ul>
  <li> Zone changes without a reload of the service </li>  
    
''''

    for example stuff like GeoDNS or failover with large set of domains, 
    with few hundred thousand domains you will have to reload BIND few times per second.
   
''''
  
  
  <li> Many backends are supported</li>
  <li> Auth and recursive servers are in different packages</li>
  <li> REST API / Python SDK for DNS record update: "python-powerdns"</li>
  
  
</ul>


