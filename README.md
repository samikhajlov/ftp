# ftp
creating ftp with SSL

1) <code>/etc/ssh/sshd_config</code> add line <code>AllowGroups root</code> for close ssh for new users. 
2) <code>sudo apt-get install vsftpd</code>
3) replace config vsftpd.conf
4) run <code>sudo adduser ftpuser</code>
6) run <code>sudo chown root:root /home/ftpuser</code>
7) run <code>sudo mkdir /home/ftpuser/files</code>
8) run <code>sudo chown ftpuser:ftpuser /home/ftpuser/files<code>
9) run <code>sudo openssl req -x509 -nodes -days 365 -newkey rsa:1024 -keyout /etc/ssl/private/vsftpd.pem -out /etc/ssl/private/vsftpd.pem<code>
10) run <code>sudo service vsftpd restart</code>
