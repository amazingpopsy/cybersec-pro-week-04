# Network Scan Report
    
  ## Target
  - IP Address: 192.168.230.131
     - Date: 21-09-2026
     - Scanned by: Ayomipo Adeleke
    
     ## Executive Summary
    The Nmap scan found that the host **192.168.230.131 (Metasploitable2)** is running Linux with many exposed services, including FTP, SSH, Telnet, HTTP, SMB, MySQL, PostgreSQL, VNC, and NFS. Several services appear insecure or outdated, such as **anonymous FTP access, disabled SMB signing, SSLv2 support, and an exposed root shell on port 1524**, indicating multiple potential security weaknesses.
    
     ## Findings
     ### Open Ports
     | Port | Service | Version | Risk |
     |------|---------|---------|------|
    | 21 | FTP | vsftpd 2.3.4 | High |
     | 22 | SSH | OpenSSH 4.7p1 Debian 8ubuntu1 (protocol 2.0) | High |
     | 23 | Telnet | Linux Telnetd | High |
     | 25 | SMTP |  Postfix smtpd | High |
     | 53 | DOMAIN | ISC BIND 9.4.2 | High |
    | 80 | HTTP | Apache httpd 2.2.8 ((Ubuntu) DAV/2) | High |
     | 111 | RPCBIND |  2 (RPC #100000) | High |
      | 5900 | vnc | VNC (protocol 3.3) | High |
    | 8009 | AJP13 | Apache Jserv (Protocol v1.3) | High |

     ## Recommendations
  - FTP (21/2121): Disable anonymous FTP access and replace outdated FTP services with secure alternatives such as SFTP. Upgrade or remove the outdated FTP software.
- Telnet/RSH/Rlogin (23, 512–514): Disable these insecure remote-access services and use SSH instead, preferably with strong authentication.
- SSLv2 on SMTP: Disable SSLv2 and other obsolete protocols and configure the mail server to use modern TLS versions.
- Outdated web servers (80/8180): Upgrade Apache and Tomcat to supported versions and regularly apply security patches. Remove unnecessary web applications and restrict administrative interfaces.
- SMB (139/445): Upgrade Samba and enable SMB signing. Disable SMBv1 where possible and restrict SMB access to trusted hosts.
- NFS/RPC (111/2049): Restrict NFS exports to authorized systems, use appropriate access controls, and disable NFS/RPC services if they are not required.
- Databases (3306/5432): Upgrade MySQL and PostgreSQL and restrict database access to trusted hosts instead of exposing them to the entire network.
- VNC/X11 (5900/6000): Disable these services when unnecessary or restrict them through a firewall/VPN and use strong authentication.
- Port 1524 root shell: Immediately disable and remove the exposed root shell because it provides unauthenticated privileged access.
- General: Remove unnecessary services, implement host-based firewall rules, regularly patch the operating system and applications, and monitor exposed ports for unexpected changes.
    
     ## Appendix: Raw Scan Output
     [Link to your .nmap output file]
