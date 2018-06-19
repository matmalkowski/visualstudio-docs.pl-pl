---
title: IJsDebugDataTarget::WriteMemory — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.WriteMemory
apilocation:
- jscript9diag.dll
ms.assetid: 0d3c04c3-9ef8-4842-a145-3d29bca75062
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed562c1cbdd645da6cca87e45f272c25f8bc0d4b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794524"
---
# <a name="ijsdebugdatatargetwritememory-method"></a>IJsDebugDataTarget::WriteMemory — Metoda
Odczytuje pamięci procesu docelowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT WriteMemory(  
   UINT64 address,  
   const BYTE *pMemory,  
   DWORD size  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `address`  
 [in] Adres podstawowy, w którym można zapisać w pamięci procesu docelowego.  
  
 `pMemory`  
 [in] Dane do zapisania w przestrzeni adresowej określony proces.  
  
 `size`  
 [in] Liczba bajtów do zapisania do procesu.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="remarks"></a>Uwagi  
 Przed wystąpieniem transferu danych, system sprawdza, czy wszystkie dane w bazowym adresie i pamięci o określonym rozmiarze jest dostępny do zapisu, a jeśli nie jest dostępny, funkcja zgłasza błąd E_JsDEBUG_INVALID_MEMORY_ADDRESS.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [Ijsdebugdatatarget — interfejs](../../winscript/reference/ijsdebugdatatarget-interface.md)