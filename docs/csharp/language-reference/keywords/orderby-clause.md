---
title: Предложение orderby (Справочник по C#)
ms.date: 07/20/2015
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
ms.openlocfilehash: de649a7e1608e6a653f3280bfd5c4e52a3b661be
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2018
ms.locfileid: "43391201"
---
# <a name="orderby-clause-c-reference"></a>Предложение orderby (Справочник по C#)

В выражении запроса предложение `orderby` задает сортировку возвращаемой последовательности или вложенной последовательности (группы) в порядке возрастания или убывания. Для выполнения одной или нескольких операций последующей сортировки можно указать несколько ключей. Сортировка выполняется с помощью функции сравнения по умолчанию для соответствующего типа элемента. По умолчанию используется порядок сортировки по возрастанию. Также можно указать настраиваемую функцию сравнения. Тем не менее сделать это можно только с использованием синтаксиса на основе метода. Дополнительные сведения см. в разделе [Сортировка данных](../../programming-guide/concepts/linq/sorting-data.md).

## <a name="example"></a>Пример

В следующем примере первый запрос сортирует слова в алфавитном порядке, начиная с A. Второй запрос сортирует эти же слова в порядке убывания. (Ключевое слово `ascending` определяет порядок сортировки по умолчанию и может быть опущено.)

[!code-csharp[cscsrefQueryKeywords#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#20)]

## <a name="example"></a>Пример

В следующем примере выполняется первичная сортировка списка студентов по фамилиям, а затем дополнительная сортировка по именам.

[!code-csharp[cscsrefQueryKeywords#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#22)]

## <a name="remarks"></a>Примечания

Во время компиляции предложение `orderby` преобразуется в вызов метода <xref:System.Linq.Enumerable.OrderBy%2A>. Если в предложении `orderby` используется несколько ключей, они преобразуются в вызовы метода <xref:System.Linq.Enumerable.ThenBy%2A>.

## <a name="see-also"></a>См. также

- [Справочник по C#](../index.md)
- [Ключевые слова запроса (LINQ)](query-keywords.md)
- [LINQ](../../linq/index.md)
- [предложение group](group-clause.md)
- [Приступая к работе с LINQ в C#](../../programming-guide/concepts/linq/getting-started-with-linq.md)