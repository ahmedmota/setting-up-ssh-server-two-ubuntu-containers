# setting-up-ssh-server-two-ubuntu-containers
Here are the steps to set up an SSH connection between two Ubuntu containers:

## Creating and Starting the Containers
1. Create two containers on the Ubuntu image and name them `container1` and `container2`.
2. Start the containers.

## Setting Up SSH Server on Container1
1. Login to `container1` using the `docker attach container1` command.
2. Update the Ubuntu container using the `apt-get update` command.
3. Install SSH server on `container1` using the `apt-get install openssh-server` command.

## Setting Up SSH Server on Container2
1. Login to `container2`.
2. Update the Ubuntu container using the `apt-get update` command.
3. Install SSH server on `container2` using the `apt-get install openssh-server` command.

## Configuring SSH Server
1. Edit the file `/etc/ssh/sshd_config` using the `nano` editor.
2. Uncomment and edit the `PermitRootLogin no` line to `PermitRootLogin yes`.
3. Exit the file.
4. Restart the SSH server.

## Connecting to Container2
1. Login to `container1`.
2. SSH to `container2` using `ssh root@othercontaineripaddress`.
3. If you get the error message "root@172.17.0.3's password: Permission denied, please try again.", you need to generate a new password for `container2`. Type `passwd root` command and type a new password.
4. Login to `container1`.
5. SSH to `container2` using `ssh root@othercontaineripaddress`.

Note that if you don't uncomment `PermitRootLogin no` and edit it to `PermitRootLogin yes`, you will face a permission denied error while SSHing to `container2`.

