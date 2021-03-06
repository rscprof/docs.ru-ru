---
title: Отражение в .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], reflection
- EventInfo class, reflection
- common language runtime, reflection
- FieldInfo class, reflection
- ParameterInfo class, reflection
- ConstructorInfo class, reflection
- Assembly class, reflection
- value types, reflection
- reflection, about reflection
- modules, reflection
- runtime, reflection
- Module class, reflection
- MethodInfo class, reflection
- PropertyInfo class, reflection
- type browsers
- reflection
- discovering type information at run time
- type system, reflection
ms.assetid: d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a03e6760fbb233c656909fb99b48a84bddedef8
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/01/2018
ms.locfileid: "43405576"
---
# <a name="reflection-in-the-net-framework"></a>Отражение в .NET Framework
Классы в пространстве имен <xref:System.Reflection> вместе с <xref:System.Type?displayProperty=nameWithType> позволяют получить информацию о загруженных [сборках](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md) и типах, определенных в них, таких как [классы](https://msdn.microsoft.com/library/ad7d3561-271e-4546-82fc-e00b059f27a9), [интерфейсы](https://msdn.microsoft.com/library/fd9d5975-5363-4bc9-b883-609f887895e5) и [типы значений](https://msdn.microsoft.com/library/c9c567f8-8ab1-4d88-834d-00f7d92418de). Отражение можно также использовать для создания экземпляров типов во время выполнения, для вызова этих экземпляров и получения доступа к ним. Разделы, в которых описываются отдельные аспекты отражения, можно найти в подразделе [Связанные подразделы](#related_topics) в конце этого обзора.  
  
 Загрузчик [среды CLR](../../../docs/standard/clr.md) управляет [доменами приложений](../../../docs/framework/app-domains/application-domains.md), которые образуют определенные границы вокруг объектов с одной и той же областью приложения. В частности, он загружает каждую сборку в соответствующий домен приложения и контролирует распределение памяти для иерархии типов в каждой сборке.  
  
 [Сборки](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md) содержат модули, модули содержат типы, а типы содержат члены. Отражение предоставляет объекты, которые инкапсулируют сборки, модули и типы. Отражение можно использовать для динамического создания экземпляра типа, привязки типа к существующему объекту или получения типа из существующего объекта. Затем можно вызывать методы типа или получать доступ к его полям и свойствам. Ниже приведены типичные варианты использования отражения.  
  
-   Объект <xref:System.Reflection.Assembly> используется для определения и загрузки сборок, загрузки модулей, перечисленных в манифесте сборки, а также для поиска типа в сборке и создания его экземпляра.  
  
-   Объект <xref:System.Reflection.Module> используется для получения таких сведений, как имя сборки, содержащей модуль, и перечень классов этого модуля. Кроме того, можно получить все глобальные методы или определенные неглобальные методы, включенные в модуль.  
  
-   Объект <xref:System.Reflection.ConstructorInfo> используется для получения таких сведений, как имя, параметры, модификаторы доступа (например, `public` или `private`) и сведения о реализации (например, `abstract` или `virtual`) конструктора. Метод <xref:System.Type.GetConstructors%2A> или <xref:System.Type.GetConstructor%2A> типа <xref:System.Type> используется для вызова конкретного конструктора.  
  
-   Класс <xref:System.Reflection.MethodInfo> используется для получения таких сведений, как имя, возвращаемый тип, параметры, модификаторы доступа (например, `public` или `private`) и сведения о реализации (например, `abstract` или `virtual`) метода. Метод <xref:System.Type.GetMethods%2A> или <xref:System.Type.GetMethod%2A> типа <xref:System.Type> используется для вызова определенного метода.  
  
-   Класс <xref:System.Reflection.FieldInfo> используется для получения таких сведений, как имя, модификаторы доступа (например, `public` или `private`) и сведения о реализации (например, `static`) поля, а также для получения или задания значений поля.  
  
-   Класс <xref:System.Reflection.EventInfo> используется для получения таких сведений, как имя, тип данных обработчика событий, пользовательские атрибуты, объявляющий тип и отраженный тип события, а также для добавления или удаления обработчиков событий.  
  
-   Класс <xref:System.Reflection.PropertyInfo> используется для получения таких сведений, как имя, тип данных, объявляющий тип, отраженный тип и состояние доступности свойства (для записи или только для чтения), а также для получения и задания значений свойств.  
  
-   Класс <xref:System.Reflection.ParameterInfo> используется для получения таких сведений, как имя параметра, тип данных, вид параметра (входной или выходной) и его положение в подписи метода.  
  
-   Класс <xref:System.Reflection.CustomAttributeData> используется для получения сведений о настраиваемых атрибутах при работе в контексте домена приложения только для отражения. Класс <xref:System.Reflection.CustomAttributeData> позволяет проверять атрибуты, не создавая их экземпляры.  
  
 Классы пространства имен <xref:System.Reflection.Emit> реализуют особый вид отражения, который позволяет создавать типы во время выполнения.  
  
 Отражение также можно использовать для создания приложений, называемых браузерами типов, которые позволяют пользователям выбирать типы, а затем просматривать сведения о них.  
  
 Есть и другие способы использования отражения. Компиляторы таких языков программирования, как JScript, используют отражение для построения таблиц символов. Классы в пространстве имен <xref:System.Runtime.Serialization> используют отражение для доступа к данным и определения того, какие поля следует сохранить. Классы в пространстве имен <xref:System.Runtime.Remoting> используют отражение косвенным образом через сериализацию.  
  
## <a name="runtime-types-in-reflection"></a>Типы среды выполнения в отражении  
 Отражение предоставляет классы, такие как <xref:System.Type> и <xref:System.Reflection.MethodInfo>, для представления типов, членов, параметров и других объектов кода. Однако при использовании отражения вы работаете с этими классами не напрямую: большинство из них являются абстрактными (`MustInherit` в Visual Basic). Вместо этого вы работаете с типами, предоставленными средой CLR.  
  
 Например, при использовании оператора `typeof` в C# (`GetType` в Visual Basic) для получения объекта <xref:System.Type> объект фактически является `RuntimeType`. `RuntimeType` является производным от <xref:System.Type> и предоставляет реализации всех абстрактных методов.  
  
 Эти классы среды выполнения являются `internal` (`Friend` в Visual Basic). Они не документируются отдельно от своих базовых классов, так как их поведение описывается в документации базового класса.  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>См. также  
  
|Заголовок|Описание:|  
|-----------|-----------------|  
|[Просмотр сведений о типах](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)|Описывается класс <xref:System.Type> и приводятся примеры кода, иллюстрирующие использование <xref:System.Type> с несколькими классами отражения для получения информации о конструкторах, методах, полях, свойствах и событиях.|  
|[Отражение и универсальные типы](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)|Объясняется обработка отражением параметров и аргументов типа для универсальных типов и методов.|  
|[Соображения о безопасности для отражения](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md)|Описываются правила, определяющие, в какой степени отражение можно использовать для получения информации о типах и доступа к типам.|  
|[Динамическая загрузка и использование типов](../../../docs/framework/reflection-and-codedom/dynamically-loading-and-using-types.md)|Описывается интерфейс настраиваемой привязки отражения, поддерживающий позднее связывание.|  
|[Практическое руководство. Загрузка сборок в контекст, предназначенный только для отражения](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)|Описывается контекст загрузки, предназначенный только для отражения. Показано, как загрузить сборку, протестировать контекст и просмотреть атрибуты, примененные к сборке в контексте, предназначенном только для отражения.|  
|[Доступ к пользовательским атрибутам](../../../docs/framework/reflection-and-codedom/accessing-custom-attributes.md)|Показано, как использовать отражение для проверки наличия атрибутов и получения их значений.|  
|[Указание полных имен типов](../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)|Описывается формат полных имен типов в форме Бэкуса-Наура и синтаксис для указания специальных символов, имен сборок, указателей, ссылок и массивов.|  
|[Практическое руководство. Подключение делегата с помощью отражения](../../../docs/framework/reflection-and-codedom/how-to-hook-up-a-delegate-using-reflection.md)|Объясняется, как создать делегат для метода и привязать его к событию. Также объясняется, как создать метод обработки событий во время выполнения с помощью <xref:System.Reflection.Emit.DynamicMethod>.|  
|[Предоставление динамических методов и сборок](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)|Объясняется, как создавать динамические сборки и динамические методы.|  
  
## <a name="reference"></a>Ссылка  
 <xref:System.Type?displayProperty=nameWithType>  
  
 <xref:System.Reflection>  
  
 <xref:System.Reflection.Emit>  
  
