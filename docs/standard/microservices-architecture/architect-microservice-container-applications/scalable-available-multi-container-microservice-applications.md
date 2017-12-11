---
title: "Оркестрация микрослужбами и несколькими контейнера приложений высокий уровень масштабируемости и доступности"
description: "Архитектура Микрослужбами .NET для приложений .NET в контейнерах | Оркестрация микрослужбами и несколькими контейнера приложений высокий уровень масштабируемости и доступности"
keywords: "Docker, микрослужбы, ASP.NET, контейнер"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: ec33901a0ddc9e5b58263440b0e4399e687c6904
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2017
---
# <a name="orchestrating-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a><span data-ttu-id="3fbc7-104">Оркестрация микрослужбами и несколькими контейнера приложений высокий уровень масштабируемости и доступности</span><span class="sxs-lookup"><span data-stu-id="3fbc7-104">Orchestrating microservices and multi-container applications for high scalability and availability</span></span>

<span data-ttu-id="3fbc7-105">С помощью orchestrators готовый приложений важно в том случае, если приложение основана на микрослужбами или просто разнесены по нескольким контейнерам.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-105">Using orchestrators for production-ready applications is essential if your application is based on microservices or simply split across multiple containers.</span></span> <span data-ttu-id="3fbc7-106">Ранее, представленном в подход на основе микрослужбу, каждый микрослужбу владеет его модели и данные, чтобы он будет автономной для разработки и развертывания точки зрения.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-106">As introduced previously, in a microservice-based approach, each microservice owns its model and data so that it will be autonomous from a development and deployment point of view.</span></span> <span data-ttu-id="3fbc7-107">Но даже если у вас есть более традиционным приложения, состоящего из нескольких служб (например, SOA), вы также будете иметь несколько контейнеров или служб, образующих одной бизнес-приложений, необходимо развернуть как распределенная система.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-107">But even if you have a more traditional application that is composed of multiple services (like SOA), you will also have multiple containers or services comprising a single business application that need to be deployed as a distributed system.</span></span> <span data-ttu-id="3fbc7-108">Эти виды систем сложны для горизонтального масштабирования и управления ими; Таким образом абсолютной необходимости orchestrator, чтобы приложение, в рабочей среде и масштабируемость нескольких контейнера.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-108">These kinds of systems are complex to scale out and manage; therefore, you absolutely need an orchestrator if you want to have a production-ready and scalable multi-container application.</span></span>

<span data-ttu-id="3fbc7-109">На рисунке 4-23 иллюстрирует развертывание на кластеры, состоящие из нескольких микрослужбами (контейнеров) приложения.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-109">Figure 4-23 illustrates deployment into a cluster of an application composed of multiple microservices (containers).</span></span>

![](./media/image23.PNG)

<span data-ttu-id="3fbc7-110">**На рисунке 4-23**.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-110">**Figure 4-23**.</span></span> <span data-ttu-id="3fbc7-111">Кластер состоит из контейнеров</span><span class="sxs-lookup"><span data-stu-id="3fbc7-111">A cluster of containers</span></span>

<span data-ttu-id="3fbc7-112">Он будет выглядеть логического подхода.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-112">It looks like a logical approach.</span></span> <span data-ttu-id="3fbc7-113">Но, как вы балансировки нагрузки обработки и маршрутизации оркестрация эти состоят приложений?</span><span class="sxs-lookup"><span data-stu-id="3fbc7-113">But how are you handling load-balancing, routing, and orchestrating these composed applications?</span></span>

<span data-ttu-id="3fbc7-114">Обычный подсистемы Docker в одном узлах Docker потребностям управление экземплярами одного образа на одном узле, но не хватает, когда дело доходит до управление несколько контейнеров, которые развернуты на нескольких узлах для более сложных распределенных приложений.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-114">The plain Docker Engine in single Docker hosts meets the needs of managing single image instances on one host, but it falls short when it comes to managing multiple containers deployed on multiple hosts for more complex distributed applications.</span></span> <span data-ttu-id="3fbc7-115">В большинстве случаев требуется платформа управления, который будет автоматически запустить контейнеры масштабирования контейнеры с несколькими экземплярами на изображение, приостанавливать их или отключать их при необходимости и в идеале управляют как при доступе к ресурсам сети и данных хранилище.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-115">In most cases, you need a management platform that will automatically start containers, scale-out containers with multiple instances per image, suspend them or shut them down when needed, and ideally also control how they access resources like the network and data storage.</span></span>

