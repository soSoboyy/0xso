---
{"dg-publish":true,"permalink":"/htb/cjca/linux/backup-restore/","dg-note-properties":{}}
---

Linux systems provide a range of powerful tools for backing up and restoring data, designed to be both efficient and secure.
- Rsync
- Deja Dup
- Duplicity

Rsync is an open-source tool that allows for fast and secure backups, whether locally or to a remote location. One of its key advantages is that it only transfers the portions of files that have changed, making it highly efficient when dealing with large amounts of data. Rsync is particularly useful for network transfers, such as syncing files between servers or creating incremental backups over the internet.

Duplicity is another powerful tool that builds on Rsync, but adds encryption features to protect the backups.

##### Install Rsync
`sudo apt install rsync -y`

###### Rsync - Backup a local Directory to our Backup-Server
```shell
sosoBoy@htb[/htb]$ rsync -av /path/to/mydirectory user@backup_server:/path/to/backup/directory
```
This command will copy the entire directory (`/path/to/mydirectory`) to a remote host (`backup_server`), to the directory `/path/to/backup/directory`. The option `archive` (`-a`) is used to preserve the original file attributes, such as permissions, timestamps, etc., and using the `verbose` (`-v`) option provides a detailed output of the progress of the `rsync` operation.


==We can also add additional options to customise the backup process, such as using compression and incremental backups:==

```shell
sosoBoy@htb[/htb]$ rsync -avz --backup --backup-dir=/path/to/backup/folder --delete /path/to/mydirectory user@backup_server:/path/to/backup/directory
```

With this, we back up the `mydirectory` to the remote `backup_server`, preserving the original file attributes, timestamps, and permissions, and enabled compression (`-z`) for faster transfers. The `--backup` option creates incremental backups in the directory `/path/to/backup/folder`, and the `--delete` option removes files from the remote host that is no longer present in the source directory.

##### Encrypted Rsync

To ensure the security of our `rsync` file transfer between our local host and our backup server, we can combine the use of SSH and other security measures. By using SSH, we are able to encrypt our data as it is being transferred, making it much more difficult for any unauthorized individual to access it. Additionally, we can also use firewalls and other security protocols to ensure that our data is kept safe and secure during the transfer. By taking these steps, we can be confident that our data is protected and our file transfer is secure. Therefore we tell `rsync` to use SSH like the following:

---
##### Secure Transfer of our Backup

`sosoBoy@htb[/htb]$ rsync -avz -e ssh /path/to/mydirectory user@backup_server:/path/to/backup/directory`

The data transfer between our local host and the backup server occurs over the encrypted SSH connection, which provides confidentiality and integrity protection for the data being transferred. This encryption process ensures that the data is protected from any potential malicious actors who would otherwise be able to access and modify the data without authorization. The encryption key itself is also safeguarded by a comprehensive set of security protocols, making it even more difficult for any unauthorized person to gain access to the data. In addition, the encrypted connection is designed to be highly resistant to any attempts to breach security, allowing us to have confidence in the protection of the data being transferred.

---
##### Auto-Synchronization

To enable auto-synchronization using `rsync`, you can use a combination of `cron` and `rsync` to automate the synchronization process. Scheduling the cron job to run at regular intervals ensures that the contents of the two systems are kept in sync. This can be especially beneficial for organizations that need to keep their data synchronized across multiple machines. Furthermore, setting up auto-synchronization with `rsync` can be a great way to save time and effort, as it eliminates the need for manual synchronization. It also helps to ensure that the files and data stored in the systems are kept up-to-date and consistent, which helps to reduce errors and improve efficiency.

#rsync #autosync 

*Enable auto sync*
Create a new script called `RSYNC_Backup.sh`, which will trigger the `rsync` command to sync our local directory with the remote one. However, because we are using a script to perform SSH for the rsync connection, we need to configure key-based authentication. This is to bypass the need to input our password when connecting with SSH.

1. First, we generate a key pair for our user.

`sosoBoy@htb[/htb]$ ssh-keygen -t rsa -b 2048`

2. Follow the prompts to specify the location (default is `~/.ssh/id_rsa`) and optionally provide a passphrase (leave it empty for no passphrase). Then, we need to copy our public key to the remote server.

`sosoBoy@htb[/htb]$ ssh-copy-id user@backup_server`

3. Now, we can create our script to automate the rsync backup.

 4. RSYNC_Backup.sh

bash
```bash
#!/bin/bash
rsync -avz -e ssh /path/to/mydirectory user@backup_server:/path/to/backup/directory
```

To ensure that the script is able to execute properly, we must provide the necessary permissions. Additionally, it's also important to make sure that the script is owned by the correct user, as this will ensure that only the correct user has access to the script and that the script is not tampered with by any other user.

5. Give permission
`sosoBoy@htb[/htb]$ chmod +x RSYNC_Backup.sh`

6. After that, we can create a crontab that tells `cron` to run the script every hour at the 0th minute.
`sosoBoy@htb[/htb]$ crontab -e`

We can adjust the timing to suit our needs. To do so, the crontab needs the following content:

`0 * * * * /path/to/RSYNC_Backup.sh`

With this setup, `cron` will be responsible for executing the script at the desired interval, ensuring that the `rsync` command is run and the contents of the local directory are synchronised with the remote host.

##### Exercise:
Try out rsync using Pwnbox. Instead of syncing files with a remote server,  use Pwnbox as both your source and destination, which makes testing simpler. 

To do this, create two directories on Pwnbox:

1. `to_backup` (where your original data is stored) and another called
2. `synced_backup` (where the synchronized data will be copied)

You will then transfer the data from the `to_backup` directory to the `synced_backup` directory using `rsync`. To automate this process, set up a `cron` job that runs every minute to ensure continuous synchronization. 
*Remember, because we are testing this locally, we can use the loopback IP address 127.0.0.1 as the address for the "remote" host.*