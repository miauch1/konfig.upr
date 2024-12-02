## Практическое задание №4. Системы контроля версий

П.Н. Советов, РТУ МИРЭА

Работа с Git.

# Задача 1

На сайте https://onlywei.github.io/explain-git-with-d3 или http://git-school.github.io/visualizing-git/ (цвета могут отличаться, есть команды undo/redo) с помощью команд эмулятора git получить следующее состояние проекта (сливаем master с first, перебазируем second на master): см. картинку ниже. Прислать свою картинку.

![изображение](https://github.com/user-attachments/assets/8792f8c7-7887-48f8-91db-653381193c08)

![изображение](https://github.com/user-attachments/assets/1e8c4937-d192-418b-b338-a264543f6800)

# Задача 4

Написать программу на Питоне (или другом ЯП), которая выводит список содержимого всех объектов репозитория. Воспользоваться командой "git cat-file -p". Идеальное решение – не использовать иных сторонних команд и библиотек для работы с git.

```
import os
import subprocess

def get_git_objects():
    try:
        result = subprocess.run(
            ['git', 'rev-list', '--all'],
            stdout=subprocess.PIPE,
            stderr=subprocess.PIPE,
            text=True,
            check=True
        )
        objects = result.stdout.splitlines()

        for obj in objects:
            print(f"Git Commit: {obj}")
            try:
                content = subprocess.run(
                    ['git', 'cat-file', '-p', obj],
                    stdout=subprocess.PIPE,
                    stderr=subprocess.PIPE,
                    text=True,
                    check=True
                )
                print(content.stdout)
            except subprocess.CalledProcessError as e:
                print(f"Error {obj}: {e.stderr}")

    except subprocess.CalledProcessError as e:
        print(f"Error: {e.stderr}")

if __name__ == "__main__":
    if not os.path.exists('.git'):
        print("Git not found")
    else:
        get_git_objects()
```
