---
title: Практическое руководство. Определение изменения текста в TextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 1befd18220488334319a55bce2ce602aef20d3d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552956"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a>Практическое руководство. Определение изменения текста в TextBox
В этом примере показано, как использовать <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> событий для выполнения метода всякий раз, когда текст в <xref:System.Windows.Controls.TextBox> элемент управления был изменен.  
  
 В классе кода для [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , содержащий <xref:System.Windows.Controls.TextBox> управления, который требуется отслеживать изменения, вставьте метод, вызываемый при <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> события.  Этот метод должен иметь сигнатуру, которая совпадает с той, которую ожидает <xref:System.Windows.Controls.TextChangedEventHandler> делегата.  
  
 Обработчик событий вызывается всякий раз, когда содержимое <xref:System.Windows.Controls.TextBox> управления изменяются пользователем или программным путем.  
  
 **Примечание:** это событие возникает при <xref:System.Windows.Controls.TextBox> создается и первоначальном заполнении текстом элемента управления.  
  
## <a name="example"></a>Пример  
 В [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , определяющий вашей <xref:System.Windows.Controls.TextBox> контроля, указания <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> атрибут со значением, которое соответствует имени метода обработчика событий.  
  
 [!code-xaml[TextBox_MiscCode#_TextChangedXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]  
  
## <a name="example"></a>Пример  
 В классе кода для [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , содержащий <xref:System.Windows.Controls.TextBox> управления, который требуется отслеживать изменения, вставьте метод, вызываемый при <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> события.  Этот метод должен иметь сигнатуру, которая совпадает с той, которую ожидает <xref:System.Windows.Controls.TextChangedEventHandler> делегата.  
  
 [!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
 [!code-vb[TextBox_MiscCode#_TextChangedEventHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]  
  
 Обработчик событий вызывается всякий раз, когда содержимое <xref:System.Windows.Controls.TextBox> управления изменяются пользователем или программным путем.  
  
 **Примечание:** это событие возникает при <xref:System.Windows.Controls.TextBox> создается и первоначальном заполнении текстом элемента управления.  
  
 Комментарии  
  
## <a name="see-also"></a>См. также  
 <xref:System.Windows.Controls.TextChangedEventArgs>  
 [Общие сведения о TextBox](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [Общие сведения о RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
