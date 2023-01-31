# demo2023

![image](https://user-images.githubusercontent.com/43922329/215776915-998af6f2-cd79-420e-b8cb-e678c4c3e730.png)

![image](https://user-images.githubusercontent.com/43922329/215781746-9b61b071-a8cd-4781-b8c6-8f12de1b683d.png)


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

...

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


:green_circle: Set Network Adapter Address

:green_circle: Static IP

:green_circle: Static IP address: `192.168.100.200`

:green_circle: Subnet mask: `255.255.255.0`

:green_circle: Default gateway: `192.168.100.254`

**WEB-L:** 

```
apt install network-manager

nmtui
```

![image](https://user-images.githubusercontent.com/43922329/215789388-3ce2bb0f-1c0e-4e36-8687-c93712f9610b.png)

![image](https://user-images.githubusercontent.com/43922329/215789964-160e29e1-29d2-4060-94ed-1ad08a7ecb64.png)

**WEB-R:**








