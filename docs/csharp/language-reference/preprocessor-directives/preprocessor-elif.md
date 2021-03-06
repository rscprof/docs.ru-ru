---
title: '#elif (справочник по C#)'
ms.date: 07/20/2015
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
ms.openlocfilehash: 423cedfb947964172a6e06d54a6dd3c76d91e9f3
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/01/2018
ms.locfileid: "43418207"
---
# <a name="elif-c-reference"></a>#elif (Справочник по C#)
Директива `#elif` позволяет создать составную условную директиву. Выражение `#elif` будет вычисляться в том случае, если ни одна из предшествующих директив [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) или необязательных директив `#elif` после вычисления выражения не возвращает значение `true`. Если после вычисления выражения `#elif` возвращается значение `true`, компилятор вычисляет весь код между директивой `#elif` и следующей условной директивой. Пример:  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.WriteLine("Debug build");  
#elif VC7  
    Console.WriteLine("Visual Studio 7");  
#endif  
```  
  
 Для вычисления нескольких символов можно использовать операторы `==` (равенство), `!=` (неравенство), `&&` (И) и `||` (ИЛИ). Можно также группировать символы и операторы при помощи скобок.  
  
## <a name="remarks"></a>Примечания  
 Применение `#elif` эквивалентно следующему:  
  
```csharp
#else  
#if  
```  
  
 Директива `#elif` позволяет упростить код, поскольку для каждой директивы `#if` требуется отдельная директива [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), тогда как `#elif` можно использовать без соответствующей директивы `#endif`.  
  
 В разделе [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) приводится пример использования директивы `#elif`.  
  
## <a name="see-also"></a>См. также

- [Справочник по C#](../../../csharp/language-reference/index.md)  
- [Руководство по программированию на C#](../../../csharp/programming-guide/index.md)  
- [Директивы препроцессора C#](../../../csharp/language-reference/preprocessor-directives/index.md)
