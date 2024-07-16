
## Лабораторная работа - Настройка NAT для IPv4

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB12/1.JPG)

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB12/2.JPG)



## Часть 1. Создание сети и настройка основных параметров устройства

Шаг 1. Подключаем кабели сети согласно приведенной топологии.

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB12/3.JPG)

Шаг 2. Производим базовую настройку маршрутизаторов

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB12/4.JPG)

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB12/5.JPG)


Шаг 3. Настраиваем базовые параметры каждого коммутатора

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB12/6.JPG)

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB12/7.JPG)

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB12/8.JPG)


## Часть 2. Настройка и проверка NAT для IPv4

Шаг 1. Настраиваем NAT на R1, используя пул из трех адресов 209.165.200.226-209.165.200.228.

a.	Настраиваем простой список доступа, который определяет, какие хосты будут разрешены для трансляции. В этом случае все устройства в локальной сети R1 имеют право на трансляцию.

    R1(config)# access-list 1 permit 192.168.1.0 0.0.0.255 

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB12/9.JPG)

b.	Создаем пул NAT и указываем ему имя и диапазон используемых адресов.

    R1(config)# ip nat pool PUBLIC_ACCESS 209.165.200.226 209.165.200.228 netmask 255.255.255.248 

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB12/10.JPG)



