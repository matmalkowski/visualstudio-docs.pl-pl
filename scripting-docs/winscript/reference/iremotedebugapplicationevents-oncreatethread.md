---
title: IRemoteDebugApplicationEvents::OnCreateThread | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEvents.OnCreateThread
apilocation:
- jscript.dll
helpviewer_keywords:
- IRemoteDebugApplicationEvents::OnCreateThread
ms.assetid: 0b7c5181-eda6-4303-b4ae-d45962e8a3d3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3eb78f96d2621eac3794ba5c7c017590a775bd8e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794659"
---
# <a name="iremotedebugapplicationeventsoncreatethread"></a>IRemoteDebugApplicationEvents::OnCreateThread
Obsługuje tworzenie zdarzenia wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT OnCreateThread(  
   IRemoteDebugApplicationThread*  prdat  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `prdat`  
 [in] Nowo utworzony wątku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda obsługuje tworzenie zdarzenia wątku.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IRemoteDebugApplicationEvents](../../winscript/reference/iremotedebugapplicationevents-interface.md)