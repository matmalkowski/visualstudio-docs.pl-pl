---
title: IRemoteDebugApplication::CauseBreak | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IRemoteDebugApplication.CauseBreak
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::CauseBreak
ms.assetid: 6a2c27bb-dca0-475c-9918-bdbb70a50d26
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c04ea5303489a8c774adfaf65194237685a88a9c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationcausebreak"></a>IRemoteDebugApplication::CauseBreak
Powoduje przerwanie w debugerze przy najbliższej okazji aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CauseBreak();  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie tej metody nie powoduje natychmiastowe aplikacji. Jeśli aplikacja nie wykonuje obecnie kod skryptu, długo może upłynąć, zanim faktycznie dzieli aplikację.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)