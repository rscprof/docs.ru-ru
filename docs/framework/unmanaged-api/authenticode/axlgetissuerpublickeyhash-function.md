---
title: Функция _AxlGetIssuerPublicKeyHash
ms.date: 03/30/2017
api_name:
- _AxlGetIssuerPublicKeyHash
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: fb626b41-b888-4625-84c3-2c02b5e3866f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 408b71bf38427d12418e05f8b509fe841bc95ef1
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "43880169"
---
# <a name="axlgetissuerpublickeyhash-function"></a>Функция _AxlGetIssuerPublicKeyHash
Получает хэш SHA-1 открытого ключа, связанного с закрытым ключом, который используется для подписания указанного сертификата.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pChainContext`  
 [в] Большой двоичный объект открытого ключа CSP. См. в разделе [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) структуры.  
  
 `ppwszPublicKeyHash`  
 [из] Указатель на WCHAR * для получения шестнадцатеричного кодированного маркера открытого ключа.  
  
## <a name="return-value"></a>Возвращаемое значение  
 `S_OK`, если функция выполняется успешно. В противном случае — `S_FALSE`.  
  
## <a name="see-also"></a>См. также  
 [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
