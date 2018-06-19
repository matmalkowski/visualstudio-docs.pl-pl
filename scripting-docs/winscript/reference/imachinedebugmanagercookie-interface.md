---
title: Interfejs IMachineDebugManagerCookie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IMachineDebugManagerCookie interface
ms.assetid: 04770935-3ccf-41e9-b0c1-c78376ab1e3c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a03b959a7eb09f3b85530bbba07d1d2dc7f8948a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24795040"
---
# <a name="imachinedebugmanagercookie-interface"></a>Interfejs IMachineDebugManagerCookie
Podobnie jak `IMachineDebugManager` interfejsu `IMachineDebugManagerCookie` interfejs obsługuje pliki cookie debugowania.  
  
 Ten interfejs (wraz z `IDebugCookie` interfejsu) Zezwalaj na uruchamianie skryptów w procesu debugera skryptu bez konieczności zachować informacje o tych skryptów debugera.  
  
 Wywołuje debugera skryptów `IDebugCookie::SetDebugCookie` metody na proces debugowania Manager (PDM). Następnie PDM wysyła ten plik cookie oraz wszelkie żądania, aby dodać lub usunąć aplikację skryptu do lub z maszyny debugowania Manager (MDM), za pomocą metody `IMachineDebugManagerCookie` interfejsu. Zarządzania urządzeniami Przenośnymi następnie powiadamia co debuger zmiany, z wyjątkiem ten, który ma tego pliku cookie.  
  
 Oprócz dziedziczone z metody `IUnknown`, `IMachineDebugManagerCookie` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)|Dodaje aplikację do uruchamiania liście aplikacji.|  
|[IMachineDebugManagerCookie::EnumApplications](../../winscript/reference/imachinedebugmanagercookie-enumapplications.md)|Zwraca moduł wyliczający bieżącą listę uruchomionych aplikacji.|  
|[IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)|Usuwa z uruchomionym aplikacji listy aplikacji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IMachineDebugManager](../../winscript/reference/imachinedebugmanager-interface.md)   
 [Interfejs IDebugCookie](../../winscript/reference/idebugcookie-interface.md)