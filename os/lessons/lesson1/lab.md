# Лабораторна робота №1  
**Дисципліна:** Операційні системи  
**Тема:** “Знайомство з робочим середовищем віртуальних машин та особливостями операційної системи Linux”  
**Виконали:** Глядченко, Козуб 

---

## Мета роботи
1. Знайомство з гіпервізорами різного типу, віртуалізацією при роботі з операційними системами.  
2. Знайомство з основними видами сучасних ОС, короткий огляд їх можливостей.

---

## Glossary of terms — словник термінів

- **Virtual machine (VM)** — a software-based computer inside a real one.  

- **Virtualization** — running multiple systems on one physical machine.  

- **Hypervisor** — software that creates and manages virtual machines.  

- **Host operating system (Host OS)** — the main operating system of a computer.  

- **Guest operating system (Guest OS)** — an operating system running inside a virtual machine.  

- **Kernel** — the core part of an operating system.  

- **Linux kernel** — the core of the Linux operating system.  

- **Distribution (distro)** — a complete Linux system with software and tools.  

- **Open source** — software with freely available and modifiable source code.  

- **Command Line Interface (CLI)** — a text-based way to control a computer.  

- **Graphical User Interface (GUI)** — a visual interface with windows and icons.  

- **Operating system (OS)** — software that manages hardware and programs.  

- **Java Virtual Machine (JVM)** — a virtual machine that runs Java programs.  

---

## Відповіді на питання

### 1. Етапи розгортання ОС у VirtualBox
1. Встановити VirtualBox.  
2. Створити нову віртуальну машину.  
3. Обрати тип і версію ОС.  
4. Виділити оперативну пам’ять (RAM).  
5. Створити віртуальний жорсткий диск.  
6. Підключити ISO-образ ОС.  
7. Запустити VM та встановити ОС.  

---

### 2. Апаратні обмеження для 32- та 64-бітних ОС

**32-bit ОС:**
- працює на 32- і 64-бітних процесорах  
- максимум 4 ГБ RAM  

**64-bit ОС:**
- потребує 64-бітний процесор  
- обов’язкова підтримка віртуалізації (Intel VT-x / AMD-V)  
- дозволяє використовувати більше 4 ГБ RAM  

---

### 3. Основні етапи встановлення Linux в текстовому режимі
1. Завантаження з ISO-образу  
2. Вибір мови та клавіатури  
3. Налаштування мережі(можна і без цього, але краще підключити для нових версій пакетів) 
4. Розмітка диска  
5. Встановлення системи

---

### 4. Встановлення GNOME та KDE в Linux

**Ubuntu:**
sudo apt update

sudo apt install ubuntu-gnome-desktop

sudo apt install kubuntu-desktop

**Fedora:**

sudo dnf groupinstall "GNOME Desktop"

sudo dnf groupinstall "KDE Plasma Workspaces"

### 5. Характеристика графічних інтерфейсів Глядченко 4-й варіант (KDE, Fluxbox):
**KDE Plasma** — це сучасне, потужне та дуже гнучке графічне середовище для Linux.

Основні характеристики - привабливий, сучасний інтерфейс, дуже широкі можливості налаштування, підтримка віджетів, тем, ефектів, зручний для користувачів Windows.

**Fluxbox** — це легке, швидке та мінімалістичне графічне середовище.

Основні характеристики - дуже низьке споживання ресурсів, висока швидкість роботи, мінімалістичний дизайн, орієнтований на досвідчених користувачів, конфігурується через текстові файли
