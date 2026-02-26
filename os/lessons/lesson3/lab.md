# Лабораторна робота №3
**Дисципліна:** Операційні системи  
**Тема:** “Знайомство з базовими командами CLI-режиму в Linux”  
**Виконали:** Глядченко, Козуб 

---

## Мета роботи

Знайомство з базовими командами CLI-режиму в Linux.
Знайомство з базовими текстовими командами в термінальному режимі роботи в різних ОС.

---

## Vocabulary of English Terms

| Term | Definition/Explanation |
| :--- | :--- |
| **Shell** | A command-line interpreter that provides an interface between the user and the operating system. |
| **Command Line** | A text-based interface where users type commands to perform operations. |
| **CLI** | Command Line Interface. A method of interacting with a computer by typing text commands. |
| **Prompt** | A sequence of characters (e.g., `user@host:~$`) displayed by the shell to indicate it is ready to accept commands. |
| **Command** | A software program or built-in function that performs a specific action when executed. |
| **Argument** | An item of information provided to a command, such as a filename, directory, or text string, that the command acts upon. |
| **Variable** | A named storage location in memory that holds a value, which can be text or a number. |
| **Alias** | A custom shortcut or nickname created for a longer command or sequence of commands to save typing. |
| **Scripting** | The process of writing and executing a series of commands stored in a file (a script) for automation. |
| **Built-in command** | A command that is integrated directly into the shell itself and does not exist as an external file in the filesystem (e.g., `cd`, `echo`, `export`). |
| **External command** | A command that exists as a separate executable file in the filesystem (e.g., `ls`, `cp`, `man`). |
| **History** | A feature of the shell that keeps a list of previously executed commands, allowing for easy recall, editing, and re-execution. |
| **Manual page (man)** | A built-in documentation system accessed via the `man` command, providing detailed information about commands, system calls, file formats, and more. |

---

## Хід роботи

### Визначення понять

*   **Командний інтерпретатор (Command Interpreter):** Це програма, яка отримує рядки тексту (команди), введені користувачем, аналізує їх і передає ядру операційної системи для виконання або виконує їх самостійно, якщо це вбудовані команди.
*   **Оболонка (Shell):** Синонім командного інтерпретатора в UNIX-подібних системах. Це користувацький інтерфейс до операційної системи. Найпоширеніша оболонка в Linux — Bash (Bourne Again SHell).
*   **Команда (Command):** Це ім'я програми, вбудованої функції оболонки, псевдоніма або скрипта, яке користувач вводить у командному рядку для виконання певних дій.

### Відповіді на питання

**1. Яку базову інформацію надає рядок запрошення (prompt)?**
Рядок запрошення надає контекстну інформацію про поточний сеанс роботи. У типовому форматі `sysadmin@localhost:~$` міститься:
*   Ім'я користувача (`sysadmin`).
*   Ім'я системи (хоста) (`localhost`).
*   Поточний робочий каталог (`~`, що означає домашню директорію користувача).
*   Символ запрошення (`$` для звичайного користувача, `#` для root).

