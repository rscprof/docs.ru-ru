---
title: Рекомендуется использовать XML-теги для комментариев документации (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlDocComment
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
ms.openlocfilehash: 3b2dec4224006d35fb9add11e170b9dcbeeafcf3
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "43881286"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a><span data-ttu-id="e68ea-102">Рекомендуется использовать XML-теги для комментариев документации (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e68ea-102">Recommended XML Tags for Documentation Comments (Visual Basic)</span></span>
<span data-ttu-id="e68ea-103">Компилятор Visual Basic может обработать комментарии документации в коде в XML-файл.</span><span class="sxs-lookup"><span data-stu-id="e68ea-103">The Visual Basic compiler can process documentation comments in your code to an XML file.</span></span> <span data-ttu-id="e68ea-104">Дополнительные средства можно использовать для обработки XML-файла в документации.</span><span class="sxs-lookup"><span data-stu-id="e68ea-104">You can use additional tools to process the XML file into documentation.</span></span>  
  
 <span data-ttu-id="e68ea-105">Комментарии XML разрешены в конструкциях кода, таких как типы и члены типов.</span><span class="sxs-lookup"><span data-stu-id="e68ea-105">XML comments are allowed on code constructs such as types and type members.</span></span> <span data-ttu-id="e68ea-106">Для разделяемых типов только одна часть типа может содержать комментарии XML, несмотря на то, что нет никаких ограничений на комментирование его членов.</span><span class="sxs-lookup"><span data-stu-id="e68ea-106">For partial types, only one part of the type can have XML comments, although there is no restriction on commenting its members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e68ea-107">Комментарии документации не может применяться к пространствам имен.</span><span class="sxs-lookup"><span data-stu-id="e68ea-107">Documentation comments cannot be applied to namespaces.</span></span> <span data-ttu-id="e68ea-108">Причина заключается в одно пространство имен может охватывать несколько сборок, что не все сборки должны загружаться в то же время.</span><span class="sxs-lookup"><span data-stu-id="e68ea-108">The reason is that one namespace can span several assemblies, and not all assemblies have to be loaded at the same time.</span></span>  
  
 <span data-ttu-id="e68ea-109">Компилятор обрабатывает любой тег, допустимый XML-код.</span><span class="sxs-lookup"><span data-stu-id="e68ea-109">The compiler processes any tag that is valid XML.</span></span> <span data-ttu-id="e68ea-110">Следующие теги предоставляют часто используемые возможности в документации для пользователей.</span><span class="sxs-lookup"><span data-stu-id="e68ea-110">The following tags provide commonly used functionality in user documentation.</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="e68ea-111">\<c></span><span class="sxs-lookup"><span data-stu-id="e68ea-111">\<c></span></span>](../../../visual-basic/language-reference/xmldoc/c.md)|[<span data-ttu-id="e68ea-112">\<code></span><span class="sxs-lookup"><span data-stu-id="e68ea-112">\<code></span></span>](../../../visual-basic/language-reference/xmldoc/code.md)|[<span data-ttu-id="e68ea-113">\<example></span><span class="sxs-lookup"><span data-stu-id="e68ea-113">\<example></span></span>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|<span data-ttu-id="e68ea-114">[\<исключение >](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e68ea-114">[\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup></span></span>|<span data-ttu-id="e68ea-115">[\<включить >](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e68ea-115">[\<include>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup></span></span>|[<span data-ttu-id="e68ea-116">\<list></span><span class="sxs-lookup"><span data-stu-id="e68ea-116">\<list></span></span>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[<span data-ttu-id="e68ea-117">\<para></span><span class="sxs-lookup"><span data-stu-id="e68ea-117">\<para></span></span>](../../../visual-basic/language-reference/xmldoc/para.md)|<span data-ttu-id="e68ea-118">[\<PARAM >](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e68ea-118">[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup></span></span>|[<span data-ttu-id="e68ea-119">\<paramref></span><span class="sxs-lookup"><span data-stu-id="e68ea-119">\<paramref></span></span>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|<span data-ttu-id="e68ea-120">[\<разрешение >](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e68ea-120">[\<permission>](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup></span></span>|[<span data-ttu-id="e68ea-121">\<remarks></span><span class="sxs-lookup"><span data-stu-id="e68ea-121">\<remarks></span></span>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[<span data-ttu-id="e68ea-122">\<returns></span><span class="sxs-lookup"><span data-stu-id="e68ea-122">\<returns></span></span>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|<span data-ttu-id="e68ea-123">[\<см. в разделе >](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e68ea-123">[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup></span></span>|<span data-ttu-id="e68ea-124">[\<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e68ea-124">[\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup></span></span>|[<span data-ttu-id="e68ea-125">\<summary></span><span class="sxs-lookup"><span data-stu-id="e68ea-125">\<summary></span></span>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|<span data-ttu-id="e68ea-126">[\<typeparam >](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e68ea-126">[\<typeparam>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup></span></span>|[<span data-ttu-id="e68ea-127">\<value></span><span class="sxs-lookup"><span data-stu-id="e68ea-127">\<value></span></span>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 <span data-ttu-id="e68ea-128">(<sup>1</sup> компилятор проверяет синтаксис.)</span><span class="sxs-lookup"><span data-stu-id="e68ea-128">(<sup>1</sup> The compiler verifies syntax.)</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e68ea-129">В текст комментария документации угловые скобки, используйте `&lt;` и `&gt;`.</span><span class="sxs-lookup"><span data-stu-id="e68ea-129">If you want angle brackets to appear in the text of a documentation comment, use `&lt;` and `&gt;`.</span></span> <span data-ttu-id="e68ea-130">Например, строка `"&lt;text in angle brackets&gt;"` будет отображаться как `<text in angle brackets>`.</span><span class="sxs-lookup"><span data-stu-id="e68ea-130">For example, the string `"&lt;text in angle brackets&gt;"` will appear as `<text in angle brackets>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e68ea-131">См. также</span><span class="sxs-lookup"><span data-stu-id="e68ea-131">See Also</span></span>  
 [<span data-ttu-id="e68ea-132">Документирование кода с помощью XML</span><span class="sxs-lookup"><span data-stu-id="e68ea-132">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)  
 [<span data-ttu-id="e68ea-133">/doc</span><span class="sxs-lookup"><span data-stu-id="e68ea-133">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)  
 [<span data-ttu-id="e68ea-134">Практическое руководство. Создание XML-документации</span><span class="sxs-lookup"><span data-stu-id="e68ea-134">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)