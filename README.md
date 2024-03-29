<h1 align="center"> demo2023 | work in progress.. </h1>

![image](https://user-images.githubusercontent.com/43922329/215776915-998af6f2-cd79-420e-b8cb-e678c4c3e730.png)

![topology drawio](https://user-images.githubusercontent.com/43922329/216103519-fddd5a45-fd21-43a9-bd5a-44916d930f9c.png)

|Name VM         |ОС                  |RAM             |CPU             |IP                    |Additionally                       |
|  ------------- | -------------      | -------------  |  ------------- |  -------------       |  -------------                    |  
|RTR-L           |Debian 11/CSR       |2 GB            |2/4             |7.7.7.100/24          |                                   |
|                |                    |                |                |192.168.100.254/24    |                                   |
|RTR-R           |Debian 11/CSR       |2 GB            |2/4             |8.8.8.100/24          |                                   |
|                |                    |                |                |172.16.100.254 /24    |                                   |
|SRV             |Debian 11/Win 2019  |2 GB /4 GB      |2/4             |192.168.100.200/24    |Доп диски 2 шт по 5 GB             |
|WEB-L           |Debian 11           |2 GB            |2               |192.168.100.100/24    |                                   |
|WEB-R           |Debian 11           |2 GB            |2               |172.16.100.100/24     |                                   |
|ISP             |Debian 11           |2 GB            |2               |7.7.7.1/24            |                                   |
|                |                    |                |                |8.8.8.1/24            |                                   |
|                |                    |                |                |3.3.3.1/24            |                                   |
|CLI             |Win 10              |4 GB            |4               |3.3.3.10/24           |                                   |


<h1 align="center"> Модуль 1 </h1>

## 1. Выполнение проектирования кабельной структуры и разработка сетевых топологий в соответствии с требованиями технического задания.

### 1.1. На основе предоставленных ВМ или шаблонов ВМ создайте отсутствующие виртуальные машины в соответствии со схемой.
### a. Характеристики ВМ установите в соответствии с Таблицей 1;
### b. Коммутацию (если таковая не выполнена) выполните всоответствии со схемой сети.

### 1.2. Имена хостов в созданных ВМ должны быть установлены в соответствии со схемой.

**RTR-L:** `hostname RTR-L`

**RTR-R:** `hostname RTR-R`

**SRV:** Запускаем cmd :arrow_right: `sconfig` :arrow_right: `2` :arrow_right: `SRV` 

**WEB-L:** `hostnamectl set-hostname WEB-L`

**WEB-R:** `hostnamectl set-hostname WEB-R`

**ISP:** `hostnamectl set-hostname ISP`

**CLI:** 

![image](https://user-images.githubusercontent.com/43922329/215823038-1e02bbcf-5096-47e5-9b13-5033de5f2892.png)

![image](https://user-images.githubusercontent.com/43922329/215823058-8847b0f3-af8b-428d-977a-b6dfa0042307.png)

![image](https://user-images.githubusercontent.com/43922329/215823084-22e09822-b1ad-489e-a262-0da9889ce7d6.png)

### 1.3.Адресация должна быть выполнена в соответствии с Таблицей 1;

**RTR-L:** 

```
int gi1
ip address 7.7.7.100 255.255.255.0
no shutdown

int gi2
ip address 192.168.100.254 255.255.255.0
no shutdown
```

**RTR-R:**

```
int gi1
ip address 8.8.8.100 255.255.255.0
no shutdown

int gi2
ip address 172.16.100.254 255.255.255.0
no shutdown
```

**SRV:** 

Запускаем cmd :arrow_right: `sconfig` :arrow_right: `8` :arrow_right: `1` 

![image](https://user-images.githubusercontent.com/43922329/215787262-0e0740fa-48ba-4c6a-a076-af85fe6421b4.png)

![image](https://user-images.githubusercontent.com/43922329/215787487-85d8c72a-6a8b-4c8e-ac22-e544511c72fc.png)


- Set Network Adapter Address

- Static IP

- Static IP address: `192.168.100.200`

- Subnet mask: `255.255.255.0`

- Default gateway: `192.168.100.254`

**WEB-L:** 

```
apt install network-manager

nmtui
```

![image](https://user-images.githubusercontent.com/43922329/215789388-3ce2bb0f-1c0e-4e36-8687-c93712f9610b.png)

![image](https://user-images.githubusercontent.com/43922329/215805313-93d9f009-6236-4f68-8ef9-7adedb6208c8.png)

![image](https://user-images.githubusercontent.com/43922329/217788934-a43f6802-bc71-43b1-aae5-6f1f81736f74.png)

**WEB-R:**

```
apt install network-manager

nmtui
```
![image](https://user-images.githubusercontent.com/43922329/215789388-3ce2bb0f-1c0e-4e36-8687-c93712f9610b.png)

![image](https://user-images.githubusercontent.com/43922329/215805318-5d0675f9-ac58-48a1-bb63-ab20d5b53ea4.png)

![image](https://user-images.githubusercontent.com/43922329/217789159-5d4a4959-6df8-42f4-b730-d71a5c4558f3.png)

**ISP:**

```
apt install network-manager

nmtui
```

**CLI:**

![image](https://user-images.githubusercontent.com/43922329/215810811-a77687aa-8f07-4574-aff3-21740b48c2e6.png)

![image](https://user-images.githubusercontent.com/43922329/215810927-6ab11f9d-5ea7-47d7-9c4b-bbfc8e5ac3f8.png)

![image](https://user-images.githubusercontent.com/43922329/215810954-ab6fbe82-4bba-4869-9c36-b88598023559.png)

![image](https://user-images.githubusercontent.com/43922329/215810984-c744564c-4dec-4dd0-ab9c-19dbb1f80a6d.png)

![image](https://user-images.githubusercontent.com/43922329/215811029-153cef3f-f80e-468b-8f9b-eaedfbc239ce.png)

### 1.4.Обеспечьте ВМ дополнительными дисками, если таковое необходимо в соответствии с Таблицей 1

## 2. Осуществление выбора технологии, инструментальных средств и средств вычислительной техники при организации процесса разработки и исследования объектов профессиональной деятельности

**ISP:** Открываем файл sysctl ➡️ `nano /etc/sysctl.conf` 

Теперь нужно раскоменнтировать строку `net.ipv4.ip_forward=1`

### 2.1. Настройте статический маршрут по умолчанию на маршрутизаторах RTR-L и RTR-R

**RTR-L:** `ip route 0.0.0.0 0.0.0.0 7.7.7.1`

**RTR-R:** `ip route 0.0.0.0 0.0.0.0 8.8.8.1`

### 2.2. Настройте динамическую трансляцию портов (PAT):

- На маршрутизаторе RTR-L настройте динамическую трансляцию 
портов (PAT) для сети 192.168.100.0/24 в соответствующие адреса 
исходящего интерфейса
- На маршрутизаторе RTR-R настройте динамическую трансляцию 
портов (PAT) для сети 172.16.100.0/24 в соответствующие адреса 
исходящего интерфейса

**RTR-L:**

```
int gi1
ip nat outside

int gi2
ip nat inside

access-list 1 permit 192.168.100.0 0.0.0.255
ip nat inside source list 1 interface Gi1 overload
```

**RTR-R:**

```
int gi1
ip nat outside

int gi2
ip nat inside

access-list 1 permit 172.16.100.0 0.0.0.255
ip nat inside source list 1 interface Gi1 overload
```

### 2.3. Между платформами RTR-L и RTR-R должен быть установлен туннель, позволяющий осуществлять связь между регионами с применением внутренних адресов со следующими параметрами
- Используйте в качестве VTI интерфейс Tunnel1
- Между платформами должен быть установлен туннель, позволяющий осуществлять связь между регионами с применением внутренних адресов

**RTR-L**: `username webui privilege 15 password cisco` 

Далее заходим на CLI :arrow_right: Открываем браузер Microsoft Edge :arrow_right: Заходим на 7.7.7.100

В интерфейсе создаем туннель ...

**RTR-R**: `username webui privilege 15 password cisco` 

Далее заходим на CLI :arrow_right: Открываем браузер Microsoft Edge :arrow_right: Заходим на 8.8.8.100

В интерфейсе создаем туннель ...

### 2.4. Настройте динамическую маршрутизацию между платформами RTR-L и RTR-R.

**RTR-L:** 

```
router eigrp 6500
network 192.168.100.0 0.0.0.255
network 172.16.1.0 0.0.0.255
```

**RTR-R:** 

```
router eigrp 6500
network 172.16.100.0 0.0.0.255
network 172.16.1.0 0.0.0.255
```

### 2.5.Трафик, идущий по туннелю между регионами по внутренним адресам, не должен транслироваться.

<h1 align="center"> Модуль 2 </h1>

| Зона         | Тип записи | Ключ     | Значение         |
|--------------|------------|----------|-----------------|
| demo.wsr     | A          | isp      | 3.3.3.1         |
|              | A          | www      | 7.7.7.100       |
|              | A          | www      | 8.8.8.100       |
|              | CNAME      | internet | isp             |
|              |            |          |                 |
| int.demo.wsr | A          | web-l    | 192.168.100.100 |
|              | A          | web-r    | 172.16.100.100  |
|              | A          | srv      | 192.168.100.200 |
|              | A          | rtr-l    | 192.168.100.254 |
|              | A          | rtr-r    | 172.16.100.254  |
|              | CNAME      | webapp   | web-l           |
|              | CNAME      | webapp   | web-r           |
|              | CNAME      | ntp      | srv             |
|              | CNAME      | dns      | srv             |

## 1. Администрирование локальных вычислительных сетей и принятие мер по устранению возможных сбоев 

### 1.1. Сети, подключенные к ISP, считаются внешними:
- Запрещено прямое попадание трафика из внутренних сетей во внешние и наоборот;

### 1.2. Обеспечьте настройку служб SSH региона Left:

- Подключения со стороны внешних сетей по протоколу к платформе управления трафиком RTR-L на порт 2222 должны быть перенаправлены на ВМ Web-L;
- Подключения со стороны внешних сетей по протоколу к платформе управления трафиком RTR-L на порт 2244 должны быть перенаправлены на ВМ WEB-R.


**RTR-L:** 
```
ip nat inside source static tcp 192.168.100.100 22 7.7.7.100 2222

ip nat inside source static tcp 172.16.100.100 22 7.7.7.100 2244
```

### 2.1. Выполните настройку первого уровня DNS-системы стенда

- Используется ВМ ISP;
- Обслуживается зона demo.wsr.
- Наполнение зоны должно быть реализовано в соответствии с Таблицей 2;
- Сервер делегирует зону int.demo.wsr на SRV;
- Поскольку SRV находится во внутренней сети западного региона, делегирование происходит на внешний адрес маршрутизатора данного региона.
- Маршрутизатор региона должен транслировать соответствующие порты DNS-службы в порты сервера SRV.
- Внешний клиент CLI должен использовать DNS-службу, развернутую на ISP, по умолчанию;

**RTR-L:**

Пробрасываем порт на роутере для получения доступа к DNS по внешнему адресу

```
ip nat inside source static tcp 192.168.100.200 53 7.7.7.100 53

ip nat inside source static udp 192.168.100.200 53 7.7.7.100 53
```

**ISP:** 

```
apt install bind9

mkdir /opt/dns
cp /etc/bind/db.local /opt/dns/demo.db
chown -R bind:bind /opt/dns

nano /etc/apparmor.d/usr.sbin.named
```

Прописываем в файл `/opt/dns/** rw,` как на скриншоте.

![image](https://user-images.githubusercontent.com/43922329/216106902-0c1103ab-9f27-4471-a96d-704ccdb68fae.png)

Открываем файл с настройками :arrow_right: `nano /etc/bind/named.conf.options`

Здесь нужно раскомметировать и прописать следующее:

```
forwarders {
        7.7.7.100;
};
```

К тому, же сверяем и по необходимости прописываем:
```
dnssec-validation no;
listen-on-v6 { none; };
allow-query { any; };
```

![image](https://user-images.githubusercontent.com/43922329/216119749-4fe4c3b3-5d46-43a0-b580-78eb5cb481c6.png)

Открываем файл с зонами :arrow_right: `nano /etc/bind/named.conf.default-zones`

Добавляем зону demo.wsr

```
zone "demo.wsr" {
        type master;
        allow-transfer { any; };
        file "/opt/dns/demo.db";
};
```

![image](https://user-images.githubusercontent.com/43922329/216122208-6aa53fff-b063-412b-88b1-9b7ae18072f0.png)

Открываем файл с зоной demo.wsr :arrow_right: `nano /opt/dns/demo.db`

Приводим файл к следующему виду:

![image](https://user-images.githubusercontent.com/43922329/218047192-e7ad6554-c549-45d4-ba1a-38aeef00fb42.png)

Перезапускаем службы:

```
systemctl restart apparmor

systemctl restart bind9
```

### 2.2. Выполните настройку второго уровня DNS-системы стенда;
- Используется ВМ SRV;
b. Обслуживается зона int.demo.wsr;
- Наполнение зоны должно быть реализовано в соответствии с Таблицей 2;
- Обслуживаются обратные зоны для внутренних адресов регионов
- Имена для разрешения обратных записей следует брать из Таблицы 2;
- Сервер принимает рекурсивные запросы, исходящие от адресов внутренних регионов;
- Обслуживание клиентов(внешних и внутренних), обращающихся к зоне int.demo.wsr, должно производится без каких либо ограничений по адресу источника;
- Внутренние хосты регионов (равно как и платформы управления трафиком) должны использовать данную DNS-службу для разрешения всех запросов имен;

**SRV:**

Устанавливаем AD DS

![image](https://user-images.githubusercontent.com/43922329/218957073-100946ec-6933-4622-af36-810b67ab4483.png)

![image](https://user-images.githubusercontent.com/43922329/218957228-9e297f03-3899-4fc0-b5ea-3017b3790253.png)

![image](https://user-images.githubusercontent.com/43922329/218957448-d932c0ac-539e-4252-afd9-62ceb398601d.png)

![image](https://user-images.githubusercontent.com/43922329/218958308-40a471f3-1fc2-411c-bc91-9009c0ec190f.png)

![image](https://user-images.githubusercontent.com/43922329/218958733-725cbf2c-cfe7-44fd-8415-3f4d214d24fb.png)

![image](https://user-images.githubusercontent.com/43922329/218958885-bdea98ca-7c37-45c8-a463-eff1c73947cb.png)

![image](https://user-images.githubusercontent.com/43922329/218958992-a6fa73a6-8154-4ef5-814f-66c1480188b3.png)

![image](https://user-images.githubusercontent.com/43922329/218959160-45313c94-acf8-4578-a649-aa08b3895196.png)

![image](https://user-images.githubusercontent.com/43922329/218959587-814fc400-5e00-4652-bffe-08af80686381.png)


Создаем контроллер домена с зоной `int.demo.wsr` 

![image](https://user-images.githubusercontent.com/43922329/218959707-31f279e1-c95b-4546-b37d-11b91840f0e8.png)

![image](https://user-images.githubusercontent.com/43922329/218959907-3dbcef09-35f2-4ed6-b553-31968d62c0dd.png)

![image](https://user-images.githubusercontent.com/43922329/218066299-40a9d22a-c7ab-4864-925f-db47a805743e.png)

![image](https://user-images.githubusercontent.com/43922329/218960299-45fdcc92-1e0b-49e2-a0da-cbcdbd3c86dc.png)

![image](https://user-images.githubusercontent.com/43922329/218960434-e580756f-2645-4b01-a4e1-bd439508c5b2.png)

![image](https://user-images.githubusercontent.com/43922329/218960760-4f0f4b29-3b78-42cb-ad48-7a5153e5d381.png)

![image](https://user-images.githubusercontent.com/43922329/218961058-79c0d161-e600-4e8b-ae88-db695184eb66.png)

![image](https://user-images.githubusercontent.com/43922329/218961213-709e5192-8427-4d75-a934-d2bfa5aed1b6.png)

![image](https://user-images.githubusercontent.com/43922329/218961458-61ed555e-7df2-4d4f-8408-f8bd4bd5c7d6.png)


После настройки контролллера домена наполняем сервер записями в соответствии с таблицей 2.

Добавляем форвардинг на 7.7.7.1.

### 2.3. Выполните настройку первого уровня системы синхронизации времени:
- Используется сервер ISP.
- Сервер считает собственный источник времени верным, **stratum=4;**
- Сервер допускает подключение только через внешний адрес соответствующей платформы управления трафиком;
- Подразумевается обращение SRV для синхронизации времени;
- Клиент CLI должен использовать службу времени ISP;
- Выполните конфигурацию службы второго уровня времени на SRV.
- Сервер синхронизирует время с хостом ISP;
- Синхронизация с другими источникам запрещена;
- Сервер должен допускать обращения внутренних хостов регионов, в том числе и платформ управления трафиком, для синхронизации времени;
- Все внутренние хосты(в том числе и платформы управления трафиком) должны синхронизировать свое время с SRV;

**ISP:**

Устанавливаем chrony ➡️ `apt install chrony`

Открываем файл конфигурации chrony ➡️ `nano /etc/chrony/chrony.conf`

Приводим файл к следующему виду:

![image](https://user-images.githubusercontent.com/43922329/216813058-2ecc5962-4964-4f9e-aa6a-3611080d9133.png)

Перезапускаем службу chrony ➡️ `systemctl restart chrony`

**CLI:**

Синхронизируем время с NTP сервером ISP

![image](https://user-images.githubusercontent.com/43922329/216810050-99d8cec3-e6e1-4402-b12b-fe9ddc302b51.png)

![image](https://user-images.githubusercontent.com/43922329/216810060-6419ede0-7035-4b3c-8d5d-52a4593d1254.png)

![image](https://user-images.githubusercontent.com/43922329/216810053-48ace3fb-8d16-4257-bd1f-c501b0ee5c78.png)

Делаем запуск службы автоматическим

![image](https://user-images.githubusercontent.com/43922329/216810096-420a9728-5fd6-44e3-bac5-0b83629f2bd3.png)

![image](https://user-images.githubusercontent.com/43922329/216810092-47b4713f-5201-4560-8325-b25de2998f15.png)

![image](https://user-images.githubusercontent.com/43922329/216810102-d7ba2a03-f637-45c0-aa76-1e4228510273.png)

![image](https://user-images.githubusercontent.com/43922329/216810100-384fbdbc-3d75-483d-8244-b3ae1ce74c07.png)

**SRV:**

Настраиваем службу времени через Powershell ISE :arrow_right: `w32tm /config /manualpeerlist:7.7.7.1 /syncfromflags:manual /reliable:yes /update`

**WEB-L:**

Устанавливаем chrony :arrow_right: `apt install chrony`

Добавляем строчки

```
pool ntp.int.demo.wsr iburst

maxdistance 16.0
```

![image](https://user-images.githubusercontent.com/43922329/218083886-22070cbf-187a-43b1-9d64-930b322ec7f7.png)

Перезапускаем службу `systemctl restart chrony`

**WEB-R:**

Устанавливаем chrony :arrow_right: `apt install chrony`

Добавляем строчки

```
pool ntp.int.demo.wsr iburst

maxdistance 16.0
```

![image](https://user-images.githubusercontent.com/43922329/218083886-22070cbf-187a-43b1-9d64-930b322ec7f7.png)


Перезапускаем службу `systemctl restart chrony`


**RTR-L:**

```
ip domain name int.demo.wsr

ip name-server 192.168.100.200

ntp server ntp.int.demo.wsr
```

**RTR-R:**

```
ip domain name int.demo.wsr

ip name-server 192.168.100.200

ntp server ntp.int.demo.wsr
```

### 2.5. Реализуйте файловый SMB-сервер на базе SRV

- Сервер должен предоставлять доступ для обмена файлами серверам WEB-L и WEB-R;
- Сервер, в зависимости от ОС, использует следующие каталоги для хранения файлов:
        
/mnt/storage для система на базе Linux;

Диск R:\ для систем на базе Windows;

- Хранение файлов осуществляется на диске (смонтированном по указанным выше адресам), реализованном по технологии RAID типа “Зеркало”;

**SRV:**

Создаем RAID1 в менеджере дисков.

Даем ему метку R, делаем из него шару. Название даем share.

![image](https://user-images.githubusercontent.com/43922329/219453829-5912078a-54e0-4dc6-accb-ed1a0866e4e5.png)

![image](https://user-images.githubusercontent.com/43922329/219454045-7ed7142b-5a9c-4be9-b001-58be0e625382.png)

![image](https://user-images.githubusercontent.com/43922329/219454463-bb54302f-41e6-4135-8114-74d59bbddc8a.png)


Выдаем доступ на чтение и запись нужной учётке.

![image](https://user-images.githubusercontent.com/43922329/219454790-441ca3eb-32b5-4edf-96ce-f8cbf71ce78f.png)

![image](https://user-images.githubusercontent.com/43922329/219454937-e30dd3e7-f5b3-481f-b27f-4407feea6fd8.png)

![image](https://user-images.githubusercontent.com/43922329/219455428-8a591d5e-d1ec-4370-8f62-695be91bc9d0.png)

![image](https://user-images.githubusercontent.com/43922329/219455650-8e1fec73-4729-4f1b-9f61-f09ccef5b2e2.png)

### Сервера WEB-L и WEB-R должны использовать службу, настроенную на SRV, для обмена файлами между собой

**WEB-L:**

Создаем папку share :arrow_right: mkdir /opt/share


Устанавливаем cifs `apt install cifs-utils`

Создаем файл с данными учетки :arrow_right: `nano /root/.smbshare`

В файле .smbshare вводим следующие данные:

```
username=Логин учётки
password=Пароль учётки
```

Открываем файл fstab :arrow_right: `nano /etc/fstab`

Добавляем в него строку `//srv.int.demo.wsr/share /opt/share cifs user,rw,credentials=/root/.smbshare 0 0`

Монтируем шару `mount -a`

**WEB-R:**

Создаем папку share :arrow_right: mkdir /opt/share

Устанавливаем cifs `apt install cifs-utils`

Создаем файл с данными учетки :arrow_right: `nano /root/.smbshare`

В файле .smbshare вводим следующие данные:

```
username=Логин учётки
password=Пароль учётки
```

Открываем файл fstab :arrow_right: `nano /etc/fstab`

Добавляем в него строку `//srv.int.demo.wsr/share /opt/share cifs user,rw,credentials=/root/.smbshare 0 0`

Монтируем шару `mount -a`

### 2.7. Выполните настройку центра сертификации на базе SRV:
- В случае применения решения на базе Linux используется центр сертификации типа OpenSSL и располагается по адресу /var/ca;
- Выдаваемые сертификаты должны иметь срок жизни не менее 500 дней;

Параметры выдаваемых сертификатов:

- Страна RU;

- Организация DEMO.WSR;

- Прочие поля (за исключением CN) должны быть пусты;

Устанавливаем центр сертификации AD CS

![image](https://user-images.githubusercontent.com/43922329/218957073-100946ec-6933-4622-af36-810b67ab4483.png)

![image](https://user-images.githubusercontent.com/43922329/218957228-9e297f03-3899-4fc0-b5ea-3017b3790253.png)

![image](https://user-images.githubusercontent.com/43922329/218957448-d932c0ac-539e-4252-afd9-62ceb398601d.png)

![image](https://user-images.githubusercontent.com/43922329/219578243-b0bc3063-1b85-434a-a963-d4beddd1978d.png)

![image](https://user-images.githubusercontent.com/43922329/219578471-89f83286-6001-4c7b-8390-a3f93fc67a46.png)

![image](https://user-images.githubusercontent.com/43922329/219578599-0aaf2b76-ae1c-4da3-8394-00080789ef54.png)

![image](https://user-images.githubusercontent.com/43922329/219578858-95907cac-3eab-422a-85b9-a0172322094c.png)

![image](https://user-images.githubusercontent.com/43922329/219578995-46c06bed-2ce0-41cc-ad5b-58a81ec499c8.png)

![image](https://user-images.githubusercontent.com/43922329/219579091-4c7350d1-84b6-4591-9032-6caff791034b.png)

![image](https://user-images.githubusercontent.com/43922329/219579193-b5655255-c5b9-430a-afd4-feae35829c75.png)

![image](https://user-images.githubusercontent.com/43922329/219579564-66742f8b-ede4-45a2-8e12-03139f017adc.png)

Настраиваем AD CS

![image](https://user-images.githubusercontent.com/43922329/219580698-09c27a4f-eb9e-4f1a-a45c-f3576faafd85.png)

![image](https://user-images.githubusercontent.com/43922329/219580950-e301ca18-3df2-4032-8851-a29b499d517e.png)

![image](https://user-images.githubusercontent.com/43922329/219581138-d338462a-a98b-4704-8e91-5cf5e6a7a365.png)

![image](https://user-images.githubusercontent.com/43922329/219581427-e9aaa94d-41e1-4980-baca-6311ba0503ac.png)

![image](https://user-images.githubusercontent.com/43922329/219581576-6c8fab3f-bba0-4583-a2a9-c62d96a0eec6.png)

![image](https://user-images.githubusercontent.com/43922329/219581747-a201f4d3-c882-4f49-921b-e84f754ae5ce.png)

![image](https://user-images.githubusercontent.com/43922329/219582083-f8179651-1f92-4f46-9239-a69e511e0b90.png)

![image](https://user-images.githubusercontent.com/43922329/219582277-673b72b6-3eb1-4d1d-8b77-cf32d2ed3c9e.png)

![image](https://user-images.githubusercontent.com/43922329/219582437-ae26ac58-1986-4d22-9b8a-edef06b7ca7b.png)

![image](https://user-images.githubusercontent.com/43922329/219582554-1f46d3f6-8d71-4926-b819-816d2e22af2f.png)

![image](https://user-images.githubusercontent.com/43922329/219582696-87c84ce5-ece9-4c37-8862-bbcd9265ccf6.png)

![image](https://user-images.githubusercontent.com/43922329/219582813-e125bd2b-06fd-4a79-92fb-d594c9e5b518.png)

![image](https://user-images.githubusercontent.com/43922329/219580698-09c27a4f-eb9e-4f1a-a45c-f3576faafd85.png)

![image](https://user-images.githubusercontent.com/43922329/219583123-2d1845dd-bdd5-4004-8ecd-9f716a25861c.png)

![image](https://user-images.githubusercontent.com/43922329/219583236-c6e2eb10-abe9-4f78-883b-531b0bc82a43.png)

![image](https://user-images.githubusercontent.com/43922329/219583420-a7383eb4-7b75-4665-bb96-8053064fce42.png)

### Получение сертификата

![image](https://github.com/84h3p/demo2023/assets/43922329/4956ea12-f12e-4432-bc92-9309f922b9e2)

![image](https://github.com/84h3p/demo2023/assets/43922329/f5375d17-7fe2-4b84-82e8-b7d75c24c867)

![image](https://github.com/84h3p/demo2023/assets/43922329/ddcdbde8-0e55-4855-a17e-58166526189a)

![image](https://github.com/84h3p/demo2023/assets/43922329/3591b0ec-a5a3-416f-b4c0-373a6e6fb168)

![image](https://github.com/84h3p/demo2023/assets/43922329/0c746dea-a3c9-4850-8542-ff772e73308d)

![image](https://github.com/84h3p/demo2023/assets/43922329/f6bdddc2-d85f-423f-9ce4-1b662119a513)

![image](https://github.com/84h3p/demo2023/assets/43922329/79779c49-9c87-41d5-99a0-9584d9192a41)

![image](https://github.com/84h3p/demo2023/assets/43922329/23e32023-3570-492c-9dd7-5674193f48a0)

![image](https://github.com/84h3p/demo2023/assets/43922329/7d7ebc48-b1af-4aeb-93af-863a0b8b5d7b)

![image](https://github.com/84h3p/demo2023/assets/43922329/7d3dabb4-fdcb-44e0-b57a-f275bb4ac490)

![image](https://github.com/84h3p/demo2023/assets/43922329/c809a856-dc1d-41ed-a747-e33d5d854557)

![image](https://github.com/84h3p/demo2023/assets/43922329/78f4e205-6f4a-4ef4-9670-c61083c41fd1)

![image](https://github.com/84h3p/demo2023/assets/43922329/25998cc5-bf5a-4ae5-b550-c9dfb88a9cfd)

### Установка сертификатов

**WEB-L:**

`apt install -y nginx`

`cd /opt/share`

`openssl pkcs12 -nodes -nocerts -in www.pfx -out www.key`

`openssl pkcs12 -nodes -nokeys -in www.pfx -out www.cer`

`cp /opt/share/www.key /etc/nginx/www.key`

`cp /opt/share/www.cer /etc/nginx/www.cer`

`nano /etc/nginx/snippets/snakeoil.conf`

![image](https://github.com/84h3p/demo2023/assets/43922329/cfc89cbd-5d9b-45ca-9422-a1e1215ef007)

`nano /etc/nginx/sites-avaliable/default`

```
upstream backend { 
 server 192.168.100.100:8080 fail_timeout=25; 
 server 172.16.100.100:8080 fail_timeout=25; 
} 
 
server { 
    listen 443 ssl default_server; 
    include snippers/snakeoil.config;

    server_name www.demo.wsr; 

 location / { 
  proxy_pass http://backend ;
 } 
}

server { 
  listen 80  default_server; 
  server_name _; 
  return 301 https://www.demo.wsr;

}
```

![image](https://github.com/84h3p/demo2023/assets/43922329/8f01dc00-963f-4f47-95ae-7d812ca95557)

`systemctl restart nginx`

**WEB-R:**

`apt install nginx`

`cp /opt/share/www.key /etc/nginx/www.key`

`cp /opt/share/www.cer /etc/nginx/www.cer`

`nano /etc/nginx/snippets/snakeoil.conf`

![image](https://github.com/84h3p/demo2023/assets/43922329/818185f4-026e-4a77-b676-bacfd89339b0)

`nano /etc/nginx/sites-available/default`

``` 
upstream backend {
        server 192.168.100.100:8080 fail_timeout=25;
        server 172.16.100.100:8080 fail_timeout=25;
}

server {
        listen 443 ssl default_server;
        include snippets/snakeoil.conf;

        server_name www.demo.wsr;

        location / {
                proxy_pass http://backend;
        }
}

server {
        listen 80 default_server;
        server_name _;
        return 301 https://www.demo.wsr
}
```
`systemctl restart nginx`

### 3 Взаимодействие со специалистами смежного профиля при разработке методов, средств и технологий применения объектов профессиональной деятельности

...

> Спасибо за материалы:
> - https://github.com/cupespresso22/DEMO2022-2023-linux-only
> - https://angelina-bocharova.blogspot.com/p/2022.html
> - https://github.com/vladimir-shalnev/DEMO2022
