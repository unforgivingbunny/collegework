 
# Звіт з лабораторної роботи №10
**Тема:** Зміна власників і прав доступу до файлів в Linux. Спеціальні каталоги та файли в Linux.  
**Виконали:** Глядченко, Козуб 

**Мета роботи:** Отримання практичних навиків роботи з командною оболонкою Bash. Знайомство з базовими діями при зміні власників файлів, прав доступу до файлів. Знайомство з спеціальними каталогами та файлами в Linux.

---

### Хід роботи

#### 1. Таблиця вивчених команд

| Назва команди | Її призначення та функціональність |
| :--- | :--- |
| `id` | Виведення інформації про поточного користувача (UID) та його членство в групах (GID). |
| `ls -l` | Перегляд детальної інформації про файли та каталоги (власник, група, права доступу, розмір). |
| `ls -ld` | Перегляд прав доступу та власників самої директорії (а не файлів всередині неї). |
| `groups` | Виведення списку всіх груп, до яких належить вказаний користувач. |
| `newgrp` | Тимчасова зміна поточної основної групи користувача в новій оболонці (shell). |
| `touch` | Створення нового порожнього файлу або оновлення часу доступу/модифікації існуючого файлу. |
| `chown` | Зміна користувача-власника файлу або каталогу (може змінювати і групу). |
| `chgrp` | Зміна групи-власника файлу або каталогу. |
| `chmod` | Зміна прав доступу до файлу або каталогу символьним чи числовим методом. |
| `usermod` | Зміна параметрів існуючого облікового запису (наприклад, зміна первинної групи). |
| `umask` | Перегляд або встановлення маски прав доступу за замовчуванням при створенні нових файлів та каталогів. |
| `ln` | Створення жорсткого посилання (hard link) на існуючий файл. |
| `ln -s` | Створення символічного посилання (symlink/ярлика) на файл або каталог. |
| `passwd` | Зміна пароля користувача (програма зі встановленим дозволом Setuid). |
| `su` | Зміна поточного користувача в терміналі (Switch User). |
| `file` | Визначення типу файлу за його вмістом. |

#### 2. Практичні завдання у терміналі

**2.1. Створення користувачів та груп:**
*   `sudo useradd -m user1`
*   `sudo useradd -m user2`
*   `sudo useradd -m user3`
*   `sudo groupadd group`
*   `sudo usermod -aG group user1`
*   `sudo usermod -aG group user2`
> ![Скріншот 1](https://raw.githubusercontent.com/unforgivingbunny/collegework/main/os/lessons/lesson10/img/1.png)

**2.2. Робота з файлом та правами:**
*   `touch script.sh`
*   `chmod 700 script.sh` *(доступ тільки власнику)*
*   `sudo chgrp group script.sh`
*   `chmod 750 script.sh` *(власнику rwx, групі r-x, іншим заборонено)*
> ![Скріншот 2](https://raw.githubusercontent.com/unforgivingbunny/collegework/main/os/lessons/lesson10/img/2.png)

**2.3. Робота з каталогами:**
*   `mkdir dir_all && chmod 777 dir_all`
*   `mkdir dir_owner && chmod 700 dir_owner`
*   `mkdir dir_group && sudo chgrp group dir_group && chmod 750 dir_group`
> ![Скріншот 3](https://raw.githubusercontent.com/unforgivingbunny/collegework/main/os/lessons/lesson10/img/3.png)

**2.4. Експеримент з числовоми значеннями `chmod`:**
*   `touch emptyfile`
*   `chmod 000 emptyfile`
*   При використанні `chmod 4 emptyfile` система зчитує значення справа наліво (доповнюючи нулями), тобто це еквівалентно `004` (доступ на читання лише для "інших"). Значення `chmod 44` еквівалентне `044` (читання для групи та інших). Якщо вказано три цифри, система припускає, що перша цифра (спеціальні дозволи) дорівнює нулю.

**2.5. Створення каталогу з Setgid та Sticky Bit:**
*   `mkdir /tmp/shared_dir`
*   `sudo chgrp group /tmp/shared_dir`
*   `chmod 3770 /tmp/shared_dir` *(3 означає Sticky bit (1) + Setgid (2))*
> ![Скріншот 4](https://raw.githubusercontent.com/unforgivingbunny/collegework/main/os/lessons/lesson10/img/4.png)

**2.6. Створення файлів та посилань:**
*   `su user1`
*   `cd /tmp/shared_dir`
*   `touch file_user1.txt`
*   `ln file_user1.txt hard_user1`
*   `ln -s file_user1.txt sym_user1`

> ![Скріншот 5](https://raw.githubusercontent.com/unforgivingbunny/collegework/main/os/lessons/lesson10/img/5.png)

**2.7. Перевірка доступу на читання іншими користувачами:**
Заходимо під `user2` та пробуємо переглянути вміст файлу першого користувача:
*   `su user2`
*   `cd /tmp/shared_dir`
*   `cat file_user1.txt`
> *Система дозволяє переглянути файл. Це відбувається тому, що при створенні файлу стандартна маска (umask) зазвичай надає права на читання для групи та інших користувачів (наприклад, rw-r--r--).*
> ![Скріншот 6](https://raw.githubusercontent.com/unforgivingbunny/collegework/main/os/lessons/lesson10/img/6.png)

**2.8. Перевірка доступу на видалення та фінальні висновки:**
Залишаючись в обліковому записі `user2`, пробуємо видалити файл, який належить `user1`:
*   `rm file_user1.txt`
Система блокує дію та видає повідомлення "Operation not permitted" (Операція заборонена).
> ![Скріншот 7](https://raw.githubusercontent.com/unforgivingbunny/collegework/main/os/lessons/lesson10/img/7.png)

**Висновки щодо видалення файлів:** 
Хоча користувачі `user1` та `user2` належать до однієї групи, яка є власником каталогу, `user2` не може видалити файл першого користувача. Це зумовлено тим, що на каталог `/tmp/shared_dir` встановлено спеціальний дозвіл "липкий біт" (Sticky Bit). Цей механізм гарантує, що видалити або перейменувати файл у спільному каталозі може виключно його безпосередній творець-власник або суперкористувач root.

---

### Conclusion
During this laboratory work, I acquired practical skills in managing file ownership and permissions using the Bash shell. I learned how Linux associates ownership with UIDs and GIDs and successfully applied commands such as `chmod`, `chown`, and `chgrp`. Furthermore, I explored advanced security concepts including Setuid, Setgid, and the Sticky Bit, understanding their critical role in collaborative environments and secure system administration.