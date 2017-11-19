---
title: IDebugApplicationThread::SetStateString | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplicationThread.SetStateString
apilocation: pdm.dll
helpviewer_keywords: IDebugApplicationThread::SetStateString
ms.assetid: a59001d5-ea00-4fd0-bb20-0b592d9c795d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2eafe5477759dbad109e5ae6294b477d56f9ee14
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthreadsetstatestring"></a>IDebugApplicationThread::SetStateString
Ustawia opis stan wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetStateString(  
   LPCOLESTR  pstrState  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrState`  
 [in] Opis stanu wątku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda ustawia opis stan wątku.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md)