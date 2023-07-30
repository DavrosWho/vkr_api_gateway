# vkr_api_gateway
## В целом о проекте
Данная программа является частью проекта "Web-приложение для автоматизации работы предприятия". Здесь реализован API Gateway для связи двух других частей приложения.  
Для правильной работы всего приложения необходимо запустить все три программы.  
[Ссылка на часть с основным функционалом](https://github.com/DavrosWho/VKR)  
[Ссылка на часть с авторизационным функционалом](https://github.com/DavrosWho/vkr_auth)  

Используемые технологии всей серверной части проекта: Java, Spring Boot, REST, API Gateway, PostgreSQL
## Как запустить 
Проект разработан в среде IntelliJ IDEA (Протестирован в Build #IC-221.6008.13, built on July 19, 2022)  
Настройте IDE для запуска vkr_api_gateway/src/main/java/org/example/Main.java

## Структура приложения
Функции авторизации-регистрации и остальные распределены между двумя микросервисами. Для того, чтобы клиенту они виделись единым приложением, 
использован шаблон проектирования API Gateway. Задействовано решение для экосистемы Spring Cloud – Spring Cloud Gateway. 
Spring Cloud Gateway представляет собой Spring-Boot приложение, которое позволяет настраивать маршрутизацию в файле настроек yaml или в коде приложения,
а также расширять логику путём написания своего кода.  

Реализована схема, при которой все запросы на endpoint (конечную точку) /registration и /login перенаправляются на сервис авторизации, /help ведёт на сайт Spring,
а остальные маршрутизируются в vkr (микросервис, отвечающий за основные функции приложения).  
В файле application.yml сконфигурированы все маршруты для запросов.  

_Схема работы Spring Cloud Gateway приведена на рисунке ниже:_
![image](https://github.com/DavrosWho/vkr_api_gateway/assets/71879137/28231597-d9d4-416d-baf3-84bf10d79a1a)
