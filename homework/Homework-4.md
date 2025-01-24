# Homework 4 – FTP

1. **Question:** The default two ports for FTP are `__,__`.
   - **Answer:** `20,21`

1. In passive FTP mode, the server opens a random port between `________` and `_______ `for data transfer. Assume no directives have modified this range.
   - **Answer:** `1024,65535`

1. **Question:** Anonymous FTP access allows users to log in without a password. (True/False)
   - **Answer:** `True`

1. **Question:** Anonymous FTP is commonly used for secure file transfers.  
    - **Answer:** `False`

1. **Question:** To disable anonymous user login you must set `_______=__`
   - **Answer:** `anonymous_enable=NO` or `anonymous_enable,NO`

1. **Question:** The command used to download a file in FTP is `get filename`. (True/False)
   **Answer:** `True`

1. **Question:** FTP uses port `__` for its control channel.  (True/False)
   **Answer:** `21`

1. **Question:** FTPS is different from FTP because FTPS uses `e________`.  
   **Answer:** `encryption`

1. **Question:** To terminate an FTP session, the correct command is `quit`. (True/False) 
   **Answer:** `True`

1. **Question:** The command used to upload a file in FTP is `get filename`. (True/False)
   **Answer:** `False`

1. **Question:** In FTP, a failed login attempt due to an incorrect password returns the code `___`.  
   **Answer:** `530`

1. **Question:** What is the command to print the current working directory in FTP?
   - **Answer:** `pwd`

1. **Question:** Which FTP command is used to change the working directory?  
   - **Answer:** `cwd`

1. **Question:** The `dele` command in FTP is used to `__________` a file.  
   - **Answer:** `delete`

1. **Question:** The `help` command provides a list of available FTP commands.  
   **Answer:** True.

1. **Question:** The setting `local_enable=___` allows local user access.  
   **Answer:** `YES`

1. **Question:** The setting `write_enable=YES` permits `_______` operations by users.  
   - **Answer:** `write`

1. **Question:** What two directives need to be set to configure passive FTP to restrict the ports passive FTP can use?
    - **Answer:** `pasv_min_port,pasv_max_port` or `pasv_max_port,pasv_min_port`

1. **Question:** The setting `chroot_list_file=/etc/vsftpd.chroot_list` specifies users exempt from being jailed in their home directory.  
    - **Answer:** `True`

1. **Question:** The setting `chroot_local_user=YES` prevents users from navigating outside their home directory. (True/False)  
    - **Answer:** `True`

1. **Question:** By setting only `ssl_enable=YES`, all FTP traffic is encrypted. (True/False)  
    - **Answer:** `False`

1. **Question:** What command would you use to change the directory on an FTP server?  
   - **Answer:** `cd`

1. **Question:** The setting `ssl_tlsv1=YES` enables the use of the TLS v1.0 protocol and is a reccommended practice. (True/False)  
    - **Answer:** `False`

1. **Question:** If the default file permission is `666` and the `umask` is set to `022`, what will the final permissions of a newly created file be? Give your answer as the 3-digit Linux file permission value.
   - **Answer**: `644`

1. **Question:** If the default file permission is `666` and the `umask` is set to `222`, what will the final permissions of a newly created file be? Give your answer as the 3-digit Linux file permission value.
   - **Answer**: `444`

1. **Question:** If the default directory permission is `777` and the `umask` is set to `022`, what will the final permissions of a newly created folder be? Give your answer as the 3-digit Linux file permission value.
   - **Answer**: `755`

1. **Question:** The `cdup` command is used to change to the parent directory.  
   **Answer:** `True`

1. **Question:** The setting `ssl_ciphers=___` ensures that only high-strength encryption algorithms are used.  
   **Answer:** `HIGH`

1. **Question:** With `force_local_data_ssl=YES`, local users are forced to use SSL for data transfers.  
   **Answer:** `True`

1. **Question:** The `bye` command in FTP is used to end the FTP session.  
   **Answer:** `True`