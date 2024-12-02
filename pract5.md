## Практическое занятие №5. Вопросы виртуализации

П.Н. Советов, РТУ МИРЭА

# Задача 1

Исследование виртуальной стековой машины CPython.

Изучите возможности просмотра байткода ВМ CPython.

```
import dis

def foo(x):
    while x:
        x -= 1
    return x + 1

print(dis.dis(foo))
```

Опишите по шагам, что делает каждая из следующих команд (приведите эквивалентное выражение на Python):

 11           0 LOAD_FAST                0 (x)
              2 LOAD_CONST               1 (10)
              4 BINARY_MULTIPLY
              6 LOAD_CONST               2 (42)
              8 BINARY_ADD
             10 RETURN_VALUE

__Описание команд:__

0 LOAD_FAST - 0 (x): x (загружаем переменную х в стек)

LOAD_CONST - 1 (10): кладём 1 в стек

4 BINARY_MULTIPLY - a*b (умножение двух аргументов)

6 LOAD_CONST - 2 (42): кладём 42 в стек

8 BINARY_ADD - a+b (сложение двух аргументов)

10 RETURN_VALUE - return (возвращаем вершину стека)

# Задача 2

Что делает следующий байткод (опишите шаги его работы)? Это известная функция, назовите ее.

```
  5           0 LOAD_CONST               1 (1)
              2 STORE_FAST               1 (r)

  6     >>    4 LOAD_FAST                0 (n)
              6 LOAD_CONST               1 (1)
              8 COMPARE_OP               4 (>)
             10 POP_JUMP_IF_FALSE       30

  7          12 LOAD_FAST                1 (r)
             14 LOAD_FAST                0 (n)
             16 INPLACE_MULTIPLY
             18 STORE_FAST               1 (r)

  8          20 LOAD_FAST                0 (n)
             22 LOAD_CONST               1 (1)
             24 INPLACE_SUBTRACT
             26 STORE_FAST               0 (n)
             28 JUMP_ABSOLUTE            4

  9     >>   30 LOAD_FAST                1 (r)
             32 RETURN_VALUE
```

```
  5           0 LOAD_CONST               1 (1)    //Кладём единицу в вершину стека
              2 STORE_FAST               1 (r)    //Присваиваем r = 1

  6     >>    4 LOAD_FAST                0 (n)    //Добавляем n в стек
              6 LOAD_CONST               1 (1)    // Добавляем 1 в стек
              8 COMPARE_OP               4 (>)    //Логический оператор > (n>1)
             10 POP_JUMP_IF_FALSE       30        //Если результат сравнения ложь идти в 30, если нет переходим в 4

  7          12 LOAD_FAST                1 (r)    //Добавляем r в стек
             14 LOAD_FAST                0 (n)    //Добавляем n в стек
             16 INPLACE_MULTIPLY		  //r*=n
             18 STORE_FAST               1 (r) 

  8          20 LOAD_FAST                0 (n)    //Добавляем n в стек
             22 LOAD_CONST               1 (1)    //Добавляем 1 в стек
             24 INPLACE_SUBTRACT		  //n-=1
             26 STORE_FAST               0 (n)
             28 JUMP_ABSOLUTE            4        //Переходим в 30

  9     >>   30 LOAD_FAST                1 (r)    //Добавляем r в стек
             32 RETURN_VALUE		          //Возвращаем r
```

__Это факториал числа__

# Задача 3

Приведите результаты из задач 1 и 2 для виртуальной машины JVM (Java) или .Net (C#).

