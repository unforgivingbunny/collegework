# Work-case №4
## Виконали: Глядченко, Козуб 

# Glossary of Terms

- **Package:** A compressed archive file containing all the necessary files, metadata, and instructions to install, configure, or remove a specific software application.
- **Repository (Repo):** A centralized storage location (usually a server on the internet) hosting software packages, structured so that a package manager can easily search, retrieve, and install them.
- **Package Manager:** A software tool that automates the process of installing, upgrading, configuring, resolving dependencies, and removing computer programs in a consistent manner.
- **Dependency:** A distinct piece of software (such as a system library) that another program requires in order to be installed and function correctly.
- **GUI (Graphical User Interface):** A visual way of interacting with a computer using items such as windows, icons, and menus.
- **Terminal (CLI):** A text-based interface used to interact with the operating system by typing and executing commands directly.

---

# 1 Визначення та огляд менеджерів пакетів

## Основні поняття

- **Пакет (Package):** Це стиснений архів, який містить скомпільовані файли програми, конфігураційні файли, а також метадані та скрипти, необхідні для коректного встановлення та видалення програми в системі.

- **Репозиторій (Repository):** Це спеціальне централізоване сховище, де зберігаються та підтримуються пакети програмного забезпечення. Менеджери пакетів завантажують звідси програми для безпечного встановлення.

## Огляд існуючих менеджерів пакетів у Linux

### APT (Advanced Package Tool)

- **Використовується в:** дистрибутивах на базі Debian (Ubuntu, Linux Mint)
- **Формат пакетів:** `.deb`
- **Можливості:** автоматичне вирішення залежностей, зручне масове оновлення системи, величезна кількість доступних репозиторіїв

### DNF (Dandified YUM)

- **Використовується в:** Fedora, RHEL, CentOS
- **Формат пакетів:** `.rpm`
- **Можливості:** швидка робота, оптимізоване споживання пам'яті, строгий алгоритм вирішення залежностей

### Pacman

- **Використовується в:** Arch Linux та його похідних
- **Можливості:** висока швидкість роботи, максимальна простота конфігурації, підтримка концепції "плаваючого релізу" (rolling release)

### Snap та Flatpak

- **Використовується в:** незалежно від дистрибутива (універсальні менеджери пакетів)
- **Можливості:** встановлення програм у безпечній "пісочниці", вирішення проблеми конфлікту версій бібліотек, оскільки пакет вже містить всі необхідні залежності

# 2. Робота з менеджером пакетів

## Інформація про систему
* Мій дистрибутив: **Fedora Workstation 43**
* Менеджер пакетів: **DNF (Dandified YUM)**

## 2.1. Пошук, скачування та установка пакетів

### Основні команди DNF

```bash
# Оновлення списку доступних пакетів з усіх репозиторіїв
sudo dnf update
sudo dnf check-update  # Перевірка оновлень без встановлення

# Пошук пакета за назвою або описом
dnf search firefox
dnf search "video editor"
dnf search all vlc  # Розширений пошук

# Перегляд детальної інформації про пакет
dnf info vlc
dnf info gimp

# Встановлення пакета зі сховища за замовчуванням
sudo dnf install vlc
sudo dnf install git curl wget -y  # -y для автоматичного підтвердження

# Встановлення пакета з конкретної версії
sudo dnf install package-name-1.2.3-4

# Завантаження пакета без встановлення
dnf download vlc

# Встановлення локального .rpm файлу
sudo dnf install ./package.rpm
# або
sudo rpm -ivh package.rpm  # Класичний спосіб
```

