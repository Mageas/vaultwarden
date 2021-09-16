# **How to sefhost vaultwarden with certginx**

Tutorial to easily host your vaultwarden instance.

### **Secure your VPS**

I highly suggest your to secure your VPS. You can follow [this tutorial](https://gitlab.com/Mageas/how-to-secure-a-vps) to secure your VPS.

### **Installing certginx**

Please follow [this tutorial](https://gitlab.com/certginx/certginx) to install certginx.

Use `nginx.conf` in this repository instead of `subdomain.domain.com.conf` in certginx repository as template to generate your ssl certificate.

### **Configuring certginx**

Once your ssl is configured, in your nginx config replace `localhost` with `vaultwarden`.

### **Configuring docker-compose**

Match the `user` with your **UID** and **GID**.

### **Environment variables**

Environment variables are in `data/docker-config.env`.

Full documentation [here](https://github.com/dani-garcia/vaultwarden/blob/main/.env.template).

### **Setup backups**

Requirements:
- GPG configured (Only store your public key!).

**Configuration**

Update the variables at the top of the script to match your configuration.

**Permissions**

Make sure `backup.sh` have the *execute* permission.

**Automatic backups**

You can use crontab with `crontab -e` to automate your backups. In the example below you have 2 backups per day, one at midnight and one at noon.
```
# m h  dom mon dow   command
0 0 * * * ${HOME}/path_to_backup_script/backup.sh >> ${HOME}/path_to_backup_folder/backups.log
0 12 * * * ${HOME}/path_to_backup_script/backup.sh >> ${HOME}/path_to_backup_folder/backups.log
```

### **Test your backups**

TODO