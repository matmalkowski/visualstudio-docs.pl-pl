---
title: IMachineDebugManagerCookie::EnumApplications | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IMachineDebugManagerCookie.EnumApplications
apilocation: scrobj.dll
helpviewer_keywords: IMachineDebugManagerCookie::EnumApplications
ms.assetid: 03f863cf-fa7f-4ec4-b1a1-1ae0ad296c39
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 927457fca1972148798b543dceefa19e107f45d6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="imachinedebugmanagercookieenumapplications"></a>IMachineDebugManagerCookie::EnumApplications
Zwraca moduł wyliczający bieżącą listę uruchomionych aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumApplications(  
   IEnumRemoteDebugApplications**  ppeda  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppeda`  
 [out] Moduł wyliczający zawierający bieżącą listę uruchomionych aplikacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca moduł wyliczający bieżącą listę uruchomionych aplikacji. Debuger IDE używa tej metody, aby wyświetlić i dołączania aplikacji na potrzeby debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IMachineDebugManagerCookie](../../winscript/reference/imachinedebugmanagercookie-interface.md)