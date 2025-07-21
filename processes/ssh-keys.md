# SSH Keys

## Requirements

[#how-to-ssh-into-a-server](../welcome/quick-start.md#how-to-ssh-into-a-server "mention")

[#basic-terminal-commands](../welcome/quick-start.md#basic-terminal-commands "mention")

[bitwarden.md](../service-overviews/security/bitwarden.md "mention")

## SSH keys explained

SSH keys contain 2 pieces, a public key and a private key.

The public key is installed on whatever hardware you wish to SSH into. The private key is installed on the machine you will SSH from.

<img src="../.gitbook/assets/file.excalidraw (2).svg" alt="" class="gitbook-drawing">

## How to install the Public Key

Public Keys allow the user with the private key to SSH into the machine

### Ubuntu

1.  SSH into the server and run the below command to elevate to Root user, input the password you used to log in

    ```bash
    sudo -i
    ```
2.  &#x20;Run the below commands\


    ```bash
    mkdir -p ~/.ssh
    echo ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIDhKliloNg32f9J8xtnLi0wal4FVnTYkNNQRhqTdPNcT trentnbauer@gmail.com >> ~/.ssh/authorized_keys
    chmod -R go= ~/.ssh
    ```

### Windows

1. Log into the server as an administrator
2.  Open Powershell as administrator and run the below command\


    ```powershell
    echo "ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIDhKliloNg32f9J8xtnLi0wal4FVnTYkNNQRhqTdPNcT trentnbauer@gmail.com" | Out-File -filepath $ENV:userprofile\.ssh\id_rsa.pub -Force -verbose
    ```

## How to install the Private Key

The private key is used to SSH into servers configured with the public key

### Ubuntu

1. SSH into the server and SU into the Root account
2.  Run the below commands

    ```bash
    mkdir -p ~/.ssh/
    nano ~/.ssh/id_rsa
    ```
3. In the text editor, copy and paste the contents of the Private Key and save
4.  Run the below commands to make the key usable

    ```bash
    chmod 700 ~/.ssh/
    chmod 600 ~/.ssh/id_rsa
    ```

### Windows

1. Log into the server as an administrator
2.  Open Powershell as administrator and run the below command, putting the contents of the private key between the " "

    ```powershell
    $privkey = ""
    ```
3.  Run the below command to output the private key into the keystore

    <pre class="language-powershell"><code class="lang-powershell"><strong>echo $privkey | Out-File -filepath $ENV:userprofile.ssh\id_rsa -Force -verbose VERBOSE: Performing the operation "Output to File" on target "C:\Users\x.ssh\id_rsa"
    </strong></code></pre>
