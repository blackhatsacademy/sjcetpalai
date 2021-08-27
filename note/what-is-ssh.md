## Secure Shell (SSH)
    SSH, also known as Secure Shell or Secure Socket Shell, is a network protocol that gives users,
    particularly system administrators, a secure way to access a computer over an unsecured network
    
### eg:-
    ssh UserName@SSHserver.example.com
    
   ![](https://www.hostinger.com/tutorials/wp-content/uploads/sites/2/2017/07/symmetric-encryption-ssh-tutorial.jpg)
   
   This command will cause the client to attempt to connect to the server named server.example.com,
   using the user ID UserName. If this is the first time negotiating a connection between the local host
   and the server, the user will be prompted with the remote host's public key fingerprint and prompted to connect,
   despite there having been no prior connection:
```
        The authenticity of host 'sample.ssh.com' cannot be established.
         DSA key fingerprint is 01:23:45:67:89:ab:cd:ef:ff:fe:dc:ba:98:76:54:32:10.
         Are you sure you want to continue connecting (yes/no)?
```
   Answering yes to the prompt will cause the session to continue, and the host key is stored in the local system's
   known_hosts file. This is a hidden file, stored by default in a hidden directory, called /.ssh/known_hosts,
   in the user's home directory. Once the host key has been stored in the known_hosts file, the client system can connect
   directly to that server again without need for any approvals; the host key authenticates the connection.
   

### Secure Shell capabilities
#### Functions that SSH enables include the following:

*    secure remote access to SSH-enabled network systems or devices for users, as well as automated processes;
*    secure and interactive file transfer sessions;
*    automated and secured file transfers;
*    secure issuance of commands on remote devices or systems; and
*    secure management of network infrastructure components.
