---
title: IDebugApplication::FIsAutoJitDebugEnabled | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugApplication.FIsAutoJitDebugEnabled
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::FIsAutoJitDebugEnabled
ms.assetid: 0551dd3b-e6eb-442a-8201-418f96fe62df
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 268a10cc829e2d217bb9a90b355405dd8f3b15b6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationfisautojitdebugenabled"></a>IDebugApplication::FIsAutoJitDebugEnabled
Określa, czy debuger just in time (JIT) jest zarejestrowany do hostów bez automatycznego debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
BOOL FIsAutoJitDebugEnabled();  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się pomyślnie i debugera JIT nie jest zarejestrowana dla hostów bez automatycznego debugowania, metoda zwraca `TRUE`. W przeciwnym razie zwraca `FALSE`.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda określa, czy debugera JIT jest zarejestrowana dla hostów bez automatycznego debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugApplication](../../winscript/reference/idebugapplication-interface.md)