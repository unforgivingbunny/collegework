# Лабораторна робота №2
**Дисципліна:** Операційні системи  
**Тема:** “Знайомство з інтерфейсом та можливостями ОС Linux”  
**Виконали:** Глядченко, Козуб 

---

## Мета роботи

Знайомство з інтерфейсами ОС Linux. Отримання практичних навиків роботи в середовищах ОС Linux та мобільної ОС – їх графічною оболонкою, входом і виходом з системи, ознайомлення зі структурою робочого столу, вивчення основних дій та налаштувань при роботі в системі

---

## Словник термінів

*   **Kernel**  
    The core of an operating system. It manages communication between hardware and software, allocating resources like memory and CPU time to running programs.

*   **Command Line Interface (CLI)**  
    A text-based interface where users type commands to interact with the system directly. It provides more control than a graphical interface.

*   **Terminal (GUI Terminal)**  
    A program that runs inside a graphical environment and emulates a command line, allowing users to access the CLI without leaving the desktop.

*   **Virtual Terminal**  
    A text-based console accessed outside the GUI (using `Ctrl+Alt+F1`...`F6`). It requires a separate login and provides a full-screen CLI session.

*   **Process**  
    An instance of a program that is currently running and being managed by the kernel. The kernel tracks all processes and their resource usage.

*   **Multitasking**  
    The ability of an operating system to run multiple processes simultaneously by quickly switching between them, giving the illusion of parallelism.

*   **Distribution (Distro)**  
    A complete operating system built from the Linux kernel, together with a collection of software applications and a package manager. Examples: Ubuntu, Fedora.

*   **Package Manager**  
    A tool that automates installing, updating, and removing software. It handles dependencies to ensure all required components are present.

---

## Хід роботи

### Робота в ОС Linux (Ubuntu + GNOME)

**Обрана ОС:** Ubuntu (графічна оболонка GNOME)

**Опис робочого простору GNOME:**
Робочий стіл складається з верхньої панелі (годинник, індикатори, меню користувача) та меню "Activites", яке викликається кнопкою в лівому верхньому куті.

