

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


</ul>
