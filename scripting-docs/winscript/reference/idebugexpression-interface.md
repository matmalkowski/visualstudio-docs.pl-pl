---
title: Interfejs IDebugExpression | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugExpression interface
ms.assetid: 36c00ffb-7160-4c30-a2c9-c9d70c8213cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 39e139e09362fc392d1110e26837c52fd4c642c4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794491"
---
# <a name="idebugexpression-interface"></a>Interfejs IDebugExpression
Reprezentuje asynchronicznie obliczane wyrażenie. Liczba aparatów skryptów zwykle implementuje ten interfejs. Debuger IDE zazwyczaj używa tego interfejsu do włączania okna wykonania natychmiastowej lub okno czujki.  
  
> [!NOTE]
>  `IDebugExpression` Interfejs jest dostępny tylko w ramce stosu.  
  
 Oprócz dziedziczone z metody `IUnknown`, `IDebugExpression` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugExpression::Start](../../winscript/reference/idebugexpression-start.md)|Rozpoczyna się obliczania wyrażenia.|  
|[IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)|Przerywa wyrażenie.|  
|[IDebugExpression::QueryIsComplete](../../winscript/reference/idebugexpression-queryiscomplete.md)|Określa, czy operacja została zakończona.|  
|[IDebugExpression::GetResultAsString](../../winscript/reference/idebugexpression-getresultasstring.md)|Zwraca wynik wyrażenia jako ciąg i wartość zwracana operacji.|  
|[IDebugExpression::GetResultAsDebugProperty](../../winscript/reference/idebugexpression-getresultasdebugproperty.md)|Zwraca wynik wyrażenia jako właściwość debugowania i wartość zwracana operacji.|