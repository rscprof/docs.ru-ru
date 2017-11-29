---
title: "Метод ICorDebugController::Stop"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.Stop
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::Stop
helpviewer_keywords:
- Stop method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Stop method [.NET Framework debugging]
ms.assetid: c34e79be-a7fb-479e-8dec-d126a4c330e5
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4b92d07f8d162123d20c6861d204d73789060906
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcontrollerstop-method"></a><span data-ttu-id="da9ec-102">Метод ICorDebugController::Stop</span><span class="sxs-lookup"><span data-stu-id="da9ec-102">ICorDebugController::Stop Method</span></span>
<span data-ttu-id="da9ec-103">Выполняет совместную остановку всех потоков, выполняющих управляемый код в процессе.</span><span class="sxs-lookup"><span data-stu-id="da9ec-103">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da9ec-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="da9ec-104">Syntax</span></span>  
  
```  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="da9ec-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="da9ec-105">Parameters</span></span>  
 `dwTimeoutIgnored`  
 <span data-ttu-id="da9ec-106">Не используется.</span><span class="sxs-lookup"><span data-stu-id="da9ec-106">Not used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da9ec-107">Примечания</span><span class="sxs-lookup"><span data-stu-id="da9ec-107">Remarks</span></span>  
 <span data-ttu-id="da9ec-108">`Stop`выполняет согласованную остановку всех потоков, выполняющих управляемый код в процессе.</span><span class="sxs-lookup"><span data-stu-id="da9ec-108">`Stop` performs a cooperative stop on all threads running managed code in the process.</span></span> <span data-ttu-id="da9ec-109">Во время сеанса отладки только управляемого, неуправляемые потоки может продолжить свое выполнение (но будет блокироваться при попытке вызова управляемого кода).</span><span class="sxs-lookup"><span data-stu-id="da9ec-109">During a managed-only debugging session, unmanaged threads may continue to run (but will be blocked when trying to call managed code).</span></span> <span data-ttu-id="da9ec-110">Во время сеанса отладки взаимодействия также можно остановить неуправляемые потоки.</span><span class="sxs-lookup"><span data-stu-id="da9ec-110">During an interop debugging session, unmanaged threads will also be stopped.</span></span> <span data-ttu-id="da9ec-111">`dwTimeoutIgnored` В настоящее время значение игнорируется и обрабатывается как INFINITE (-1).</span><span class="sxs-lookup"><span data-stu-id="da9ec-111">The `dwTimeoutIgnored` value is currently ignored and treated as INFINITE (-1).</span></span> <span data-ttu-id="da9ec-112">Если согласованная остановка завершилась сбоем из-за взаимоблокировки, все потоки приостанавливаются и возвращается значение E_TIMEOUT.</span><span class="sxs-lookup"><span data-stu-id="da9ec-112">If the cooperative stop fails due to a deadlock, all threads are suspended and E_TIMEOUT is returned.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da9ec-113">`Stop`является единственным методом синхронизации в API отладки.</span><span class="sxs-lookup"><span data-stu-id="da9ec-113">`Stop` is the only synchronous method in the debugging API.</span></span> <span data-ttu-id="da9ec-114">Если `Stop` возвращает значение S_OK, процесс останавливается.</span><span class="sxs-lookup"><span data-stu-id="da9ec-114">When `Stop` returns S_OK, the process is stopped.</span></span> <span data-ttu-id="da9ec-115">Обратный вызов не предоставляется для уведомления прослушивателей об остановке.</span><span class="sxs-lookup"><span data-stu-id="da9ec-115">No callback is given to notify listeners of the stop.</span></span> <span data-ttu-id="da9ec-116">Отладчик должен вызвать [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) позволяет возобновить процесс.</span><span class="sxs-lookup"><span data-stu-id="da9ec-116">The debugger must call [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) to allow the process to resume.</span></span>  
  
 <span data-ttu-id="da9ec-117">Отладчик поддерживает счетчик stop.</span><span class="sxs-lookup"><span data-stu-id="da9ec-117">The debugger maintains a stop counter.</span></span> <span data-ttu-id="da9ec-118">Когда значение счетчика становится равным нулю, возобновляется контроллера.</span><span class="sxs-lookup"><span data-stu-id="da9ec-118">When the counter goes to zero, the controller is resumed.</span></span> <span data-ttu-id="da9ec-119">Каждый вызов `Stop` или каждого отправленного обратного вызова увеличивает на единицу счетчик.</span><span class="sxs-lookup"><span data-stu-id="da9ec-119">Each call to `Stop` or each dispatched callback increments the counter.</span></span> <span data-ttu-id="da9ec-120">Каждый вызов `ICorDebugController::Continue` уменьшает значение счетчика.</span><span class="sxs-lookup"><span data-stu-id="da9ec-120">Each call to `ICorDebugController::Continue` decrements the counter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da9ec-121">Требования</span><span class="sxs-lookup"><span data-stu-id="da9ec-121">Requirements</span></span>  
 <span data-ttu-id="da9ec-122">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da9ec-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da9ec-123">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="da9ec-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="da9ec-124">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da9ec-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da9ec-125">**Версии платформы .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da9ec-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da9ec-126">См. также</span><span class="sxs-lookup"><span data-stu-id="da9ec-126">See Also</span></span>  
 