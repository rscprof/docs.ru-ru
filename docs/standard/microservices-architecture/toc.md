

# [Микрослужбы .NET: архитектура контейнерных приложений .NET](index.md)


## [Общие сведения о контейнерах и Docker](container-docker-introduction/index.md)


### [Что такое Docker?](container-docker-introduction/docker-defined.md)


### [Терминология Docker](container-docker-introduction/docker-terminology.md)


### [Контейнеры, образы и реестры Docker](container-docker-introduction/docker-containers-images-registries.md)


## [Выбор между .NET Core и .NET Framework для контейнеров Docker](net-core-net-framework-containers/index.md)


### [Общие рекомендации](net-core-net-framework-containers/general-guidance.md)


### [Выбор .NET Core для контейнеров Docker](net-core-net-framework-containers/net-core-container-scenarios.md)


### [Выбор .NET Framework для контейнеров Docker](net-core-net-framework-containers/net-framework-container-scenarios.md)


### [Таблица для принятия решений: использование платформ .NET для Docker](net-core-net-framework-containers/container-framework-choice-factors.md)


### [Для какой ОС использовать контейнеры .NET](net-core-net-framework-containers/net-container-os-targets.md)


### [Официальные .NET-образы Docker](net-core-net-framework-containers/official-net-docker-images.md)


## [Проектирование архитектуры приложений на основе контейнеров и микрослужб](architect-microservice-container-applications/index.md)


### [Контейнеризация монолитных приложений](architect-microservice-container-applications/containerize-monolithic-applications.md)


### [Состояние и данные в приложениях Docker](architect-microservice-container-applications/docker-application-state-data.md)


### [Сервисноориентированная архитектура](architect-microservice-container-applications/service-oriented-architecture.md)


### [Архитектура микрослужб](architect-microservice-container-applications/microservices-architecture.md)


### [Владение данными в каждой микрослужбе](architect-microservice-container-applications/data-sovereignty-per-microservice.md)


### [Логическая и физическая архитектура](architect-microservice-container-applications/logical-versus-physical-architecture.md)


### [Распределенное управление данными: проблемы и решения](architect-microservice-container-applications/distributed-data-management.md)


### [Определение границ модели предметной области для каждой микрослужбы](architect-microservice-container-applications/identify-microservice-domain-model-boundaries.md)


### [Взаимодействие между микрослужбами](architect-microservice-container-applications/communication-between-microservices.md)


### [Асинхронное взаимодействие на основе сообщений](architect-microservice-container-applications/asynchronous-message-based-communication.md)


### [Создание, развитие и управление версиями API-интерфейсов и контрактов микрослужб](architect-microservice-container-applications/maintain-microservice-apis.md)


### [Возможность адресации микрослужб и реестр службы](architect-microservice-container-applications/microservices-addressability-service-registry.md)


### [Создание составного пользовательского интерфейса на основе микрослужб, включая создание его визуальной формы и структуры несколькими микрослужбами](architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md)


### [Устойчивость и высокий уровень доступности в микрослужбах](architect-microservice-container-applications/resilient-high-availability-microservices.md)


### [Управление микрослужбами и многоконтейнерными приложениями для обеспечения высокого уровня масштабируемости и доступности](architect-microservice-container-applications/scalable-available-multi-container-microservice-applications.md)


### [Использование Azure Service Fabric](architect-microservice-container-applications/using-azure-service-fabric.md)


## [Процесс разработки для приложений на основе Docker](docker-application-development-process/index.md)


### [Рабочий процесс разработки для приложений Docker](docker-application-development-process/docker-app-development-workflow.md)


## [Развертывание одноконтейнерных веб-приложений .NET Core на узлах Linux или Windows Nano Server](net-core-single-containers-linux-windows-server-hosts/index.md)


## [Перенос устаревших монолитных приложений .NET Framework в контейнеры Windows](containerize-net-framework-applications/index.md)


## [Проектирование и разработка приложений .NET на основе множества контейнеров и микрослужб](multi-container-microservice-net-applications/index.md)


### [Разработка ориентированного на микрослужбы приложения](multi-container-microservice-net-applications/microservice-application-design.md)


### [Создание простой CRUD-микрослужбы, основанной на данных](multi-container-microservice-net-applications/data-driven-crud-microservice.md)


### [Определение многоконтейнерного приложения с помощью docker-compose.yml](multi-container-microservice-net-applications/multi-container-applications-docker-compose.md)


### [Использование сервера баз данных, работающего в качестве контейнера](multi-container-microservice-net-applications/database-server-container.md)


### [Реализация взаимодействия между микрослужбами на основе событий (события интеграции)](multi-container-microservice-net-applications/integration-event-based-microservice-communications.md)


