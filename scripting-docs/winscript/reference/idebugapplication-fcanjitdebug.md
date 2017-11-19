---
title: IDebugApplication::FCanJitDebug | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplication.FCanJitDebug
apilocation: pdm.dll
helpviewer_keywords: IDebugApplication::FCanJitDebug
ms.assetid: d7ddac65-4864-411f-bf66-34a46c03f239
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ca6b990011252bde581168a272da1041dc24f41
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationfcanjitdebug"></a>IDebugApplication::FCanJitDebug
Określa, czy jest zarejestrowany debuger just in time (JIT).  
  
## <a name="syntax"></a>Składnia  
  
```  
BOOL FCanJitDebug();  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się pomyślnie i debugera JIT jest zarejestrowany, metoda zwraca `TRUE`. W przeciwnym razie zwraca `FALSE`.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda określa, czy jest zarejestrowany debugera JIT.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugApplication](../../winscript/reference/idebugapplication-interface.md)