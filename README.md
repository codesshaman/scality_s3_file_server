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

### Шаг 4. 
