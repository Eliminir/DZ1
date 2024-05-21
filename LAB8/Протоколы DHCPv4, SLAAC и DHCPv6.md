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
