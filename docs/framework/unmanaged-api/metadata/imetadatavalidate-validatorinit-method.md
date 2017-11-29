---
title: "Метод IMetaDataValidate::ValidatorInit"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataValidate.ValidatorInit
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataValidate::ValidatorInit
helpviewer_keywords:
- IMetaDataValidate::ValidatorInit method [.NET Framework metadata]
- ValidatorInit method [.NET Framework metadata]
ms.assetid: 6bafd75a-e2d0-4aea-aed1-074374d5dff6
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e2a9b265b4fcc75406f5d5f1dbddb8bd74b5832d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="imetadatavalidatevalidatorinit-method"></a><span data-ttu-id="82dcd-102">Метод IMetaDataValidate::ValidatorInit</span><span class="sxs-lookup"><span data-stu-id="82dcd-102">IMetaDataValidate::ValidatorInit Method</span></span>
<span data-ttu-id="82dcd-103">Устанавливает флаг, который указывает тип модуля в текущей области метаданных, и регистрирует указанный метод обратного вызова для ошибок проверки.</span><span class="sxs-lookup"><span data-stu-id="82dcd-103">Sets a flag that specifies the type of the module in the current metadata scope, and registers the specified callback method for validation errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82dcd-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="82dcd-104">Syntax</span></span>  
  
```  
HRESULT ValidatorInit (  
   [in] DWORD       dwModuleType,  
   [in] IUnknown    *pUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="82dcd-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="82dcd-105">Parameters</span></span>  
 `dwModule`  
 <span data-ttu-id="82dcd-106">[in] Значение [CorValidatorModuleType](../../../../docs/framework/unmanaged-api/metadata/corvalidatormoduletype-enumeration.md) перечисления, которое указывает тип модуля в текущей области метаданных.</span><span class="sxs-lookup"><span data-stu-id="82dcd-106">[in] A value of the [CorValidatorModuleType](../../../../docs/framework/unmanaged-api/metadata/corvalidatormoduletype-enumeration.md) enumeration that specifies the type of the module in the current metadata scope.</span></span>  
  
 `pUnk`  
 <span data-ttu-id="82dcd-107">[in] Указатель на <<!--zzxref:IUnknown --> `IUnknown`> экземпляр, который служит в качестве функции обратного вызова для ошибок проверки.</span><span class="sxs-lookup"><span data-stu-id="82dcd-107">[in] A pointer to an <<!--zzxref:IUnknown --> `IUnknown`> instance that serves as a function callback for validation errors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82dcd-108">Требования</span><span class="sxs-lookup"><span data-stu-id="82dcd-108">Requirements</span></span>  
 <span data-ttu-id="82dcd-109">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82dcd-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82dcd-110">**Заголовок:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="82dcd-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="82dcd-111">**Библиотека:** используется как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="82dcd-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="82dcd-112">**Версии платформы .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82dcd-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82dcd-113">См. также</span><span class="sxs-lookup"><span data-stu-id="82dcd-113">See Also</span></span>  
 [<span data-ttu-id="82dcd-114">Интерфейс IMetaDataValidate</span><span class="sxs-lookup"><span data-stu-id="82dcd-114">IMetaDataValidate Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-interface.md)