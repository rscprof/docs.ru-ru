---
title: LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 73d13345-eece-471a-af40-4cc7a2f11655
ms.openlocfilehash: 499311f4db9d36f9f95d20c6ef0441ff42f0029b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/04/2018
ms.locfileid: "43529386"
---
# <a name="linq-to-sql"></a>LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] является компонентом [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] версии 3.5, предоставляющим инфраструктуру времени выполнения для управления реляционными данными как объектами.  
  
> [!NOTE]
>  Реляционные данные отображаются в виде коллекции двумерных таблиц (*отношений* или *плоских файлов*),где общие столбцы связывают таблицы друг с другом. Для эффективного использования [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] необходимо ознакомиться с основными принципами реляционных баз данных.  
  
 В [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] модель данных реляционной базы данных сопоставляется объектной модели, выраженной в языке программирования разработчика. При запуске приложения [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] преобразует запросы LINQ из объектной модели в SQL и отправляет их в базу данных для выполнения. Когда база данных возвращает результаты, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] преобразует их обратно в объекты, с которыми можно работать на собственном языке программирования.  
  
 Разработчики, обычно с помощью Visual Studio с помощью [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)], который предоставляет пользовательский интерфейс для реализации многих возможностей [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 Документация, включенная в эту версию [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], описывает основные строительные блоки, процессы и методики, необходимые для построения приложений [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Можно также поискать документы Microsoft для конкретных проблем, и вы можете принять участие в [LINQ Forum](https://go.microsoft.com/fwlink/?LinkId=76488), где можно обсудить со специалистами более сложные вопросы подробно. Наконец [LINQ to SQL: запросы запросы LINQ .NET для реляционных данных](https://go.microsoft.com/fwlink/?LinkId=93205) документ содержит описание [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] технологии, проиллюстрированные примерами кода Visual Basic и C#.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Начало работы](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)  
 Содержит краткие общие сведения о [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], а также сведения о начале работы с [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 [Руководство по программированию](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 Содержит описание действий по сопоставлению, осуществлению запросов, обновлению, отладке и выполнению схожих задач.  
  
 [Ссылки](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 Содержит справочные сведения о ряде аспектов [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Представлены следующие разделы: "Сопоставление типов SQL-CLR", "Преобразование стандартного оператора запросов" и многие другие.  
  
 [Примеры](../../../../../../docs/framework/data/adonet/sql/linq/samples.md)  
 Содержит ссылки на примеры Visual Basic и C#.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Встроенный язык запросов LINQ](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 Предоставляет общие сведения о технологиях [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].  
  
 [LINQ](../../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 Описывает [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] технологии для пользователей Visual Basic.  
  
 [LINQ to ADO.NET](https://msdn.microsoft.com/library/be3297b9-1b54-4d4c-82a8-add0d79c2006)  
 Ссылки на портал [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)].  
  
 [Пошаговые руководства LINQ to SQL](https://msdn.microsoft.com/library/308e66ac-f704-4e00-9b4e-7af0045a2374)  
 Содержит список пошаговых руководств, доступных для [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 [Загрузка примеров баз данных](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 Содержит инструкции по загрузке примеров баз данных, используемых в документации.  
  
 [Общие сведения о технологии LinqDataSource](https://msdn.microsoft.com/library/104cfc3f-7385-47d3-8a51-830dfa791136)  
 Описывает, каким образом элемент управления <xref:System.Web.UI.WebControls.LinqDataSource> предоставляет [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] для веб-разработчиков посредством архитектуры элементов управления источниками данных [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)].
