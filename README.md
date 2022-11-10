# srvupdate

Скрипт для инкрементального обновления по коммиту в gitlab;

Пример запуска содержится в srv_test.bat

Параметры запуска:

- commitid - идентификатор коммита;
- project - наименование проекта внутри проекта edt;
- edt - версия EDT, например edt@2022.1.1
- platform - путь к 1cv8.exe
- base - строка подключения к базе, для серверной базы - "/S servername\basename";
- usr - имя пользователя информационной базы;
- pwd - пароль ползователя информационной базы;

Пример шага в gitlab.yml:

```yml

BaseUpdate: # Конвертация проекта из формата EDT в формат XML
  stage: build 
  script:
   -  oscript srvupdate.os $PR_BASE_NAME $CI_COMMIT_SHA
  tags:
    - myrunner
  only:
    - mybranch
```
