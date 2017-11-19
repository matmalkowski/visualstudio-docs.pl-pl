---
title: IDebugApplication::StartDebugSession | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplication.StartDebugSession
apilocation: pdm.dll
helpviewer_keywords: IDebugApplication::StartDebugSession
ms.assetid: 737f8424-bbcf-473f-9cf1-6601b9aa250d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aea5caead4921206428c2f1f36b74d057c8cef36
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationstartdebugsession"></a>IDebugApplication::StartDebugSession
Uruchamia domyślny debuger zintegrowane środowisko programistyczne (IDE) i dołącza sesji debugowania do tej aplikacji, jeśli nie jest już dołączony.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT StartDebugSession();  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda służy do implementowania debugowanie just in time.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugApplication](../../winscript/reference/idebugapplication-interface.md)