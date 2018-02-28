---
title: IDebugAsyncOperation::QueryIsComplete | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugAsyncOperation.QueryIsComplete
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::QueryIsComplete
ms.assetid: fcf6e229-4d40-46d9-ab81-d3561bc8e084
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e985697e425ec4966f2260792a9698fa50b4c98d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugasyncoperationqueryiscomplete"></a>IDebugAsyncOperation::QueryIsComplete
Określa, czy operacja debugowania została ukończona.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT QueryIsComplete();  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Operacja została zakończona.|  
|`S_FALSE`|Operacja nie jest ukończone.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda określa, czy operacja debugowania została ukończona.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)