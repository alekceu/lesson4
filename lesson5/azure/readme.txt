Создание 2 AZ VM
Одна с внешним ip
Другая только внутрення сеть

ssh-keygen -t rsa -f ~/.ssh/gcpuser -C gcpuser -P ""

Подключение по ssh к первой powershell
ssh azuser@20.213.14.28 -i C:\Users\a.shved\.ssh\azuser

Подключение по ssh к второй машине из сесии первой
ssh 10.0.0.5
The authenticity of host '10.0.0.5 (10.0.0.5)' can't be established.
ECDSA key fingerprint is SHA256:QU1XLV4aXu2UZmg3Z1O/78k+ohSEaXl4NbIXuT0wYb0.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '10.0.0.5' (ECDSA) to the list of known hosts.
azuser@10.0.0.5: Permission denied (publickey).

Ошибка! Все логично!

Настроим SSH Forwarding на вашей локальной
машине
Start-Service ssh-agent
ssh-add.exe .\azuser
Identity added: .\azuser (azuser)

ssh -i .\azuser -A azuser@20.213.14.28
и с нее подключаемся далее

ssh 10.0.0.5
OK!


Исследовать способ подключения к internalhost в
одну команду из вашего рабочего устройства, 
проверить работоспособность найденного решения и
внести его в README.md в вашем репозитории

Подключение через одну команду 
-J jump host!
ssh -A -J azuser@20.213.14.28 azuser@10.0.0.5

Доп. задание: Предложить вариант решения для
подключения из консоли при помощи команды вида
ssh internalhost из локальной консоли рабочего
устройства, чтобы подключение выполнялось по
алиасу internalhost и внести его в README.md в вашем
репозитории

ssh alias manual
Создаем файл ~/.ssh/config
Host AZInternetHost
	Hostname 20.213.14.28
	User azuser
	IdentityFIle C:\users\a.shved\.ssh\azuser
	
Host AZIntraNetHost
	Hostname 10.0.0.5
	User azuser
	IdentityFIle C:\users\a.shved\.ssh\azuser
	ProxyJump AZInternetHost

 ssh AZIntraNetHost
И все ОК!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!









