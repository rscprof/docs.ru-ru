---
title: "Метод IMetaDataDispenser::OpenScope"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenser.OpenScope
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenser::OpenScope
helpviewer_keywords:
- IMetaDataDispenser::OpenScope method [.NET Framework metadata]
- OpenScope method, IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 65063ad5-e0d9-4c01-8f8b-9a5950109fa6
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 09c057f42bb849b89d78d2d32af6637640ad22ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatadispenseropenscope-method"></a><span data-ttu-id="382f9-102">Метод IMetaDataDispenser::OpenScope</span><span class="sxs-lookup"><span data-stu-id="382f9-102">IMetaDataDispenser::OpenScope Method</span></span>
<span data-ttu-id="382f9-103">Открывает существующий файл на диске и сопоставляет его метаданные в память.</span><span class="sxs-lookup"><span data-stu-id="382f9-103">Opens an existing, on-disk file and maps its metadata into memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="382f9-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="382f9-104">Syntax</span></span>  
  
```  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="382f9-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="382f9-105">Parameters</span></span>  
 `szScope`  
 <span data-ttu-id="382f9-106">[in] Имя файла для открытия.</span><span class="sxs-lookup"><span data-stu-id="382f9-106">[in] The name of the file to be opened.</span></span> <span data-ttu-id="382f9-107">Этот файл должен содержать метаданных CLR среды выполнения (CLR).</span><span class="sxs-lookup"><span data-stu-id="382f9-107">The file must contain common language runtime (CLR) metadata.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="382f9-108">[in] Значение [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) перечисления для задания режима (чтение, запись и так далее) для открытия.</span><span class="sxs-lookup"><span data-stu-id="382f9-108">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="382f9-109">[in] Идентификатор IID интерфейса новых метаданных должен быть возвращен; вызывающий объект будет использовать интерфейс для импорта (чтение) или выдачи метаданных (запись).</span><span class="sxs-lookup"><span data-stu-id="382f9-109">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="382f9-110">Значение `riid` необходимо указать один из интерфейсов «import» или «выдачи».</span><span class="sxs-lookup"><span data-stu-id="382f9-110">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="382f9-111">Допустимые значения: IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 или IID_IMetaDataImport2.</span><span class="sxs-lookup"><span data-stu-id="382f9-111">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="382f9-112">[out] Указатель на возвращенный интерфейс.</span><span class="sxs-lookup"><span data-stu-id="382f9-112">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="382f9-113">Примечания</span><span class="sxs-lookup"><span data-stu-id="382f9-113">Remarks</span></span>  
 <span data-ttu-id="382f9-114">Копия в памяти метаданных можно запрашивать с помощью методов одного из интерфейсов «импорт», или добавить в методы одного из интерфейсов «выдачи».</span><span class="sxs-lookup"><span data-stu-id="382f9-114">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="382f9-115">Если целевой файл не содержит метаданные среды CLR, `OpenScope` метод завершится с ошибкой.</span><span class="sxs-lookup"><span data-stu-id="382f9-115">If the target file does not contain CLR metadata, the `OpenScope` method will fail.</span></span>  
  
 <span data-ttu-id="382f9-116">В платформе .NET Framework версии 1.0 и 1.1, если область открывается с `dwOpenFlags` значение ofRead, он имеет право управления доступом.</span><span class="sxs-lookup"><span data-stu-id="382f9-116">In the .NET Framework version 1.0 and version 1.1, if a scope is opened with `dwOpenFlags` set to ofRead, it is eligible for sharing.</span></span> <span data-ttu-id="382f9-117">То есть если последующие вызовы `OpenScope` передайте имя файла, который ранее был открыт повторно существующую область и не создается новый набор структур данных.</span><span class="sxs-lookup"><span data-stu-id="382f9-117">That is, if subsequent calls to `OpenScope` pass in the name of a file that was previously opened, the existing scope is reused and a new set of data structures is not created.</span></span> <span data-ttu-id="382f9-118">Тем не менее могут возникнуть проблемы из-за этого для управления доступом.</span><span class="sxs-lookup"><span data-stu-id="382f9-118">However, problems can arise due to this sharing.</span></span>  
  
 <span data-ttu-id="382f9-119">В платформе .NET Framework версии 2.0 области открывается с `dwOpenFlags` задано значение ofRead не являются общими.</span><span class="sxs-lookup"><span data-stu-id="382f9-119">In the .NET Framework version 2.0, scopes opened with `dwOpenFlags` set to ofRead are no longer shared.</span></span> <span data-ttu-id="382f9-120">Значение ofReadOnly используется для разрешения области для совместного использования.</span><span class="sxs-lookup"><span data-stu-id="382f9-120">Use the ofReadOnly value to allow the scope to be shared.</span></span> <span data-ttu-id="382f9-121">При совместном использовании области запросы, использующие «чтение/запись» интерфейсы метаданных завершится ошибкой.</span><span class="sxs-lookup"><span data-stu-id="382f9-121">When a scope is shared, queries that use "read/write" metadata interfaces will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="382f9-122">Требования</span><span class="sxs-lookup"><span data-stu-id="382f9-122">Requirements</span></span>  
 <span data-ttu-id="382f9-123">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="382f9-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="382f9-124">**Заголовок:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="382f9-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="382f9-125">**Библиотека:** используется как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="382f9-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="382f9-126">**Версии платформы .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="382f9-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="382f9-127">См. также</span><span class="sxs-lookup"><span data-stu-id="382f9-127">See Also</span></span>  
 [<span data-ttu-id="382f9-128">IMetaDataDispenser-интерфейс</span><span class="sxs-lookup"><span data-stu-id="382f9-128">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [<span data-ttu-id="382f9-129">Интерфейс IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="382f9-129">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="382f9-130">Интерфейс IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="382f9-130">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [<span data-ttu-id="382f9-131">Imetadataassemblyimport-интерфейс</span><span class="sxs-lookup"><span data-stu-id="382f9-131">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="382f9-132">IMetaDataEmit-интерфейс</span><span class="sxs-lookup"><span data-stu-id="382f9-132">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="382f9-133">Интерфейс IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="382f9-133">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="382f9-134">IMetaDataImport-интерфейс</span><span class="sxs-lookup"><span data-stu-id="382f9-134">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="382f9-135">IMetaDataImport2-интерфейс</span><span class="sxs-lookup"><span data-stu-id="382f9-135">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)