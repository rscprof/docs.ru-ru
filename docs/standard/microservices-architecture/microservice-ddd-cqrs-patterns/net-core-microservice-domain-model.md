---
title: "Реализация модели домена микрослужбу с .NET Core"
description: "Архитектура Микрослужбами .NET для приложений .NET в контейнерах | Реализация модели домена микрослужбу с .NET Core"
keywords: "Docker, микрослужбы, ASP.NET, контейнер"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 26c480a82ad7bb806734decebdfbe5b4a07998e6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-a-microservice-domain-model-with-net-core"></a><span data-ttu-id="0b75d-104">Реализация модели домена микрослужбу с .NET Core</span><span class="sxs-lookup"><span data-stu-id="0b75d-104">Implementing a microservice domain model with .NET Core</span></span> 

<span data-ttu-id="0b75d-105">В предыдущем разделе были представлены основные принципы и шаблоны для проектирования модели домена.</span><span class="sxs-lookup"><span data-stu-id="0b75d-105">In the previous section, the fundamental design principles and patterns for designing a domain model were explained.</span></span> <span data-ttu-id="0b75d-106">Теперь настало время для изучения способов реализации модели домена с помощью .NET Core (plain C\# кода) и EF Core.</span><span class="sxs-lookup"><span data-stu-id="0b75d-106">Now it is time to explore possible ways to implement the domain model by using .NET Core (plain C\# code) and EF Core.</span></span> <span data-ttu-id="0b75d-107">Обратите внимание, что модель домена будет состоять просто из кода.</span><span class="sxs-lookup"><span data-stu-id="0b75d-107">Note that your domain model will be composed simply of your code.</span></span> <span data-ttu-id="0b75d-108">Он будет иметь только EF основных требований модели, но не реальными зависимости EF.</span><span class="sxs-lookup"><span data-stu-id="0b75d-108">It will have just the EF Core model requirements, but not real dependencies on EF.</span></span> <span data-ttu-id="0b75d-109">Не следует жестких зависимостей или ссылки на основные EF или любые другие ORM в модели домена.</span><span class="sxs-lookup"><span data-stu-id="0b75d-109">You should not have hard dependencies or references to EF Core or any other ORM in your domain model.</span></span>

## <a name="domain-model-structure-in-a-custom-net-standard-library"></a><span data-ttu-id="0b75d-110">Структура модели домена в пользовательская библиотека .NET Standard</span><span class="sxs-lookup"><span data-stu-id="0b75d-110">Domain model structure in a custom .NET Standard library</span></span>

<span data-ttu-id="0b75d-111">Используется для приложений ссылки eShopOnContainers организации папки демонстрирует DDD модели для приложения.</span><span class="sxs-lookup"><span data-stu-id="0b75d-111">The folder organization used for the eShopOnContainers reference application demonstrates the DDD model for the application.</span></span> <span data-ttu-id="0b75d-112">Может оказаться, что организация другую папку более четко взаимодействует конструктора, выбранные для вашего приложения.</span><span class="sxs-lookup"><span data-stu-id="0b75d-112">You might find that a different folder organization more clearly communicates the design choices made for your application.</span></span> <span data-ttu-id="0b75d-113">Как видно на рисунке 9-10 упорядочивания модели домена существует два статистических выражений, статистическое выражение order и покупатель агрегатной функции.</span><span class="sxs-lookup"><span data-stu-id="0b75d-113">As you can see in Figure 9-10, in the ordering domain model there are two aggregates, the order aggregate and the buyer aggregate.</span></span> <span data-ttu-id="0b75d-114">Каждый агрегат — это группа домена сущностей и объектов значение, несмотря на то, что у вас может быть статистического выражения, состоящие из одного домена сущности (статистические корневой или корневую сущность) также.</span><span class="sxs-lookup"><span data-stu-id="0b75d-114">Each aggregate is a group of domain entities and value objects, although you could have an aggregate composed of a single domain entity (the aggregate root or root entity) as well.</span></span>

![](./media/image11.png)

<span data-ttu-id="0b75d-115">**Рис. 9-10**.</span><span class="sxs-lookup"><span data-stu-id="0b75d-115">**Figure 9-10**.</span></span> <span data-ttu-id="0b75d-116">Структура модели домена для упорядочивания микрослужбу в eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="0b75d-116">Domain model structure for the ordering microservice in eShopOnContainers</span></span>

<span data-ttu-id="0b75d-117">Кроме того уровень модели домена содержит контракты репозитория (интерфейсы), которые требований к инфраструктуре модели домена.</span><span class="sxs-lookup"><span data-stu-id="0b75d-117">Additionally, the domain model layer includes the repository contracts (interfaces) that are the infrastructure requirements of your domain model.</span></span> <span data-ttu-id="0b75d-118">Другими словами, эти интерфейсы express репозиториев, какие необходимо реализовать уровень инфраструктуры и каким образом.</span><span class="sxs-lookup"><span data-stu-id="0b75d-118">In other words, these interfaces express what repositories the infrastructure layer must implement and how.</span></span> <span data-ttu-id="0b75d-119">Очень важно, что реализация репозиториями располагаться за пределами уровень модели домена, в библиотеке инфраструктуры слоя, уровень модели домена не «окрашены» API или классы из технологий инфраструктуры, такие как Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="0b75d-119">It is critical that the implementation of the repositories be placed outside of the domain model layer, in the infrastructure layer library, so the domain model layer is not “contaminated” by API or classes from infrastructure technologies, like Entity Framework.</span></span>

<span data-ttu-id="0b75d-120">Можно также просмотреть [SeedWork](https://martinfowler.com/bliki/Seedwork.html) папку, содержащую пользовательские базовые классы, которые можно использовать в качестве базы для сущности домена и значение объектов, поэтому нет избыточный код в класс объекта для каждого домена.</span><span class="sxs-lookup"><span data-stu-id="0b75d-120">You can also see a [SeedWork](https://martinfowler.com/bliki/Seedwork.html) folder that contains custom base classes that you can use as a base for your domain entities and value objects, so you do not have redundant code in each domain’s object class.</span></span>

## <a name="structuring-aggregates-in-a-custom-net-standard-library"></a><span data-ttu-id="0b75d-121">Структурирование статистические выражения в пользовательская библиотека .NET Standard</span><span class="sxs-lookup"><span data-stu-id="0b75d-121">Structuring aggregates in a custom .NET Standard library</span></span>

<span data-ttu-id="0b75d-122">Статистическое выражение ссылается на кластере объекты домена, сгруппированных для сопоставления согласованность транзакций.</span><span class="sxs-lookup"><span data-stu-id="0b75d-122">An aggregate refers to a cluster of domain objects grouped together to match transactional consistency.</span></span> <span data-ttu-id="0b75d-123">Плюс любые объекты дополнительное значение этих объектов может быть экземпляры сущностей (один из которых является корневой статистические или корневой объект).</span><span class="sxs-lookup"><span data-stu-id="0b75d-123">Those objects could be instances of entities (one of which is the aggregate root or root entity) plus any additional value objects.</span></span>

<span data-ttu-id="0b75d-124">Согласованность транзакций означает, что статистическое гарантированно согласованное и обновлен на конец действия бизнес.</span><span class="sxs-lookup"><span data-stu-id="0b75d-124">Transactional consistency means that an aggregate is guaranteed to be consistent and up to date at the end of a business action.</span></span> <span data-ttu-id="0b75d-125">Например порядок статистическое выражение из eShopOnContainers, упорядочение модель домена микрослужбу состоит как показано на рисунке 9-11.</span><span class="sxs-lookup"><span data-stu-id="0b75d-125">For example, the order aggregate from the eShopOnContainers ordering microservice domain model is composed as shown in Figure 9-11.</span></span>

![](./media/image12.png)

<span data-ttu-id="0b75d-126">**Рис. 9-11**.</span><span class="sxs-lookup"><span data-stu-id="0b75d-126">**Figure 9-11**.</span></span> <span data-ttu-id="0b75d-127">Порядок агрегатных в решении Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0b75d-127">The order aggregate in Visual Studio solution</span></span>

<span data-ttu-id="0b75d-128">При открытии этих файлов в папке aggregate, вы увидите как она помечена как пользовательского базового класса или интерфейса, как сущность или значение объекта, как осуществляется в [Seedwork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork) папки.</span><span class="sxs-lookup"><span data-stu-id="0b75d-128">If you open any of the files in an aggregate folder, you can see how it is marked as either a custom base class or interface, like entity or value object, as implemented in the [Seedwork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork) folder.</span></span>

## <a name="implementing-domain-entities-as-poco-classes"></a><span data-ttu-id="0b75d-129">Реализация сущностей домена как классов POCO</span><span class="sxs-lookup"><span data-stu-id="0b75d-129">Implementing domain entities as POCO classes</span></span>

<span data-ttu-id="0b75d-130">Реализуйте модель домена в .NET путем создания классов POCO, реализующих сущности домена.</span><span class="sxs-lookup"><span data-stu-id="0b75d-130">You implement a domain model in .NET by creating POCO classes that implement your domain entities.</span></span> <span data-ttu-id="0b75d-131">В следующем примере определяется класс Order, как сущность, а также как статистические корневой каталог.</span><span class="sxs-lookup"><span data-stu-id="0b75d-131">In the following example, the Order class is defined as an entity and also as an aggregate root.</span></span> <span data-ttu-id="0b75d-132">Поскольку класс Order является производным от базового класса сущности, можно повторно использовать общий код, относящиеся к сущности.</span><span class="sxs-lookup"><span data-stu-id="0b75d-132">Because the Order class derives from the Entity base class, it can reuse common code related to entities.</span></span> <span data-ttu-id="0b75d-133">Не забывайте, что эти базовые классы и интерфейсы определяются вы в проекте модели домена, поэтому код, с ORM как EF не код инфраструктуры.</span><span class="sxs-lookup"><span data-stu-id="0b75d-133">Bear in mind that these base classes and interfaces are defined by you in the domain model project, so it is your code, not infrastructure code from an ORM like EF.</span></span>

```csharp
// COMPATIBLE WITH ENTITY FRAMEWORK CORE 1.0
// Entity is a custom base class with the ID
public class Order : Entity, IAggregateRoot
{
    public int BuyerId { get; private set; }
    public DateTime OrderDate { get; private set; }
    public int StatusId { get; private set; }
    public ICollection<OrderItem> OrderItems { get; private set; }
    public Address ShippingAddress { get; private set; }
    public int PaymentId { get; private set; }
    protected Order() { } //Design constraint needed only by EF Core
    public Order(int buyerId, int paymentId)
    {
        BuyerId = buyerId;
        PaymentId = paymentId;
        StatusId = OrderStatus.InProcess.Id;
        OrderDate = DateTime.UtcNow;
        OrderItems = new List<OrderItem>();
    }

    public void AddOrderItem(productName,
        pictureUrl,
        unitPrice,
        discount,
        units)
    {
        //...
        // Domain rules/logic for adding the OrderItem to the order
        // ...
        OrderItem item = new OrderItem(this.Id, ProductId, productName,
            pictureUrl, unitPrice, discount, units);
  
        OrderItems.Add(item);
    }
    // ...
    // Additional methods with domain rules/logic related to the Order aggregate
    // ...
}
```

<span data-ttu-id="0b75d-134">Это важно отметить, что это сущности домена, реализованы в виде класса POCO.</span><span class="sxs-lookup"><span data-stu-id="0b75d-134">It is important to note that this is a domain entity implemented as a POCO class.</span></span> <span data-ttu-id="0b75d-135">Он не имеет прямой зависимости в Entity Framework Core или любой другой структуре инфраструктуры.</span><span class="sxs-lookup"><span data-stu-id="0b75d-135">It does not have any direct dependency on Entity Framework Core or any other infrastructure framework.</span></span> <span data-ttu-id="0b75d-136">Эта реализация является ожидаемым значениям, просто C\# код, реализующий модель домена.</span><span class="sxs-lookup"><span data-stu-id="0b75d-136">This implementation is as it should be, just C\# code implementing a domain model.</span></span>

<span data-ttu-id="0b75d-137">Кроме того класс снабжен интерфейс с именем IAggregateRoot.</span><span class="sxs-lookup"><span data-stu-id="0b75d-137">In addition, the class is decorated with an interface named IAggregateRoot.</span></span> <span data-ttu-id="0b75d-138">Этот интерфейс является пустой интерфейс, иногда называется *интерфейс-маркер*, в котором используется только для указания, что этого класса сущности также корневого каталога статистические.</span><span class="sxs-lookup"><span data-stu-id="0b75d-138">That interface is an empty interface, sometimes called a *marker interface*, that is used just to indicate that this entity class is also an aggregate root.</span></span>

<span data-ttu-id="0b75d-139">Иногда интерфейс считается антишаблон; Однако это также чистой способ пометить класс, особенно в том случае, если этот интерфейс может развивается.</span><span class="sxs-lookup"><span data-stu-id="0b75d-139">A marker interface is sometimes considered as an anti-pattern; however, it is also a clean way to mark a class, especially when that interface might be evolving.</span></span> <span data-ttu-id="0b75d-140">Атрибут может быть другой Выбор маркера, но проще и быстрее просмотреть базовый класс (сущности) рядом с интерфейс IAggregate вместо того, чтобы маркер на статистическом атрибуте выше класса.</span><span class="sxs-lookup"><span data-stu-id="0b75d-140">An attribute could be the other choice for the marker, but it is quicker to see the base class (Entity) next to the IAggregate interface instead of putting an Aggregate attribute marker above the class.</span></span> <span data-ttu-id="0b75d-141">Это metter предпочтений, в любом случае.</span><span class="sxs-lookup"><span data-stu-id="0b75d-141">It is a metter of preferences, in any case.</span></span>

<span data-ttu-id="0b75d-142">Наличие статистических корневой означает, что большая часть кода, связанные с согласованности и бизнес-правила сущностей статистической функции должны быть реализованы как методы в классе корневого статистические заказа (например, AddOrderItem при добавлении объекта к OrderItem статистического выражения) .</span><span class="sxs-lookup"><span data-stu-id="0b75d-142">Having an aggregate root means that most of the code related to consistency and business rules of the aggregate’s entities should be implemented as methods in the Order aggregate root class (for example, AddOrderItem when adding an OrderItem object to the aggregate).</span></span> <span data-ttu-id="0b75d-143">Не следует создать или обновить объекты OrderItems независимо друг от друга или напрямую. Класс AggregateRoot должно сохраняться, управления и согласованность любой операции обновления от его дочерних сущностей.</span><span class="sxs-lookup"><span data-stu-id="0b75d-143">You should not create or update OrderItems objects independently or directly; the AggregateRoot class must keep control and consistency of any update operation against its child entities.</span></span>

<span data-ttu-id="0b75d-144">Например, вы должны *не* выполните следующие действия на любой обработчик метода или приложения уровня класс команд:</span><span class="sxs-lookup"><span data-stu-id="0b75d-144">For example, you should *not* do the following from any command handler method or application layer class:</span></span>

```csharp
// WRONG ACCORDING TO DDD PATTERNS – CODE AT THE APPLICATION LAYER OR
// COMMAND HANDLERS
// Code in command handler methods or Web API controllers
//... (WRONG) Some code with business logic out of the domain classes ...
OrderItem myNewOrderItem = new OrderItem(orderId, productId, productName,
    pictureUrl, unitPrice, discount, units);

//... (WRONG) Accessing the OrderItems colletion directly from the application layer // or command handlers
myOrder.OrderItems.Add(myNewOrderItem);
//...
```

<span data-ttu-id="0b75d-145">В этом случае метод Add может выполняться исключительно для добавления данных с прямой доступ к коллекции OrderItems.</span><span class="sxs-lookup"><span data-stu-id="0b75d-145">In this case, the Add method is purely an operation to add data, with direct access to the OrderItems collection.</span></span> <span data-ttu-id="0b75d-146">Таким образом большая часть логики домена, правил или проверки, относящиеся к, операции с на дочерние объекты будут распределяться на уровне приложения (обработчики команд и контроллеров веб-API).</span><span class="sxs-lookup"><span data-stu-id="0b75d-146">Therefore, most of the domain logic, rules, or validations related to that operation with the child entities will be spread across the application layer (command handlers and Web API controllers).</span></span>

<span data-ttu-id="0b75d-147">При переходе вокруг статистические корневой статистические корневой не может гарантировать его инварианты его действительность и ее согласованности.</span><span class="sxs-lookup"><span data-stu-id="0b75d-147">If you go around the aggregate root, the aggregate root cannot guarantee its invariants, its validity, or its consistency.</span></span> <span data-ttu-id="0b75d-148">В конечном итоге будет иметь тестированию кода или код скрипта транзакций.</span><span class="sxs-lookup"><span data-stu-id="0b75d-148">Eventually you will have spaghetti code or transactional script code.</span></span>

<span data-ttu-id="0b75d-149">Следовать DDD шаблонов, сущности не должен иметь открытый задания все свойства сущности.</span><span class="sxs-lookup"><span data-stu-id="0b75d-149">To follow DDD patterns, entities must not have public setters in any entity property.</span></span> <span data-ttu-id="0b75d-150">Изменения в сущности должны управляться явные методы с явной единый язык об изменениях, которые они выполняют в сущности.</span><span class="sxs-lookup"><span data-stu-id="0b75d-150">Changes in an entity should be driven by explicit methods with explicit ubiquitous language about the change they are performing in the entity.</span></span>

<span data-ttu-id="0b75d-151">Кроме того, коллекции сущности (например, элементов заказа), должны быть только для чтения свойства (метод AsReadOnly рассматривается позже).</span><span class="sxs-lookup"><span data-stu-id="0b75d-151">Furthermore, collections within the entity (like the order items) should be read-only properties (the AsReadOnly method explained later).</span></span> <span data-ttu-id="0b75d-152">Вы сможете обновить его только из внутри корневой статистические методы класса или дочерних методов сущности.</span><span class="sxs-lookup"><span data-stu-id="0b75d-152">You should be able to update it only from within the aggregate root class methods or the child entity methods.</span></span>

<span data-ttu-id="0b75d-153">Как видно в коде для корня статистические порядок, все задания должны быть закрытым или хотя бы доступны только для чтения извне, чтобы выполнения любой операции над сущности данных или ее дочерних сущностей должно выполняться с помощью методов в классе сущностей.</span><span class="sxs-lookup"><span data-stu-id="0b75d-153">As you can see in the code for the Order aggregate root, all setters should be private or at least read-only externally, so that any operation against the entity’s data or its child entities has to be performed through methods in the entity class.</span></span> <span data-ttu-id="0b75d-154">Это обеспечивает согласованность управляемой и объектно ориентированного способом вместо реализации код скрипта транзакций.</span><span class="sxs-lookup"><span data-stu-id="0b75d-154">This maintains consistency in a controlled and object-oriented way instead of implementing transactional script code.</span></span>

<span data-ttu-id="0b75d-155">В следующем фрагменте кода показан правильный способ кодирования задачу при добавлении объекта OrderItem статистическое выражение Order.</span><span class="sxs-lookup"><span data-stu-id="0b75d-155">The following code snippet shows the proper way to code the task of adding an OrderItem object to the Order aggregate.</span></span>

```csharp
// RIGHT ACCORDING TO DDD--CODE AT THE APPLICATION LAYER OR COMMAND HANDLERS
// The code in command handlers or WebAPI controllers, related only to application stuff
// There is NO code here related to OrderItem object’s business logic
myOrder.AddOrderItem(productId, productName, pictureUrl, unitPrice, discount, units);

// The code related to OrderItem params validations or domain rules should
// be WITHIN the AddOrderItem method.

//...
```

<span data-ttu-id="0b75d-156">В этом фрагменте кода большинство проверки и процедуры, относящиеся к созданию объекта OrderItem будут управляться статистические корневого заказа — в методе AddOrderItem — особенно проверок и логику, связанные с другими элементами в агрегатной.</span><span class="sxs-lookup"><span data-stu-id="0b75d-156">In this snippet, most of the validations or logic related to the creation of an OrderItem object will be under the control of the Order aggregate root—in the AddOrderItem method—especially validations and logic related to other elements in the aggregate.</span></span> <span data-ttu-id="0b75d-157">Например можно получить тот же элемент продукта, в результате нескольких вызовов AddOrderItem.</span><span class="sxs-lookup"><span data-stu-id="0b75d-157">For instance, you might get the same product item as the result of multiple calls to AddOrderItem.</span></span> <span data-ttu-id="0b75d-158">В этом методе можно проверить элементы по продукту и консолидировать тем же элементам продукта в один объект OrderItem с несколькими единицами.</span><span class="sxs-lookup"><span data-stu-id="0b75d-158">In that method, you could examine the product items and consolidate the same product items into a single OrderItem object with several units.</span></span> <span data-ttu-id="0b75d-159">Кроме того Если существуют разные скидки суммы, но идентификатор продукта совпадает, скорее всего применить выше скидки.</span><span class="sxs-lookup"><span data-stu-id="0b75d-159">Additionally, if there are different discount amounts but the product ID is the same, you would likely apply the higher discount.</span></span> <span data-ttu-id="0b75d-160">Этот принцип применяется к другой логики домена OrderItem объекта.</span><span class="sxs-lookup"><span data-stu-id="0b75d-160">This principle applies to any other domain logic for the OrderItem object.</span></span>

<span data-ttu-id="0b75d-161">Кроме того новая операция OrderItem(params) также быть управляются и выполняемое методом AddOrderItem от корня статистические заказа.</span><span class="sxs-lookup"><span data-stu-id="0b75d-161">In addition, the new OrderItem(params) operation will also be controlled and performed by the AddOrderItem method from the Order aggregate root.</span></span> <span data-ttu-id="0b75d-162">Таким образом большая часть логики или проверкам, относящиеся к что операция (особенно все, что влияет на согласованность между другими сущностями дочернего) будет в одном месте в пределах статистической корневого каталога.</span><span class="sxs-lookup"><span data-stu-id="0b75d-162">Therefore, most of the logic or validations related to that operation (especially anything that impacts the consistency between other child entities) will be in a single place within the aggregate root.</span></span> <span data-ttu-id="0b75d-163">Это назначение ultimate статистические корневой шаблон.</span><span class="sxs-lookup"><span data-stu-id="0b75d-163">That is the ultimate purpose of the aggregate root pattern.</span></span>

<span data-ttu-id="0b75d-164">При использовании Entity Framework 1.1 сущности DDD можно выполнить быстрее, так как одна из новых функций Entity Framework Core 1.1 является то, что [сопоставление с полями](https://docs.microsoft.com/ef/core/modeling/backing-field) Помимо свойств.</span><span class="sxs-lookup"><span data-stu-id="0b75d-164">When you use Entity Framework 1.1, a DDD entity can be better expressed because one of the new features of Entity Framework Core 1.1 is that it allows [mapping to fields](https://docs.microsoft.com/ef/core/modeling/backing-field) in addition to properties.</span></span> <span data-ttu-id="0b75d-165">Это полезно при защите коллекции дочерних сущностей или объектов значение.</span><span class="sxs-lookup"><span data-stu-id="0b75d-165">This is useful when protecting collections of child entities or value objects.</span></span> <span data-ttu-id="0b75d-166">Это улучшение можно использовать простой закрытых полей вместо свойств и вы реализовать любое обновление для коллекции полей в открытых методов и предоставить доступ только для чтения в методе AsReadOnly.</span><span class="sxs-lookup"><span data-stu-id="0b75d-166">With this enhancement, you can use simple private fields instead of properties and you can implement any update to the field collection in public methods and provide read-only access through the AsReadOnly method.</span></span>

<span data-ttu-id="0b75d-167">Поэтому ддд, необходимо обновить только через методы в сущности (или конструктор), чтобы управлять любой инвариантный и согласованность данных в сущности, свойства определяются только с методом доступа get.</span><span class="sxs-lookup"><span data-stu-id="0b75d-167">In DDD you want to update the entity only through methods in the entity (or the constructor) in order to control any invariant and the consistency of the data, so properties are defined only with a get accessor.</span></span> <span data-ttu-id="0b75d-168">Закрытые поля, поддерживаемых свойств.</span><span class="sxs-lookup"><span data-stu-id="0b75d-168">The properties are backed by private fields.</span></span> <span data-ttu-id="0b75d-169">Закрытые члены может осуществляться только из класса.</span><span class="sxs-lookup"><span data-stu-id="0b75d-169">Private members can only be accessed from within the class.</span></span> <span data-ttu-id="0b75d-170">Однако есть одно исключение: необходимо установить эти поля также EF Core.</span><span class="sxs-lookup"><span data-stu-id="0b75d-170">However, there one exception: EF Core needs to set these fields as well.</span></span>

```csharp
// ENTITY FRAMEWORK CORE 1.1 OR LATER
// Entity is a custom base class with the ID
public class Order : Entity, IAggregateRoot
{
    // DDD Patterns comment
    // Using private fields, allowed since EF Core 1.1, is a much better
    // encapsulation aligned with DDD aggregates and domain entities (instead of
    // properties and property collections)
    private bool _someOrderInternalState;
    private DateTime _orderDate;
    public Address Address { get; private set; }
    public Buyer Buyer { get; private set; }
    private int _buyerId;
    public OrderStatus OrderStatus { get; private set; }
    private int _orderStatusId;

    // DDD patterns comment
    // Using a private collection field is better for DDD aggregate encapsulation.
    // OrderItem objects cannot be added from outside the aggregate root
    // directly to the collection, but only through the
    // OrderAggrergateRoot.AddOrderItem method, which includes behavior.
    private readonly List<OrderItem> _orderItems;
    public IEnumerable<OrderItem> OrderItems => _orderItems.AsReadOnly();
    // Using List<>.AsReadOnly()
    // This will create a read-only wrapper around the private list so it is
    // protected against external updates. It's much cheaper than .ToList(),
    // because it will not have to copy all items in a new collection.
    // (Just one heap alloc for the wrapper instance)
    // https://msdn.microsoft.com/en-us/library/e78dcd75(v=vs.110).aspx
    public PaymentMethod PaymentMethod { get; private set; }
    private int _paymentMethodId;

    protected Order() { }

    public Order(int buyerId, int paymentMethodId, Address address)
    {
        _orderItems = new List<OrderItem>();
        _buyerId = buyerId;
        _paymentMethodId = paymentMethodId;
        _orderStatusId = OrderStatus.InProcess.Id;
        _orderDate = DateTime.UtcNow;
        Address = address;
    }

    // DDD patterns comment
    // The Order aggregate root method AddOrderitem() should be the only way
    // to add items to the Order object, so that any behavior (discounts, etc.)
    // and validations are controlled by the aggregate root in order to
    // maintain consistency within the whole aggregate.
    public void AddOrderItem(int productId, string productName, decimal unitPrice,
        decimal discount, string pictureUrl, int units = 1)
    {
        // ...
        // Domain rules/logic here for adding OrderItem objects to the order
        // ...
        OrderItem item = new OrderItem(this.Id, productId, productName,
            pictureUrl, unitPrice, discount, units);
        OrderItems.Add(item);
    }

    // ...
    // Additional methods with domain rules/logic related to the Order aggregate
    // ...
}
```

### <a name="mapping-properties-with-only-get-accessors-to-the-fields-in-the-database-table"></a><span data-ttu-id="0b75d-171">Сопоставление свойств только с методы доступа get для поля в таблице базы данных</span><span class="sxs-lookup"><span data-stu-id="0b75d-171">Mapping properties with only get accessors to the fields in the database table</span></span>

<span data-ttu-id="0b75d-172">Сопоставления свойств для столбцов таблицы базы данных не ответственности домена, но часть слоя инфраструктуры и сохраняемость.</span><span class="sxs-lookup"><span data-stu-id="0b75d-172">Mapping properties to the database table columns is not a domain responsibility, but part of the infrastructure and persistence layer.</span></span> <span data-ttu-id="0b75d-173">Мы ссылаются на этот здесь точно так же, поэтому существует вероятность, новые возможности в версии 1.1 EF, относящиеся к как можно моделировать сущности.</span><span class="sxs-lookup"><span data-stu-id="0b75d-173">We mention this here just so you are aware of the new capabilities in EF 1.1 related to how you can model entities.</span></span> <span data-ttu-id="0b75d-174">Дополнительные сведения по этой теме описаны в разделе инфраструктуры и сохраняемость.</span><span class="sxs-lookup"><span data-stu-id="0b75d-174">Additional details on this topic are explained in the infrastructure and persistence section.</span></span>

<span data-ttu-id="0b75d-175">При использовании EF 1.0, в течение DbContext, необходимо сопоставить свойства, которые определены только для методов получения фактического полей в таблице базы данных.</span><span class="sxs-lookup"><span data-stu-id="0b75d-175">When you use EF 1.0, within the DbContext you need to map the properties that are defined only with getters to the actual fields in the database table.</span></span> <span data-ttu-id="0b75d-176">Это делается с помощью метода HasField PropertyBuilder класса.</span><span class="sxs-lookup"><span data-stu-id="0b75d-176">This is done with the HasField method of the PropertyBuilder class.</span></span>

### <a name="mapping-fields-without-properties"></a><span data-ttu-id="0b75d-177">Сопоставление полей без свойств</span><span class="sxs-lookup"><span data-stu-id="0b75d-177">Mapping fields without properties</span></span>

<span data-ttu-id="0b75d-178">С помощью новой функции в версии 1.1 Core EF для сопоставления столбцов с полями можно также использовать свойства не.</span><span class="sxs-lookup"><span data-stu-id="0b75d-178">With the new feature in EF Core 1.1 to map columns to fields, it is also possible to not use properties.</span></span> <span data-ttu-id="0b75d-179">Вместо этого можно сопоставить только столбцы из таблицы с полями.</span><span class="sxs-lookup"><span data-stu-id="0b75d-179">Instead, you can just map columns from a table to fields.</span></span> <span data-ttu-id="0b75d-180">Распространенным вариантом применения для этого является закрытым полям для внутреннего состояния, не должны быть доступны извне сущности.</span><span class="sxs-lookup"><span data-stu-id="0b75d-180">A common use case for this is private fields for an internal state that does not need to be accessed from outside the entity.</span></span>

<span data-ttu-id="0b75d-181">Например, в предыдущем примере \_someOrderInternalState поле не имеет связанных свойств для setter или getter.</span><span class="sxs-lookup"><span data-stu-id="0b75d-181">For example, in the preceding code example, the \_someOrderInternalState field has no related property for either a setter or getter.</span></span> <span data-ttu-id="0b75d-182">Это поле также вычисляются в порядке бизнес-логики и будут использоваться с помощью методов заказа, но он должен быть сохранен в базе данных также.</span><span class="sxs-lookup"><span data-stu-id="0b75d-182">That field will also be calculated within the order’s business logic and used from the order’s methods, but it needs to be persisted in the database as well.</span></span> <span data-ttu-id="0b75d-183">Таким образом в версии 1.1 EF дает возможность сопоставить поле без связанного свойства со столбцом в базе данных.</span><span class="sxs-lookup"><span data-stu-id="0b75d-183">So, in EF 1.1 there is a way to map a field without a related property to a column in the database.</span></span> <span data-ttu-id="0b75d-184">Это также объясняется [уровень инфраструктуры](#the-infrastructure-layer) данного руководства.</span><span class="sxs-lookup"><span data-stu-id="0b75d-184">This is also explained in the [Infrastructure layer](#the-infrastructure-layer) section of this guide.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="0b75d-185">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="0b75d-185">Additional resources</span></span>

-   <span data-ttu-id="0b75d-186">**Вон Вернон (Vaughn Vernon). Моделирование агрегаты с DDD и Entity Framework.**</span><span class="sxs-lookup"><span data-stu-id="0b75d-186">**Vaughn Vernon. Modeling Aggregates with DDD and Entity Framework.**</span></span> <span data-ttu-id="0b75d-187">Обратите внимание, что это *не* Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="0b75d-187">Note that this is *not* Entity Framework Core.</span></span>
    [<span data-ttu-id="0b75d-188">*https://vaughnvernon.co/?p=879*</span><span class="sxs-lookup"><span data-stu-id="0b75d-188">*https://vaughnvernon.co/?p=879*</span></span>](https://vaughnvernon.co/?p=879)

-   <span data-ttu-id="0b75d-189">**Джули Лерман. Кодирование для разработки на основе домена: советы по ориентированные на данные разработчики**
    [*https://msdn.microsoft.com/en-us/magazine/dn342868.aspx*](https://msdn.microsoft.com/en-us/magazine/dn342868.aspx)</span><span class="sxs-lookup"><span data-stu-id="0b75d-189">**Julie Lerman. Coding for Domain-Driven Design: Tips for Data-Focused Devs**
[*https://msdn.microsoft.com/en-us/magazine/dn342868.aspx*](https://msdn.microsoft.com/en-us/magazine/dn342868.aspx)</span></span>

-   <span data-ttu-id="0b75d-190">**UDI Dahan. Как создать полностью инкапсулирован моделей домена**
    [*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)</span><span class="sxs-lookup"><span data-stu-id="0b75d-190">**Udi Dahan. How to create fully encapsulated Domain Models**
[*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="0b75d-191">[Предыдущие] (микрослужбу домена model.md) [Далее] (seedwork-domain-model-base-classes-interfaces.md)</span><span class="sxs-lookup"><span data-stu-id="0b75d-191">[Previous] (microservice-domain-model.md) [Next] (seedwork-domain-model-base-classes-interfaces.md)</span></span>