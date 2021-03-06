# Тестовое задание "Веб-приложение поиска по ключевым словам через внешний веб-сервис"

1. ТРЕБОВАНИЯ

1.1. Обслуживать HTTP запросы по URL /search. В параметрах запроса
передается параметр “query”, содержащий ключевое слово для поиска.
Параметров может быть несколько, в этом случае мы работаем с
несколькими ключевыми словами. Пример
" http://localhost:8080/search?query=air&query=water ”. Предполагаем, что
клиент будет передавать только алфавитно-цифровые запросы в ASCII.

1.1.1. Наличие корректной поддержки русского языка в кодировке UTF-8
будет плюсом.

1.2. 
Сервис может обращаться к API Яндекса для поиска
( https://yandex.ru/dev/xml/doc/dg/concepts/get-request-docpage/ ) или любой
другой аналогичный API по выбору исполнителя.

1.2.1. В случае, если ключевых слов передано несколько, запросы должны
выполняться параллельно (по одному запросу на ключевое слово).

1.2.2. Должно быть ограничение на максимальное количество
одновременных http запросов, это значение нельзя превышать.

1.2.3. Если ключевых слов больше, необходимо организовать очередь
обработки так, чтобы больше указанного количества соединений не
открывалось.

1.2.4. По каждому слову ищем только первые 10[00] записей. Можно
использовать любые необходимые параметры запроса, если
необходимо.

1.3. Для каждого результата извлекаем основную ссылку, из ссылки берем
hostname, домен только второго уровня.

1.4. В результате работы приложения должна быть возвращена статистика по
разным доменам второго уровня, сколько раз в сумме использовался домен
по всем ключевым словам.

1.4.1. В случае, если по разным ключевым словам был найдены
идентичные ссылки хост должен учитываться один раз.

1.5. Результат http запроса должен быть предоставлен в формате JSON

1.6. Можно использовать любые open-source компоненты, доступные на maven
central или в репозитории typesafe или любых других публичных
репозиториях. Можно использовать любое средство разработки
веб-приложений, включая сервлеты, spring boot, mvc, play, spray - любые.

1.7. Приветствуются короткие решения, использующие сторонние компоненты.

2. Ожидаемый результат

2.1. Необходимо предоставить исходные коды приложения, на сервисе
github.com или аналогичном, с историей разработки.

2.1.1. Хорошая история коммитов, отображенные процессы приема
запросов на изменения (pull request) будут большим плюсом.

2.2. Приложение должно компилироваться и работать.

2.3. Приложение должно собираться однострочной командой при помощи
любого средства сборки (gradle, docker, ci)

2.4. Приложение должно запускаться одной командой, без необходимости
отдельно разворачивать какие-либо серверы приложений.



# Сборка
mvn install

# Запуск

java -jar Seacher.jar

* через UI - открыть http://localhost:8080 ввести в поле слова для поиска, разделенные пробелом
* Rest API - http://localhost:8080/search?query=air&query=water ответ в виде JSON


