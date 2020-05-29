Данный проект разрабатывался в качестве НИР на 1-курсе

## Используемые технологии

## Полезные ссылки

## Todo-лист
- [X] 1. ~~Создать файл с зависимостями - requirements.txt~~
- [X] 2. ~~Создать скрипт для получения с Youtube-видео: русских суббтитров в txt формате (без знаков препинания, парсинг из srt),исходного видео в mp4, обрезанного видео (передаются секунды до и после) в mp4, дорожки обрезанного видео в wav и mp3~~
- [X] 3. ~~Создать скрипт для получения textGrid с MAUS TextAligner~~
- [ ] 4. Создать скрипт для получения из словаря слов словаря слово->фонемная транскрипция
- [ ] 5. Добавить словари: слова->транскрипции по фонемам, словарь фонем (с ключом и значением, для работы классификатора), словарь фонем с примерами использования



## Структура проекта
- [README.md](README.md) - Описание репозитория
- [Скрипты](scripts/)
  - get_info_from_youtube.py - получения с Youtube-видео: русских суббтитров в txt формате (без знаков препинания, парсинг из srt),исходного видео в mp4, обрезанного видео (передаются секунды до и после) в mp4, дорожки обрезанного видео в wav и mp3
- Документация
## Использование
### 
### Установка зависимостей
Для установки всех требуемых зависимостей воспользуйтесь командой:
```
pip install -r requirements.txt
```
### Получение информации с Youtube-видео
```
python get_info_from_youtube.py --u 'https://www.youtube.com/watch?v=vyhzVJBln6k' --p '/content/pedagog' --s 0 --e 68
```
- --u - ссылка на видео
- --p - путь к папке, в которую будет помещен файл subtitles.txt. Дефолтно: /default
- --s - секунда старта для обрезки видео
- --e - секунда окончания для обрезки видео

### Получение textGrid от MAUS TextAlignment
```
python get_maus_textgrid.py --a '/content/pedagog/audio.wav' --t '/content/pedagog/subtitles.txt' --p '/content/pedagog'
```
- --a - путь к wav файлу
- --t - путь к txt файлу текстовой аннотации (транскрипции для wav файла)
- --p - путь к папке, в которую будет положен выходной maus_out.TextGrid file


## Отчетная информация
#### Проблема
Неспособность распознать речь говорящего из-за частичного или полного отсутствия аудиоряда, либо при наличии его дефектов.

#### Цель
Разработать систему распознавания русскоязычного текста только по видеоряду записи речи (video-only speech recognition).

#### Задачи
1. Подобрать датасет, включающий видео/аудио и транскрипцию речи.
2. Подобрать/разработать инструмент для преобразования речи в набор фонем для возможности сопоставления кадра в фонеме.
3. Формирование обучающей и тестовых выборок, выделение губ на кадрах и сопоставление с фонемой.
4. Подобрать/разработать инструмент для классификации фонем по кадру, содержащему губы (провести обучение в случае сети).
5. Провести проверку на тестирующей выборке.
6. Проанализировать результат, тюнинг моделей.
7. Подобрать/разработать инструмент для объединения фонем в осмысленные слова.
8. Проанализировать результат.

#### Требуемый формат и набор данных
Видеофайл (аудио и видео дорожки) со спикерами - формат mp4

#### Требования к видеофайлам
1. На видео находится 1 говорящий  без дефектов речи, для которого язык - родной;
2. Съёмка ведётся анфас;
3. Спонтанная речь;
4. Высокое качество изображения ~480p +;
5. Нет искажения аудиоряда;
6. Транскрипция речи из видеофайла - формат txt (другой совместимый текстовый формат)

#### Требования к транскрипции
1. Транскрипция полностью соответствует аудиофайлу
2. Не содержит знаков пунктуации

#### Источник и состав датасета
- Видео с youtube-канала интервью (скриншот-пример в приложении)
- Аннотация - получение текста полумашинным способом (инструменты speach2text, контроль человека и корректировки)
- Для MVP планируется использовать 10 роликов (включающих как женщин, так и мужчин), в среднем 25 минут речи.

#### MVP
MVP представляет из себя python-скрипт, по входному видеофайлу без аудио выдающий текст речи в форме слов, составленных из фонем. Требования к видеофайлу аналогичны требованиям к видео для датасета.

#### Развитие проекта
- Исходя из анализа результатов MVP - доработка точности и устойчивости модели.
- Расширение датасета - увеличение количества спикеров.
- Создание пользовательского интерфейса/приложения.
