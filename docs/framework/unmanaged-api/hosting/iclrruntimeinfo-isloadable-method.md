---
title: "Метод ICLRRuntimeInfo::IsLoadable"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.IsLoadable
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::IsLoadable
helpviewer_keywords:
- IsLoadable method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoadable method [.NET Framework hosting]
ms.assetid: 205ca53b-e78e-49b2-9a46-2a7823e96b8c
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ada33942af97f476de25c2ea3243818808e2dc9d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimeinfoisloadable-method"></a><span data-ttu-id="f52f9-102">Метод ICLRRuntimeInfo::IsLoadable</span><span class="sxs-lookup"><span data-stu-id="f52f9-102">ICLRRuntimeInfo::IsLoadable Method</span></span>
<span data-ttu-id="f52f9-103">Указывает, возможна ли загрузка среды выполнения, связанных с этим интерфейсом в текущий процесс, принимая во внимание других сред выполнения, которые уже могли быть загружены в процесс.</span><span class="sxs-lookup"><span data-stu-id="f52f9-103">Indicates whether the runtime associated with this interface can be loaded into the current process, taking into account other runtimes that might already be loaded into the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f52f9-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f52f9-104">Syntax</span></span>  
  
```  
HRESULT IsLoadable(  
        [out, retval] BOOL *pbLoadable);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f52f9-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="f52f9-105">Parameters</span></span>  
 `pbLoadable`  
 <span data-ttu-id="f52f9-106">[out] `true` Если эта среда выполнения может быть загружена в текущем процессе; в противном случае — `false`.</span><span class="sxs-lookup"><span data-stu-id="f52f9-106">[out] `true` if this runtime could be loaded into the current process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f52f9-107">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="f52f9-107">Return Value</span></span>  
 <span data-ttu-id="f52f9-108">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="f52f9-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f52f9-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f52f9-109">HRESULT</span></span>|<span data-ttu-id="f52f9-110">Описание</span><span class="sxs-lookup"><span data-stu-id="f52f9-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f52f9-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f52f9-111">S_OK</span></span>|<span data-ttu-id="f52f9-112">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="f52f9-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="f52f9-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="f52f9-113">E_POINTER</span></span>|<span data-ttu-id="f52f9-114">Параметр `pbLoadable` имеет значение NULL.</span><span class="sxs-lookup"><span data-stu-id="f52f9-114">`pbLoadable` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f52f9-115">Примечания</span><span class="sxs-lookup"><span data-stu-id="f52f9-115">Remarks</span></span>  
 <span data-ttu-id="f52f9-116">Если в процесс уже загружена другая среда выполнения, среда выполнения, связанных с этим интерфейсом можно загрузить для выполнения в процессе side-by-side `pbLoadable` возвращает `true`.</span><span class="sxs-lookup"><span data-stu-id="f52f9-116">If another runtime is already loaded into the process and the runtime associated with this interface can be loaded for in-process side-by-side execution, `pbLoadable` returns `true`.</span></span> <span data-ttu-id="f52f9-117">Если две среды выполнения не может выполнять side-by-side в процессе, `pbLoadable` возвращает `false`.</span><span class="sxs-lookup"><span data-stu-id="f52f9-117">If the two runtimes cannot run side-by-side in-process, `pbLoadable` returns `false`.</span></span> <span data-ttu-id="f52f9-118">Например среда CLR версии 4 можно запустить side-by-side, в том же процессе, в среде CLR версии 2.0 или среда CLR версии 1.1.</span><span class="sxs-lookup"><span data-stu-id="f52f9-118">For example, the common language runtime (CLR) version 4 can run side-by-side in the same process with CLR version 2.0 or CLR version 1.1.</span></span> <span data-ttu-id="f52f9-119">Тем не менее среда CLR версии 1.1 и среда CLR версии 2.0 не может выполняться side-by-side внутри процесса.</span><span class="sxs-lookup"><span data-stu-id="f52f9-119">However, CLR version 1.1 and CLR version 2.0 cannot run side-by-side in-process.</span></span>  
  
 <span data-ttu-id="f52f9-120">Если нет сред выполнения, загружаются в процесс, этот метод всегда возвращает `true`.</span><span class="sxs-lookup"><span data-stu-id="f52f9-120">If no runtimes are loaded into the process, this method always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f52f9-121">Требования</span><span class="sxs-lookup"><span data-stu-id="f52f9-121">Requirements</span></span>  
 <span data-ttu-id="f52f9-122">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f52f9-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f52f9-123">**Заголовок:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="f52f9-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f52f9-124">**Библиотека:** включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f52f9-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f52f9-125">**Версии платформы .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f52f9-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f52f9-126">См. также</span><span class="sxs-lookup"><span data-stu-id="f52f9-126">See Also</span></span>  
 [<span data-ttu-id="f52f9-127">ICLRRuntimeInfo-интерфейс</span><span class="sxs-lookup"><span data-stu-id="f52f9-127">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="f52f9-128">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="f52f9-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="f52f9-129">Размещение</span><span class="sxs-lookup"><span data-stu-id="f52f9-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)