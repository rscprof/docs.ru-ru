---
title: Разработка параметров
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines [.NET Framework], parameters
- members [.NET Framework], parameters
- names [.NET Framework], parameters
- parameters, design guidelines
- reserved parameters
ms.assetid: 3f33bf46-4a7b-43b3-bb78-1ffebe0dcfa6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea5311de8cef266af23b259d943568bfa95eaf72
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/07/2018
ms.locfileid: "44128830"
---
# <a name="parameter-design"></a>Разработка параметров
Этот раздел содержит общие рекомендации по разработке параметров, включая разделы с рекомендации по проверке аргументов. Кроме того, следует ознакомиться с рекомендации, приведенные в [именования параметров](../../../docs/standard/design-guidelines/naming-parameters.md).  
  
 **✓ DO** использовать бы производный тип параметра, который предоставляет функциональные возможности, необходимые для элемента.  
  
 Например предположим, что необходимо разработать метод, который перечисляет коллекцию и печатает каждый элемент в консоль. Такой метод должен принимать <xref:System.Collections.IEnumerable> как параметр, не <xref:System.Collections.ArrayList> или <xref:System.Collections.IList>, например.  
  
 **X DO NOT** использовать зарезервированные параметры.  
  
 Если в одной из последующих версий необходимо дополнительные входные данные для члена, могут добавляться новая перегрузка.  
  
 **X DO NOT** открытым методы, принимающие указатели, массивы указателей или многомерных массивов в качестве параметров.  
  
 Указатели и многомерные массивы являются довольно сложно использовать правильно. Практически во всех случаях API-интерфейсов может быть переработано избежать этих типов в качестве параметров.  
  
 **✓ DO** поместите все `out` параметров после всех по значению и `ref` параметров (за исключением массивы параметров), даже если это приводит к несогласованность параметров перегрузки в (см. [члена Перегрузка](../../../docs/standard/design-guidelines/member-overloading.md)).  
  
 `out` Параметры можно рассматривать как очень возвращаемые значения и сгруппировать их метод подпись становится легче понять.  
  
 **✓ DO** быть согласованы в именовании параметров при перегрузке членов или реализации интерфейсов.  
  
 Это лучше взаимодействует связь между этими методами.  
  
### <a name="choosing-between-enum-and-boolean-parameters"></a>Выбор между Enum и логических параметров  
 **✓ DO** использовать перечисления, если член будет иметь два или более логических параметров.  
  
 **X DO NOT** используйте логические значения, пока не будет точно знать, никогда не возникнет необходимость использования более двух значений.  
  
 Перечисления предоставляют некоторый запас будущих сложение значений, но следует иметь в виду возможное влияние добавления значения перечислений, которые описаны в [Разработка перечислений](../../../docs/standard/design-guidelines/enum.md).  
  
 **✓ CONSIDER** с помощью логических значений для параметров конструктора, действительно два значения состояния и используются исключительно для инициализации свойства типа Boolean.  
  
### <a name="validating-arguments"></a>Проверка аргументов  
 **✓ DO** проверить аргументы, передаваемые открытый, защищенный или явно реализованный членов. Исключение <xref:System.ArgumentException?displayProperty=nameWithType>, или одного из его подклассов, если проверка не пройдена.  
  
 Обратите внимание, что фактическая проверка не обязательно должна производиться в сам открытый или защищенный элемент. Может произойти на более низком уровне в подпрограмме некоторые закрытым или внутренним. Самое главное, что всей контактной зоной, предоставляемая конечным пользователям проверяет аргументы.  
  
 **✓ DO** throw <xref:System.ArgumentNullException> Если передается аргумент null и элемент не поддерживает аргументы null.  
  
 **✓ DO** проверки для параметров перечислений.  
  
 Не считайте, что аргументы enum будет находиться в диапазоне, определяемых перечислением. Среда CLR позволяет приведение любого целого числа в значение перечисления, даже если значение не определено в перечислении.  
  
 **X DO NOT** использовать <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> диапазона перечисления проверяет.  
  
 **✓ DO** Имейте в виду, что изменяемые аргументы могут были изменены после они были проверены.  
  
 Если член является влияет на безопасность, вы, рекомендуется создать копию, а затем проверить и обработать аргумент.  
  
### <a name="parameter-passing"></a>Передача параметров  
 С точки зрения конструктор framework, существует три основных группы параметров: параметры, по значению `ref` параметров, и `out` параметров.  
  
 Если аргумент, передаваемый в качестве параметра по значению, член получает копию фактического аргумента, переданного в. Если аргумент является типом значения, копию аргумента помещается в стек. Если аргумент является ссылочным типом, копии ссылки помещается в стек. Наиболее популярных языков среды CLR, таких как C#, VB.NET и C++, по умолчанию для передачи параметров по значению.  
  
 Если аргумент, передаваемый через `ref` параметра, члена получает ссылку на фактический аргумент, передаваемый в. Если аргумент является типом значения, ссылка на аргумент помещается в стек. Если аргумент является ссылочным типом, ссылку на ссылку помещается в стек. `Ref` параметры могут использоваться, элемент изменить аргументы, передаваемые в вызывающем объекте.  
  
 `Out` параметры аналогичны `ref` параметров, некоторые небольшие различия. Параметр считается изначально неназначенных и не удается прочитать в теле элемента перед его присваиванием некоторое значение. Кроме того параметр должен быть назначен некоторое значение, прежде чем элемент возвращает.  
  
 **X AVOID** с помощью `out` или `ref` параметров.  
  
 С помощью `out` или `ref` параметров требуется опыт работы с указателями, понимание отличия между типами значения и ссылочными типами и умение работать с методами с несколькими возвращаемыми значениями. Кроме того, разница между `out` и `ref` параметров не все понимают. Архитекторы Framework, разработке для широкого использования не должен ожидать пользователям разрабатывающим `out` или `ref` параметров.  
  
 **X DO NOT** передачи ссылочных типов по ссылке.  
  
 Существует несколько исключений для правила, например метод, который может использоваться для замены ссылок.  
  
