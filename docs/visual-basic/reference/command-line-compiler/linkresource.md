---
title: -linkresource (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
ms.openlocfilehash: 4f4b3db768b5466f8912b66a0a4709d0f773c1f3
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/07/2018
ms.locfileid: "44047195"
---
# <a name="-linkresource-visual-basic"></a>-linkresource (Visual Basic)
Создает ссылку на управляемый ресурс.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-linkresource:filename[,identifier[,public|private]]  
' -or-  
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>Аргументы  
 `filename`  
 Обязательно. Файл ресурсов, ссылки на сборку. Если имя файла содержит пробел, заключите имя в кавычки (» «).  
  
 `identifier`  
 Необязательный. Логическое имя ресурса. Имя, которое используется для загрузки ресурса. По умолчанию используется имя файла. При необходимости можно указать, является ли файл открытым или закрытым в манифесте сборки, например: `-linkres:filename.res,myname.res,public`. По умолчанию `filename` является открытым в сборке.  
  
## <a name="remarks"></a>Примечания  
 `-linkresource` Параметр не внедрить файл ресурсов в выходной файл; используйте `-resource` параметр, чтобы это сделать.  
  
 `-linkresource` Параметр требует одного из `-target` параметры, отличные от `-target:module`.  
  
 Если `filename` — [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] файл ресурсов, созданным, например, по [Resgen.exe (генератор файлов ресурсов)](https://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) или в среде разработки, он может осуществляться с помощью членов пространства <xref:System.Resources> пространства имен. (Дополнительные сведения см. в разделе <xref:System.Resources.ResourceManager>.) Чтобы получить доступ к всем остальным ресурсам во время выполнения, используйте методы, которые начинаются с `GetManifestResource` в <xref:System.Reflection.Assembly> класса.  
  
 Имя файла может иметь любой формат файла. Например, может потребоваться сделать имеющуюся на компьютере библиотеку DLL частью сборки, поэтому ее можно разместить в глобальном кэше сборок и обеспечить к ней доступ из управляемого кода сборки.  
  
 Краткой формой `-linkresource` является `-linkres`.  
  
> [!NOTE]
>  `-linkresource` Параметр недоступен в среде разработки Visual Studio; она доступна только при компиляции из командной строки.  
  
## <a name="example"></a>Пример  
 Следующий код компилирует `in.vb` и ссылки на файл ресурсов `rf.resource`.  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a>См. также  
 [Компилятор Visual Basic с интерфейсом командной строки](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [-ресурсов (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)  
 [Примеры командных строк компиляции](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
