---
title: Создание запросов LINQ на языке C#
description: Узнайте, как создавать запросы LINQ на языке C#.
ms.date: 12/1/2016
ms.assetid: 30703f79-cf3a-4d02-b892-c95d58a1d9ed
ms.openlocfilehash: 2ebba0d2d601932c976a88726fbe3ed37daffdcb
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2018
ms.locfileid: "43463108"
---
# <a name="write-linq-queries-in-c"></a>Создание запросов LINQ на языке C# #

В этой статье рассматриваются три способа создания запросов LINQ в C#:

1. Используя синтаксис запроса.

2. Используя синтаксис метода.

3. Используя комбинацию синтаксиса запроса и синтаксиса метода.

Следующие примеры демонстрируют некоторые простые запросы LINQ, составленные с использованием каждого из указанных выше методов. Как правило, по возможности следует использовать метод (1), а (2) или (3) при необходимости.

> [!NOTE]
> Эти запросы обращаются к простым коллекциям в памяти, однако базовый синтаксис при этом точно такой же, как в запросах LINQ to Entities и LINQ to XML.

## <a name="example---query-syntax"></a>Пример синтаксиса запросов

Для создания запросов рекомендуется использовать *синтаксис запроса*, позволяющий создавать *выражения запросов*. В следующем примере показаны три выражения запросов. Первое выражение запроса показывает, как фильтровать или ограничивать результаты, применяя условия в предложении `where`. Оно возвращает все элементы исходной последовательности, значения которых больше 7 или меньше 3. Второе выражение показывает, как сортировать возвращаемые результаты. Третье выражение показывает, как группировать результаты по ключу. Этот запрос возвращает две группы на основе первой буквы слова.

[!code-csharp[csProgGuideLINQ#5](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_1.cs)]

Обратите внимание, что запросы имеют тип <xref:System.Collections.Generic.IEnumerable%601>. Все эти запросы можно написать с помощью `var`, как показано в следующем примере:

`var query = from num in numbers...`

В каждом из предыдущих примеров запросы фактически не выполняются, пока не произойдет итерация переменной запроса в операторе `foreach` или другом операторе. Дополнительные сведения см. в разделе [Введение в запросы LINQ](../programming-guide/concepts/linq/introduction-to-linq-queries.md).

## <a name="example---method-syntax"></a>Пример синтаксиса метода

Некоторые операции запросов должны быть выражены как вызов метода. Как правило, такие методы возвращают одноэлементные числовые значения, например <xref:System.Linq.Enumerable.Sum%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.Average%2A> и другие. Эти методы необходимо вызывать в запросе последними, поскольку представляют только одно значение и не могут служить источником для дополнительной операции запроса. В следующем примере показан вызов метода в выражении запроса:

[!code-csharp[csProgGuideLINQ#6](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_2.cs)]

Если метод имеет параметры Action или Func, они предоставляются в виде [лямбда](../programming-guide/statements-expressions-operators/lambda-expressions.md)-выражения, как показано в следующем примере:

[!code-csharp[csProgGuideLINQ#7](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_3.cs)]

Из числа предыдущих запросов незамедлительно выполняется только запрос 4. Это связано с тем, что возвращается одно значение, а не универсальная коллекция <xref:System.Collections.Generic.IEnumerable%601>. Сам метод для вычисления значения должен использовать `foreach`.

Каждый из предыдущих запросов может быть написан с использованием неявной типизации по переменной [var](../language-reference/keywords/var.md), как показано в следующем примере:

[!code-csharp[csProgGuideLINQ#8](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_4.cs)]

## <a name="example---mixed-query-and-method-syntax"></a>Пример смешанного синтаксиса запроса и метода

В этом примере показано, как применять синтаксис метода к результатам предложения запроса. Просто заключите выражение запроса в круглые скобки, а затем примените оператор точки и вызовите метод. В следующем примере запрос 7 возвращает количество чисел со значением от 3 до 7. При этом в целом сохранять результат вызова метода лучше во вторую переменную. В этом случае меньше вероятность спутать запрос с его результатами.

[!code-csharp[csProgGuideLINQ#9](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_5.cs)]

Поскольку запрос 7 возвращает одно значение, а не коллекцию, он выполняется незамедлительно.

Предыдущий запрос можно написать, используя неявную типизацию с переменной `var`, как показано ниже:

```csharp
var numCount = (from num in numbers...
```

При записи в синтаксисе метода он будет выглядеть следующим образом:

```csharp
var numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

При записи с явной типизацией он будет выглядеть следующим образом:

```csharp
int numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

## <a name="see-also"></a>См. также

- [Пошаговое руководство. Написание запросов на C#](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)
- [LINQ](index.md)
- [предложение where](../language-reference/keywords/where-clause.md)