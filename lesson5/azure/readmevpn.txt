Разрешаем 80 порт на Azure в политиках сети
Это для проверки апач


Теперь ставим на ВМ vpn сервер

Welcome to this OpenVPN road warrior installer!

This server is behind NAT. What is the public IPv4 address or hostname?
Public IPv4 address / hostname [20.213.14.28]:

Which protocol should OpenVPN use?
   1) UDP (recommended)
   2) TCP
Protocol [1]:

What port should OpenVPN listen to?
Port [1194]:

Select a DNS server for the clients:
   1) Current system resolvers
   2) Google
   3) 1.1.1.1
   4) OpenDNS
   5) Quad9
   6) AdGuard
DNS server [1]:

Enter a name for the first client:
Name [client]: azvpnuser

OpenVPN installation is ready to begin.


Finished!

The client configuration is available in: /root/azvpnuser.ovpn
New clients can be added by running this script again.

Разрешил порт 1194 на azure

Скопировал файл подлючения на локальную машину
scp.exe azuser@20.213.14.28:~/openvpninstall/azvpnuser.ovpn azvpnuser.ovpn

Установил OpenVPn Client
Подключился

Проверил пингами все машину через внутренние ip
Все OK!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!