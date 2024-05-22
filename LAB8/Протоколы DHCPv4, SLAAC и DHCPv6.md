## Реализация DHCPv4/6

### Реализация DHCPv4

### *Топология сети*

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB8/1.JPG)

### *Таблица адресации*

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB8/2.JPG)

### *Таблица VLAN*

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB8/3.JPG)

Задачи

Часть 1. Создание сети и настройка основных параметров устройства

Часть 2. Настройка и проверка двух серверов DHCPv4 на R1

Часть 3. Настройка и проверка DHCP-ретрансляции на R2
____

## Часть 1.	Создание сети и настройка основных параметров устройства

В первой части лабораторной работы нам предстоит создать топологию сети и настроить базовые параметры для узлов ПК и коммутаторов

Шаг 1.	Создание схемы адресации

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB8/4.JPG)

Шаг 2.	Создаем сеть согласно топологии

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB8/5.JPG)


Шаг 3.	Производим базовую настройку маршрутизаторов

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB8/6.JPG)

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB8/7.JPG)

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB8/8.JPG)

Шаг 4.	Настройка маршрутизации между сетями VLAN на маршрутизаторе R1

Активируем интерфейс G0/0/1 на маршрутизаторе

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB8/9.JPG)


Настраиваем подинтерфейсы для каждой VLAN в соответствии с таблицей IP-адресации
Все субинтерфейсы используют инкапсуляцию 802.1Q и назначаются первый полезный адрес из вычисленного пула IP-адресов
Включаем описание для каждого подинтерфейса

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB8/10.JPG)

Проверяем, что вспомогательные интерфейсы работают

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB8/11.JPG)

Шаг 5.	Настраиваем G0/1 на R2, затем G0/0/0 и статическую маршрутизацию для обоих маршрутизаторов

Настраиваем G0/0/1 на R2 с первым IP-адресом подсети C, рассчитанным ранее

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB8/12.JPG)

Настраиваем интерфейс G0/0/0 для каждого маршрутизатора на основе приведенной выше таблицы IP-адресации

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB8/13.JPG)

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB8/14.JPG)

Настраиваем маршрут по умолчанию на каждом маршрутизаторе, указываемом на IP-адрес G0/0/0 на другом маршрутизаторе

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB8/15.JPG)

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB8/16.JPG)

Проверяем, что статическая маршрутизация работает с помощью пинга до адреса G0/0/1 R2 от R1

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB8/17.JPG)

Сохраняем текущую конфигурацию в файл загрузочной конфигурации

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB8/18.JPG)

Шаг 6.	Настраиваем базовые параметры каждого коммутатора

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB8/19.JPG)

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB8/20.JPG)

Шаг 7.	Создаем сети VLAN на коммутаторе S1

a.	Создаем необходимые VLAN на коммутаторе 1 и присвойте им имена из приведенной выше таблицы

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB8/21.JPG)

b.	Настраиваем и активируем интерфейс управления на S1 (VLAN 200), используя второй IP-адрес из подсети, рассчитанный ранее. Устанавливаем шлюз по умолчанию на S1

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB8/22.JPG)

c.	Настраиваем и активируем интерфейс управления на S2 (VLAN 1), используя второй IP-адрес из подсети, рассчитанный ранее. Устанавливаем шлюз по умолчанию на S2

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB8/23.JPG)

d.	Назначаем все неиспользуемые порты S1 VLAN Parking_Lot, настраиваем их для статического режима доступа и административно деактивируйте их. На S2 административно деактивируйте все неиспользуемые порты

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB8/24.JPG)

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB8/25.JPG)

Шаг 8.	Назначаем сети VLAN соответствующим интерфейсам коммутатора

Назначаем используемые порты соответствующей VLAN (указанной в таблице VLAN выше) и настраиваем их для режима статического доступа

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB8/26.JPG)

b.	Убеждаемся, что VLAN назначены на правильные интерфейсы

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB8/27.JPG)

Интерфейс F0/5 находиться в VLAN 1 потому, что это VLAN по умолчанию а сам интерфейс не был настроен

Шаг 9.	Вручную настраиваем интерфейс S1 F0/5 в качестве транка 802.1Q

a.	Изменяем режим порта коммутатора, чтобы принудительно создать магистральный канал

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB8/28.JPG)

b.	В рамках конфигурации транка  устанавливаем для native VLAN значение 1000

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB8/29.JPG)

c.	В качестве другой части конфигурации магистрали указываем, что VLAN 100, 200 и 1000 могут проходить по транку

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB8/30.JPG)

d.	Сохраняем текущую конфигурацию в файл загрузочной конфигурации

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB8/31.JPG)


e.	Проверяем состояние транка

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB8/32.JPG)


Если бы пк не был подключен к сети с помощью DHCP, он бы автоматически себе бы сам настроийл IP в диапозоне 169.254.x.x

## Часть 2.	Настройка и проверка двух серверов DHCPv4 на R1

Шаг 1.	Настраиваем R1 с пулами DHCPv4 для двух поддерживаемых подсетей

a.	Исключаем первые пять используемых адресов из каждого пула адресов

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB8/33.JPG)

b.	Создаем пул DHCP

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB8/34.JPG)

c.	Указываем сеть, поддерживающую этот DHCP-сервер

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB8/35.JPG)

d.	В качестве имени домена указываем CCNA-lab.com

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB8/36.JPG)

e.	Настраиваем соответствующий шлюз по умолчанию для каждого пула DHCP

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB8/37.JPG)

f.	Настраиваем время аренды на 2 дня 12 часов и 30 минут

