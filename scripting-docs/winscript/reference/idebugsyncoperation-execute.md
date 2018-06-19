---
title: IDebugSyncOperation::Execute | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugSyncOperation.Execute
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugSyncOperation::Execute
ms.assetid: a45b8c7d-c51a-4098-877f-fbec2f1f6947
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 69e07c646bfa176f5e2dc07539f301a8ef5c5273
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794239"
---
# <a name="idebugsyncoperationexecute"></a>IDebugSyncOperation::Execute
Synchronicznie wykonuje operację i zwraca.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Execute(  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppunkResult`  
 [out] Parametr obiektu zwrócony przez operację.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_ABORT`|Operacja została przerwana przez wywołanie metody `IDebugSyncOperation::InProgressAbort` metody.|  
  
## <a name="remarks"></a>Uwagi  
 Menedżer debugowania procesu w wywołaniach wątek docelowy `Execute` metody synchronicznie.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md)