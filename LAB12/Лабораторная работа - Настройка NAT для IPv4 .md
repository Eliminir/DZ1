
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

c.	Настраиваем перевод, связывая ACL и пул с процессом преобразования.

    R1(config)# ip nat inside source list 1 pool PUBLIC_ACCESS 

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB12/11.JPG)

d.	Задаем внутренний (inside) интерфейс.

    R1(config)# interface g0/0/1
    R1(config-if)# ip nat inside

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB12/12.JPG)

e.	Определяем внешний (outside) интерфейс.
        
    R1(config)# interface g0/0/0
    R1(config-if)# ip nat outside

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB12/13.JPG)

Шаг 2. Проверьте и проверьте конфигурацию. 

a.	С PC-B,  запускаем эхо-запрос интерфейса Lo1 (209.165.200.1) на R2. Если эхо-запрос не прошел, выполняем процесс поиска и устранения неполадок. На R1 отоброжаем таблицу NAT на R1 с помощью команды show ip nat translations.

    R1# show ip nat translations
    Pro Inside global Inside local Outside local Outside global
    --- 209.165.200.226 192.168.1.3 --- --- 
    226:1 192.168.1. 3:1 209.165.200. 1:1 209.165.200. 1:1 
    Total number of translations: 2

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB12/14.JPG)


