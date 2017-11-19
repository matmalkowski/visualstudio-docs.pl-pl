---
title: IDebugStackFrame::GetLanguageString | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugStackFrame.GetLanguageString
apilocation: jscript.dll
helpviewer_keywords: IDebugStackFrame::GetLanguageString
ms.assetid: 561d6306-f214-422f-abc9-b502cbfbe208
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 724ca98278eb8885d29aad1799f822ac57251597
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugstackframegetlanguagestring"></a>IDebugStackFrame::GetLanguageString
Zwraca krótka lub długo tekstowy opis języka.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetLanguageString(  
   BOOL   fLong,  
   BSTR*  pbstrLanguage  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fLong`  
 [in] Flaga, gdzie `TRUE` zwraca długi opis i `FALSE` zwraca krótki opis.  
  
 `pbstrLanguage`  
 [out] Opis języka.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Zwykle Jeśli `fLong` jest `FALSE`, ta metoda zapewnia tylko nazwę języka ramki stosu. Gdy `fLong` jest `TRUE`, ta metoda może podać opis pełnej wersji produktu.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugStackFrame](../../winscript/reference/idebugstackframe-interface.md)