**2. Для чого команді потрібні параметри та аргументи?**
*   **Параметри (Options)** потрібні для зміни стандартної поведінки команди. Вони дозволяють налаштувати вивід, формат або дію команди (наприклад, `-l` для детального списку замість простого).
*   **Аргументи (Arguments)** вказують команді, на чому саме слід виконувати дію. Вони є "об'єктами" впливу команди (наприклад, ім'я файлу для відкриття, шлях до каталогу для перегляду).

**3. Яке призначення команд `ls`, які параметри та аргументи вона може мати? Наведіть 3 приклади.**
Команда `ls` призначена для виведення списку вмісту каталогів.
*   **Приклад 1:** `ls` - вивести список файлів та папок у поточному каталозі.
*   **Приклад 2:** `ls -l /home` - вивести детальну інформацію (параметр `-l`) про вміст каталогу `/home` (аргумент).
*   **Приклад 3:** `ls -a` - вивести весь вміст поточного каталогу, включаючи приховані файли (параметр `-a`).

**4. Яким чином можна використати історію команд, які переваги це надає?**
Історію команд можна використовувати за допомогою:
*   Клавш "вгору/вниз" для навігації по раніше введених командах.
*   Команди `history` для виведення всього списку.
*   Комбінації `Ctrl+R` для пошуку по історії.
*   Виконання команди з історії за номером: `!номер`.
*   **Переваги:** Економія часу, уникнення помилок при повторному введенні складних команд, можливість проаналізувати попередні дії.

**5. Яке призначення команди `echo`?**
Команда `echo` використовується для виведення рядка тексту або значення змінної на стандартний вивід (екран).

**6. Охарактеризуйте поняття змінної в оболонці Bash, які типи змінних вона підтримує?**
Змінна в Bash — це іменована комірка пам'яті, яка зберігає певне значення (найчастіше рядок тексту). Bash підтримує два основні типи змінних:
*   **Локальні змінні (Local variables):** Доступні лише в поточному екземплярі оболонки.
*   **Змінні оточення (Environment variables):** Успадковуються всіма дочірніми процесами, запущеними з даної оболонки.

**7. Яке призначення команд `env`, `export` та `unset`?**
*   **`env`:** Використовується для перегляду всіх поточних змінних оточення або для запуску програми в модифікованому оточенні.
*   **`export`:** Робить локальну змінну змінною оточення, роблячи її доступною для дочірніх процесів.
*   **`unset`:** Видаляє змінну або функцію оболонки.

**8. Які команди для отримання довідки по командам в терміналі ви знаєте?**
*   **`man команда`:** Відкриває детальний посібник (manual page) з описом, параметрами, прикладами.
*   **`команда --help`** або **`команда -h`:** Виводить коротку довідку з використанням команди.
*   **`info команда`:** Відкриває довідку в альтернативному форматі (info pages).
*   **`whatis команда`:** Виводить однорядковий опис команди.

---



### 2.2 Робота в терміналі (закріплення практичних навичок)

#### 2.2.1. Робота зі змінними (Variables) та псевдонімами (Aliases)

**Мета:** Навчитися створювати змінні для зберігання даних та створювати короткі псевдоніми для довгих команд.

1.  **Створення змінних:**
    ```bash
    var_name1="Олег"
    var_name2="Макар"
    var_name3="Женя"
    ```
    *Очікуваний результат: команди не виводять нічого на екран, просто створюють змінні.*

2.  **Виведення імен за допомогою `echo`:**
    ```bash
    echo $var_name1 $var_name2 $var_name3
    ```

    *Скріншот: 2.2.1_echo_vars.png*
![2.2.1_echo_vars](https://raw.githubusercontent.com/unforgivingbunny/collegework/main/os/lessons/lesson3/img/2.2.1_echo_vars.png)

3.  **Створення псевдонімів:**
    ```bash
    alias mycal1='cal 2007'
    alias mycal2='cal 2008'
    alias mycal3='cal 2007'
    ```

4.  **Перевірка роботи псевдонімів:**
    ```bash
    mycal1
    mycal2
    mycal3
    ```

    *Скріншот: 2.2.1_aliases.png*
![2.2.1_aliases](https://raw.githubusercontent.com/unforgivingbunny/collegework/main/os/lessons/lesson3/img/2.2.1_aliases.png)

5.  **Перегляд усіх псевдонімів:**
    ```bash
    alias
    ```

---

#### 2.2.2. Робота з функціями (Functions)

**Мета:** Навчитися створювати просту функцію, яка виконує послідовність дій.

1.  **Створення функції `students_report`:**
    ```bash
    students_report () {
        echo "Імена студентів:"
        echo "$var_name1"
        echo "$var_name2"
        echo "$var_name3"
        echo "Роки народження:"
        echo "2007"
        echo "2008"
        echo "2007"
    }
    ```
    *Скріншот: 2.2.2_function_create.png*
![2.2.2_function_create](https://raw.githubusercontent.com/unforgivingbunny/collegework/main/os/lessons/lesson3/img/2.2.2_function_create.png)

2.  **Виклик функції:**
    ```bash
    students_report
    ```
    
    *Скріншот: 2.2.2_function_call.png*
![2.2.2_function_call](https://raw.githubusercontent.com/unforgivingbunny/collegework/main/os/lessons/lesson3/img/2.2.2_function_call.png)

---

#### 2.2.3. Робота з лапками (Quoting)

**Мета:** Зрозуміти різницю між одинарними (`'`), подвійними (`"`) лапками та виконанням команд.

1.  **Виведення речення з назвами змінних та їх вмістом:**
    Тут ми використовуємо `\$`, щоб вивести символ долара, а не підставляти значення змінної. Одинарні лапки всередині подвійних дозволяють виділити частину тексту.
    ```bash
    echo "'We create such variables as' \$var_name1, \$var_name2, \$var_name3, 'which stored our names' $var_name1, $var_name2, $var_name3"
    ```
    *Скріншот: 2.2.3_quoting_1.png*
![2.2.3_quoting_1](https://raw.githubusercontent.com/unforgivingbunny/collegework/main/os/lessons/lesson3/img/2.2.3_quoting_1.png)

2.  **Виведення речення з назвами псевдонімів та результатом їх роботи:**
    ```bash
    echo "'We create such Aliases as' mycal1, mycal2, mycal3, 'which can show our calendars:' $(mycal1 | head -1), $(mycal2 | head -1), $(mycal3 | head -1)"
    ```
    *Примітка: `| head -1` бере лише перший рядок виводу (назву року), щоб ВДРУГЕ не захаращувати термінал усім календарем. :)*

    *Скріншот: 2.2.3_quoting_2.png*
![2.2.3_quoting_2](https://raw.githubusercontent.com/unforgivingbunny/collegework/main/os/lessons/lesson3/img/2.2.3_quoting_2.png)

---

#### 2.2.4. Робота з інструкціями керування (Control Statements)

**Мета:** Навчитися виконувати декілька команд в одному рядку за допомогою крапки з комою `;`.

1.  **Виконання завдань 2.1 та 2.2 одним рядком:**
    Цей рядок створить змінні, виведе їх, а потім виконає дії, аналогічні функції `students_report`. Крапка з комою розділяє окремі команди. Весь цей довгий рядок копіюється та вставляється в термінал як одна дія.
    ```bash
    var_name1=Олег; var_name2=Макар; var_name3=Женя; echo "--- Завдання 2.1 ---"; echo "Імена студентів:"; echo $var_name1 $var_name2 $var_name3; echo "--- Завдання 2.2 ---"; echo "Імена студентів:"; echo "$var_name1"; echo "$var_name2"; echo "$var_name3"; echo "Роки народження:"; echo "2007"; echo "2008"; echo "2007"
    ```

    *Скріншот: 2.2.4_control_statements.png*
![2.2.4_control_statements](https://raw.githubusercontent.com/unforgivingbunny/collegework/main/os/lessons/lesson3/img/2.2.4_control_statements.png)

---

#### 2.2.5. Робота з командами довідки (Man Pages)

**Мета:** Навчитися користуватися вбудованою документацією та знаходити різні параметри команд.

1.  **Отримання довідки для команди `uname`:**
    ```bash
    man uname
    ```
    *Скріншот: 2.2.5_man_uname.png*
![2.2.5_man_uname](https://raw.githubusercontent.com/unforgivingbunny/collegework/main/os/lessons/lesson3/img/2.2.5_man_uname.png)

2.  **5 різних варіантів виводу команди `uname`:**
    ```bash
    uname
    uname -n
    uname -r
    uname -m
    uname -a
    ```

    *Скріншот: 2.2.5_uname_examples.png*
![2.2.5_uname_examples](https://raw.githubusercontent.com/unforgivingbunny/collegework/main/os/lessons/lesson3/img/2.2.5_uname_examples.png)
