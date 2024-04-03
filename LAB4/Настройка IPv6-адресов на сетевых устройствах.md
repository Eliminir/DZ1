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

  *Видим, что PC-B получил глобальный префикс маршрутизации и идентификатор подсети. Так как на R1 все интерфейсы IPv6 теперь являются частью многоадресной группы FF02::2. Это позволяет маршрутизатору отправлять сообщения с информацией о префиксе всем узлам в локальной сети*

 *Шаг 3. Назначаем IPv6-адреса интерфейсу управления (SVI) на S1.*

*Назначаем адрес IPv6 для S1. Также назначаем этому интерфейсу локальный адрес канала*
  
  
 ![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB4/12.JPG)

 *Проверим правильность назначения IPv6-адресов интерфейсу управления с помощью команды show ipv6 interface vlan1*

  ![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB4/13.JPG)

*Шаг 4. Назначаем компьютерам статические IPv6-адреса*

 ![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB4/14.JPG)
  

  ### *Часть 3. Проверка сквозного подключения*

  *С PC-A отправим эхо-запрос на FE80::1. Это локальный адрес канала, назначенный G0/1 на R1*

   ![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB4/15.JPG)

*Отправляем эхо-запрос на интерфейс управления S1 с PC-A*

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB4/16.JPG)

*Вводим команду tracert на PC-A, чтобы проверить наличие сквозного подключения к PC-B*

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB4/17.JPG)

*С PC-B отправляем эхо-запрос на PC-A*

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB4/18.JPG)

*С PC-B отправляем эхо-запрос на локальный адрес канала G0/0 на R1*

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB4/19.JPG)


 *Так как линк локал пакеты не покидают лоакальную сеть, поэтому один и тот же адрес может использоваться на интерфейсе, связанном с другой локальной сетью*

 

