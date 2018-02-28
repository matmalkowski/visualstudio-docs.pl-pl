---
title: IDebugApplicationThread110::GetActiveThreadRequestCount | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110::GetActiveThreadRequestCount
ms.assetid: 025d2072-1d7f-4448-8aa3-38a014313570
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb4d19bb77a4380c3c0a04f7e7808b82ca3f6ae4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthread110getactivethreadrequestcount"></a>IDebugApplicationThread110::GetActiveThreadRequestCount
Zwraca liczbę żądań wątku z wątku PDM przełączanie mechanizmy, które są obecnie przetwarzane. Ta liczba jest zwykle 0 lub 1. Jednak liczba może być wyższy Jeśli jedno wywołanie wątku uruchamia przetwarzanie, ale wyzwala synchroniczne wywołanie z wątku, lub w przeciwnym razie wstrzymuje wątku i zezwala na połączenia przychodzące do przetworzenia ponownie (na przykład, wyzwalając [ Interfejs IRemoteDebugApplicationEvents](../../winscript/reference/iremotedebugapplicationevents-interface.md) zdarzeń, które wydaje na wątek debugera).  
  
> [!IMPORTANT]
>  [Interfejs IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md) jest implementowany przez PDM v11.0 i większa. Znajduje się w zestawie activdbg100.h.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetActiveThreadRequestCount([out, annotation("_Out_")] UINT * puiThreadRequests);  
```  
  
#### <a name="parameters"></a>Parametry  
 `puiThreadRequests`  
 [out] Liczba żądań wątku.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugApplicationThread110](../../winscript/reference/idebugapplicationthread110-interface.md)