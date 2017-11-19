---
title: IDebugSyncOperation::GetTargetThread | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugSyncOperation.GetTargetThread
apilocation: jscript.dll
helpviewer_keywords: IDebugSyncOperation::GetTargetThread
ms.assetid: e6eeeb90-b5ed-4727-8434-fa3186c25013
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df3e65d53e20dd51d045f26855c4f5e058dff159
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugsyncoperationgettargetthread"></a>IDebugSyncOperation::GetTargetThread
Zwraca wątku aplikacji docelowej dla tej operacji synchronicznych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetTargetThread(  
   IDebugApplicationThread**  ppatTarget  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppatTarget`  
 [out] Wątek aplikacji docelowej dla tej operacji synchronicznych.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca wątku aplikacji docelowej dla tej operacji synchronicznych.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md)