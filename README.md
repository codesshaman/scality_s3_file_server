# Установка

> Все действия выполняются под суперпользователем

### Шаг 1. Установка vsftpd

```apt update```

```apt install vsftpd```

```service vsftpd status```

### Шаг 2. Конфигурация firewall

```ufw allow 20/tcp```

```ufw allow 21/tcp```

```ufw allow 40000:50000/tcp```

```ufw allow 990/tcp```

```ufw allow openssh```

```ufw enable```

```ufw status```

### Шаг 3. Создание пользователя и директорий

```adduser ftpd```

```mkdir /home/ftpd/ftp```

```chown nobody:nogroup /home/ftpd/ftp```

```chmod a-w /home/ftpd/ftp```

```mkdir /home/ftpd/ftp/files```

```chown ftpd:ftpd /home/ftpd/ftp/files```

### Шаг 4. Редактирование конфига

```cp /etc/vsftpd.conf /etc/vsftpd.conf_default```

```nano /etc/vsftpd.conf```

### Новая конфигурация:

```
listen=NO
listen_ipv6=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
force_dot_files=YES
pasv_min_port=40000
pasv_max_port=50000

user_sub_token=$USER
local_root=/home/$USER/ftp
```
### Шаг 5. Перезагрузка демона

```systemctl restart vsftpd.service```

```systemctl status vsftpd.service```

### Шаг 6. Создание сертификата

```openssl req -x509 -nodes -days 3650 -newkey rsa:2048 -keyout /etc/ssl/private/vsftpd.pem -out /etc/ssl/private/vsftpd.pem```
