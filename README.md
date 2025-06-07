# Дополнительное задание.

## 1. Перенос кода в репозиторий
- Создан новый репозиторий на GitHub
- Добавлены файлы: main.cpp, CMakeLists.txt, build.yml
- Создана папка images с файлом 15.png
- Результат: код успешно размещен в репозитории, готов к сборке
---
## 2. Настройка сборки через GitHub Actions
- В файле build.yml настроена сборка для windows через .msi
- Указаны необходимые зависимости: SFML 2.6.1, CMake, WiX Toolset
- Actions выдал галочку, в подразделе Artifacts появился *15-pazzle.msi*
![изображение](https://github.com/user-attachments/assets/33d9e8da-59c1-4e03-a531-b07704c8dd33)
---
## 3. Установка
- Скачиваем файл 15-puzzle.msi из подраздела Artifacts
- Разархивируем и запускаем .msi файл, устанавливаем игру
![изображение](https://github.com/user-attachments/assets/b4e26f54-2e39-44a9-a251-097cff2757db)

- Установка выполнена в папку (C:\Program Files (x86)\15-Puzzle)
- Переходим в вышеуказанную папку и запускаем exe-шник
![изображение](https://github.com/user-attachments/assets/db382bd2-81a9-4985-b4ac-144996a788fc)
---
## Вывод:
Игра создается, ниже представлено видео с работой игры

https://github.com/user-attachments/assets/8fdedea1-2287-47fc-9c4b-2d8440be8037

**Карев Георгий | ИУ8-21**
