---
title: "IJsDebugProcess::CreateBreakPoint — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugProcess.CreateBreakPoint
apilocation: jscript9diag.dll
ms.assetid: a2cb4233-2846-4d11-aa13-21de43abda9f
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 10d734f32d092d341dbb1b02a5cc7a0c127223a4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugprocesscreatebreakpoint-method"></a>IJsDebugProcess::CreateBreakPoint — Metoda
Ustawia punkt przerwania w pozycji określonego dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CreateBreakPoint(  
   UINT64 documentId,  
   DWORD characterOffset,  
   DWORD characterCount,  
   BOOL isEnabled,  
   IJsDebugBreakPoint **ppDebugBreakPoint  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `documentId`  
 [in] Wskaźnik do IDebugDocumentText.  
  
 `characterOffset`  
 [in] Znak przesunięcie od początku pliku.  
  
 `characterCount`  
 [in] Długość tekstu dokument, w którym można wstawić punktu przerwania.  
  
 `isEnabled`  
 [in] Określa, czy punkt przerwania jest włączone.  
  
 `ppDebugBreakPoint`  
 [out] Obiekt reprezentujący punkt przerwania, który został utworzony.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [Ijsdebugprocess — interfejs](../../winscript/reference/ijsdebugprocess-interface.md)