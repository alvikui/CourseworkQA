# Курсовой проект по модулю «Автоматизация тестирования» для профессии «Инженер по тестированию»

## Описание приложения

Приложение предлагает купить тур по определённой цене с помощью двух способов:

1. Обычная оплата по дебетовой карте
2. Уникальная технология: выдача кредита по данным банковской карты
   
Само приложение не обрабатывает данные по картам, а пересылает их банковским сервисам:
* сервису платежей (Payment Gate);
* кредитному сервису (Credit Gate).

Приложение в собственной СУБД должно сохранять информацию о том, успешно ли был совершён платёж и каким способом. 
Данные карт при этом сохранять не допускается.

<details>
<summary>Техническая часть</summary>

Само приложение расположено в файле [`./artifacts/aqa-shop.jar`](aqa-shop.jar) 
и запускается стандартным способом `java -jar ./artifacts/aqa-shop.jar` на порту 8080.

В файле [`application.properties`](application.properties) приведён ряд типовых настроек:
* учётные данные и URL для подключения к СУБД;
* URL-адреса банковских сервисов.

</details>

## Начало работы

**Выполнить команды в терминале:**
* `git clone https://github.com/alvikui/CourseworkQA`
* `cd CourseworkQA`

### Prerequisites

**Необходимо наличие установленных приложений:**
* Java 11
* Git
* Docker, Docker compose
* IDE: IntelliJ IDEA
* DBeaver

### Установка и запуск

1. Запустить контейнер БД

* `docker compose up`

2. Запустить приложение

для запуска сервиса с БД postresql

* `java -Dspring.datasource.url=jdbc:postgresql://localhost:5432/app -jar ./artifacts/aqa-shop.jar`

для запуска сервиса с БД mysql

* `java -Dspring.datasource.url=jdbc:mysql://localhost:3306/app -jar ./artifacts/aqa-shop.jar`

3. Запустить автотесты

для запуска тестов с БД postresql:

* `./gradlew clean test -DdbUrl=jdbc:postgresql://localhost:5432/app`

для запуска тестов с БД mysql:

* `./gradlew clean test -DdbUrl=jdbc:mysql://localhost:3306/app`

4. Сформировать и открыть отчёт

* `./gradlew allureServe`  

5. Остановить контейнер

* `docker-compose down`  