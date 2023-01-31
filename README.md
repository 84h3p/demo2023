# demo2023 | work in progress..

![image](https://user-images.githubusercontent.com/43922329/215776915-998af6f2-cd79-420e-b8cb-e678c4c3e730.png)

![image](https://user-images.githubusercontent.com/43922329/215781746-9b61b071-a8cd-4781-b8c6-8f12de1b683d.png)

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


![image](https://user-images.githubusercontent.com/43922329/215805161-d17d90e7-f9de-4b87-91fa-691bfdc3a06f.png)

**WEB-R:**

```
apt install network-manager

nmtui
```
![image](https://user-images.githubusercontent.com/43922329/215789388-3ce2bb0f-1c0e-4e36-8687-c93712f9610b.png)

![image](https://user-images.githubusercontent.com/43922329/215805318-5d0675f9-ac58-48a1-bb63-ab20d5b53ea4.png)

![image](https://user-images.githubusercontent.com/43922329/215804986-ed9892b0-586d-47d0-9ad0-d62c12295277.png)

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

**ISP:** `nano /etc/sysctl.conf` 

Теперь нужно раскоменнтировать строку `net.ipv4.ip_forward=1`

## 2.1. Настройте статический маршрут по умолчанию на маршрутизаторах RTR-L и RTR-R

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

> Спасибо за материалы 
> - https://github.com/cupespresso22/DEMO2022-2023-linux-only
> - https://angelina-bocharova.blogspot.com/p/2022.html
