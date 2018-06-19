---
title: IJsDebug::OpenVirtualProcess — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebug.OpenVirtualProcess
apilocation:
- jscript9diag.dll
ms.assetid: 5612bf1b-a4e3-4eaf-ac5e-c2e1f147c395
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f5acb137337e46a6e84f7d68c9330a3ca847f2e5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794362"
---
# <a name="ijsdebugopenvirtualprocess-method"></a>IJsDebug::OpenVirtualProcess — Metoda
Metoda fabryki użyta do utworzenia nowego obiektu procesu wirtualnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
 HRESULT OpenVirtualProcess(  
   DWORD processId,  
   UINT64 runtimeJsBaseAddress,  
   IJsDebugDataTarget *pDataTarget,  
   IJsDebugProcess **ppProcess  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `processId`  
 [in] Identyfikator procesu, który można dołączyć debugera do.  
  
 `runtimeJsBaseAddress`  
 [in] Adres podstawowy, w którym środowiska wykonawczego języka JavaScript został załadowany do procesu docelowego.  
  
 `pDataTarget`  
 [in] Debuger interfejs dostarczony do zapytanie o stan procesu.  
  
 `ppProcess`  
 [out] Nowy obiekt proces debugowania  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="remarks"></a>Uwagi  
 Zwraca E_JsDEBUG_MISMATCHED_RUNTIME, jeśli Jscript9diag i Jscript9 nie są zgodne.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [Ijsdebug — interfejs](../../winscript/reference/ijsdebug-interface.md)