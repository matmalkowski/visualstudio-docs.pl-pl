---
title: IRemoteDebugApplicationThread::SetNextStatement | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationThread.SetNextStatement
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplicationThread::SetNextStatement
ms.assetid: 356766da-f7b7-4e8d-b4f3-2ab8da0609b8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb23fa643f9a2333e17239a74d0da2f75e1ea791
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794899"
---
# <a name="iremotedebugapplicationthreadsetnextstatement"></a>IRemoteDebugApplicationThread::SetNextStatement
Wymusza wykonanie kontynuowanie możliwie najbliżej kontekstu podanego kodu w kontekście danego ramki.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetNextStatement(  
   IDebugStackFrame*   pStackFrame,  
   IDebugCodeContext*  pCodeContext  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pStackFrame`  
 [in] Obiekt ramki stosu. Ten argument może być NULL, co oznacza, że bieżącej ramki stosu, powinny być używane.  
  
 `pCodeContext`  
 [in] Kontekst kodu. Ten argument może mieć wartości NULL, co oznacza, że powinien być używany bieżący kontekst kodu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda wymusza wykonanie kontynuowanie możliwie najbliżej kontekst kodu określonego przez `pCodeContext`, w kontekście ramki określony przez `pStackFrame`. Może być jedną z tych argumentów `NULL`, reprezentujący bieżącą ramkę lub kontekstu.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IRemoteDebugApplicationThread](../../winscript/reference/iremotedebugapplicationthread-interface.md)