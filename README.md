# Лабораторная работа: Запуск контейнера Ubuntu с Web-сервером Apache

## Цель работы
Данная лабораторная работа призвана напомнить основные команды ОС Debian/Ubuntu. Также она позволит познакомиться с Docker и его основными командами.

## Задание
Запустить контейнер Ubuntu, установить Web-сервер Apache и вывести в браузере страницу с текстом "Hello, World!".

## Подготовка
Для выполнения данной работы необходимо иметь установленный на компьютере Docker.

## Выполнение

### 1. Создание репозитория
Создаю репозиторий `containers04` и склонирую его себе на компьютер:
```sh
git clone https://github.com/your_username/containers04.git
cd containers04
```

### 2. Запуск контейнера Ubuntu
Открываю терминал в папке `containers04` и выполняю команду:
```sh
docker run -ti -p 8000:80 --name containers04 ubuntu bash
```
Эта команда запускает контейнер на основе образа Ubuntu, пробрасывает порт 8000 контейнера на порт 80 и открывает терминал внутри контейнера.
![Image](https://github.com/user-attachments/assets/d24e7652-5938-4cf7-842a-9d445d062d48)


### 3. Установка и запуск Apache
Выполняю следующие команды внутри контейнера:
```sh
apt update
```
Обновляет список пакетов в контейнере.
![Image](https://github.com/user-attachments/assets/46b9fc28-4b7e-43ee-9777-bc123b5bc0db)
```sh
apt install apache2 -y
```
Устанавливает веб-сервер Apache.
![Image](https://github.com/user-attachments/assets/3ce91172-5ee2-4384-8b4b-c1523469b228)
```sh
service apache2 start
```
Запускает Apache в контейнере.
![Image](https://github.com/user-attachments/assets/911d237b-4ef6-4435-8c14-f6d35ef7207e)

### 4. Проверка работы сервера
Открываю браузер и ввожу в адресной строке:
```
http://localhost:8000
```
Вижу стандартную страницу Apache.
![Image](https://github.com/user-attachments/assets/7a941de5-dad7-46c1-9c5a-2ba50f8eee63)

### 5. Изменение содержимого веб-страницы
Выполняю следующие команды:
```sh
ls -l /var/www/html/
```
Отобразит список файлов в корневой директории веб-сервера.
![Image](https://github.com/user-attachments/assets/7d3be885-42a6-4130-a085-4533e39a264b)
```sh
echo '<h1>Hello, World!</h1>' > /var/www/html/index.html
```
Создает HTML-файл с текстом "Hello, World!".

Обновляю страницу в браузере. Теперь на экране появился текст "Hello, World!".
![Image](https://github.com/user-attachments/assets/6de9b7c9-4d7a-469b-a050-c4d877f71430)

### 6. Анализ конфигурации Apache
Перехожу в директорию конфигурации Apache и вывожу содержимое файла `000-default.conf`:
```sh
cd /etc/apache2/sites-enabled/
cat 000-default.conf
```
Этот файл содержит конфигурацию виртуального хоста Apache.
![Image](https://github.com/user-attachments/assets/df34a200-7729-4b39-9944-e906ec47bea7)

### 8. Завершение работы контейнера
Выполняю команду:
```sh
exit
```
Закроет терминал контейнера и остановит его.

### . Управление контейнером
Проверка списка контейнеров:
```sh
docker ps -a
```
Выведет список всех контейнеров, включая остановленные.
![Image](https://github.com/user-attachments/assets/35303fa0-9083-402b-a12b-b9cfb86d9f5b)

Удаление контейнера:
```sh
docker rm containers04
```
Удаляет контейнер с именем `containers04`.

## Выводы
- В ходе работы были изучены основные команды Docker.
- Был развернут контейнер с Ubuntu и установлен веб-сервер Apache.
- Проверена работа веб-сервера, создана кастомная веб-страница.
- Разобраны основные команды управления контейнерами в Docker.

## Репозиторий
Ссылка на GitHub: [https://github.com/your_username/containers04](https://github.com/your_username/containers04)