### [Реализация шины событий с помощью RabbitMQ для среды разработки или тестирования](multi-container-microservice-net-applications/rabbitmq-event-bus-development-test-environment.md)


### [Подписка на события](multi-container-microservice-net-applications/subscribe-events.md)


### [Тестирование служб и веб-приложений ASP.NET Core](multi-container-microservice-net-applications/test-aspnet-core-services-web-apps.md)


## [Использование микрослужб с шаблонами DDD и CQRS для решения сложных бизнес-задач](microservice-ddd-cqrs-patterns/index.md)


### [Применение в микрослужбе упрощенных шаблонов CQRS и DDD](microservice-ddd-cqrs-patterns/apply-simplified-microservice-cqrs-ddd-patterns.md)


### [Применение подходов CQRS и CQS в микрослужбе DDD в eShopOnContainers](microservice-ddd-cqrs-patterns/eshoponcontainers-cqrs-ddd-microservice.md)


### [Реализация операций чтения и запросов в микрослужбе CQRS](microservice-ddd-cqrs-patterns/cqrs-microservice-reads.md)


### [Проектирование микрослужбы, ориентированной на DDD](microservice-ddd-cqrs-patterns/ddd-oriented-microservice.md)


### [Проектирование модели предметной области микрослужбы](microservice-ddd-cqrs-patterns/microservice-domain-model.md)


### [Реализация модели предметной области микрослужбы с помощью .NET Core](microservice-ddd-cqrs-patterns/net-core-microservice-domain-model.md)


### [Seedwork (многократно используемые базовые классы и интерфейсы для модели предметной области)](microservice-ddd-cqrs-patterns/seedwork-domain-model-base-classes-interfaces.md)


### [Реализации объектов значений](microservice-ddd-cqrs-patterns/implement-value-objects.md)


### [Использование классов перечисления вместо типов перечисления](microservice-ddd-cqrs-patterns/enumeration-classes-over-enum-types.md)


### [Проектирование проверок на уровне модели предметной области](microservice-ddd-cqrs-patterns/domain-model-layer-validations.md)


### [Проверка на стороне клиента (проверка на уровнях представления)](microservice-ddd-cqrs-patterns/client-side-validation.md)


### [События предметной области: проектирование и реализация](microservice-ddd-cqrs-patterns/domain-events-design-implementation.md)


### [Проектирование уровня сохраняемости инфраструктуры](microservice-ddd-cqrs-patterns/infrastructure-persistence-layer-design.md)


### [Реализация уровня сохраняемости инфраструктуры с помощью Entity Framework Core](microservice-ddd-cqrs-patterns/infrastructure-persistence-layer-implemenation-entity-framework-core.md)


### [Использование баз данных NoSQL в качестве инфраструктуры сохраняемости](microservice-ddd-cqrs-patterns/nosql-database-persistence-infrastructure.md)


### [Разработка веб-API и уровня приложений для микрослужб](microservice-ddd-cqrs-patterns/microservice-application-layer-web-api-design.md)


### [Реализация уровня приложений для микрослужб с помощью веб-API](microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)


## [Реализация устойчивых приложений](implement-resilient-applications/index.md)


### [Обработка частичного сбоя](implement-resilient-applications/handle-partial-failure.md)


### [Стратегии для обработки частичного сбоя](implement-resilient-applications/partial-failure-strategies.md)


### [Реализация повторных попыток с экспоненциальной выдержкой](implement-resilient-applications/implement-retries-exponential-backoff.md)


### [Реализация устойчивых SQL-подключений Entity Framework Core](implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md)


### [Реализация настраиваемых повторных попыток HTTP-вызова с экспоненциальной выдержкой](implement-resilient-applications/implement-custom-http-call-retries-exponential-backoff.md)


### [Реализация повторных попыток HTTP-вызова с экспоненциальной выдержкой при помощи библиотеки Polly](implement-resilient-applications/implement-http-call-retries-exponential-backoff-polly.md)


### [Реализация шаблона размыкателя цепи](implement-resilient-applications/implement-circuit-breaker-pattern.md)


### [Мониторинг работоспособности](implement-resilient-applications/monitor-app-health.md)


## [Обеспечение безопасности веб-приложений и микрослужб .NET](secure-net-microservices-web-applications/index.md)


### [Об авторизации в веб-приложениях и микрослужбах .NET](secure-net-microservices-web-applications/authorization-net-microservices-web-applications.md)


### [Безопасное хранение секретов приложения во время разработки](secure-net-microservices-web-applications/developer-app-secrets-storage.md)


### [Использование Azure Key Vault для защиты секретов во время эксплуатации](secure-net-microservices-web-applications/azure-key-vault-protects-secrets.md)


## [Главные выводы](key-takeaways.md)