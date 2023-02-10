# demo2023 | work in progress..

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


# Модуль 1

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

# Модуль 2

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
        file "/opt/dns/demo.db"
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

...

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

В Powershell ISE пишим: `w32tm /config /manualpeerlist:7.7.7.1 /syncfromflags:manual /reliable:yes /update`

**WEB-L:**

Устанавливаем chrony :arrow_right: `apt install chrony`

Добавляем строку `pool ntp.int.demo.wsr iburst`

Перезапускаем службу `systemctl restart chrony`

**WEB-R:**

Устанавливаем chrony :arrow_right: `apt install chrony`

Добавляем строку `pool ntp.int.demo.wsr iburst`

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

Выдаем доступ на чтение и запись нужной учётке.

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

> Спасибо за материалы:
> - https://github.com/cupespresso22/DEMO2022-2023-linux-only
> - https://angelina-bocharova.blogspot.com/p/2022.html
> - https://github.com/vladimir-shalnev/DEMO2022
