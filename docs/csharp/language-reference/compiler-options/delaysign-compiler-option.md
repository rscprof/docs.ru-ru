---
title: -delaysign (параметры компилятора C#)
ms.date: 05/15/2018
f1_keywords:
- /delaysign
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
ms.openlocfilehash: 105f564d40799c1c006caf8b59d6199dbd8e9318
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/01/2018
ms.locfileid: "43400200"
---
# <a name="-delaysign-c-compiler-options"></a>-delaysign (параметры компилятора C#)

Этот параметр указывает компилятору зарезервировать пространство в выходном файле, чтобы впоследствии добавить в него цифровую подпись.

## <a name="syntax"></a>Синтаксис

```console
-delaysign[ + | - ]
```

## <a name="arguments"></a>Аргументы

`+` &#124; `-`

Если требуется полностью подписанная сборка, используйте параметр **-delaysign-**. Если нужно лишь поместить в сборку открытый ключ, используйте параметр **-delaysign+**. Значение по умолчанию — **-delaysign-**.

## <a name="remarks"></a>Примечания

Параметр **-delaysign** никак не действует, если не использовать его с [-keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) или [-keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).

Параметры **-delaysign** и **-publicsign** — взаимоисключающие.

При запросе полностью подписанной сборки компилятор хэширует файл, содержащий манифест (метаданные сборки), и подписывает хэш закрытым ключом. Эта операция предназначена для создания итоговой цифровой подписи, которая хранится в файле, содержащем манифест. При использовании отложенной подписи компилятор не вычисляет и не сохраняет подпись, а резервирует место в файле для добавления подписи в сборку в будущем.

Например, чтобы поместить сборку в глобальный кэш для тестирования, используйте параметр **-delaysign+**. После тестирования можно полностью подписать сборку, поместив в нее закрытый ключ с помощью [компоновщика сборок](../../../framework/tools/al-exe-assembly-linker.md).

Дополнительные сведения см. в разделах [Создание и использование сборок со строгими именами](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) и [Отложенная подпись сборки](../../../framework/app-domains/delay-sign-assembly.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Установка данного параметра компилятора в среде разработки Visual Studio

1. Откройте страницу **свойств** для проекта.
1. Измените свойство **Только отложенная подпись**.

Сведения об установке этого параметра компилятора программными средствами см. в разделе <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.

## <a name="see-also"></a>См. также

- [Параметр -publicsign в C#](publicsign-compiler-option.md)  
- [Параметры компилятора C# ](index.md)  
- [Управление свойствами проектов и решений](/visualstudio/ide/managing-project-and-solution-properties)
