# ftp
creating ftp with SSL

1) <code>/etc/ssh/sshd_config</code> add line <code>AllowGroups root</code> for close ssh for new users and run <code>service ssh restart
</code>. 
2) <code>sudo apt-get install vsftpd</code>
3) replace config vsftpd.conf
4) run <code>sudo adduser ftpuser</code>
5) run <code>sudo chown root:root /home/ftpuser</code>
6) run <code>sudo mkdir /home/ftpuser/files</code>
7) run <code>sudo chown ftpuser:ftpuser /home/ftpuser/files</code>
8) run <code>sudo openssl req -x509 -nodes -days 365 -newkey rsa:1024 -keyout /etc/ssl/private/vsftpd.pem -out /etc/ssl/private/vsftpd.pem</code>
9) run <code>sudo service vsftpd restart</code>

open ports for ftp:
<ul>
  <li>iptables -A OUTPUT -p tcp --sport 21 -m state --state ESTABLISHED -j ACCEPT</li>
  <li>iptables -A OUTPUT -p tcp --sport 20 -m state --state ESTABLISHED,RELATED -j ACCEPT</li>
  <li>iptables -A OUTPUT -p tcp --sport 1024: --dport 1024: -m state --state ESTABLISHED -j ACCEPT</li>
  <li>iptables -A INPUT -p tcp --dport 21 -m state --state NEW,ESTABLISHED -j ACCEPT</li></li>
  <li>iptables -A INPUT -p tcp --dport 20 -m state --state ESTABLISHED -j ACCEPT</li>
  <li>iptables -A INPUT -p tcp --sport 1024: --dport 1024: -m state --state ESTABLISHED,RELATED,NEW -j ACCEPT</li>
</ul>
<br>
<p><b>After that use FTP port 21 and SSL/TLS for connection</b></p>
