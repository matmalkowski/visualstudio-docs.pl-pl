---
title: IJsDebugDataTarget::ReadMemory — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.ReadMemory
apilocation:
- jscript9diag.dll
ms.assetid: 664e0f7d-2007-45f4-b993-36fe8b1944e5
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fc1b67b33e17761a675d6ced9e175b4206ede2e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794704"
---
# <a name="ijsdebugdatatargetreadmemory-method"></a>IJsDebugDataTarget::ReadMemory — Metoda
Odczytuje pamięci procesu docelowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ReadMemory(  
   UINT64 address,  
   JsDebugReadMemoryFlags flags,  
   BYTE *pBuffer,  
   DWORD size,  
   DWORD *pBytesRead  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `address`  
 [in] Adres podstawowy, z którego można odczytać pamięci procesu docelowego.  
  
 `flags`  
 [in] Flagi sterujące zachowaniem ReadMemory.  
  
 `pBuffer`  
 [out] Buforu, który odbiera zawartość z przestrzeni adresowej procesu docelowego. W przypadku awarii zawartość tego bufora jest nieokreślony.  
  
 `size`  
 [in] Liczba bajtów do odczytu w procesie.  
  
 `pBytesRead`  
 [out] Wskazuje liczbę bajtów odczytanych z procesu docelowego. Jeśli JsDebugAllowPartialRead nie zostanie zaznaczone, w przypadku powodzenia tę wartość zawsze będzie równy rozmiarowi wejściowych. Jeśli określono JsDebugAllowPartialRead, w przypadku powodzenia, ta wartość będzie większa niż zero.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="remarks"></a>Uwagi  
 Zwraca wartość S_OK na sukces i niepowodzenie kody są używane w przypadku błędu. Zwraca E_JsDEBUG_INVALID_MEMORY_ADDRESS, jeśli adres nie jest prawidłowy. Aby uzyskać więcej informacji zobacz JsDebugAllowPartialRead.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [Ijsdebugdatatarget — interfejs](../../winscript/reference/ijsdebugdatatarget-interface.md)