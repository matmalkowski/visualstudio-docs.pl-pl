---
title: IDebugSyncOperation::InProgressAbort | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugSyncOperation.InProgressAbort
apilocation: jscript.dll
helpviewer_keywords: IDebugSyncOperation::InProgressAbort
ms.assetid: bfd0889c-b627-4843-b1c6-b6b918f42d61
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1df0b0ca1d775d4d99e1da5f88a207bd4f78f99b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugsyncoperationinprogressabort"></a>IDebugSyncOperation::InProgressAbort
Anuluje operację w toku w innym wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT InProgressAbort();  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_NOTIMPL`|Nie można anulować operację.|  
|`E_ABORT`|Nie można ukończyć operacji.|  
  
## <a name="remarks"></a>Uwagi  
 Menedżer debugowania procesu wywołuje tę metodę z wewnątrz wątek debugera, aby anulować operację, która jest w toku w innym wątku.  
  
 Jeśli `InProgressAbort` metody nie można ukończyć operacji, zwraca `E_ABORT` tak szybko, jak to możliwe. Ta metoda może zwracać `E_NOTIMPL` Jeśli nie można anulować operację.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md)