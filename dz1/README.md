# 1. Клонирование репозитория

Склонируйте репозиторий с исходным кодом и тестами:

```bash
git clone <URL репозитория>
cd <директория проекта/dz/dz1>
```

# 2. Установка зависимостей и запуска
Тесты не требуют внешних зависимостей - unittest

## Запуск
```bash
python emulator.py
```

# 3. Структура проекта
Проект содержит следующие файлы и директории, связанные с тестированием:
```bash
emulator.py           # Файл с реализацией команд
test_emulator.py      # Файл с тестами для команд
fs.tar                # Файл с файловой системой
```

# 4. Запуск тестов
В этом руководстве описывается, как запустить тесты для команд эмулятора оболочки. Используется модуль Python `unittest` для тестирования.
```bash
python test_emulator.py
```