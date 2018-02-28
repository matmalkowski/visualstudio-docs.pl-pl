---
title: IRemoteDebugApplication::ConnectDebugger | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IRemoteDebugApplication.ConnectDebugger
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::ConnectDebugger
ms.assetid: ded94101-7efe-466f-aa70-b3e30a38c4d8
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 538b7a3f76e6026297839e4a7a37e6c21a72d7d0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationconnectdebugger"></a>IRemoteDebugApplication::ConnectDebugger
Nawiązuje połączenie debugera do tej aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ConnectDebugger(  
   IApplicationDebugger*  pad  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pad`  
 [in] Debuger do dołączenia do tej aplikacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_FAIL`|Debuger jest już połączony z tej aplikacji.|  
  
## <a name="remarks"></a>Uwagi  
 Aplikacja może mieć tylko jeden debugera połączony w czasie. Ta metoda zakończy się niepowodzeniem, jeśli debuger jest już połączony.  
  
## <a name="see-also"></a>Zobacz też  
 [IRemoteDebugApplication::GetDebugger](../../winscript/reference/iremotedebugapplication-getdebugger.md)   
 [Interfejs IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)