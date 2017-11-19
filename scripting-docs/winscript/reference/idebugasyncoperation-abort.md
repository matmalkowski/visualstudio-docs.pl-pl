---
title: IDebugAsyncOperation::Abort | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugAsyncOperation.Abort
apilocation: pdm.dll
helpviewer_keywords: IDebugAsyncOperation::Abort
ms.assetid: 232541c6-81b8-4eb7-96a7-a8e5fe087b31
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 274f09ae2a8851b897a825c32f18091c2f4250d0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugasyncoperationabort"></a>IDebugAsyncOperation::Abort
Anuluje operację.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Abort();  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|S_OK|Wykonanie metody powiodło się.|  
|E_NOTIMPL|Nie można anulować operacji.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest zwykle wywołane wewnątrz wątek debugera, aby anulować operację, która nie odpowiada. Ta metoda powoduje `InProgressAbort` metoda `IDebugSyncOperation` obiekt do wywołania.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)   
 [IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)