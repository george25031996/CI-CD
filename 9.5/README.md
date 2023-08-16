# Домашнее задание к занятию 11 «Teamcity»

## Подготовка к выполнению

1. В Yandex Cloud создайте новый инстанс (4CPU4RAM) на основе образа `jetbrains/teamcity-server`.
2. Дождитесь запуска teamcity, выполните первоначальную настройку.
3. Создайте ещё один инстанс (2CPU4RAM) на основе образа `jetbrains/teamcity-agent`. Пропишите к нему переменную окружения `SERVER_URL: "http://<teamcity_url>:8111"`.

Виртуальные машины я собрал с помощью [docker-compose.yml](https://github.com/george25031996/CI-CD/blob/main/9.5/teamcity/docker-compose.yml)

4. Авторизуйте агент.
5. Сделайте fork [репозитория](https://github.com/aragastmatb/example-teamcity).

Сделал [fork](https://github.com/george25031996/example-teamcity)

6. Создайте VM (2CPU4RAM) и запустите [playbook](./infrastructure).

## Основная часть

1. Создайте новый проект в teamcity на основе fork.

Создал новый проект в teamcity на основе fork:

<p align="center">
  <img width="1200" height="600" src="./images/1.png">
</p>


2. Сделайте autodetect конфигурации.

Сделал autodetect конфигурации:

<p align="center">
  <img width="1200" height="600" src="./images/2.png">
</p>

3. Сохраните необходимые шаги, запустите первую сборку master.

<p align="center">
  <img width="1200" height="600" src="./images/3.png">
</p>

4. Поменяйте условия сборки: если сборка по ветке `master`, то должен происходит `mvn clean deploy`, иначе `mvn clean test`.

<p align="center">
  <img width="1200" height="600" src="./images/4.png">
</p>

5. Для deploy будет необходимо загрузить [settings.xml](./teamcity/settings.xml) в набор конфигураций maven у teamcity, предварительно записав туда креды для подключения к nexus.

<p align="center">
  <img width="1200" height="600" src="./images/5.png">
</p>

6. В pom.xml необходимо поменять ссылки на репозиторий и nexus.

Поменял

7. Запустите сборку по master, убедитесь, что всё прошло успешно и артефакт появился в nexus.

<p align="center">
  <img width="1200" height="600" src="./images/6.png">
</p>

<p align="center">
  <img width="1200" height="600" src="./images/7.png">
</p>

8. Мигрируйте `build configuration` в репозиторий.

<p align="center">
  <img width="1200" height="600" src="./images/8.png">
</p>
9. Создайте отдельную ветку `feature/add_reply` в репозитории.

<p align="center">
  <img width="1200" height="600" src="./images/9.png">
</p>

10. Напишите новый метод для класса Welcomer: метод должен возвращать произвольную реплику, содержащую слово `hunter`.

<p align="center">
  <img width="1200" height="600" src="./images/10.png">
</p>

11. Дополните тест для нового метода на поиск слова `hunter` в новой реплике.

<p align="center">
  <img width="1200" height="600" src="./images/11.png">
</p>

12. Сделайте push всех изменений в новую ветку репозитория.

Сделал

13. Убедитесь, что сборка самостоятельно запустилась, тесты прошли успешно.

<p align="center">
  <img width="1200" height="600" src="./images/12.png">
</p>

<p align="center">
  <img width="1200" height="600" src="./images/13.png">
</p>

14. Внесите изменения из произвольной ветки `feature/add_reply` в `master` через `Merge`.

Внёс изменения

15. Убедитесь, что нет собранного артефакта в сборке по ветке `master`.

<p align="center">
  <img width="1200" height="600" src="./images/14.png">
</p>

16. Настройте конфигурацию так, чтобы она собирала `.jar` в артефакты сборки.

<p align="center">
  <img width="1200" height="600" src="./images/17.png">
</p>

17. Проведите повторную сборку мастера, убедитесь, что сбора прошла успешно и артефакты собраны.

<p align="center">
  <img width="1200" height="600" src="./images/15.png">
</p>

<p align="center">
  <img width="1200" height="600" src="./images/16.png">
</p>

18. Проверьте, что конфигурация в репозитории содержит все настройки конфигурации из teamcity.

[Настройки конфигурации из teamcity](https://github.com/george25031996/example-teamcity/tree/master/.teamcity)

19. В ответе пришлите ссылку на репозиторий.

[Репозиторий example-teamcity](https://github.com/george25031996/example-teamcity)