### <a name="members-with-variable-number-of-parameters"></a>Члены с переменным числом параметров  
 Члены, которые могут принимать переменное число аргументов выражаются, предоставляя параметр массива. Например <xref:System.String> предоставляет следующий метод:  
  
```  
public class String {  
    public static string Format(string format, object[] parameters);  
}  
```  
  
 Пользователь может затем вызвать <xref:System.String.Format%2A?displayProperty=nameWithType> метода, как показано ниже:  
  
 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`  
  
 Добавление ключевого слова C# params к параметру массива изменяет параметр к параметру массива так называемые params и сочетание клавиш для создания временного массива.  
  
```  
public class String {  
    public static string Format(string format, params object[] parameters);  
}  
```  
  
 Это позволяет вызывать метод, передав элементы массива непосредственно в списке аргументов.  
  
 `String.Format("File {0} not found in {1}",filename,directory);`  
  
 Обратите внимание, что ключевое слово params могут добавляться только к последнему параметру в списке параметров.  
  
 **✓ CONSIDER** Добавление ключевого слова params параметров массива, если ожидается, что конечных пользователей для передачи массивов с небольшим числом элементов. Если предполагается, что большое количество элементов будут передаваться в распространенных сценариях, пользователи скорее всего, не будет передавать эти встроенные элементы в любом случае, и ключевого слова params не требуется.  
  
 **X AVOID** использование массивов params в том случае, если вызывающий объект будет почти всегда уже входные данные в виде массива.  
  
 Например элементы с помощью параметров-массивов байтов практически никогда не будет называться путем передачи отдельных байтов. По этой причине параметров массива байтов в .NET Framework не используйте ключевое слово params.  
  
 **X DO NOT** используйте массивы params, если массив изменен членом, принимающим параметр params массива.  
  
 Из-за того, что многие компилятор преобразует аргументы в элемент во временный массив во время вызова массив может быть временным объектом, и таким образом будут потеряны все изменения в массив.  
  
 **✓ CONSIDER** с помощью ключевого слова params в простой перегрузке, даже если более сложная перегрузка не может использовать его.  
  
 Спросите себя, если бы значение для пользователей с массивом параметров в одной перегрузке, даже если он не был в все перегрузки.  
  
 **✓ DO** попытайтесь Упорядочить параметры, чтобы сделать возможным использование ключевого слова params.  
  
 **✓ CONSIDER** предусматривать особые перегрузки и ветви кода для вызовов с небольшим числом аргументов в API-интерфейсы важна высокая производительность.  
  
 Это позволяет избежать создания массива объектов при вызове API с небольшим числом аргументов. Имена параметров образуют единственном параметра массива и добавление числовой суффикс.  
  
 Это следует только сделать Если предполагается особым путь весь код, не просто создать массив и вызвать метод более общими.  
  
 **✓ DO** Имейте в виду, null может быть передан в качестве аргумента массива params.  
  
 Обязательно проверяйте, что массив не равен null, если перед обработкой.  
  
 **X DO NOT** использовать `varargs` методы, также известный как кнопку с многоточием.  
  
 Некоторых языков среды CLR, например C++, поддерживают альтернативные соглашение о передаче вызывается списки параметров переменных `varargs` методы. Соглашение не следует на платформах, так как он не является CLS-совместимым.  
  
### <a name="pointer-parameters"></a>Параметры-указатели  
 В общем случае указатели не должны отображаться в общую контактную зону структуры хорошо спроектированной управляемого кода. В большинстве случаев, должна быть включена указатели. Однако в некоторых случаях указатели являются обязательными в целях взаимодействия, и с использованием указателей в таких случаях подходит.  
  
 **✓ DO** предоставляют альтернативный для любого элемента, который принимает указатель в качестве аргумента, так как указатели не являются CLS-совместимыми.  
  
 **X AVOID** затратного контроля аргументов указатель аргументов.  
  
 **✓ DO** соглашениям общих указателей при разработке члены с указателями.  
  
 Например нет необходимости передавать начальный индекс, так как простой указателями может использоваться для достижения такого же результата.  
  
 *Фрагменты: © Корпорация Майкрософт (Microsoft Corporation), 2005, 2009. Все права защищены.*  
  
 *Перепечатано с разрешения Pearson Education, Inc. из книги [Инфраструктура программных проектов. Соглашения, идиомы и шаблоны для многократно используемых библиотек .NET (2-е издание)](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619), авторы: Кржиштоф Цвалина (Krzysztof Cwalina) и Брэд Абрамс (Brad Abrams). Книга опубликована 22 октября 2008 г. издательством Addison-Wesley Professional в рамках серии, посвященной разработке для Microsoft Windows.*  
  
## <a name="see-also"></a>См. также

- [Правила разработки членов](../../../docs/standard/design-guidelines/member.md)  
- [Рекомендации по проектированию на основе Framework](../../../docs/standard/design-guidelines/index.md)
