# Work-case №8
## Виконали: Глядченко, Козуб 

### Glossary  
*   CLI (Command Line Interface) - Інтерфейс командного рядка  
*   Package Manager - Менеджер пакетів (інструмент для встановлення програм)  
*   Terminal emulator - Емулятор терміналу  
*   Text editor - Текстовий редактор  
*   System monitor - Системний монітор (диспетчер задач)

---

### Завдання 1. Аналоги графічних програм у терміналі  

**1. Перегляд файлів та папок через файловий менеджер у терміналі.**  
Для цього завдання було обрано Midnight Commander (пакет `mc`). Це популярний двопанельний файловий менеджер, який дозволяє зручно копіювати, переміщувати та редагувати файли без мишки.  
*   **Команда встановлення:** `sudo apt install mc`  
*   **Команда запуску:** `mc`  
![скріншот 1](https://github.com/unforgivingbunny/collegework/raw/main/os/workcases/wc8/img/1.png)

**2. Перегляд веб-сторінок через браузер, що працює у терміналі.**  
Використано консольний браузер `lynx`.  
*   **Команда встановлення:** `sudo apt install lynx`  
*   **Команда запуску:** `lynx uk.wikipedia.org`  
![скріншот 2](https://github.com/unforgivingbunny/collegework/raw/main/os/workcases/wc8/img/2.png)

**3. Перегляд електронної пошти в терміналі.**  
Використано поштовий клієнт `mutt`.  
*   **Команда встановлення:** `sudo apt install mutt`  
*   **Команда запуску:** `mutt`  
![скріншот 3](https://github.com/unforgivingbunny/collegework/raw/main/os/workcases/wc8/img/3.png)

**4. Слухати музику через термінал.**  
Для відтворення аудіо використано консольний плеєр `cmus`.  
*   **Команда встановлення:** `sudo apt install cmus`  
*   **Команда запуску:** `cmus`  
![скріншот 4](https://github.com/unforgivingbunny/collegework/raw/main/os/workcases/wc8/img/4.png)

**5. Скачувати торенти через термінал.**  
Використано консольний BitTorrent-клієнт `rtorrent`.  
*   **Команда встановлення:** `sudo apt install rtorrent`  
*   **Команда запуску:** `rtorrent`  
![скріншот 5](https://github.com/unforgivingbunny/collegework/raw/main/os/workcases/wc8/img/5.png)

**6. Планувати дії в календарі та нагадувати про них.**  
Для швидкого виводу календаря використано вбудовану утиліту `cal`.  
*   **Команда запуску:** `cal`  
![скріншот 6](https://github.com/unforgivingbunny/collegework/raw/main/os/workcases/wc8/img/6.png)

**7. Переглядати зображення в терміналі.**  
Використано утиліту `catimg`, яка дозволяє рендерити картинку блоками прямо в консолі.  
*   **Команда встановлення:** `sudo apt install catimg`  
*   **Команда запуску:** `catimg cat.png`  
![скріншот 7](https://github.com/unforgivingbunny/collegework/raw/main/os/workcases/wc8/img/7.png)

---

### Завдання 2. Дії адміністратора  

**1. Вводити, редагувати, видаляти текст (редактори файлів).**  
Використано текстовий редактор `nano` для створення та правки текстових файлів.  
*   **Команда запуску:** `nano 1.txt`  
![скріншот 8](https://github.com/unforgivingbunny/collegework/raw/main/os/workcases/wc8/img/8.png) 

**2. Здійснювати моніторинг процесів та ресурсів системи.**  
Використано утиліту `htop` — потужний інтерактивний аналог системного монітора.  
*   **Команда встановлення:** `sudo apt install htop`  
*   **Команда запуску:** `htop`  
![скріншот 9](https://github.com/unforgivingbunny/collegework/raw/main/os/workcases/wc8/img/9.png)

---

### Завдання 3. «Пасхалки» в терміналі  

1. Паровий локомотив.  
Анімація поїзда, що проїжджає по екрану.  
*   Команда встановлення: sudo apt install sl  
*   Команда запуску: sl  
![скріншот 10](https://github.com/unforgivingbunny/collegework/raw/main/os/workcases/wc8/img/10.png)

2. Зоряні війни.  
Перегляд ASCII-версії фільму через віддалений сервер.  
*   Команда запуску: telnet telehack.com (команда starwars)  
![скріншот 11](https://github.com/unforgivingbunny/collegework/raw/main/os/workcases/wc8/img/11.png)

3. Діалог з коровою.  
Утиліта, яка виводить ASCII-корову з вказаним текстом.  
*   Команда встановлення: sudo apt install cowsay  
*   Команда запуску: cowsay "Hello, World"  
![скріншот 12](https://github.com/unforgivingbunny/collegework/raw/main/os/workcases/wc8/img/12.png)

4. Власна знахідка (ефект Матриці).  
Ефект падаючого цифрового дощу з фільму "Матриця".  
*   Команда встановлення: sudo apt install cmatrix  
*   Команда запуску: cmatrix  
![скріншот 13](https://github.com/unforgivingbunny/collegework/raw/main/os/workcases/wc8/img/13.png)

---

### Conclusion  
During this laboratory work, I familiarized myself with the capabilities of the Linux operating system without a graphical user interface. I learned how to install and use terminal-based alternatives for common graphical applications, such as a file manager, web browser, and media players. Furthermore, I practiced using essential system administration tools like text editors and process monitors. This experience demonstrated that the terminal is a powerful and versatile environment capable of handling complex tasks efficiently.
