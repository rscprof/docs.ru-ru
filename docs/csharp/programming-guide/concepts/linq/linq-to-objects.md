---
title: LINQ to Objects (C#)
ms.date: 07/20/2015
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
ms.openlocfilehash: dce90ce78668b3732db31dee6d0a233c4d39557f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323502"
---
# <a name="linq-to-objects-c"></a>LINQ to Objects (C#)
Термин "LINQ to Objects" означает использование запросов LINQ с любой коллекцией <xref:System.Collections.IEnumerable> или <xref:System.Collections.Generic.IEnumerable%601> напрямую, без привлечения промежуточного поставщика LINQ, API [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md) или [LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13). Вы можете выполнить запрос LINQ к любой перечислимой коллекции, такой как <xref:System.Collections.Generic.List%601>, <xref:System.Array> или <xref:System.Collections.Generic.Dictionary%602>. Коллекция может быть определена пользователем или возвращена API .NET Framework.  
  
 В общем смысле LINQ to Objects представляет собой новый подход к коллекциям. Раньше нужно было написать сложные циклы `foreach`, определяющие порядок извлечения данных из коллекции. При использовании LINQ пишется декларативный код, описывающий, какие данные необходимо извлечь.  
  
 Кроме того, запросы LINQ предлагают три основных преимущества по сравнению с традиционными циклами `foreach`:  
  
1.  Они более краткие и удобочитаемые, особенно при фильтрации нескольких условий.  
  
2.  Они предоставляют широкие возможности фильтрации, упорядочивания и группировки с минимумом кода приложения.  
  
3.  Они могут переноситься в другие источники данных практически без изменений.  
  
 В общем, чем сложнее операция, которую нужно выполнить с данными, тем больше преимуществ вы получаете при использовании LINQ вместо традиционных способов итерации.  
  
 Целью этого раздела является демонстрация подхода LINQ с помощью нескольких примеров. Он не претендует на исчерпывающий характер.  
  
## <a name="in-this-section"></a>В этом разделе  
 [LINQ и строки (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)  
 Использование LINQ для запроса и преобразования строк и коллекций строк. Ссылки на разделы, демонстрирующие эти принципы.  
  
 [LINQ и отражение (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-reflection.md)  
 Ссылки на пример, демонстрирующий, как LINQ использует отражение.  
  
 [LINQ и каталоги файлов (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)  
 Использование LINQ для взаимодействия с файловыми системами. Ссылки на разделы, демонстрирующие эти понятия.  
  
 [Практическое руководство. Выполнение запроса к ArrayList с помощью LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)  
 Выполнение запроса ArrayList в C#.  
  
 [Практическое руководство. Добавление настраиваемых методов для запросов LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md)  
 Расширение набора методов, которые можно использовать для запросов LINQ путем добавления методов расширения в интерфейс <xref:System.Collections.Generic.IEnumerable%601>.  
  
 [LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)  
 Ссылки на разделы, рассказывающие LINQ и содержащие примеры кода выполнения запросов.
