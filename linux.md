

<ul>
<li>what is the CentOS equivalent of /var/log/syslog (on Ubuntu)?</li>
    
    
'''

    Red Hat family distributions (including CentOS and Fedora) use /var/log/messages and 
    /var/log/secure where Debian-family distributions use /var/log/syslog and /var/log/auth.log.

    Note that in newer Fedora (or RHEL/CentOS 7 if someone has gone out of their way to configure it this way), 
    you may have no traditional syslog daemon running. In that case, the same data can be shown with journalctl
    (which defaults to producing text output in the syslog format).


'''

<li>Linux terminal emulator:  terminator</li>
<li>How To Assign Output of a Linux Command to a Variable</li>


'''

     To store the output of a command in a variable, you can use the shell command substitution feature in the forms below:
     variable_name=$(command)
     variable_name=$(command [option ...] arg1 arg2 ...)
     OR
     variable_name='command'
     variable_name='command [option ...] arg1 arg2 ...'
'''

<li> <a href="https://stackoverflow.com/questions/3455625/linux-command-to-print-directory-structure-in-the-form-of-a-tree">Linux command to print directory structure in the form of a tree</a></li>

<li> <a href="https://www.cyberciti.biz/faq/how-do-i-add-jobs-to-cron-under-linux-or-unix-oses/"> Linux Cron job </a> 
    &nbsp; <a href="https://www.cnblogs.com/funnyway/p/9005937.html">利用crontab定时提交svn遇到的几个问题</a>
</li>


'''

     # crontab -e
     
     * * * * * command to be executed
     - - - - -
     | | | | |
     | | | | ----- Day of week (0 - 7) (Sunday=0 or 7)
     | | | ------- Month (1 - 12)
     | | --------- Day of month (1 - 31)
     | ----------- Hour (0 - 23)
     ------------- Minute (0 - 59)
     
     To run /path/to/command five minutes after midnight, every day, enter:
     5 0 * * * /path/to/command
     
'''

<li><a href="https://www.tecmint.com/ssh-passwordless-login-using-ssh-keygen-in-5-easy-steps/"> SSH Passwordless Login Using SSH Keygen in 5 Easy Steps</a></li>

<li><a href="https://www.liberiangeek.net/2014/07/enable-ssh-key-logon-disable-password-password-less-logon-centos/">Enable SSH Key Logon and Disable Password (Password-Less) Logon in CentOS</a></li>
    
<li> Remove the entry from known_hosts when the key gets changed </li>

'''

     Remove the entry from known_hosts using:

     ssh-keygen -R *ip_address_or_hostname*

     This will remove the problematic IP or hostname from known_hosts file and try to connect again

'''

<li> <a href="https://askubuntu.com/questions/218/command-to-list-services-that-start-on-startup">Command to list services that start on startup </a> </li>

'''

     The long answer is: For current versions of Ubuntu, you probably have a mix of Upstart, and SystemV. Newer versions of Ubuntu after 15.04 "Vivid Vervet" (and other Linux distros like RHEL/CentOS 7) are moving to use SystemD.
     
     Upstart:  
          > initctl list
          
     System V:
          > service --status-all

     SystemD:
          > systemctl list-unit-files --type=service
          
'''

<li> <a href="https://serverfault.com/questions/628610/increasing-nproc-for-processes-launched-by-systemd-on-centos-7"> increase process/service max open files </a> </li>

'''
     
     Edit the /etc/systemd/system/xxx.service file by adding 'LimitNOFILE' option.
     [Service]
     Type=notify
     LimitNOFILE=49152

'''

<li> <a href="https://superuser.com/questions/1125250/systemctl-access-denied-when-root">systemctl access denied when root</a> </li>

'''

      #Work-around:
      > getenforce
       Enforcing
      > setenforce 0
      
'''      

<li> <a href="https://ma.ttias.be/logrotate-on-rhelcentos-7-complains-about-insecure-permissions-on-parent-directory-world-writable/" > Logrotate On RHEL/CentOS 7 Complains About Insecure Permissions on Parent Directory, World Writable </a> </li>

</ul>