<span data-ttu-id="3fbc7-116">Выходит за пределы управления индивидуальных контейнеров или очень простой составных приложений, а также Постепенная больших корпоративных приложений с микрослужбами, необходимо включить orchestration и кластеризации платформы.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-116">To go beyond the management of individual containers or very simple composed apps and move toward larger enterprise applications with microservices, you must turn to orchestration and clustering platforms.</span></span>

<span data-ttu-id="3fbc7-117">С архитектуры и разработки точки зрения при построении крупных предприятий, состоящие из приложений на основе микрослужбами важно понимать следующие платформы и продукты, которые поддерживают сложные сценарии:</span><span class="sxs-lookup"><span data-stu-id="3fbc7-117">From an architecture and development point of view, if you are building large enterprise composed of microservices-based applications, it is important to understand the following platforms and products that support advanced scenarios:</span></span>

<span data-ttu-id="3fbc7-118">**Кластеры и orchestrators**.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-118">**Clusters and orchestrators**.</span></span> <span data-ttu-id="3fbc7-119">Когда необходимо получить масштабировании приложений на множестве узлов Docker, как при больших микрослужбу приложением, крайне важно иметь возможность управлять все узлы в одном кластере посредством абстрагирования сложности базовой платформы.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-119">When you need to scale out applications across many Docker hosts, as when a large microservice-based application, it is critical to be able to manage all those hosts as a single cluster by abstracting the complexity of the underlying platform.</span></span> <span data-ttu-id="3fbc7-120">Это кластеров контейнера и orchestrators предоставляют.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-120">That is what the container clusters and orchestrators provide.</span></span> <span data-ttu-id="3fbc7-121">Примеры orchestrators: Azure Service Fabric, Kubernetes, помощью Docker Swarm и Mesosphere DC/OS.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-121">Examples of orchestrators are Azure Service Fabric, Kubernetes, Docker Swarm and Mesosphere DC/OS.</span></span> <span data-ttu-id="3fbc7-122">Последние три orchestrators открытым исходным кодом, доступны в Azure через службы контейнера Azure.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-122">The last three open-source orchestrators are available in Azure through Azure Container Service.</span></span>

<span data-ttu-id="3fbc7-123">**Планировщики**.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-123">**Schedulers**.</span></span> <span data-ttu-id="3fbc7-124">*Планирование* означает возможность администратор может запустить контейнеры в кластере, поэтому они также предоставляют пользовательский Интерфейс.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-124">*Scheduling* means to have the capability for an administrator to launch containers in a cluster so they also provide a UI.</span></span> <span data-ttu-id="3fbc7-125">Планировщик кластера имеет несколько функций: для эффективного использования ресурсов кластера, чтобы задать ограничения, предоставленный пользователем, эффективно контейнеры балансировки нагрузки между узлами или узлы и быть надежными от ошибок, обеспечивая высокий доступность.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-125">A cluster scheduler has several responsibilities: to use the cluster’s resources efficiently, to set the constraints provided by the user, to efficiently load-balance containers across nodes or hosts, and to be robust against errors while providing high availability.</span></span>

<span data-ttu-id="3fbc7-126">Основные понятия кластера и планировщик тесно связаны, поэтому продукты, предоставляемые различными поставщиками, часто содержат оба набора возможностей.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-126">The concepts of a cluster and a scheduler are closely related, so the products provided by different vendors often provide both sets of capabilities.</span></span> <span data-ttu-id="3fbc7-127">Ниже перечислены наиболее важные платформы и программного обеспечения варианты выбора для кластеров и планировщики.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-127">The following list shows the most important platform and software choices you have for clusters and schedulers.</span></span> <span data-ttu-id="3fbc7-128">Эти orchestrators обычно предоставляются в общедоступных облаках, таких как Azure.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-128">These orchestrators are generally offered in public clouds like Azure.</span></span>

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a><span data-ttu-id="3fbc7-129">Программное обеспечение платформы для контейнера кластеризации, управление и планирование</span><span class="sxs-lookup"><span data-stu-id="3fbc7-129">Software platforms for container clustering, orchestration, and scheduling</span></span>