![скріншот 1](https://github.com/unforgivingbunny/collegework/raw/main/os/workcases/wc4/img/1.png)

![скріншот 2](https://github.com/unforgivingbunny/collegework/raw/main/os/workcases/wc4/img/2.png)

### Додавання нового репозиторію

```bash
# Додавання COPR репозиторію (аналог PPA в Ubuntu)
sudo dnf copr enable user/project
sudo dnf install package-name

# Додавання репозиторію через .repo файл
sudo dnf config-manager --add-repo https://example.com/repo.repo
```

## 2.2. Перегляд інформації про пакети

```bash
# Список всіх встановлених пакетів
dnf list --installed
dnf list --installed | wc -l  # Підрахунок кількості

# Список доступних пакетів у репозиторіях
dnf list --available

# Пошук конкретного встановленого пакета
dnf list --installed | grep python3
rpm -qa | grep python3  # Альтернативний спосіб (rpm)

# Показати версію та джерело пакета
dnf info firefox
dnf list firefox

# Групи пакетів (метапакети)
dnf group list
dnf group info "Development Tools"

# Залежності пакета
dnf repoquery --requires vlc
dnf repoquery --whatrequires python3  # Зворотні залежності

# Інформація про пакунок через rpm
rpm -qi firefox  # Детальна інформація
rpm -ql firefox  # Список файлів пакета
rpm -qc firefox  # Конфігураційні файли
```

![скріншот 3](https://github.com/unforgivingbunny/collegework/raw/main/os/workcases/wc4/img/3.png)

![скріншот 4](https://github.com/unforgivingbunny/collegework/raw/main/os/workcases/wc4/img/4.png)

## 2.3. Видалення пакетів

```bash
# Видалення пакета (конфігураційні файли залишаються)
sudo dnf remove firefox
sudo dnf remove firefox thunderbird  # Видалення декількох пакетів

# Повне видалення з залежностями
sudo dnf autoremove firefox  # Видаляє пакет та непотрібні залежності

# Видалення непотрібних пакетів-залежностей
sudo dnf autoremove

# Очищення кешу завантажених пакетів
sudo dnf clean all
sudo dnf clean packages  # Тільки пакети
sudo dnf clean dbcache   # Тільки кеш бази даних
```

![скріншот 5](https://github.com/unforgivingbunny/collegework/raw/main/os/workcases/wc4/img/5.png)

## 2.4. Оновлення системи та менеджера пакетів

```bash
# Оновлення списку пакетів та встановлення оновлень
sudo dnf update

# Перевірка наявності оновлень (без встановлення)
sudo dnf check-update

# Оновлення конкретного пакета
sudo dnf update firefox

# Повне оновлення системи (включаючи ядро)
sudo dnf upgrade --refresh

# Оновлення менеджера пакетів DNF
sudo dnf update dnf

# Оновлення версії дистрибутиву (наприклад, Fedora 40 -> 41)
sudo dnf system-upgrade download --releasever=41
sudo dnf system-upgrade reboot
```

![скріншот 6](https://github.com/unforgivingbunny/collegework/raw/main/os/workcases/wc4/img/6.png)

---

# 3. Практичне встановлення програм

## 3.1. Встановлення відеоплеєра

Я вибрав **VLC Media Player** — універсальний медіаплеєр з підтримкою всіх форматів.

```bash
sudo dnf install vlc
```

![скріншот 7](https://github.com/unforgivingbunny/collegework/raw/main/os/workcases/wc4/img/7.png)

![скріншот 8](https://github.com/unforgivingbunny/collegework/raw/main/os/workcases/wc4/img/8.png)

![скріншот 9](https://github.com/unforgivingbunny/collegework/raw/main/os/workcases/wc4/img/9.png)

## 3.2. Встановлення середовища для мови програмування

```bash
# Встановлення Python та інструментів
sudo dnf install python3 python3-pip python3-virtualenv python3-devel -y
```

![скріншот 10](https://github.com/unforgivingbunny/collegework/raw/main/os/workcases/wc4/img/10.png)

```bash
# Перевірка версій
python3 --version
pip3 --version
```

![скріншот 11](https://github.com/unforgivingbunny/collegework/raw/main/os/workcases/wc4/img/11.png)

```bash
# Створення віртуального середовища
mkdir ~/python_project && cd ~/python_project
python3 -m venv venv
source venv/bin/activate
```a

```bash
# Встановлення бібліотек
pip install numpy pandas requests
```

![скріншот 12](https://github.com/unforgivingbunny/collegework/raw/main/os/workcases/wc4/img/12.png)

# 4. Встановлення програм у графічному середовищі (GUI)

У сучасних графічних середовищах (наприклад, GNOME, XFCE) встановлення програм часто відбувається за допомогою вбудованих "магазинів додатків" або графічних оболонок для системних менеджерів пакетів. Це дозволяє користувачам встановлювати софт в один клік, подібно до смартфонів.

## Методика встановлення через магазин додатків (на прикладі GNOME Software)

1. Відкрити графічний додаток **Ubuntu Software**.
2. Використати рядок пошуку для знаходження потрібної програми.
3. Перейти на сторінку програми та натиснути кнопку **"Install"**.
4. Ввести пароль адміністратора системи для підтвердження дії.
5. Дочекатися автоматичного завантаження та встановлення пакета.

## Методика встановлення через графічний менеджер пакетів

1. Запустити **Synaptic Package Manager**.
2. Натиснути кнопку **"Search"** та ввести назву програми (наприклад, `gimp`).
3. Клікнути правою кнопкою миші на знайдений пакет і вибрати **"Mark for Installation"**. Менеджер автоматично відмітить всі додаткові залежності, необхідні для роботи програми.
4. Натиснути кнопку **"Apply"** на верхній панелі інструментів для початку завантаження та встановлення.

# Conclusion

Understanding package management is a fundamental skill for Linux system administration. During this work-case, the core concepts of packages, dependencies, and software repositories were established. Various package managers, such as **APT**, **DNF**, and **Pacman**, were analyzed, highlighting their distinct features and corresponding distributions. Furthermore, the practical methods of installing software through graphical user interfaces — using both user-friendly App Stores and advanced graphical package managers like **Synaptic** — were explored. This demonstrates that modern Linux systems provide both robust command-line tools and intuitive visual options for efficient software management.