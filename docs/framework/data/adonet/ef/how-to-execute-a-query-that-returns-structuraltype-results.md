---
title: Практическое руководство. Выполнение запроса, возвращающего результаты StructuralType
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2314f2a2-b1c3-40c4-95bb-cdf9b21a7b53
ms.openlocfilehash: 1a53ab6ab455975f0597eab76aeaa2db3ffd42a3
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "43882724"
---
# <a name="how-to-execute-a-query-that-returns-structuraltype-results"></a>Практическое руководство. Выполнение запроса, возвращающего результаты StructuralType
В этом подразделе показано выполнение команды для концептуальной модели с помощью объекта <xref:System.Data.EntityClient.EntityCommand>, а также получение результатов <xref:System.Data.Metadata.Edm.StructuralType> с помощью <xref:System.Data.EntityClient.EntityDataReader>. Классы <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.RowType> и <xref:System.Data.Metadata.Edm.ComplexType> являются производными класса <xref:System.Data.Metadata.Edm.StructuralType>.  
  
### <a name="to-run-the-code-in-this-example"></a>Выполнение кода в этом примере  
  
1.  Добавить [модели AdventureWorks Sales](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) в проект и настроить проект для использования [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Дополнительные сведения см. в разделе [как: использовать мастер моделей EDM](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
2.  На странице кода приложения добавьте следующие инструкции `using` (`Imports` в Visual Basic):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a>Пример  
 В этом примере выполняется запрос, который возвращает результаты <xref:System.Data.Metadata.Edm.EntityType>. При передаче следующего запроса в качестве аргумента функции `ExecuteStructuralTypeQuery` функция отобразит подробные сведения о `Products`:  
  
 [!code-csharp[DP EntityServices Concepts 2#SelectProduct](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#selectproduct)]  
  
 Передавая параметризованный запрос, подобный следующему, добавьте объекты <xref:System.Data.EntityClient.EntityParameter> к свойству <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> объекта <xref:System.Data.EntityClient.EntityCommand>.  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER_OR_EQUALS](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater_or_equals)]  
  
 [!code-csharp[DP EntityServices Concepts#eSQLStructuralTypes](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#esqlstructuraltypes)]
 [!code-vb[DP EntityServices Concepts#eSQLStructuralTypes](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#esqlstructuraltypes)]  
  
## <a name="see-also"></a>См. также  
 [Справочник по Entity SQL](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Поставщик EntityClient для Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)
