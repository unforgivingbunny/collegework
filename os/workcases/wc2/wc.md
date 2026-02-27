# Work-case №2
## Виконали: Глядченко, Козуб 

## Glossary

* Virtual Machine (VM) – A software-based emulation of a physical computer that runs an operating system and applications independently from the host system.
* Type 2 Hypervisor – A virtualization platform that runs on top of an existing operating system and allows multiple virtual machines to operate simultaneously.
* Bridged Networking – A network configuration mode in which a virtual machine connects directly to the physical network through the host’s network adapter and appears as a separate device.
* Command Line Interface (CLI) – A text-based interface that allows users to interact with the operating system by typing commands.
* Desktop Environment (DE) – A graphical user interface layer that provides windows, panels, icons, and system tools for user interaction.
* USB Passthrough – A feature that enables a USB device connected to the host machine to be directly accessed by a virtual machine.

## 1. Встановлення гіпервізора

Для виконання роботи було використано гіпервізор ІІ типу Oracle VM VirtualBox.

![Головне вікно VirtualBox](https://raw.githubusercontent.com/unforgivingbunny/collegework/main/os/workcases/wc2/img/01_VirtualBox_Main.jpg)

## 2. Базові дії в гіпервізорі (перша ВМ)

### Створення та налаштування
Було створено віртуальну машину **Ubuntu_Desktop_1**. Для неї виділено 4 ГБ оперативної пам’яті, 2 ядра процесора та 25 ГБ дискового простору, що забезпечує стабільну роботу системи.

![Налаштування ВМ](https://raw.githubusercontent.com/unforgivingbunny/collegework/main/os/workcases/wc2/img/02_VM_Settings.jpg)

### Мережа
Налаштовано режим «Мережевий міст» (Bridged Adapter), завдяки чому віртуальна машина отримує доступ до локальної мережі як окремий пристрій.

![Тип мережі](https://raw.githubusercontent.com/unforgivingbunny/collegework/main/os/workcases/wc2/img/03_Network_Type.jpg)
![Мережевий міст](https://raw.githubusercontent.com/unforgivingbunny/collegework/main/os/workcases/wc2/img/04_Network_Bridged.jpg)

### Зовнішні носії
Було активовано контролер USB 3.0 (xHCI) та додано фільтр для автоматичного підключення накопичувача TOSHIBA USB FLASH DRIVE.

![USB Накопичувач](https://raw.githubusercontent.com/unforgivingbunny/collegework/main/os/workcases/wc2/img/05_USB_Flash.jpg)

## 3. Встановлення GNU/Linux (графічна конфігурація)

Було встановлено **Ubuntu Desktop 25.10** зі стандартним графічним середовищем. Після завершення інсталяції система була готова до повноцінної роботи в GUI-режимі.

![Встановлення Ubuntu](https://raw.githubusercontent.com/unforgivingbunny/collegework/main/os/workcases/wc2/img/06_Ubuntu_Install.jpg)
![Робочий стіл Ubuntu](https://raw.githubusercontent.com/unforgivingbunny/collegework/main/os/workcases/wc2/img/07_Ubuntu_Desktop.jpg)

## 4. Робота з другою ВМ (CLI та GUI)

### Мінімальна конфігурація
На другій віртуальній машині було встановлено **Ubuntu Server**, що передбачає роботу виключно через інтерфейс командного рядка (CLI).

![Server CLI](https://raw.githubusercontent.com/unforgivingbunny/collegework/main/os/workcases/wc2/img/08_Server_CLI.jpg)

### Встановлення GNOME
Додатково встановлено графічне середовище GNOME (`sudo apt install ubuntu-desktop`), що забезпечило доступ до повноцінного графічного інтерфейсу.

![Server GNOME](https://raw.githubusercontent.com/unforgivingbunny/collegework/main/os/workcases/wc2/img/09_Server_GNOME.jpg)

### Встановлення XFCE
Також було встановлено альтернативну оболонку XFCE (`sudo apt install xfce4`).

![Server XFCE](https://raw.githubusercontent.com/unforgivingbunny/collegework/main/os/workcases/wc2/img/10_Server_XFCE.jpg)

### Порівняння GNOME та XFCE
* **GNOME** — сучасне та функціонально насичене середовище з розширеними можливостями пошуку й керування вікнами, однак воно споживає більше системних ресурсів.
* **XFCE** — легковагове та мінімалістичне середовище, що забезпечує швидку роботу навіть за обмежених ресурсів, особливо у віртуальному середовищі.

## Conclusion

During this work-case, Oracle VM VirtualBox was deployed and two virtual machines were configured. Hardware resources, bridged networking, and USB passthrough were successfully set up. Ubuntu Desktop 25.10 was installed as a primary GUI-based system, while Ubuntu Server was deployed as a CLI-oriented environment. After installing both GNOME and XFCE desktop environments on the server instance, it was determined that XFCE provides significantly better performance and lower resource consumption, whereas GNOME offers a more modern and feature-rich user experience at the cost of higher system requirements.
