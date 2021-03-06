---
title: Массив имеет фиксированный размер или временно заблокирован (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: e912bd202603d9a0f427418708ad584c7d6203e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593568"
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a>Массив имеет фиксированный размер или временно заблокирован (Visual Basic)
Эта ошибка имеет следующие возможные причины:  
  
-   С помощью `ReDim` изменение числа элементов массива фиксированного размера.  
  
-   Изменение размерности динамического массива на уровне модуля, в котором один элемент был передан процедуре в качестве аргумента. Если передается элемент, массив заблокирован, чтобы предотвратить освобождение памяти для параметра ссылки в пределах процедуры.  
  
-   Попытка присвоить значение `Variant` переменная, содержащая массив, но `Variant` заблокирован.  
  
## <a name="to-correct-this-error"></a>Исправление ошибки  
  
1.  Сделайте исходный массив динамическим, а не фиксированным, объявив его с `ReDim` (если массив объявлен внутри процедуры), либо путем объявления его без указания числа элементов (если массив объявляется на уровне модуля.  
  
2.  Определите, требуется ли передача элемента, так как он является видимым в пределах всех процедур в модуле.  
  
3.  Определите, почему заблокирована `Variant` и разблокируйте ее.  
  
## <a name="see-also"></a>См. также  
 [Массивы](../../../visual-basic/programming-guide/language-features/arrays/index.md)
