
## Лабораторная работа - Настройка NAT для IPv4 :space_invader: :space_invader: :space_invader:

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

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB12/21.JPG)




Во что был транслирован внутренний локальный адрес PC-B? 

209.165.200.226

Какой тип адреса NAT является переведенным адресом?

Inside


b.	С PC-A, запускаем эхо-запрос интерфейса Lo1 (209.165.200.1) на R2. Если эхо-запрос не прошел, выполните отладку. На R1 отобразите таблицу NAT на R1 с помощью команды show ip nat translations.

  ![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB12/22.JPG)

c.	Обратите внимание, что предыдущая трансляция для PC-B все еще находится в таблице. Из S1, эхо-запрос интерфейса Lo1 (209.165.200.1) на R2. Если эхо-запрос не прошел, выполните отладку. На R1 отобразите таблицу NAT на R1 с помощью команды show ip nat translations.
      
   ![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB12/23.JPG)
    
d.	Теперь запускаем пинг R2 Lo1 из S2. На этот раз перевод завершается неудачей, и мы получаем эти сообщения на консоли R1:

    Sep 23 15:43:55.562: %IOSXE-6-PLATFORM: R0/0: cpp_cp: QFP:0.0 Thread:000 TS:00000001473688385900 %NAT-6-ADDR_ALLOC_FAILURE: Address allocation failed; pool 1 may be exhausted [2]


f.	Учитывая, что пул ограничен тремя адресами, NAT для пула адресов недостаточно для нашего приложения. Очищаем преобразование NAT и статистику, и переходим к PAT.

    R1# clear ip nat translation * 

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB12/14.JPG)


## Часть 3. Настройка и проверка PAT для IPv4.

В части 3 необходимо настроить замену NAT на PAT в пул адресов, а затем на PAT с помощью интерфейса.

Шаг 1. Удаляем команду преобразования на R1.

    R1(config)# no ip nat inside source list 1 pool PUBLIC_ACCESS

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB12/15.JPG)

Шаг 2. Добавляем команду PAT на R1 

    R1(config)# ip nat inside source list 1 pool PUBLIC_ACCESS overload

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB12/16.JPG)

Шаг 3. Тестируем и проверяем конфигурацию

  ![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB12/24.JPG)
    
Вопросы:

Во что был транслирован внутренний локальный адрес PC-B?

209.165.200.226
 
Какой тип адреса NAT является переведенным адресом?

inside
 
Чем отличаются выходные данные команды show ip nat translations из упражнения NAT?

translation между insade и outside адресами в списке нет


b.	С PC-A, запускаем эхо-запрос интерфейса Lo1 (209.165.200.1) на R2. На R1 отобразите таблицу NAT на R1 с помощью команды show ip nat translations.

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB12/25.JPG)
    


c.	Генерируем трафик с нескольких устройств для наблюдения PAT. На PC-A и PC-B используйте параметр -t с командой ping, чтобы отправить безостановочный ping на интерфейс Lo1 R2 (ping -t 209.165.200.1), затем вернитесь к R1 и выполните команду show ip nat translations:

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB12/26.JPG)

Как маршрутизатор отслеживает, куда идут ответы? 

он присваивает уникальные номера портов

d.	PAT в пул является очень эффективным решением для малых и средних организаций. Тем не менее есть неиспользуемые адреса IPv4, задействованные в этом сценарии. Мы перейдем к PAT с перегрузкой интерфейса, чтобы устранить эту трату IPv4 адресов. Очищаем трансляции и статистику:

    R1# clear ip nat translation * 
    R1# clear ip nat statistics

Шаг 4. На R1 удаляем команды преобразования nat pool

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB12/19.JPG)

Шаг 5. Добавляем команду PAT overload, указав внешний интерфейс.

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB12/20.JPG)


Шаг 6. Протестируем и проверяем конфигурацию.

a.	Давайте проверим PAT, чтобы интерфейс работал. С PC-B,  запустите эхо-запрос интерфейса Lo1 (209.165.200.1) на R2. Если эхо-запрос не прошел, выполните отладку. На R1 отобразите таблицу NAT на R1 с помощью команды show ip nat translations.

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB12/27.JPG)

b.	Делаем трафик с нескольких устройств для наблюдения PAT. На PC-A и PC-B используйте параметр -t с командой ping для отправки безостановочного ping на интерфейс Lo1 R2 (ping -t 209.165.200.1). На S1 и S2 выполните привилегированную команду exec ping 209.165.200.1 повторить 2000. Затем вернитесь к R1 и выполните команду

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB12/28.JPG)

## Часть 4. Настройка и проверка статического NAT для IPv4.


Шаг 1. На R1 очищаем текущие трансляции и статистику.

    R1# clear ip nat translation * 

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB12/14.JPG)

Шаг 2. На R1 настраиваем команду NAT, необходимую для статического сопоставления внутреннего адреса с внешним адресом.

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB12/29.JPG)

Шаг 3. Протестируем и проверяем конфигурацию.
a.	Давайте проверим, что статический NAT работает. На R1 отобразите таблицу NAT на R1 с помощью команды show ip nat translations, и вы увидите статическое сопоставление.

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB12/30.JPG)

b.	Таблица перевода показывает, что статическое преобразование действует. Проверяем это, запустив ping  с R2 на 209.165.200.229. 

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB12/31.JPG)


c.	На R1 отображаем таблицу NAT на R1 с помощью команды show ip nat translations, и видим статическое сопоставление и преобразование на уровне порта для входящих pings.

![alt text](https://github.com/Eliminir/OTUSLABS/blob/Labs/LAB12/32.JPG)

Это подтверждает, что статический NAT работает.


