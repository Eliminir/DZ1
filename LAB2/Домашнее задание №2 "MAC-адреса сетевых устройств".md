## *Лабораторная работа. Просмотр таблицы MAC-адресов коммутатора* ##
___
#### 	*Топология сети*
![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB2/1.JPG)

#### *Таблица адресации*
![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB2/2.JPG)
	
 ## *Цели*
 *Часть 1. Создание и настройка сети*
 
 *Часть 2. Изучение таблицы МАС-адресов коммутатора*
___



## *Часть 1. Создание и настройка сети*

*Шаг 1. Подключаем сеть в соответствии с топологией*

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB2/3.JPG)



*Шаг 2. Настраиваем узлы ПК.*


![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB2/4.JPG)

*Шаг 3. Выполняем инициализацию и перезагрузку коммутаторов*


![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB2/5.JPG)


*Шаг 4. Настраиваем базовые параметры каждого коммутатора*

a.	Настраиваем имена устройств в соответствии с топологией.

b.	Настраиваем IP-адреса, как указано в таблице адресации.

c.	Назначаем cisco в качестве паролей консоли и VTY.

d.	Назначаем class в качестве пароля доступа к привилегированному режиму EXEC.


![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB2/6.1.JPG)

*Аналогично для второго*


![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB2/6.2.JPG)

___

### *Часть 2. Изучение таблицы МАС-адресов коммутатора*

*Шаг 1. Записываем МАС-адреса сетевых устройств*

MAC-адрес компьютера PC-A: 0002.4A5D.DC73

MAC-адрес компьютера PC-B: 0003.E466.2398

МАС-адрес коммутатора S1 Fast Ethernet 0/1: 0001.645e.0001

МАС-адрес коммутатора S2 Fast Ethernet 0/1: 00e0.f923.0d01

___


*Шаг 2. Просматриваем таблицу МАС-адресов коммутатора*


a.	Подключаемся к коммутатору S2 через консоль

b.	Вводим команду show mac address-table



![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB2/7.JPG)

В таблице МАС-адресов видим только MAC-адрес коммутатора S1 который сопоставлен с портом Fa0/1


*Шаг 3. Очищаем таблицу МАС-адресов коммутатора S2 и снова отоброжаем таблицу МАС-адресов*

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB2/8.JPG)



