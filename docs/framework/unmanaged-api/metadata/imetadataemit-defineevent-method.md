---
title: "Метод IMetaDataEmit::DefineEvent"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineEvent
helpviewer_keywords:
- IMetaDataEmit::DefineEvent method [.NET Framework metadata]
- DefineEvent method [.NET Framework metadata]
ms.assetid: cf064bac-9a9f-41c5-9e1d-108ff7af3afe
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bf790ce270565abaf1d91e54c9e3569a50ab3435
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefineevent-method"></a><span data-ttu-id="d2ea4-102">Метод IMetaDataEmit::DefineEvent</span><span class="sxs-lookup"><span data-stu-id="d2ea4-102">IMetaDataEmit::DefineEvent Method</span></span>
<span data-ttu-id="d2ea4-103">Создает определение события с заданной подписью метаданных и получает маркер для этого определения событий.</span><span class="sxs-lookup"><span data-stu-id="d2ea4-103">Creates a definition for an event with the specified metadata signature, and gets a token to that event definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2ea4-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d2ea4-104">Syntax</span></span>  
  
```  
HRESULT DefineEvent (   
    [in]  mdTypeDef    td,   
    [in]  LPCWSTR      szEvent,   
    [in]  DWORD        dwEventFlags,   
    [in]  mdToken      tkEventType,   
    [in]  mdMethodDef  mdAddOn,   
    [in]  mdMethodDef  mdRemoveOn,   
    [in]  mdMethodDef  mdFire,   
    [in]  mdMethodDef  rmdOtherMethods[],   
    [out] mdEvent      *pmdEvent   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d2ea4-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="d2ea4-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="d2ea4-106">[in] Токен для целевого класса или интерфейса.</span><span class="sxs-lookup"><span data-stu-id="d2ea4-106">[in] The token for the target class or interface.</span></span> <span data-ttu-id="d2ea4-107">Это может быть вызвано `mdTypeDef` или `mdTypeDefNil` токена.</span><span class="sxs-lookup"><span data-stu-id="d2ea4-107">This is either a `mdTypeDef` or `mdTypeDefNil` token.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="d2ea4-108">[in] Имя события.</span><span class="sxs-lookup"><span data-stu-id="d2ea4-108">[in] The name of the event.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="d2ea4-109">[in] Флаги событий.</span><span class="sxs-lookup"><span data-stu-id="d2ea4-109">[in] Event flags.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="d2ea4-110">[in] Токен для класса событий.</span><span class="sxs-lookup"><span data-stu-id="d2ea4-110">[in] The token for the event class.</span></span> <span data-ttu-id="d2ea4-111">Это `mdTypeDef`, `mdTypeRef`, или `mdTokenNil` токена.</span><span class="sxs-lookup"><span data-stu-id="d2ea4-111">This is a `mdTypeDef`, a `mdTypeRef`, or a `mdTokenNil` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="d2ea4-112">[in] Метод, используемый для подписки на событие, или значение null.</span><span class="sxs-lookup"><span data-stu-id="d2ea4-112">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="d2ea4-113">[in] Метод, используемый для отмены подписки на событие, или значение null.</span><span class="sxs-lookup"><span data-stu-id="d2ea4-113">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="d2ea4-114">[in] Метод, используемый (производным классом), чтобы вызвать это событие.</span><span class="sxs-lookup"><span data-stu-id="d2ea4-114">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="d2ea4-115">[in] Массив маркеров для других методов, связанный с событием.</span><span class="sxs-lookup"><span data-stu-id="d2ea4-115">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="d2ea4-116">Заканчивается массива `mdMethodDefNil` токена.</span><span class="sxs-lookup"><span data-stu-id="d2ea4-116">The array is terminated with a `mdMethodDefNil` token.</span></span>  
  
 `pmdEvent`  
 <span data-ttu-id="d2ea4-117">[out] Токен метаданных, присвоенный событию.</span><span class="sxs-lookup"><span data-stu-id="d2ea4-117">[out] The metadata token assigned to the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2ea4-118">Требования</span><span class="sxs-lookup"><span data-stu-id="d2ea4-118">Requirements</span></span>  
 <span data-ttu-id="d2ea4-119">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2ea4-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2ea4-120">**Заголовок:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d2ea4-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d2ea4-121">**Библиотека:** используется как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d2ea4-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d2ea4-122">**Версии платформы .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2ea4-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2ea4-123">См. также</span><span class="sxs-lookup"><span data-stu-id="d2ea4-123">See Also</span></span>  
 [<span data-ttu-id="d2ea4-124">IMetaDataEmit-интерфейс</span><span class="sxs-lookup"><span data-stu-id="d2ea4-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="d2ea4-125">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="d2ea4-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)