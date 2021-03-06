---
title: Общие сведения об элементе управления SplitContainer (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- SplitContainer
helpviewer_keywords:
- SplitContainer control [Windows Forms], about SplitContainer control
ms.assetid: 6de5a5f7-97a5-402d-be6d-7e2785483db5
ms.openlocfilehash: 81898e09ff513043b205cde13378ae24ee755226
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "44039177"
---
# <a name="splitcontainer-control-overview-windows-forms"></a>Общие сведения об элементе управления SplitContainer (Windows Forms)
Элемент управления Windows Forms <xref:System.Windows.Forms.SplitContainer> состоит из двух панелей, разделенных подвижной полосой. При наведении указателя мыши на полосу его форма изменяется, показывая, что полоса является перемещаемой.  
  
> [!IMPORTANT]
>  В **элементов**, <xref:System.Windows.Forms.SplitContainer> элемент управления заменяет <xref:System.Windows.Forms.Splitter> элемента управления, который имелся в предыдущей версии Visual Studio. Элемент управления <xref:System.Windows.Forms.SplitContainer> намного предпочтительнее, чем элемент управления <xref:System.Windows.Forms.Splitter>. <xref:System.Windows.Forms.Splitter> Класс по-прежнему включен в [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] для совместимости с существующими приложениями, но мы настоятельно рекомендуем использовать <xref:System.Windows.Forms.SplitContainer> управления для новых проектов.  
  
 С помощью <xref:System.Windows.Forms.SplitContainer> элемента управления, вы можете создавать сложные пользовательские интерфейсы; часто выбор на одной панели определяет объекты, отображаемые на панели. Такой подход является весьма эффективным для отображения и просмотра информации. Две панели для сбора информации в областях, а также панели, или «разделитель», упрощают изменение размера панелей.  
  
 Более одного <xref:System.Windows.Forms.SplitContainer> управления также могут быть вложенными, со вторым <xref:System.Windows.Forms.SplitContainer> управления ориентирован горизонтально, создайте верхней и нижней панели.  
  
 Имейте в виду, что <xref:System.Windows.Forms.SplitContainer> управления клавиатуры по умолчанию; пользователи могут нажимайте клавиши со стрелками для перемещения разделителя, если <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> свойству `false`.  
  
 <xref:System.Windows.Forms.SplitContainer.Orientation%2A> Свойство <xref:System.Windows.Forms.SplitContainer> управления определяет направление разделителя, а не сам элемент управления. Таким образом, если этому свойству присвоено <xref:System.Windows.Forms.Orientation.Vertical>, разделитель выполняется сверху вниз, создание левой и правой панели.  
  
 Кроме того, следует помнить, значение <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> свойство изменяется в зависимости от значения <xref:System.Windows.Forms.SplitContainer.Orientation%2A> свойство. Дополнительные сведения см. в разделе <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> свойство.  
  
 Также можно ограничить размер и перемещения <xref:System.Windows.Forms.SplitContainer> элемента управления. <xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> Свойство определяет, какая панель останется на тот же размер после <xref:System.Windows.Forms.SplitContainer> изменения размеров элемента управления и <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> свойство определяет, если разделитель является перемещаемым, клавиатуры или мыши.  
  
> [!NOTE]
>  Даже если <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> свойству `true`, разделитель может по-прежнему быть перемещен программных средств; например, с помощью <xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> свойство.  
  
 Наконец, каждой панели <xref:System.Windows.Forms.SplitContainer> элемент управления имеет свойства, чтобы определить его размер отдельных.  
  
## <a name="commonly-used-properties-methods-and-events"></a>Часто используемые свойства, методы и события  
  
|name|Описание|  
|----------|-----------------|  
|Свойство <xref:System.Windows.Forms.SplitContainer.FixedPanel%2A>|Определяет, какая из панелей не меняется размер после <xref:System.Windows.Forms.SplitContainer> размер элемента управления.|  
|Свойство <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A>|Определяет, если разделитель можно перемещать с помощью клавиатуры или мыши.|  
|Свойство <xref:System.Windows.Forms.SplitContainer.Orientation%2A>|Определяет, если расположение разделителя вертикально или горизонтально.|  
|Свойство <xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A>|Определяет расстояние в пикселях от левого или верхнего края для перемещаемой полосы-разделителя.|  
|Свойство <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>|Определяет минимальное расстояние в пикселях, что разделитель может быть перемещен пользователем.|  
|Свойство <xref:System.Windows.Forms.SplitContainer.SplitterWidth%2A>|Определяет ширину в пикселях разделителя.|  
|Событие <xref:System.Windows.Forms.SplitContainer.SplitterMoving>|Происходит, когда разделитель является перемещение.|  
|Событие <xref:System.Windows.Forms.SplitContainer.SplitterMoved>|Происходит при перемещении разделителя.|  
  
## <a name="see-also"></a>См. также  
 <xref:System.Windows.Forms.SplitContainer>  
 [Элемент управления SplitContainer](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)  
 [Пример элемента управления SplitContainer](https://msdn.microsoft.com/library/9015fad0-7108-4d85-a83a-a72d038c4f65)
