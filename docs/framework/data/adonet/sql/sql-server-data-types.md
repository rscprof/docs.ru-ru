---
title: Типы данных SQL Server и ADO.NET
ms.date: 03/30/2017
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
ms.openlocfilehash: 878bbe41f259f1e50cd0a41669c7a352e78bc0f1
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/07/2018
ms.locfileid: "44097039"
---
# <a name="sql-server-data-types-and-adonet"></a>Типы данных SQL Server и ADO.NET
В SQL Server и .NET Framework используются различные системы типов, что может привести к потенциальной потере данных. Чтобы сохранить целостность данных, поставщик данных .NET Framework для SQL Server (<xref:System.Data.SqlClient>) предоставляет типизированные методы доступа для работы с данными SQL Server. Для указания типов данных <xref:System.Data.SqlDbType> можно использовать перечисления классов <xref:System.Data.SqlClient.SqlParameter>.  
  
 Дополнительные сведения и таблицу с описанием данные сопоставления типов между SQL Server и типы данных .NET Framework, см. в разделе [сопоставления типов данных SQL Server](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md).  
  
 В SQL Server 2008 появились новые типы данных, разработанные для удовлетворения бизнес-потребностей по работе с датами и временем, структурированными, частично структурированными и неструктурированными данными. Новые типы данных описаны в электронной документации по SQL Server 2008.  
  
 Типы данных SQL Server, которые можно использовать в приложениях, зависят от используемой версии SQL Server. Дополнительные сведения см. в электронной документации для соответствующей версии SQL Server в приведенной ниже таблице.  
  
 **Электронная документация по SQL Server**  
  
1.  [Типы данных (ядро СУБД)](https://go.microsoft.com/fwlink/?LinkID=107468)  
  
## <a name="in-this-section"></a>В этом разделе  
 [Типы SqlType и набор данных](../../../../../docs/framework/data/adonet/sql/sqltypes-and-the-dataset.md)  
 Описывается поддержка типов для объекта `SqlTypes` в объекте `DataSet`.  
  
 [Обработка значений NULL](../../../../../docs/framework/data/adonet/sql/handling-null-values.md)  
 Демонстрируется работа со значениями NULL и тройственной логикой.  
  
 [Сравнение значений идентификатора GUID и uniqueidentifier](../../../../../docs/framework/data/adonet/sql/comparing-guid-and-uniqueidentifier-values.md)  
 Демонстрируется работа со значениями GUID и uniqueidentifier в SQL Server и .NET Framework.  
  
 [Данные даты и времени](../../../../../docs/framework/data/adonet/sql/date-and-time-data.md)  
 Описывается использование новых типов данных даты и времени, появившихся в SQL Server 2008.  
  
 [Большие определяемые пользователем типы](../../../../../docs/framework/data/adonet/sql/large-udts.md)  
 Демонстрируется извлечение данных из определяемых пользователем типов данных большого размера, появившихся в SQL Server 2008.  
  
 [Данные XML в SQL Server](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)  
 Описание работы с данными XML, извлеченными из SQL Server.  
  
## <a name="reference"></a>Ссылка  
 <xref:System.Data.DataSet>  
 Описывает класс `DataSet` и все его члены.  
  
 <xref:System.Data.SqlTypes>  
 Описывает пространство имен `SqlTypes` и все его элементы.  
  
 <xref:System.Data.SqlDbType>  
 Описывает перечисление `SqlDbType` и все его члены.  
  
 <xref:System.Data.DbType>  
 Описывает перечисление `DbType` и все его члены.  
  
## <a name="see-also"></a>См. также  
 [Сопоставления типов данных SQL Server](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [Настройка параметров и типы данных параметров](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [Возвращающие табличное значение параметры](../../../../../docs/framework/data/adonet/sql/table-valued-parameters.md)  
 [Двоичные данные и данные большого объема SQL Server](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [Центр разработчиков наборов данных и управляемых поставщиков ADO.NET](https://go.microsoft.com/fwlink/?LinkId=217917)
