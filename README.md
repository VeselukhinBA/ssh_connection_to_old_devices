# Подключаемся по SSH к старенькому оборудованию
Практическая ситуация: при попытке залогиниться на устройство получаем ошибку
```bash
ssh -l admin x.x.x.x
Unable to negotiate with x.x.x.x port 22: no matching cipher found. Their offer: 3des-cbc
```
Это значит, что клиент и сервер не могут договориться об алгоритме шифрования.
Поэтому в ```/home/user/.ssh``` конкретного пользователя создаем/редактируем файл *config*. Итоговый конфиг выглядит так:
```bash
Host x.x.x.x
 KexAlgorithms +diffie-hellman-group1-sha1
 Ciphers aes128-cbc,3des-cbc,aes192-cbc,aes256-cbc
```
Повторяем попытку подключения. Должно появится приглашение ввести пароль.
