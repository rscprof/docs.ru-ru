---
title: Многомерные массивы (Руководство по программированию на C#)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
ms.openlocfilehash: 12cc7ff4f0a688145f2dee130e66dbe9a05ec7e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33313853"
---
# <a name="multidimensional-arrays-c-programming-guide"></a>Многомерные массивы (Руководство по программированию на C#)
Массивы могут иметь несколько измерений. Например, следующее объявление создает двухмерный массив из четырех строк и двух столбцов.  
  
 [!code-csharp[csProgGuideArrays#11](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_1.cs)]  
  
 Следующее объявление создает массив из трех измерений: 4, 2 и 3.  
  
 [!code-csharp[csProgGuideArrays#12](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_2.cs)]  
  
## <a name="array-initialization"></a>Инициализация массива  
 Массив можно инициализировать при объявлении, как показано в следующем примере.  
  
 [!code-csharp[csProgGuideArrays#13](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_3.cs)]  
  
 Также можно инициализировать массив без указания ранга.  
  
 [!code-csharp[csProgGuideArrays#14](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_4.cs)]  
  
 Чтобы объявить переменную массива без инициализации, используйте оператор `new` для присвоения массива переменной. Использование оператора `new` показано в следующем примере.  
  
 [!code-csharp[csProgGuideArrays#15](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_5.cs)]  
  
 В следующем примере присваивается значение конкретному элементу массива.  
  
 [!code-csharp[csProgGuideArrays#16](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_6.cs)]  
  
 Аналогичным образом, в следующем примере получается значение конкретного элемента массива, которое присваивается переменной `elementValue`.  
  
 [!code-csharp[csProgGuideArrays#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_7.cs)]  
  
 В следующем примере кода элементы массива инициализируются с использованием значений по умолчанию (кроме массивов массивов).  
  
 [!code-csharp[csProgGuideArrays#17](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_8.cs)]  
  
## <a name="see-also"></a>См. также  
 [Руководство по программированию на C#](../../../csharp/programming-guide/index.md)  
 [Массивы](../../../csharp/programming-guide/arrays/index.md)  
 [Одномерные массивы](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [Массивы массивов](../../../csharp/programming-guide/arrays/jagged-arrays.md)
