---
title: Практическое руководство. Перемещение элемента ToolStrip из контейнера ToolStripContainer в форму
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], parenting to forms
- Windows Forms, parenting ToolStrip controls
ms.assetid: a1c94a7f-6fc5-4e4c-84cf-ff11dc573d33
ms.openlocfilehash: a4b6e3bbc0750ba69607b5c0f96bdbb542aea1be
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/04/2018
ms.locfileid: "43529402"
---
# <a name="how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a>Практическое руководство. Перемещение элемента ToolStrip из контейнера ToolStripContainer в форму
Используйте следующую процедуру для перемещения <xref:System.Windows.Forms.ToolStrip> из <xref:System.Windows.Forms.ToolStripContainer> на форму.  
  
> [!NOTE]
>  Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a>Для перемещения ToolStrip из контейнера ToolStripContainer в форму  
  
1.  Выберите <xref:System.Windows.Forms.ToolStrip>.  
  
2.  Вырезать <xref:System.Windows.Forms.ToolStrip> , нажав сочетание клавиш CTRL + X, или щелкните правой кнопкой мыши <xref:System.Windows.Forms.ToolStrip> и выберите **Вырезать** в контекстном меню.  
  
3.  Выберите форму.  
  
4.  Вставить <xref:System.Windows.Forms.ToolStrip> , нажав сочетание клавиш CTRL + V, или выберите **вставить** из **изменить** меню.  
  
5.  Задайте <xref:System.Windows.Forms.ToolStrip.Dock%2A> свойство <xref:System.Windows.Forms.ToolStrip> для **верхней**.  
  
## <a name="see-also"></a>См. также  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripContainer>  
 [Общие сведения об элементе управления ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