<span data-ttu-id="3fbc7-130">Kubernetes</span><span class="sxs-lookup"><span data-stu-id="3fbc7-130">Kubernetes</span></span>

![https://PBS.twimg.com/Media/BT\_pEfqCAAAiVyz.png](./media/image24.png)

> <span data-ttu-id="3fbc7-132">Kubernetes — это продукт с открытым исходным кодом, предоставляет функциональные возможности, в диапазоне от инфраструктуры кластера и контейнера, по возможности, управляя операциями.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-132">Kubernetes is an open-source product that provides functionality that ranges from cluster infrastructure and container scheduling to orchestrating capabilities.</span></span> <span data-ttu-id="3fbc7-133">Он позволяет автоматизировать развертывание, масштабирование и операций контейнеров приложения ко всем кластерам узлов.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-133">It lets you automate deployment, scaling, and operations of application containers across clusters of hosts.</span></span>
>
> <span data-ttu-id="3fbc7-134">Kubernetes предоставляет ориентированные на контейнер инфраструктуру, которая группирует контейнеров приложений в логические устройства для упрощения управления и обнаружения.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-134">Kubernetes provides a container-centric infrastructure that groups application containers into logical units for easy management and discovery.</span></span>
>
> <span data-ttu-id="3fbc7-135">Kubernetes зрелой в Linux, менее зрелой в Windows.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-135">Kubernetes is mature in Linux, less mature in Windows.</span></span>

<span data-ttu-id="3fbc7-136">Docker группу мелких объектов</span><span class="sxs-lookup"><span data-stu-id="3fbc7-136">Docker Swarm</span></span>

![http://rancher.com/WP-Content/Themes/rancher-2016/Assets/Images/swarm.PNG?v=2016-07-10-AM](./media/image25.png)

> <span data-ttu-id="3fbc7-138">Docker группу мелких объектов позволяет кластера и запланировать контейнеры Docker.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-138">Docker Swarm lets you cluster and schedule Docker containers.</span></span> <span data-ttu-id="3fbc7-139">С помощью группу мелких объектов, можно включить пул узлах Docker в один, виртуальный узел Docker.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-139">By using Swarm, you can turn a pool of Docker hosts into a single, virtual Docker host.</span></span> <span data-ttu-id="3fbc7-140">Клиенты могут выполнять запросы API на скапливаются так же, как они выполнять на узлах, это означает, что группу мелких объектов позволяет с легкостью приложениям масштабироваться с несколькими узлами.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-140">Clients can make API requests to Swarm the same way they do to hosts, meaning that Swarm makes it easy for applications to scale to multiple hosts.</span></span>
>
> <span data-ttu-id="3fbc7-141">Docker группу мелких объектов — это продукт из Docker компании.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-141">Docker Swarm is a product from Docker, the company.</span></span>
>
> <span data-ttu-id="3fbc7-142">Docker v1.12 или более поздней версии может выполнять собственный и встроенные скапливаются режим.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-142">Docker v1.12 or later can run native and built-in Swarm Mode.</span></span>

<span data-ttu-id="3fbc7-143">Mesosphere DC/OS</span><span class="sxs-lookup"><span data-stu-id="3fbc7-143">Mesosphere DC/OS</span></span>

![https://mesosphere.com/WP-Content/uploads/2016/04/Logo-Horizontal-styled.PNG](./media/image26.png)

> <span data-ttu-id="3fbc7-145">Mesosphere DC/OS предприятия (с учетом Apache Mesos) — это платформа готов для выполнения контейнеров и распределенных приложений.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-145">Mesosphere Enterprise DC/OS (based on Apache Mesos) is a production-ready platform for running containers and distributed applications.</span></span>
>
> <span data-ttu-id="3fbc7-146">Контроллер домена/OS осуществляется посредством абстрагирования коллекцию ресурсов, доступных в кластере и предоставление доступа к этим ресурсам компоненты, созданные на основе.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-146">DC/OS works by abstracting a collection of the resources available in the cluster and making those resources available to components built on top of it.</span></span> <span data-ttu-id="3fbc7-147">Как планировщик, интегрированные с контроллера домена/OS обычно используется Marathon.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-147">Marathon is usually used as a scheduler integrated with DC/OS.</span></span>
>
> <span data-ttu-id="3fbc7-148">Контроллер домена/OS зрелой в Linux, менее зрелой в Windows.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-148">DC/OS is mature in Linux, less mature in Windows.</span></span>

<span data-ttu-id="3fbc7-149">Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="3fbc7-149">Azure Service Fabric</span></span>

![https://Azure.Microsoft.com/svghandler/Service-Fabric?Width=600&Height=315](./media/image27.png)

> <span data-ttu-id="3fbc7-151">[Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) — это платформа микрослужбами Microsoft для создания приложений.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-151">[Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) is a Microsoft microservices platform for building applications.</span></span> <span data-ttu-id="3fbc7-152">Это [orchestrator](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction) из службы и создает кластеры компьютеров.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-152">It is an [orchestrator](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction) of services and creates clusters of machines.</span></span> <span data-ttu-id="3fbc7-153">Service Fabric можно развернуть службы, как контейнеры, или как обычный процессы.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-153">Service Fabric can deploy services as containers or as plain processes.</span></span> <span data-ttu-id="3fbc7-154">Это возможно даже набора служб в процессах со службами в контейнерах одного приложения и кластера.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-154">It can even mix services in processes with services in containers within the same application and cluster.</span></span>
>
> <span data-ttu-id="3fbc7-155">Service Fabric предоставляет дополнительные и необязательные конкретные [Service Fabric модели программирования ](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework) как [служб с отслеживанием состояния](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) и [службы Reliable Actor](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).</span><span class="sxs-lookup"><span data-stu-id="3fbc7-155">Service Fabric provides additional and optional prescriptive [Service Fabric programming models ](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework) like [stateful services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) and [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).</span></span>
>
> <span data-ttu-id="3fbc7-156">Service Fabric для старшего в Windows (годы развивается в Windows), меньше зрелой в Linux.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-156">Service Fabric is mature in Windows (years evolving in Windows), less mature in Linux.</span></span> 
> <span data-ttu-id="3fbc7-157">Контейнеры Linux и Windows, поддерживаются в Service Fabric с момента 2017 г.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-157">Both Linux and Windows containers are supported in Service Fabric since 2017.</span></span>

## <a name="using-container-based-orchestrators-in-microsoft-azure"></a><span data-ttu-id="3fbc7-158">С помощью orchestrators на основе контейнера в Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="3fbc7-158">Using container-based orchestrators in Microsoft Azure</span></span>

<span data-ttu-id="3fbc7-159">Несколько поставщиков облачных обеспечивают поддержку контейнеры Docker, а также кластеры Docker и поддержки orchestration, включая Microsoft Azure, контейнер службы Amazon EC2 и подсистема контейнеров Google.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-159">Several cloud vendors offer Docker containers support plus Docker clusters and orchestration support, including Microsoft Azure, Amazon EC2 Container Service, and Google Container Engine.</span></span> <span data-ttu-id="3fbc7-160">Microsoft Azure поддерживает Docker кластера и orchestrator через службу контейнера Azure (ACS), как описано в следующем разделе.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-160">Microsoft Azure provides Docker cluster and orchestrator support through Azure Container Service (ACS), as explained in the next section.</span></span>

<span data-ttu-id="3fbc7-161">Другой вариант — использовать Microsoft Azure Service Fabric (микрослужбами платформы), поддерживающий на основе Linux и Windows контейнеры Docker.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-161">Another choice is to use Microsoft Azure Service Fabric (a microservices platform), which also supports Docker based on Linux and Windows Containers.</span></span> <span data-ttu-id="3fbc7-162">Service Fabric работает на Azure или любые другие облака, а также [локальной](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere).</span><span class="sxs-lookup"><span data-stu-id="3fbc7-162">Service Fabric runs on Azure or any other cloud, and also runs [on-premises](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere).</span></span>

## <a name="using-azure-container-service"></a><span data-ttu-id="3fbc7-163">С помощью службы Azure контейнера</span><span class="sxs-lookup"><span data-stu-id="3fbc7-163">Using Azure Container Service</span></span>

<span data-ttu-id="3fbc7-164">Кластер с Docker пулов на нескольких узлах Docker и предоставляет их как один виртуальный узел Docker, чтобы можно было развернуть несколько контейнеров в кластер.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-164">A Docker cluster pools multiple Docker hosts and exposes them as a single virtual Docker host, so you can deploy multiple containers into the cluster.</span></span> <span data-ttu-id="3fbc7-165">Кластер будет обрабатывать сложные управления всё, как масштабируемость, работоспособности и т. д.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-165">The cluster will handle all the complex management plumbing, like scalability, health, and so forth.</span></span> <span data-ttu-id="3fbc7-166">Рис. 4-24 представляет сопоставление для контейнера службы Azure (ACS) в кластере Docker для составных приложений.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-166">Figure 4-24 represents how a Docker cluster for composed applications maps to Azure Container Service (ACS).</span></span>

<span data-ttu-id="3fbc7-167">ACS предоставляет способ для упрощения создания, настройки и управления, кластера виртуальных машин, настроенных для запуска приложений в контейнерах.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-167">ACS provides a way to simplify the creation, configuration, and management of a cluster of virtual machines that are preconfigured to run containerized applications.</span></span> <span data-ttu-id="3fbc7-168">С помощью оптимизированного конфигурации популярных средств планирования и orchestration открытым исходным кодом, ACS позволяет использовать существующие навыки или отрисовки в теле большое и возрастающее опытом сообщества для развертывания и управления контейнера-приложениям на базе Microsoft Azure .</span><span class="sxs-lookup"><span data-stu-id="3fbc7-168">Using an optimized configuration of popular open-source scheduling and orchestration tools, ACS enables you to use your existing skills or draw on a large and growing body of community expertise to deploy and manage container-based applications on Microsoft Azure.</span></span>

<span data-ttu-id="3fbc7-169">Служба Azure контейнера оптимизирует конфигурации популярных Docker кластеризации открытым исходным кодом и технологии специально для Azure.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-169">Azure Container Service optimizes the configuration of popular Docker clustering open source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="3fbc7-170">Вы получаете открытое решение, который обеспечивает совместимость для вашего контейнеров и конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-170">You get an open solution that offers portability for both your containers and your application configuration.</span></span> <span data-ttu-id="3fbc7-171">Выберите размер, количество узлов и средств orchestrator и контейнер службы обрабатывает все остальное.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-171">You select the size, the number of hosts, and the orchestrator tools, and Container Service handles everything else.</span></span>

![](./media/image28.png)

<span data-ttu-id="3fbc7-172">**Рис. 4-24**.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-172">**Figure 4-24**.</span></span> <span data-ttu-id="3fbc7-173">Кластеризация вариантов в контейнере службы Azure</span><span class="sxs-lookup"><span data-stu-id="3fbc7-173">Clustering choices in Azure Container Service</span></span>

<span data-ttu-id="3fbc7-174">ACS использует образы Docker, чтобы обеспечить полную переносимость контейнеры вашего приложения.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-174">ACS leverages Docker images to ensure that your application containers are fully portable.</span></span> <span data-ttu-id="3fbc7-175">Он поддерживает выбор orchestration с открытым исходным кодом платформы, такие как контроллер домена/OS (на платформе Apache Mesos), Kubernetes (созданного с помощью Google) и помощью Docker Swarm, чтобы убедиться, что эти приложения могут масштабироваться до тысяч или даже десятков тысяч контейнеров.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-175">It supports your choice of open-source orchestration platforms like DC/OS (powered by Apache Mesos), Kubernetes (originally created by Google), and Docker Swarm, to ensure that these applications can be scaled to thousands or even tens of thousands of containers.</span></span>

<span data-ttu-id="3fbc7-176">Служба контейнера Azure позволяет воспользоваться преимуществами возможности корпоративного уровня Azure одновременно сохраняя переносимость приложения, включая orchestration уровнями.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-176">The Azure Container service enables you to take advantage of the enterprise-grade features of Azure while still maintaining application portability, including at the orchestration layers.</span></span>

![](./media/image29.png)

<span data-ttu-id="3fbc7-177">**На рисунке 4-25**.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-177">**Figure 4-25**.</span></span> <span data-ttu-id="3fbc7-178">Orchestrators в ACS</span><span class="sxs-lookup"><span data-stu-id="3fbc7-178">Orchestrators in ACS</span></span>

<span data-ttu-id="3fbc7-179">Как показано на рисунке 4-25, контейнера службы Azure — просто инфраструктуры Azure для развертывания контроллера домена/OS, Kubernetes или помощью Docker Swarm, но ACS не реализует все дополнительные orchestrator.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-179">As shown in Figure 4-25, Azure Container Service is simply the infrastructure provided by Azure in order to deploy DC/OS, Kubernetes or Docker Swarm, but ACS does not implement any additional orchestrator.</span></span> <span data-ttu-id="3fbc7-180">Таким образом ACS не orchestrator таким образом, только это инфраструктура, которая использует существующий orchestrators открытым исходным кодом для контейнеров.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-180">Therefore, ACS is not an orchestrator as such, only an infrastructure that leverages existing open-source orchestrators for containers.</span></span>

<span data-ttu-id="3fbc7-181">С точки зрения использования службы Azure контейнера предназначена для предоставления среды размещения контейнера с помощью популярных средств с открытым исходным кодом и технологий.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-181">From a usage perspective, the goal of Azure Container Service is to provide a container hosting environment by using popular open-source tools and technologies.</span></span> <span data-ttu-id="3fbc7-182">Для этого он предоставляет стандартные конечные точки API для вашей выбранной orchestrator.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-182">To this end, it exposes the standard API endpoints for your chosen orchestrator.</span></span> <span data-ttu-id="3fbc7-183">Используя эти конечные точки, может использовать программное обеспечение, которое может взаимодействовать с этими конечными точками.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-183">By using these endpoints, you can leverage any software that can talk to those endpoints.</span></span> <span data-ttu-id="3fbc7-184">Например в случае с помощью Docker Swarm конечной точки, можно использовать интерфейс командной строки Docker (CLI).</span><span class="sxs-lookup"><span data-stu-id="3fbc7-184">For example, in the case of the Docker Swarm endpoint, you might choose to use the Docker command-line interface (CLI).</span></span> <span data-ttu-id="3fbc7-185">Для контроллера домена/OS можно использовать контроллер домена/OS CLI.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-185">For DC/OS, you might choose to use the DC/OS CLI.</span></span>

### <a name="getting-started-with-azure-container-service"></a><span data-ttu-id="3fbc7-186">Приступая к работе со службой контейнера Azure</span><span class="sxs-lookup"><span data-stu-id="3fbc7-186">Getting started with Azure Container Service</span></span> 

<span data-ttu-id="3fbc7-187">Чтобы начать использование контейнера службы Azure, вы развернуть кластер контейнера службы Azure на портале Azure с помощью шаблона Azure Resource Manager или [CLI](https://docs.microsoft.com/cli/azure/install-azure-cli).</span><span class="sxs-lookup"><span data-stu-id="3fbc7-187">To begin using Azure Container Service, you deploy an Azure Container Service cluster from the Azure portal by using an Azure Resource Manager template or the [CLI](https://docs.microsoft.com/cli/azure/install-azure-cli).</span></span> <span data-ttu-id="3fbc7-188">Доступные шаблоны включают [помощью Docker Swarm](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-swarm), [Kubernetes](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-kubernetes), и [DC/OS](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-dcos).</span><span class="sxs-lookup"><span data-stu-id="3fbc7-188">Available templates include [Docker Swarm](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-swarm), [Kubernetes](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-kubernetes), and [DC/OS](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-dcos).</span></span> <span data-ttu-id="3fbc7-189">Можно изменить шаблоны краткое руководство для включения дополнительных или дополнительные конфигурации Azure.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-189">The quickstart templates can be modified to include additional or advanced Azure configuration.</span></span> <span data-ttu-id="3fbc7-190">Дополнительные сведения о развертывании кластер контейнера службы Azure в разделе [развертывание кластера службы контейнера Azure](https://docs.microsoft.com/azure/container-service/container-service-deployment) на веб-сайте Azure.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-190">For more information on deploying an Azure Container Service cluster, see [Deploy an Azure Container Service cluster](https://docs.microsoft.com/azure/container-service/container-service-deployment) on the Azure website.</span></span>

<span data-ttu-id="3fbc7-191">Нет без сборов для любого программного обеспечения, установленного по умолчанию в рамках ACS.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-191">There are no fees for any of the software installed by default as part of ACS.</span></span> <span data-ttu-id="3fbc7-192">Все параметры по умолчанию, реализуются с программным обеспечением с открытым исходным кодом.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-192">All default options are implemented with open-source software.</span></span>

<span data-ttu-id="3fbc7-193">ACS в настоящее время доступна для ряда стандартных A, D, доменных служб Active Directory, G и GS виртуальных машин Linux в Azure.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-193">ACS is currently available for Standard A, D, DS, G, and GS series Linux virtual machines in Azure.</span></span> <span data-ttu-id="3fbc7-194">Плата взимается только для выбранных экземпляров вычислений, а также другие базовой инфраструктуры ресурсы, используемые, такие как хранилища и сети.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-194">You are charged only for the compute instances you choose, as well as the other underlying infrastructure resources consumed, such as storage and networking.</span></span> <span data-ttu-id="3fbc7-195">Отсутствуют добавочное накладные расходы для самого ACS.</span><span class="sxs-lookup"><span data-stu-id="3fbc7-195">There are no incremental charges for ACS itself.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="3fbc7-196">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="3fbc7-196">Additional resources</span></span>

-   <span data-ttu-id="3fbc7-197">**Введение в контейнер Docker размещения решений с помощью службы Azure контейнер**
    [*https://docs.microsoft.com/azure/container-service/container-service-intro*](https://docs.microsoft.com/azure/container-service/container-service-intro)</span><span class="sxs-lookup"><span data-stu-id="3fbc7-197">**Introduction to Docker container hosting solutions with Azure Container Service**
[*https://docs.microsoft.com/azure/container-service/container-service-intro*](https://docs.microsoft.com/azure/container-service/container-service-intro)</span></span>

-   <span data-ttu-id="3fbc7-198">**Общие сведения о docker группу мелких объектов**
    [*https://docs.docker.com/swarm/overview/*](https://docs.docker.com/swarm/overview/)</span><span class="sxs-lookup"><span data-stu-id="3fbc7-198">**Docker Swarm overview**
[*https://docs.docker.com/swarm/overview/*](https://docs.docker.com/swarm/overview/)</span></span>

-   <span data-ttu-id="3fbc7-199">**Общие сведения о режиме скапливаются**
    [*https://docs.docker.com/engine/swarm/*](https://docs.docker.com/engine/swarm/)</span><span class="sxs-lookup"><span data-stu-id="3fbc7-199">**Swarm mode overview**
[*https://docs.docker.com/engine/swarm/*](https://docs.docker.com/engine/swarm/)</span></span>

-   <span data-ttu-id="3fbc7-200">**Обзор DC/OS mesosphere**
    [*https://docs.mesosphere.com/1.7/overview/*](https://docs.mesosphere.com/1.7/overview/)</span><span class="sxs-lookup"><span data-stu-id="3fbc7-200">**Mesosphere DC/OS Overview**
[*https://docs.mesosphere.com/1.7/overview/*](https://docs.mesosphere.com/1.7/overview/)</span></span>

-   <span data-ttu-id="3fbc7-201">**Kubernetes.**</span><span class="sxs-lookup"><span data-stu-id="3fbc7-201">**Kubernetes.**</span></span> <span data-ttu-id="3fbc7-202">Официальный сайт. \\</span><span class="sxs-lookup"><span data-stu-id="3fbc7-202">The official site.\\</span></span>
    [<span data-ttu-id="3fbc7-203">*http://kubernetes.IO/*</span><span class="sxs-lookup"><span data-stu-id="3fbc7-203">*http://kubernetes.io/*</span></span>](http://kubernetes.io/)


>[!div class="step-by-step"]
<span data-ttu-id="3fbc7-204">[Предыдущие] (отказоустойчивое высокой доступности microservices.md) [Далее] (с помощью azure-service-fabric.md)</span><span class="sxs-lookup"><span data-stu-id="3fbc7-204">[Previous] (resilient-high-availability-microservices.md) [Next] (using-azure-service-fabric.md)</span></span>