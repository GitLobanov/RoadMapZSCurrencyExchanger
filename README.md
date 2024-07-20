Порядок разработки:

- создаем модели сущностей бд.

- создаем DTO для обмена валют. Target/base currency, rate, amount, convertedAmount

- создание CrudRepository. Interface от котого будут имплементиться остальные репозитории данных
- также создаем CurrencyRepository, ExchangeRateRepository. Имплпментим interface.
описываем и овераидим методы работы с бд: поиск по значению, crud операции.
для методов findById неплохо использовать Optional

- создание ContextListener.
описываем подключение к базе данных. Используется пул HikariCP, вместо обычного JDBC

- создаем Filter. Сервлетный фильтр занимается предварительной обработкой запроса, прежде чем тот попадает в сервлет, и/или последующей обработкой ответа, исходящего из сервлета.
преобрзование ответов в json файл

- создаем Utils по мере разработки. Отдельно выведенные методы для работы

- создаем CurrencyServlet
делаем инит нужного репозитория, получая его из контекста сервлета. (new ServletConfig.getServletContext().getAttribute)
оверайдим doGet. Обрабатываем возможные ошибки, получаем данные из бд, через репозиторий. Выводим json данных
- также создаем CurrenciesServlet (вывод всех валют), CurrencyExchangeRateServlet (вывод обменянов валют по кодам), CurrencyExchangeRateыServlet (вывод обменов валют), ExchangeServlet (обмен валют)


В ходе работы собирался War файл, производился deploy на удаленный сервер.
В качестве сервиса выступал: TimeWeb

Порядок дейстивий:
- Аренда сервера. Я также арендовал отдельно базу данных, но можно установить также на одном сервере
- Установка JDK, JRE, TomCat

Производил настройку удаленной машины Linux для работы с TomCat.
Ресурс с инструкцией (https://www.geeksforgeeks.org/how-to-install-apache-tomcat-8-on-linux/?ysclid=lytnyxvqh640412217)

Пример deploy взял из видео: https://www.youtube.com/watch?v=UC0VzH1ICEA

весь список литературы:

- Java Servlets. Сервлеты https://javarush.com/groups/posts/2529-chastjh-5-servletih-pishem-prostoe-veb-prilozhenie?ysclid=lys974y9hz468466485
- Установка TomCat в Linux систему. Консоль. https://www.geeksforgeeks.org/how-to-install-apache-tomcat-8-on-linux/?ysclid=lytnyxvqh640412217
- Deploy telegrem bot. Example deploy timeweb, vds server https://www.youtube.com/watch?v=UC0VzH1ICEA
- Сервлетный фильтр. Servlet fitler. https://java-online.ru/servlet-filter.xhtml
- HikariCP. Пул соединений к базе данных. https://egorzimowski.com/2022/10/22/hikari-connection-pool-jdbc/
- Java Servlet Context Listener Example - Java Code Geeks https://examples.javacodegeeks.com/java-development/enterprise-java/servlet/java-servlet-context-listener-example/
