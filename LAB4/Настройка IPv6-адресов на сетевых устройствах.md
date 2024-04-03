### *Настройка IPv6-адресов на сетевых устройствах*

#### *Топология*

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB4/1.JPG)

#### *Таблица адресации*

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB4/2.JPG)

___

### *Задачи*


 #### *Часть 1. Настройка топологии и конфигурация основных параметров маршрутизатора и коммутатора*
 
 #### *Часть 2. Ручная настройка IPv6-адресов*

 #### *Часть 3. Проверка сквозного соединения*
___

 ### *Часть 1. Настройка топологии и конфигурация основных параметров маршрутизатора и коммутатора*

 
 
*После подключения сети, инициализации и перезагрузки маршрутизатора и коммутатора выполняем следующие действия:*


*Шаг 1. Настраиваем маршрутизатор*


*Назначаем имя маршрутизатора и настраиваем основные параметры устройства*

 ![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB4/3.JPG)

*Шаг 2. Настраиваем коммутатор*


*Назначаем имя коммутатора и настраиваем основные параметры устройства*

 ![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB4/4.JPG)


 #### *Часть 2. Ручная настройка IPv6-адресов*

 *Шаг 1. Назначаем IPv6-адреса интерфейсам Ethernet на R1*

 *Назначаем глобальные индивидуальные IPv6-адреса, указанные в таблице адресации обоим интерфейсам Ethernet на R1*

 ![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB4/5.JPG)

 *Проверяем, назначен ли каждому интерфейсу корректный индивидуальный IPv6-адрес*

 ![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB4/6.JPG)
 

*Чтобы обеспечить соответствие локальных адресов канала индивидуальному адресу, вручную вводим локальные адреса канала на каждом интерфейсе Ethernet на R1*

 ![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB4/7.JPG)
 
 *Проверяем, что локальный адрес связи изменен на fe80::1*

  ![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB4/8.JPG)

 *Группы многоадресной рассылки интерфейса G0/0:  FF02::1, FF02::1:FF00:1*


 *Шаг 2. Активируем IPv6-маршрутизацию на R1*

 *В командной строке на PC-B вводим команду ipconfig, чтобы получить данные IPv6-адреса, назначенного интерфейсу ПК*
 
 ![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB4/9.JPG)

*Видим, что индивидуальный IPv6-адрес сетевой интерфейсной карте не назначен*

*Активируем IPv6-маршрутизацию на R1 с помощью команды IPv6 unicast-routing*


 ![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB4/10.JPG)
 

*Снова вводим команду ipconfig на PC-B*

 ![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB4/11.JPG)
 ![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB4/10.JPG)

