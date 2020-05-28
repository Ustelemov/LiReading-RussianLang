Данный проект разрабатывался в качестве НИР на 1-курсе

## Используемые технологии

## Полезные ссылки

## ToDo-лист
- [X] 1. ~~Создать файл с зависимостями - requirements.txt~~
- [ ] 2. ~~Создать скрипт для получения русских суббтитров с видео в txt формате (без знаков препинания, парсинг из srt)~~
- [ ] 3. Создать скрипт для получения: базового видео в mp4, обрезанного видео (передаются секунды до и после) в mp4, дорожки обрезанного видео в wav и mp3 

## Структура проекта
- README.md - Wiki по репозиторию
- getsubtitles.py - получение суббтитров с Youtube-видео в txt формате: без знаков препинания, спаршенное с srt формата

## Использование
### 
### Установка зависимостей
Для установки всех требуемых зависимостей воспользуйтесь командой:
```
pip install -r requirements.txt
```
### Скачивание суббтитров
```
python getcaption.py --u 'https://www.youtube.com/watch?v=vyhzVJBln6k' --p '/content/pedagog'
```
--u - ссылка на видео

--p - путь к папке, в которую будет помещен файл subtitles.txt. Дефолтно: /default

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
