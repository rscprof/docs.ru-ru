---
title: Настройка доступа к объектам через My (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
ms.assetid: 4e8279c2-ed5b-4681-8903-8a6671874000
ms.openlocfilehash: b06e71784a4d02bcbcd755d14e57ef88c4322f7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592162"
---
# <a name="customizing-which-objects-are-available-in-my-visual-basic"></a>Настройка доступа к объектам через My (Visual Basic)
В этом разделе описывается, как можно выбирать, какие `My` объекты включены, задав проекта `_MYTYPE` константы условной компиляции. Интегрированная среда разработки (IDE) Visual Studio сохраняет `_MYTYPE` константы условной компиляции для проекта, в соответствии с типом проекта.  
  
## <a name="predefined-mytype-values"></a>Предопределенные значения _MYTYPE  
 Необходимо использовать `/define` компилятора, возможность задания `_MYTYPE` константы условной компиляции. При указании значения для `_MYTYPE` константой, необходимо заключить строковое значение в обратная косая черта и кавычка (\\») последовательности. Например можно использовать:  
  
```  
/define:_MYTYPE=\"WindowsForms\"  
```  
  
 В этой таблице показано, что `_MYTYPE` имеет значение константы условной компиляции для нескольких типов проектов.  
  
|Тип проекта|Значение _MYTYPE|  
|------------------|--------------------|  
|Библиотека классов|«Windows»|  
|Консольное приложение|«Консоль»|  
|Интернет|«Web»|  
|Библиотека веб-элементов управления|«WebControl»|  
|Приложение Windows|«WindowsForms»|  
|При запуске с помощью пользовательского приложения Windows `Sub Main`|«WindowsFormsWithCustomSubMain»|  
|Библиотека элементов управления Windows|«Windows»|  
|Служба Windows|«Консоль»|  
|Empty|«Empty»|  
  
> [!NOTE]
>  Все строки условной компиляции сравнения выполняются с учетом регистра, независимо от того, как `Option Compare` инструкции set.  
  
## <a name="dependent-my-compilation-constants"></a>Зависимые константы компиляции _MY  
 `_MYTYPE` Константы условной компиляции, в свою очередь, управляет значениями из многих других `_MY` константы компиляции:  
  
|_MYTYPE|_MYAPPLICATIONTYPE|_MYCOMPUTERTYPE|_MYFORMS|_MYUSERTYPE|_MYWEBSERVICES|  
|--------------|-------------------------|----------------------|---------------|------------------|---------------------|  
|«Консоль»|«Консоль»|«Windows»|Не определено|«Windows»|true|  
|«Custom»|Не определено|Не определено|Не определено|Не определено|Не определено|  
|«Empty»|Не определено|Не определено|Не определено|Не определено|Не определено|  
|«Web»|Не определено|«Web»|false|«Web»|false|  
|«WebControl»|Не определено|«Web»|false|«Web»|true|  
|«Windows» или «»|«Windows»|«Windows»|Не определено|«Windows»|TRUE|  
|«WindowsForms»|«WindowsForms»|«Windows»|true|«Windows»|true|  
|«WindowsFormsWithCustomSubMain»|«Консоль»|«Windows»|true|«Windows»|true|  
  
 По умолчанию разрешить undefined константы условной компиляции `FALSE`. Можно указать значения для неопределенных констант при компиляции проекта, чтобы переопределить поведение по умолчанию.  
  
> [!NOTE]
>  Когда `_MYTYPE` установлено на «Custom», проект содержит `My` пространства имен, но он не содержит объектов. Однако задание `_MYTYPE` для «Empty» запрещает компилятору добавление `My` пространства имен и ее объектов.  
  
 Эта таблица описывает эффекты предопределенных значений `_MY` константы компиляции.  
  
|Константа|Значение|  
|--------------|-------------|  
|`_MYAPPLICATIONTYPE`|Позволяет `My.Application`, если константа «Консоли «Windows» или «WindowsForms»:<br /><br /> -Версию «Консоль» является производным от <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase>. и содержит меньше элементов, чем версия «Windows».<br />-Версию «Windows» является производным от <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>и имеет меньше элементов, чем версия «WindowsForms».<br />-«WindowsForms» версия `My.Application` является производным от <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>. Если `TARGET` определена константа «winexe», то класс включает `Sub Main` метод.|  
|`_MYCOMPUTERTYPE`|Позволяет `My.Computer`, если константа является «Веб» или «Windows»:<br /><br /> -Версию «Web» является производным от <xref:Microsoft.VisualBasic.Devices.ServerComputer>, и имеет меньше элементов, чем версия «Windows».<br />Версия «Windows» `My.Computer` является производным от <xref:Microsoft.VisualBasic.Devices.Computer>.|  
|`_MYFORMS`|Включает `My.Forms`, если константа является `TRUE`.|  
|`_MYUSERTYPE`|Позволяет `My.User`, если константа является «Веб» или «Windows»:<br /><br /> -«Web» версия `My.User` связан с удостоверением пользователя текущего HTTP-запроса.<br />Версия «Windows» `My.User` связанного с текущего участника потока.|  
|`_MYWEBSERVICES`|Включает `My.WebServices`, если константа является `TRUE`.|  
|`_MYTYPE`|Включает `My.Log`, `My.Request`, и `My.Response`, если константа является «Web».|  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>  
 <xref:Microsoft.VisualBasic.Devices.Computer>  
 <xref:Microsoft.VisualBasic.Logging.Log>  
 <xref:Microsoft.VisualBasic.ApplicationServices.User>  
 [Зависимость My от типа проекта](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)  
 [Условная компиляция](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [/ define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)  
 [Объект My.Forms](../../../visual-basic/language-reference/objects/my-forms-object.md)  
 [Объект My.Request](../../../visual-basic/language-reference/objects/my-request-object.md)  
 [Объект My.Response](../../../visual-basic/language-reference/objects/my-response-object.md)  
 [Объект My.WebServices](../../../visual-basic/language-reference/objects/my-webservices-object.md)
