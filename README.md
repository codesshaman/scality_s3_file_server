# Установка

> Все действия выполняются под суперпользователем

### Шаг 1. Установка vsftpd

apt update
-```apt install vsftpd```

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

```adduser ftpuser```

```mkdir /home/ftpuser/ftp```

```chown nobody:nogroup /home/ftpuser/ftp```

```chmod a-w /home/ftpuser/ftp```

```mkdir /home/ftpuser/ftp/files```

```sudo chown ftpuser:ftpuser /home/ftpuser/ftp/files```