![Загальний вигляд](https://github.com/unforgivingbunny/collegework/blob/main/os/lessons/lesson2/img/image1.png)

**Способи запуску програм:**

1.  **Через панель швидкого запуску (Dash):** У меню Activities клікнути на іконку програми на лівій панелі.

![Dash](https://github.com/unforgivingbunny/collegework/blob/main/os/lessons/lesson2/img/image2.png)

2.  **Через пошук:** Відкрити Activities, почати вводити назву ("Firefox"), клікнути на іконку в результатах.

![Пошук](https://github.com/unforgivingbunny/collegework/blob/main/os/lessons/lesson2/img/image3.png)

**Вихід з системи та завершення роботи:**

1.  **Зміна користувача:** Клікнути на меню користувача (правий верхній кут) -> **Switch User**.
2.  **Перезавантаження:** Меню користувача -> кнопка живлення -> **Restart**.
3.  **Вимкнення:** Меню користувача -> кнопка живлення -> **Power Off**.

![SwitchUser](https://github.com/unforgivingbunny/collegework/blob/main/os/lessons/lesson2/img/image4.png)
![Restart](https://github.com/unforgivingbunny/collegework/blob/main/os/lessons/lesson2/img/image5.png)
![PowerOff](https://github.com/unforgivingbunny/collegework/blob/main/os/lessons/lesson2/img/image6.png)

---

### Робота в мобільній ОС (Nothing OS)

**Мобільна ОС:** Nothing OS (на базі Android)

**Опис інтерфейсу:**
Nothing OS має мінімалістичний дизайн, монохромні іконки та власні віджети.

1.  **Головний екран та меню додатків:**
    На головному екрані розташовані віджети та папки. Меню всіх додатків викликається свайпом вгору.

![Home](https://github.com/unforgivingbunny/collegework/blob/main/os/lessons/lesson2/img/NOS4.jpg)
![Menu](https://github.com/unforgivingbunny/collegework/blob/main/os/lessons/lesson2/img/NOS3.jpg)

2.  **Налаштування:**
    Меню налаштувань містить розділи: "Підключення", "Звук", "Дисплей", "Акумулятор".

![QSettings](https://github.com/unforgivingbunny/collegework/blob/main/os/lessons/lesson2/img/NOS2.jpg)
![Settings](https://github.com/unforgivingbunny/collegework/blob/main/os/lessons/lesson2/img/NOS1.jpg)

і тут

    Скріншот головного меню "Налаштування".

3.  **Комбінації клавіш:**
    *   **Живлення + Гучність (-)**: Скріншот.
    *   **Подвійне натискання живлення**: Швидкий запуск камери.

4.  **Вимкнення:**
    Одночасне натискання кнопки живлення та гучності викликає меню "Вимкнути" або "Перезавантажити".

---

## Відповіді на контрольні запитання

## 1. Серверні додатки Linux
* **Сервери баз даних:** PostgreSQL, MySQL, MariaDB, MongoDB, Redis.
* **Сервери розсилки повідомлень:** * *Електронна пошта:* Postfix, Exim, Sendmail, Dovecot.
  * *Брокери повідомлень (Message Brokers):* RabbitMQ, Apache Kafka, Mosquitto (MQTT).
* **Файлообмінники:** Samba (для обміну з Windows), NFS (для UNIX-систем), vsftpd / ProFTPD (FTP-сервери), Nextcloud / ownCloud (хмарні файлові сховища).

---

## 2. Порівняння командних оболонок (Shells)
* **Bourne shell (sh):** Історично перша стандартна оболонка UNIX. Дуже базова, надійна для написання скриптів, але не має зручних функцій для інтерактивної роботи (наприклад, історії команд чи автодоповнення).
* **C shell (csh):** Синтаксис нагадує мову програмування C. Має кращі інтерактивні можливості, ніж базова `sh`, але вважається менш зручною для написання складних скриптів.
* **Bourne Again shell (Bash):** Найпопулярніша оболонка, стандарт за замовчуванням у більшості дистрибутивів Linux. Сумісна з `sh`, але має розширені можливості: історію команд, автодоповнення, роботу з масивами тощо.
* **tcsh:** Розширена та вдосконалена версія `csh` з кращим редагуванням командного рядка та автодоповненням.
* **Korn shell (Ksh):** Поєднує зворотну сумісність з `sh` та інтерактивні зручності `csh`. Працює дуже швидко, часто є стандартом у комерційних UNIX-системах (наприклад, AIX).
* **zsh (Z shell):** Сучасна, потужна оболонка, що увібрала найкраще з Bash, ksh та tcsh. Відрізняється надзвичайно гнучким автодоповненням, перевіркою орфографії та підтримкою тем (через фреймворки типу Oh My Zsh).

---

## 3. Менеджери пакетів
**Для чого потрібні:** Вони автоматизують процеси встановлення, оновлення, налаштування та видалення програмного забезпечення. Головна їхня перевага — автоматичне вирішення залежностей (завантаження додаткових бібліотек, необхідних для роботи програми).

**Популярні менеджери у Linux:**
* **APT** (Advanced Package Tool): Використовується в Debian, Ubuntu, Linux Mint.
* **DNF / YUM**: Використовуються в Red Hat (RHEL), CentOS, Fedora.
* **Pacman**: Стандарт для Arch Linux та Manjaro.
* **Zypper**: Використовується в openSUSE.

---

## 4. Засоби безпеки в Linux
* **Система прав доступу (Permissions):** Розподіл прав на читання, запис та виконання (rwx) для власника, групи та інших користувачів.
* **Примусовий контроль доступу (MAC):** SELinux або AppArmor, які обмежують можливості програм, навіть якщо вони запущені з правами адміністратора.
* **Міжмережеві екрани (Firewalls):** iptables, nftables, ufw для контролю мережевого трафіку.
* **PAM (Pluggable Authentication Modules):** Гнучка система автентифікації користувачів.
* **SSH (Secure Shell):** Протокол для безпечного, зашифрованого віддаленого керування системою.

---

## 5. Чому віртуалізація стала актуальною
Віртуалізація дозволяє запускати кілька ізольованих операційних систем (віртуальних машин) на одному фізичному сервері. Її актуальність зумовлена:
* **Економією ресурсів та коштів:** Сервери використовуються на 100%, замість простоювання.
* **Ізоляцією:** Збій однієї віртуальної машини не впливає на інші.
* **Гнучкістю:** Можливість швидко створювати резервні копії (сніпшоти) та мігрувати сервери між фізичним обладнанням без зупинки роботи.

---

## 6. Поняття контейнеризації
**Контейнеризація** — це легка альтернатива віртуалізації на рівні операційної системи. Замість того, щоб емулювати цілу ОС з власним ядром, контейнери використовують спільне ядро хост-системи, але ізолюють процеси, файлову систему та мережу додатку.
* *Приклади:* Docker, Podman.
* *Переваги:* Запускаються за секунди, споживають мінімум пам'яті, гарантують, що додаток працюватиме однаково на комп'ютері розробника і на сервері.

---

## 7. Переваги та недоліки Open Source (відкритого ПЗ)
| Переваги | Недоліки |
| :--- | :--- |
| **Безкоштовність:** Зниження витрат на ліцензії. | **Підтримка:** Часто відсутня офіційна цілодобова підтримка (якщо не купувати комерційні версії). |
| **Прозорість та безпека:** Код може перевірити будь-хто, що пришвидшує пошук вразливостей. | **Фрагментація:** Велика кількість версій та дистрибутивів може заплутати новачків. |
| **Незалежність від вендора:** Ви не прив'язані до політики однієї корпорації. | **Крива навчання:** Деякі інструменти вимагають глибоких технічних знань для налаштування. |

---

## 8. Віртуальні консолі (термінали) та перемикання
* **Кількість:** За замовчуванням у більшості дистрибутивів Linux працює **6 активних текстових віртуальних консолей** (від `tty1` до `tty6`).
* **Як викликати/перемикати:** Використовується комбінація клавіш `Ctrl + Alt + F1` ... `F6`. 
* *Приклад:* Якщо у вас зависло графічне середовище, ви можете натиснути `Ctrl + Alt + F3`, перейти в третій текстовий термінал, залогінитись і вбити завислий процес.

---

## 9. Яка консоль виконує функцію графічної оболонки?
Історично графічна оболонка (X Server) запускається на **7-й віртуальній консолі (`tty7`)**. Щоб повернутися до неї з текстового режиму, потрібно натиснути `Ctrl + Alt + F7`. 
*(Примітка: У сучасних дистрибутивах з systemd та дисплейним сервером Wayland графіка часто працює на `tty1` або `tty2`)*.

---

## 10. Реєстрація декілька разів під одним ім’ям
Так, **це абсолютно можливо** і є стандартною поведінкою Linux. Ви можете одночасно увійти в систему як користувач `user` на `tty1`, `tty2`, а також відкрити кілька віддалених SSH-сесій.


### Висновки

During this laboratory work, we successfully familiarized ourselves with the graphical user interface of the Linux operating system, specifically using the GNOME desktop environment in Ubuntu. We acquired practical skills in navigating the workspace, launching applications using various methods, and managing system sessions.

Additionally, we explored the interface and basic configuration of a mobile operating system (Nothing OS), analyzing its desktop structure, hardware shortcuts, and power management features.

Through the theoretical preparation and control questions, we deepened our understanding of core Linux concepts, including the Command Line Interface (CLI), virtual terminals, package managers, system security, and the fundamental differences between virtualization and containerization. Overall, this lab provided a solid practical and theoretical foundation for further work within Linux environments.