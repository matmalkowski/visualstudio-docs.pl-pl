---
title: IDebugExpression::QueryIsComplete | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugExpression.QueryIsComplete
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::QueryIsComplete
ms.assetid: 510d62e5-a316-46fb-b23f-d3ba902b295c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c1d72b2a2d41b748954f2e4b2b4aa9f0011ca670
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugexpressionqueryiscomplete"></a>IDebugExpression::QueryIsComplete
Określa, czy operacja została zakończona.  
  
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
|`S_OK`|Metoda zakończyło się pomyślnie, a operacja została zakończona.|  
|`S_FALSE`|Operacja jest nadal oczekujące.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda określa, czy operacja została zakończona.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugExpression](../../winscript/reference/idebugexpression-interface.md)