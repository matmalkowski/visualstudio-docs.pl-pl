---
title: IRemoteDebugApplication::QueryAlive | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IRemoteDebugApplication.QueryAlive
apilocation: pdm.dll
helpviewer_keywords: IRemoteDebugApplication::QueryAlive
ms.assetid: 08e49d3b-6fb3-4438-960e-f05395ba9b17
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f938ad30562cd1131e8a50077106002d33cea2b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationqueryalive"></a>IRemoteDebugApplication::QueryAlive
Wskazuje, czy aplikacja jest elastyczny.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT QueryAlive();  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda wskazuje, czy aplikacja jest elastyczny. Implementacje tej metody należy zawsze zwracają `S_OK`.  
  
 Jeśli nieoczekiwane zakończenie procesu aplikacji modelu COM zwraca błąd z kierowanie serwera proxy dla wywołania do tej metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)