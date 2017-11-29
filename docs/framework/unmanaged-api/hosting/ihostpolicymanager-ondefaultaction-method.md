---
title: "Метод IHostPolicyManager::OnDefaultAction"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostPolicyManager.OnDefaultAction
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostPolicyManager::OnDefaultAction
helpviewer_keywords:
- OnDefaultAction method [.NET Framework hosting]
- IHostPolicyManager::OnDefaultAction method [.NET Framework hosting]
ms.assetid: 071e73bd-4795-470f-9373-cfaef553b7f2
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ca5eb767c08733980c9156d04526594c62349624
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="ihostpolicymanagerondefaultaction-method"></a><span data-ttu-id="0b572-102">Метод IHostPolicyManager::OnDefaultAction</span><span class="sxs-lookup"><span data-stu-id="0b572-102">IHostPolicyManager::OnDefaultAction Method</span></span>
<span data-ttu-id="0b572-103">Уведомляет узел, который общеязыковой среды выполнения (CLR) должен предпринять действия по умолчанию, который был задан с помощью вызова [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) метода в ответ на прерывание потока или <xref:System.AppDomain> выгрузки.</span><span class="sxs-lookup"><span data-stu-id="0b572-103">Notifies the host that the common language runtime (CLR) is about to take the default action that was set by a call to the [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) method in response to a thread abort or <xref:System.AppDomain> unload.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b572-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0b572-104">Syntax</span></span>  
  
```  
HRESULT OnDefaultAction (  
    [in] EClrOperation  operation,   
    [in] EPolicyAction  action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0b572-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="0b572-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="0b572-106">[in] Один из [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) значений, указывающее тип события, к которому отвечает среды CLR.</span><span class="sxs-lookup"><span data-stu-id="0b572-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of event to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="0b572-107">[in] Один из [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) значений, указывающее действие, требующее среды CLR в ответ на событие.</span><span class="sxs-lookup"><span data-stu-id="0b572-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action that the CLR is taking in response to the event.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0b572-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="0b572-108">Return Value</span></span>  
  
|<span data-ttu-id="0b572-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0b572-109">HRESULT</span></span>|<span data-ttu-id="0b572-110">Описание</span><span class="sxs-lookup"><span data-stu-id="0b572-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0b572-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="0b572-111">S_OK</span></span>|<span data-ttu-id="0b572-112">`OnDefaultAction`успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="0b572-112">`OnDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="0b572-113">ЗНАЧЕНИЕ HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0b572-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0b572-114">Среда CLR не загружена в процесс или находится в состоянии, в котором не может выполнять управляемый код или обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="0b572-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="0b572-115">успешно</span><span class="sxs-lookup"><span data-stu-id="0b572-115">successfully</span></span>|  
|<span data-ttu-id="0b572-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0b572-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0b572-117">Истекло время ожидания вызова.</span><span class="sxs-lookup"><span data-stu-id="0b572-117">The call timed out.</span></span>|  
|<span data-ttu-id="0b572-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0b572-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0b572-119">Вызывающий объект не является владельцем блокировки.</span><span class="sxs-lookup"><span data-stu-id="0b572-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0b572-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0b572-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0b572-121">Событие было отменено заблокированный поток или ожидал волокон.</span><span class="sxs-lookup"><span data-stu-id="0b572-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0b572-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0b572-122">E_FAIL</span></span>|<span data-ttu-id="0b572-123">Неизвестная Неустранимая ошибка.</span><span class="sxs-lookup"><span data-stu-id="0b572-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0b572-124">Если метод вернет значение E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="0b572-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0b572-125">Последующие вызовы размещение методы возвращают значение HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0b572-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0b572-126">Требования</span><span class="sxs-lookup"><span data-stu-id="0b572-126">Requirements</span></span>  
 <span data-ttu-id="0b572-127">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b572-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b572-128">**Заголовок:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0b572-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0b572-129">**Библиотека:** включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0b572-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0b572-130">**Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b572-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b572-131">См. также</span><span class="sxs-lookup"><span data-stu-id="0b572-131">See Also</span></span>  
 [<span data-ttu-id="0b572-132">EClrOperation-перечисление</span><span class="sxs-lookup"><span data-stu-id="0b572-132">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="0b572-133">EPolicyAction-перечисление</span><span class="sxs-lookup"><span data-stu-id="0b572-133">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="0b572-134">Интерфейс ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="0b572-134">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="0b572-135">IHostPolicyManager-интерфейс</span><span class="sxs-lookup"><span data-stu-id="0b572-135">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)