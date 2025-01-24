# Homework 3 - SSH

1. **Question:** What does SSH stand for?
   - **Answer:** `Secure Shell`

1. **Question:** What is the command for SSHing into the machine 192.168.0.1 with the account blueteam?
   - **Answer:** `ssh blueteam@192.168.0.1`
  
1. **Question:** What is the default port of SSH?
   - **Answer:** `22`

1. **Question:** What is the flag for changing the port used?
   - **Answer:** `-p`

1. **Question:** What is the flag for using an SSH key to log in?
   - **Answer:** `-i`

1. **Question:** What is the package name on Ubuntu AND CentOS for installing an SSH server?
   - **Answer:** `openssh-server`

1. **Question:** What is the name of the ssh server service on Ubuntu?
   - **Answer:** `ssh` or `sshd`

1. **Question:** What is the name of the ssh server service on CentOS?
   - **Answer:** `sshd`

1. **Question:** What is the full file path of the config file for a local ssh server? (path + filename)
   - **Answer:** `/etc/ssh/sshd_config`

1. **Question:** Which directive in the SSH config file will allow public keys to be used to authenticate?
   - **Answer:** `PubkeyAuthentication yes` or `PubkeyAuthentication`

1. **Question:** Which directive in the SSH config file controls which files SSH references to confirm if a key is allowed to connect?
   - **Answer:** `AuthorizedKeysFile`

1. **Question:** What permissions need to be on the SSH configuration file? (three numbers)
   - **Answer:** `644`

1. **Question:** What permissions need to be on an SSH key? (three numbers)
   - **Answer:** `400`

1. **Question:** Which file controls which keys are allowed to ssh into the blueteam user account? (path + filename)
   - **Answer:** `/home/blueteam/.ssh/authorized_keys`

1. **Question:** Changing `UsePAM` to `no` will absolutely not break your SSH server but will make authentication less secure. (True/False)
   - **Answer:** `True`

1. **Question:** Where are SSH keys for your system stored by default? (path)
   - **Answer:** `/etc/ssh/` or `/etc/ssh`

1. **Question:** Which directive in the SSH config file allows other configuration files to be loaded?
   - **Answer:** `Include`

1. **Question:** What should ListenAddress be set to in the SSH configuration file?
   - **Answer:** `0.0.0.0`

1. **Question:** Which command can create new SSH keys?
   - **Answer:** `ssh-keygen`

1. **Question:** Which command can copy your SSH key to another machine?
   - **Answer:** `ssh-copy-id`

1. **Question:** What command is used to copy files from a remote host?
   - **Answer:** `scp`

1. **Question:** How would you copy the file `backup.txt` from your current directory to the machine `192.168.0.1` with the account `blueteam` stored in their home directory to your current directory on your local machine?
   - **Answer:** `scp backup.txt blueteam@192.168.0.1:~/backup.txt` or `scp backup.txt blueteam@192.168.0.1:/home/blueteam/backup.txt` or `scp backup.txt blueteam@192.168.0.1:~/` or `scp backup.txt blueteam@192.168.0.1:/home/blueteam/`

1. **Question:** `__________ no` disables password-based authentication for SSH, allowing only key-based or other authentication methods.
   - **Answer:** `PasswordAuthentication`

1. **Question:**  If you want to prevent users from logging in with an empty password, you should use `__________ __`
   - **Answer:** `PermitEmptyPasswords no`

1. **Question:** The `AllowUsers` directive specifies which users are allowed to access the system via SSH. (True/False)
   - **Answer:** `True`

1. **Question:** The `AllowGroups` directive specifies which groups are not allowed to access the system via SSH. (True/False)
   - **Answer:** `False`

1. **Question:** `systemctl reload sshd` applies changes after editing the SSH configuration file. (True/False)
   - **Answer:** `True`

1. **Question:** If multiple instances of the same directive appear in the SSH configuration file, the SSH server will apply the value of the __________ (first/last) instance of that directive.
   - **Answer:** `last`

1. **Question:** To view live ssh logs, the command `sudo tail -_ ____________ | grep ________` will display real-time logs for the SSH daemon. Type the full command as your answer, including the parts you are already given.
   - **Answer:** `sudo tail -f /var/log/auth.log | grep sshd`

1. **Question:** To limit the number of failed login attempts before an SSH connection is closed to 3 what directive and value would be used?
   - **Answer:** `MaxAuthTries 3`

1. **Question** Setting the directive `PermitRootLogin no` means that the root user can no longer log in at all. (True/False)
   - **Answer:** `False`

1. **Question:** To limit the number of concurrent SSH connections to 4 what directive and value would be used?
   - **Answer:** `MaxSessions 4`