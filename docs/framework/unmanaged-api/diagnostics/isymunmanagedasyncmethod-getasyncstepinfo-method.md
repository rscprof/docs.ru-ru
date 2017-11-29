---
title: "Метод ISymUnmanagedAsyncMethod::GetAsyncStepInfo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3ef5b4b8-4ac7-4906-849b-f932c5e3db07
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ad3fb6dba7740c3c541a446205b90d6f007635a3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedasyncmethodgetasyncstepinfo-method"></a><span data-ttu-id="6356a-102">Метод ISymUnmanagedAsyncMethod::GetAsyncStepInfo</span><span class="sxs-lookup"><span data-stu-id="6356a-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo Method</span></span>
<span data-ttu-id="6356a-103">В разделе [метод DefineAsyncStepInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="6356a-103">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6356a-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6356a-104">Syntax</span></span>  
  
```idl  
HRESULT GetAsyncStepInfo(    [in] ULONG32 cStepInfo,    [out] ULONG32 *pcStepInfo,    [in, size_is(cStepInfo)] ULONG32 yieldOffsets[],    [in, size_is(cStepInfo)] ULONG32 breakpointOffset[],    [in, size_is(cStepInfo)] mdToken breakpointMethod[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6356a-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="6356a-105">Parameters</span></span>  
  
|<span data-ttu-id="6356a-106">Параметр</span><span class="sxs-lookup"><span data-stu-id="6356a-106">Parameter</span></span>|<span data-ttu-id="6356a-107">Описание</span><span class="sxs-lookup"><span data-stu-id="6356a-107">Description</span></span>|  
|---------------|-----------------|  
|`cStepInfo`||  
|`pcStepInfo`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="6356a-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="6356a-108">Return Value</span></span>  
 <span data-ttu-id="6356a-109">Возвращает `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="6356a-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6356a-110">Требования</span><span class="sxs-lookup"><span data-stu-id="6356a-110">Requirements</span></span>  
 <span data-ttu-id="6356a-111">**Заголовок:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6356a-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6356a-112">См. также</span><span class="sxs-lookup"><span data-stu-id="6356a-112">See Also</span></span>  
 [<span data-ttu-id="6356a-113">Интерфейс ISymUnmanagedAsyncMethod</span><span class="sxs-lookup"><span data-stu-id="6356a-113">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)