# Лабораторна робота №4
**Дисципліна:** Операційні системи  
**Тема:** “Команди Linux для управління процесами”  
**Виконали:** Глядченко, Козуб 

## Мета роботи
- Отримання практичних навиків роботи з командною оболонкою Bash.
- Знайомство з базовими командами для управління процесами.

---

## 1. Попередня підготовка

### 1.1. Словник базових термінів

*   **Process:** An instance of a program that is being executed.
*   **PID (Process ID):** A unique identification number assigned to a running process.
*   **PPID (Parent Process ID):** The PID of the process that started the current process.
*   **Terminal (TTY):** A command-line interface or the device file associated with it, through which a user interacts with the system.
*   **Signal:** A software interrupt delivered to a process to notify it that an event has occurred (e.g., interrupt, terminate).
*   **Parent Process:** A process that has created one or more child processes.
*   **Child Process:** A process created by another process (the parent).
*   **Background Process:** A process that runs independently of the shell, allowing the user to continue issuing commands in the same terminal.
*   **Scheduler:** A component of the OS kernel that decides which process runs next, for how long, and in what order.

---

## 2. Хід роботи

### 2.1. Початкова робота в CLI-режимі

Після входу в ОС Linux та запуску терміналу було виконано ряд команд для дослідження базових механізмів роботи з процесами.

Для ознайомлення з віртуальною файловою системою `/proc` було виконано команду `ls -la /proc | head -20`. У виведеному списку видно числові каталоги, які відповідають ID запущених процесів, а також файли з інформацією про систему (`cpuinfo`, `meminfo`).

> **[СКРІНШОТ 1: Вивід команди `ls -la /proc | head -20`]**  
> ![Скріншот 1](https://raw.githubusercontent.com/unforgivingbunny/collegework/main/os/lessons/lesson4/img/1.png)

Далі було досліджено інформацію про поточні сеанси користувачів. Команда `who` вивела список активних сеансів. Більш детальну інформацію надала команда `w`.

> **[СКРІНШОТ 2: Вивід команд `who` та `w`]**  
> ![Скріншот 2](https://raw.githubusercontent.com/unforgivingbunny/collegework/main/os/lessons/lesson4/img/2.png)

Для демонстрації роботи сигналів було запущено процес `ping 8.8.8.8`. Після отримання кількох відповідей натиснуто `Ctrl + C` (`SIGINT`), що завершило процес з виведенням статистики.

> **[СКРІНШОТ 3: Процес `ping` після переривання `Ctrl + C`]**  
> ![Скріншот 3](https://raw.githubusercontent.com/unforgivingbunny/collegework/main/os/lessons/lesson4/img/3.png)

Потім `ping` було запущено знову і призупинено комбінацією `Ctrl + Z` (`SIGTSTP`). Команда `jobs` підтвердила статус "Stopped".

> **[СКРІНШОТ 4: Стан "Stopped" для процесу `ping` після `Ctrl + Z`]**  
> ![Скріншот 4](https://raw.githubusercontent.com/unforgivingbunny/collegework/main/os/lessons/lesson4/img/4.png)

Для керування призупиненим процесом використано команди `bg` та `fg`. Команда `bg %1` відновила виконання пінгу у фоновому режимі. `jobs` підтвердила статус "Running". Після цього `fg %1` повернула процес на передній план, звідки його було завершено `Ctrl + C`.

> **[СКРІНШОТ 5: Вивід `jobs` після виконання `bg %1`]**  
> ![Скріншот 5](https://raw.githubusercontent.com/unforgivingbunny/collegework/main/os/lessons/lesson4/img/5.png)

### 2.2. Практична робота з процесами

Наступним етапом стало дослідження спеціалізованих команд для моніторингу та управління процесами.

Було запущено команду `top`. На екрані відобразився інтерактивний інтерфейс з інформацією про час роботи системи, середнє навантаження та список найактивніших процесів.

> **[СКРІНШОТ 6: Загальний вигляд інтерфейсу команди `top`]**  
> ![Скріншот 6](https://raw.githubusercontent.com/unforgivingbunny/collegework/main/os/lessons/lesson4/img/6.png)

Виконання `top` було призупинено `Ctrl + Z`. Команда `jobs` підтвердила статус "Stopped".

> **[СКРІНШОТ 7: Вивід `jobs` із завданням `top` у стані "Stopped"]**  
> ![Скріншот 7](https://raw.githubusercontent.com/unforgivingbunny/collegework/main/os/lessons/lesson4/img/7.png)

Після призупинення `top` було виконано серію команд `ps` для отримання різноманітної інформації про процеси. Всі команди було об'єднано в одному скріншоті для демонстрації різних форматів виводу:

- `ps -ef | head -15` — повний список всіх процесів з розширеним форматом.
- `ps aux | head -15` — всі процеси з інформацією про використання CPU та пам'яті.
- `ps -u $(whoami)` — процеси поточного користувача.
- `ps -C bash` — процеси, пов'язані з оболонкою Bash.
- `ps -ef --forest | head -25` — ієрархічна структура процесів (дерево).

> **[СКРІНШОТ 8: Вивід різних варіантів команди `ps`]**  
> ![Скріншот 8](https://raw.githubusercontent.com/unforgivingbunny/collegework/main/os/lessons/lesson4/img/8.png)

Після ознайомлення зі статичними знімками `ps` було продовжено роботу з призупиненим `top`. Команда `fg %top` повернула його на передній план.

Процес знову призупинено `Ctrl + Z`. Потім командою `bg %top` його виконання відновлено у фоновому режимі. `jobs` підтвердила статус "Running".

> **[СКРІНШОТ 9: Вивід `jobs`, що показує `top` у статусі "Running" після `bg`]**  
> ![Скріншот 9](https://raw.githubusercontent.com/unforgivingbunny/collegework/main/os/lessons/lesson4/img/9.png)

На завершення фоновий процес `top` було завершено командою `kill %top`. Для підтвердження виконано `jobs` (порожній список) та `ps aux | grep top` (процес відсутній).

> **[СКРІНШОТ 10: Вивід команд `jobs` та `ps aux | grep top` після завершення процесу]**  
> ![Скріншот 10](https://raw.githubusercontent.com/unforgivingbunny/collegework/main/os/lessons/lesson4/img/10.png)
