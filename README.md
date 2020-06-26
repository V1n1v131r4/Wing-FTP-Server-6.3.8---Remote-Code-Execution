# Wing FTP Server 6.3.8 - Remote Code Execution

This PoC explain how to exploit Wing FTP Server 6.3.8 to get Remote Code Execution

_______________________________________

Multiple vulnerability was founded on Wing FTP Server 6.3.8:

- [Admin Credentials on HTTP Request](https://github.com/V1n1v131r4/Wing-FTP-Server-6.3.8---Remote-Code-Execution/blob/master/README.md#admin-credentials-on-http-request)
- [Unprotected Store Credentials](https://github.com/V1n1v131r4/Wing-FTP-Server-6.3.8---Remote-Code-Execution/blob/master/README.md#unprotected-store-credentials)
- [Remote Code Execution (authenticated)](https://github.com/V1n1v131r4/Wing-FTP-Server-6.3.8---Remote-Code-Execution/blob/master/README.md#remote-code-execution-authenticated)

_______________________________________
### About Wing FTP Server

Wing FTP Server is an easy-to-use, powerful, and free FTP server software for Windows, Linux, Mac OS, and Solaris. It supports multiple file transfer protocols, including FTP, FTPS, HTTP, HTTPS, and SFTP, giving your clients flexibility in how they connect to the server. And it provides admins with a web-based interface to administrate the server from anywhere. You can also monitor server performance and online sessions and even receive email notifications about various events taking place on the server. 

You can download Wing FTP Server here: https://www.wftpserver.com/download.htm

![p0](http://sejalivre.org/poc3/0.png)


_______________________________________
### Admin Credentials on HTTP Request

When accessing the Wing FTP Server remote management panel, the credentials are transmitted in clear, as shown in the image below:


![p1](http://sejalivre.org/poc3/1.png)

![p2](http://sejalivre.org/poc3/2.png)


_______________________________________
### Unprotected Store Credentials

Another vulnerability found is the unprotected storage of the application's admin credentials.

The **C:\Program Files (x86)Wing FTP Server\_ADMINISTRATOR\admins.xml** file stores the admin credentials by saving the password in an md5 hash, which can be easily deciphered, as shown in the image below:


![p3](http://sejalivre.org/poc3/3.png)


_______________________________________
### Remote Code Execution (authenticated)

In the remote management panel there is a console written in the LUA language, which can be exploited to execute commands in the Operating System through the **os.execute()** function native to lua.

Below is a remote command execution PoC through the lua console to obtain a reverse shell on the target machine.

![p6](http://sejalivre.org/poc3/6.png)


![p4](http://sejalivre.org/poc3/4.png)


![p5](http://sejalivre.org/poc3/5.png)


![p7](http://sejalivre.org/poc3/7.png)
