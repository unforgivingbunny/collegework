# Work-case №3
## Виконали: Глядченко, Козуб 

## 1. Клонування та експорт віртуальної машини

**Клонування:** У середовищі VirtualBox виконано повне клонування (Full Clone) базової ОС Linux Mint. Для уникнення конфліктів у мережі застосовано політику генерації нових MAC-адрес для всіх мережевих адаптерів.

![wc3_1](https://github.com/unforgivingbunny/collegework/blob/main/os/workcases/wc3/wc3_1.png)
![wc3_2](https://github.com/unforgivingbunny/collegework/blob/main/os/workcases/wc3/wc3_2.png)

**Експорт:** Процес перенесення ОС в інше середовище виконується через головне меню гіпервізора «Export Virtual Appliance».

![wc3_3](https://github.com/unforgivingbunny/collegework/blob/main/os/workcases/wc3/wc3_3.png)

---



---

## 3. Розгортання мережі між ОС та клоном

У налаштуваннях обох ВМ встановлено тип підключення **Bridged Adapter**.

![wc3_5](https://github.com/unforgivingbunny/collegework/blob/main/os/workcases/wc3/wc3_5.png)

**Перевірка зв'язку:** Командою `ip a` визначено IP-адреси машин. Мережевий зв'язок між базовою ОС та клоном успішно перевірено за допомогою команди `ping`.

![wc3_6](https://github.com/unforgivingbunny/collegework/blob/main/os/workcases/wc3/wc3_6.png)

**Доступ до Інтернету:** Перевірено шляхом успішного запуску відео на ресурсі YouTube через вбудований веб-браузер.

![wc3_7](https://github.com/unforgivingbunny/collegework/blob/main/os/workcases/wc3/wc3_7.png)

**Обмін повідомленнями:** Налаштовано за допомогою мережевої утиліти `netcat` (`nc`). На першій машині відкрито порт для прослуховування, на машині-клоні виконано підключення. Текстове повідомлення успішно передано по локальній мережі.

![wc3_9](https://github.com/unforgivingbunny/collegework/blob/main/os/workcases/wc3/wc3_9.png)
![wc3_8](https://github.com/unforgivingbunny/collegework/blob/main/os/workcases/wc3/wc3_8.png)

---

## 4. Обмін інформацією між основною ОС та віртуальною ОС

Для обміну файлами між Windows та Linux Mint використано функцію перетягування (Drag'n'Drop).

У верхньому меню віртуальної машини (**Devices → Drag and Drop**) увімкнено режим **«Двонаправлений» (Bidirectional)**.

![wc3_10](https://github.com/unforgivingbunny/collegework/blob/main/os/workcases/wc3/wc3_10.png)

Аудіо-файл `1.mp3` успішно скопійовано з робочого столу основної ОС (Windows) на робочий стіл віртуальної машини звичайним перетягуванням мишкою.

![wc3_11](https://github.com/unforgivingbunny/collegework/blob/main/os/workcases/wc3/wc3_11.png)
![wc3_12](https://github.com/unforgivingbunny/collegework/blob/main/os/workcases/wc3/wc3_12.png)
![wc3_13](https://github.com/unforgivingbunny/collegework/blob/main/os/workcases/wc3/wc3_13.png)