---
sort: 1
---

# USER GUIDES

## REMOTE ACCESS

### Secure VNC access through a SSH tunnel 

VNC connections are, by default, unencrypted. This guide shows how to tunnel VNC traffic through an SSH connection to a local port. For convenience, this guide uses the same local port number as the VNC server eg. `5901` but could be different.

**USING PUTTY IN WINDOWS**
 
- This section assumes a SSH private/public has been created and the public key has been installed in the remote server at `~/.ssh/authorized_keys`

- Copy the private key to a safe location in your local drive to be used in PuTTY.

- **Open PuTTy** and enter the IP address in the **Host Name (or IP address)** field.

- Open the menu `Connections -> SSH -> Auth`, click the **Browse** button in the **Private key file for authentication** field, browse to the location of the private key and enter it.

- Open the menu `Connections -> SSH -> Tunnels` and enter `5901` as the *Source port* and `<IP-Address>:5901` as the *Destination*. Beneath Desination, select `Local` and `Auto`. **NOTE** This example is for the user with VNC server address **:1**. Similarly, for user with VNS server **:2**, it will be *5902* 

- Click `Add` to add the tunnel info. You should see `L5901 IP-Address:5901` in the box under _Forwarded Ports:_.

- Now click `Sessions`, enter a name for the session and click **Save**

- From now on, you can open PuTTy, select the saved session, clicl **Load** and the click **Open** at the bottom.

- It will ask for username, enter your remote server username to login.

- Once the PuTTy connection is made to the remote server, there should be a secure SSH tunnel from the *local port* (eg. `5901`) to the remote server (eg. `IP-ADDR:5901`).
  - In order to check if the port is open, in a Windows command window, type the command `netstat -ano | grep 5901` and you should get an output something like:

```
TCP    127.0.0.1:5901         0.0.0.0:0              LISTENING       7856
TCP    [::1]:5901             [::]:0                 LISTENING       7856 
```

- Open the VNC client (eg. `tightVNC`) and enter `localhost:5901` in the *RemoteHost* field and enter the *VNC password*.  
  
