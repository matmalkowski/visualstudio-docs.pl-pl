---
title: IRemoteDebugApplicationEvents::OnSetName | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IRemoteDebugApplicationEvents.OnSetName
apilocation: jscript.dll
helpviewer_keywords: IRemoteDebugApplicationEvents::OnSetName
ms.assetid: 524dcff3-fb48-4d8f-8989-73eb539454fb
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d794665e02bd1280fe2a404e56e96ab1290a413f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationeventsonsetname"></a>IRemoteDebugApplicationEvents::OnSetName
Obsługuje zdarzenie nazwę zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT OnSetName(  
   LPCOLESTR  pstrName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrName`  
 [in] Nowa nazwa.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda obsługuje zdarzenia nazwę zestawu.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IRemoteDebugApplicationEvents](../../winscript/reference/iremotedebugapplicationevents-interface.md)