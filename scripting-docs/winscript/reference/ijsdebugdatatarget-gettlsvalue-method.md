---
title: "IJsDebugDataTarget::GetTlsValue — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugDataTarget.GetTlsValue
apilocation: jscript9diag.dll
ms.assetid: db575be9-7b24-45c5-9008-e4f2f76d6757
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4205adfb24a1a64d4e90f3fdcaf5a5ecbc4028de
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugdatatargetgettlsvalue-method"></a>IJsDebugDataTarget::GetTlsValue — Metoda
Pobiera wartość w miejscu magazynu lokalnego (TLS) wątku dla określonego indeksu TLS debugowany wątek.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetTlsValue(  
   DWORD threadId,  
   UINT32 tlsIndex,  
   UINT64 *pValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `threadId`  
 [in] Wątek uruchomiony w procesie docelowym do odczytu.  
  
 `tlsIndex`  
 [in] Indeks TLS alokowanej funkcja TlsAlloc wywołanego procesu docelowego.  
  
 `pValue`  
 [out] Wartość rozmiaru wskaźnika, która była przechowywana w gnieździe TLS wątku. Jeśli wątek docelowy jest 32-bitowy, górny 32-bitowej tej wartości będą miały wartość zero.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="remarks"></a>Uwagi  
 Każdy wątek procesu ma własną miejsce dla każdego indeksu TLS.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [Ijsdebugdatatarget — interfejs](../../winscript/reference/ijsdebugdatatarget-interface.md)