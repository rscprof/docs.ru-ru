---
title: Практическое руководство. Изменение внешнего вида текста и изображений элемента управления ToolStrip в Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], appearance
- toolbars [Windows Forms], images
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], appearance
- ToolStrip control [Windows Forms], images
- ToolStrip control [Windows Forms], text
- toolbars [Windows Forms], text
ms.assetid: d62dc9d1-2edd-4dfa-aed7-1335d6e13d86
ms.openlocfilehash: d3f53291e24d6a57e798725b716a7fd56eb661b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530534"
---
# <a name="how-to-change-the-appearance-of-toolstrip-text-and-images-in-windows-forms"></a>Практическое руководство. Изменение внешнего вида текста и изображений элемента управления ToolStrip в Windows Forms
Можно управлять отображением текста и изображений на <xref:System.Windows.Forms.ToolStripItem> и их выравниванием относительно друг друга и <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="to-define-what-is-displayed-on-a-toolstripitem"></a>Для определения отображаемых на элемент ToolStripItem  
  
-   Задать <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> свойства нужное значение. Возможные значения — `Image`, `ImageAndText`, `None`, и `Text`. Значение по умолчанию — `ImageAndText`.  
  
    ```vb  
    ToolStripButton2.DisplayStyle = _  
        System.Windows.Forms.ToolStripItemDisplayStyle.Image  
    ```  
  
    ```csharp  
    toolStripButton2.DisplayStyle = System.Windows.Forms.ToolStripItemDisplayStyle.Image;  
    ```  
  
### <a name="to-align-text-on-a-toolstripitem"></a>Для выравнивания текста в элементе управления ToolStripItem  
  
-   Задать <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> свойства нужное значение. Возможные значения — любое сочетание верхней, среднего и нижнего с left, center и right. Значение по умолчанию — `MiddleCenter`.  
  
    ```vb  
    ToolStripSplitButton1.TextAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.TextAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-align-an-image-on-a-toolstripitem"></a>Для выравнивания изображения на элемент ToolStripItem  
  
-   Задать <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> свойства нужное значение. Возможные значения — любое сочетание верхней, среднего и нижнего с left, center и right. Значение по умолчанию — `MiddleLeft`.  
  
    ```vb  
    ToolStripSplitButton1.ImageAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.ImageAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-define-how-toolstripitem-text-and-images-are-displayed-relative-to-each-other"></a>Чтобы настроить отображение выравниванием текста и изображения относительно друг друга  
  
-   Задать <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> свойства нужное значение. Возможные значения — `ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage`, и `TextBeforeImage`. Значение по умолчанию — `ImageBeforeText`.  
  
    ```vb  
    ToolStripButton1.TextImageRelation = _  
        System.Windows.Forms.TextImageRelation.ImageAboveText  
    ```  
  
    ```csharp  
    toolStripButton1.TextImageRelation = System.Windows.Forms.TextImageRelation.ImageAboveText;  
    ```  
  
## <a name="see-also"></a>См. также  
 <xref:System.Windows.Forms.ToolStrip>  
 [Общие сведения об элементе управления ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [Архитектура элемента управления ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [Технологии, положенные в основу работы элемента управления ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
