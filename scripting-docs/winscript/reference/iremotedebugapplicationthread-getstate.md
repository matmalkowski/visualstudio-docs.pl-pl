---
title: IRemoteDebugApplicationThread::GetState | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IRemoteDebugApplicationThread.GetState
apilocation: pdm.dll
helpviewer_keywords: IRemoteDebugApplicationThread::GetState
ms.assetid: 44503a78-efa9-4fbf-98be-a5dcfa329c5a
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce34fa73f97b92d08193c697e991c9e922ac17ee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationthreadgetstate"></a>IRemoteDebugApplicationThread::GetState
Pobiera stan tego wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetState(  
   DWORD*  pState  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pState`  
 [out] Kombinacja następujące flagi stanu wątku:  
  
|Stała|Wartość|Opis|  
|--------------|-----------|-----------------|  
|THREAD_STATE_RUNNING|0x00000001|Wątek jest uruchomiony.|  
|THREAD_STATE_SUSPENDED|0x00000002|Wątek jest zawieszony.|  
|THREAD_BLOCKED|0x00000004|Wątek jest zablokowany.|  
|THREAD_OUT_OF_CONTEXT|0x00000008|Wątek znajduje się poza zawartości.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda pobiera stan tego wątku.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IRemoteDebugApplicationThread](../../winscript/reference/iremotedebugapplicationthread-interface.md)