---
title: IDebugStackFrame::GetDescriptionString | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugStackFrame.GetDescriptionString
apilocation: jscript.dll
helpviewer_keywords: IDebugStackFrame::GetDescriptionString
ms.assetid: a2ddc069-c440-4dee-98dc-ab7c78773b94
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cdc77aa2ef2f9d7c95b0b82d5195a6a73524f055
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugstackframegetdescriptionstring"></a>IDebugStackFrame::GetDescriptionString
Zwraca opis krótka lub długo tekstową ramki stosu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetDescriptionString(  
   BOOL   fLong,  
   BSTR*  pbstrDescription  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fLong`  
 [in] Flaga, gdzie `TRUE` zwraca długi opis i `FALSE` zwraca krótki opis.  
  
 `pbstrDescription`  
 [out] Opis ramki stosu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Zwykle Jeśli `fLong` jest `FALSE`, ta metoda zapewnia tylko nazwę funkcji ramki stosu. Gdy `fLong` jest `TRUE`, ta metoda może również udostępniać parametrów funkcji i inne istotne informacje.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugStackFrame](../../winscript/reference/idebugstackframe-interface.md)