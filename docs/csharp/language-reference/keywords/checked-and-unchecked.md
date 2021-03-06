---
title: Checked и Unchecked (Справочник по C#)
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: 04f603905690497bcd4249f73c7296be2c269a60
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2018
ms.locfileid: "43468815"
---
# <a name="checked-and-unchecked-c-reference"></a>Checked и Unchecked (Справочник по C#)
Строка кода C# может выполняться как в проверенном, так и в непроверенном контексте. В проверенном контексте арифметическое переполнение создает исключение. В непроверяемом контексте арифметическое переполнение игнорируется и результат усекается путем удаления старших разрядов, которые не помещаются в целевой тип данных.  
  
-   [checked](checked.md). Укажите проверенный контекст.  
  
-   [unchecked](unchecked.md). Укажите непроверенный контекст.  
  
 Следующие операции не затрагиваются проверкой переполнения.  
  
-   Выражения, использующие следующие предопределенные операторы на целочисленных типах:  
  
     `++`, `--`; унарные `-`, `+`, `-`, `*`, `/`.  
  
-   Явные числовые преобразования между целочисленными типами либо из `float` или `double` в целочисленный тип.  
  
 Если ни `checked`, ни `unchecked` не указаны, контекст по умолчанию для неконстантных выражений (выражения, вычисляемые во время выполнения) определяется по значению параметра компилятора [-checked](../compiler-options/checked-compiler-option.md). По умолчанию значение этого параметра не задано, и арифметические операции выполняются в непроверенном контексте.
 
 Для константных выражений (выражения, которые можно полностью вычислить во время компиляции) контекстом по умолчанию является проверяемый. Если только константное выражение явным образом не размещено в непроверенном контексте, переполнения, возникающие при вычислении выражения во время компиляции, вызывают ошибки времени компиляции.
  
## <a name="see-also"></a>См. также  

- [Справочник по C#](../index.md)  
- [Руководство по программированию на C#](../../programming-guide/index.md)  
- [Ключевые слова в C#](index.md)  
- [Ключевые слова операторов](statement-keywords.md)
