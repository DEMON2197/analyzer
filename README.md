# Сервис Analyzer
Анализатор последовательностей построен с использованием  PHP7+ на базе фреймворка symfony5. <br />
В примере применяется база данных PostgreSql 11 для хранения пользовательских данных и результатовю

## Установка
Перед началом установки убедитесь, что в системе установлен PHP7+, PHP-cli, а также есть доступ к реляционной базе данных (к примеру: MySQL 5.7+, Postgres 11+).<br />
А также, установлен веб-сервер (к примеру Apache2).

1. Клонируйте репозиторий в папку вышего виртуального хоста на веб-сервере
> **git clone git@github.com:DEMON2197/analyzer.git**

2. Запустите установку Composer в дерриктории с проектом
> **composer install**

3. Настройте в файле .env перемнную среды DATABASE_URL. Пример
> **DATABASE_URL=mysql://db_user:db_password@127.0.0.1:3306/db_name?serverVersion=5.7**

4. Выполните миграции
> **php bin/console doctrine:migrations:migrate**

5. Запустите unit-тесты для проверки готовности проекта
> **php bin/phpunit**

6. Проверьте работу консольной команды get-index, с перечисленными параметрами:<br /> 
целове число num, ряд целых чисел array, id пользователя, под которым выполняется вычисления (не обязательно). Пример
> **php bin/console analyzer:get-index 5 1,5,4,5,1,-7,5 1**
<br />или<br />
> **php bin/console analyzer:get-index 2 1,5,4,2**
В последнемпримере не указан идентификатор пользователя.

## Проверка работы API
Для проверки работы сервиса воспользуйтесь любым удобным средством (к примру, Postman).<br />
Отправьте POST запрос на адрес **http://адрес_сервера:порт/index.php/setseparator** в формате JSON, содержащий поля<br />
- user_name (с тестовым пользователем: testUser) string
- auth_code (для пользователя testUser: ds23gkfj41sz6t5ghsdt4r135hr4) string
- number (к примеру, 4)
- sequence (к примеру: [1, 2, 4, 1, 14]) array(int)
