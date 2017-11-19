---
title: IRemoteDebugApplicationThread::Resume | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IRemoteDebugApplicationThread.Resume
apilocation: pdm.dll
helpviewer_keywords: IRemoteDebugApplicationThread::Resume
ms.assetid: ac290861-515d-4f06-b452-3b96f54e538c
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 265c0a368fc7f0a5faf3ced3f335b3d7d49c1b24
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationthreadresume"></a>IRemoteDebugApplicationThread::Resume
Wznawia wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Resume(  
   DWORD*  pdwCount  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdwCount`  
 [out] Wstrzymaj liczbę elementów w wątku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Gdy ta metoda wznawia wątku, jego zmniejsza suspend-count.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IRemoteDebugApplicationThread](../../winscript/reference/iremotedebugapplicationthread-interface.md)