

<h3>ftp server setup </h3>

<ul>
<li> create ftp user without home dir and no shell access </li>


'''

    useradd -r -s /bin/false img_user
    passwd img_user
    usermod -g ftp img_user
    chmod 750 /home/ftp-dir
    printf "img_user">>/etc/vsftpd.userlist
    systemctl restart vsftpd


'''


<li> vsftpd 530 login incorrect </li>


'''

    potential issue:
    1. password is not correct
    2. check  /etc/vsftpd/vsftpd.conf
       local_enable=YES  
       pam_service_name=vsftpd    
       userlist_enable=YES 
    3. check /etc/pam.d/vsftpd
       #auth    required pam_shells.so

'''

<li> correct vsftpd “500 OOPS: cannot change directory” error? </li>


'''

    chmod 750 -R /home/ftp-dir

'''
</ul>
