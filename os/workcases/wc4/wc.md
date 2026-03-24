# Work-case №4
## Виконали: Глядченко, Козуб 

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
```

```bash
# Встановлення бібліотек
pip install numpy pandas requests
```

![скріншот 12](https://github.com/unforgivingbunny/collegework/raw/main/os/workcases/wc4/img/12.png)
