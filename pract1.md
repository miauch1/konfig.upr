## Практическое занятие №1. Введение, основы работы в командной строке

П.Н. Советов, РТУ МИРЭА

Научиться выполнять простые действия с файлами и каталогами в Linux из командной строки. Сравнить работу в командной строке Windows и Linux.

# Задача 1
Вывести отсортированный в алфавитном порядке список имен пользователей в файле passwd (вам понадобится grep).

![image](https://github.com/user-attachments/assets/de02e457-5213-4eac-aede-59a6153575d1)

# Задача 2
Вывести данные /etc/protocols в отформатированном и отсортированном порядке для 5 наибольших портов, как показано в примере ниже:

    [root@localhost etc]# cat /etc/protocols ...
    142 rohc
    141 wesp
    140 shim6
    139 hip
    138 manet
    
![image](https://github.com/user-attachments/assets/48a16b8d-f81b-4573-8d00-f46148f0bff9)

# Задача 3
Написать программу banner средствами bash для вывода текстов, как в следующем примере (размер баннера должен меняться!):

    [root@localhost ~]# ./banner "Hello from RTU MIREA!"
    +-----------------------+
    | Hello from RTU MIREA! |
    +-----------------------+

![image](https://github.com/user-attachments/assets/6061e0da-14ce-4a9c-9af5-e091f4699d07)

Перед отправкой решения проверьте его в ShellCheck на предупреждения.

# Задача 4
Написать программу для вывода всех идентификаторов (по правилам C/C++ или Java) в файле (без повторений).

Пример для hello.c:

    h hello include int main n printf return stdio void world

![image](https://github.com/user-attachments/assets/257f1a45-54e8-457e-b910-8a0b226aa47b)

# Задача 5
Написать программу для регистрации пользовательской команды (правильные права доступа и копирование в /usr/local/bin).

Например, пусть программа называется reg:

    ./reg banner

В результате для banner задаются правильные права доступа и сам banner копируется в /usr/local/bin.

