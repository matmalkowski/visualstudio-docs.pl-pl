---
title: IDebugApplication::StepOutComplete | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplication.StepOutComplete
apilocation: pdm.dll
helpviewer_keywords: IDebugApplication::StepOutComplete
ms.assetid: 9675b214-7be5-4cf7-a63f-7865f3c54371
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c344f0316bda6ed5ef895c1b88ae7b1a6465e73
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationstepoutcomplete"></a>IDebugApplication::StepOutComplete
Powiadamia menedżera debugowania procesu aparat języka, w trybie pojedynczy krok o zbliżającym się zwrócić do swojego obiektu wywołującego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT StepOutComplete();  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Aparaty języka wywołać tę metodę w trybie pojedynczy krok tuż przed zwracają do ich wywołującego. Menedżer debugowania procesu używa tej możliwości do wszystkich innych aparatów skryptów, które powinny one przerwanie przy okazji pierwszego powiadomienia. Ta technika jest tryby są implementowane krok jak wielu języków.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugApplication](../../winscript/reference/idebugapplication-interface.md)