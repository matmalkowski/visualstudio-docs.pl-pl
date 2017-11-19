---
title: IActiveScriptError::GetSourcePosition | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptError.GetSourcePosition
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptError_GetSourcePosition
ms.assetid: ae9b26b1-82a7-4645-9686-3261d8248664
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d63310a8ba5cfda39d48a482eaf7c345cd492adc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescripterrorgetsourceposition"></a>IActiveScriptError::GetSourcePosition
Pobiera lokalizacji w kodzie źródłowym, w którym błąd wystąpił w trakcie skryptu aparatu skryptów.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetSourcePosition(  
    DWORD *pdwSourceContext,  // context cookie  
    ULONG *pulLineNumber,     // line number of error  
    LONG *pichCharPosition    // character position of error  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdwSourceContext`  
 [out] Adres zmiennej, która odbiera pliku cookie, który identyfikuje kontekst. Interpretacja tego parametru jest zależna od aplikacji hosta.  
  
 `pulLineNumber`  
 [out] Adres zmiennej, która odbiera numer wiersza pliku źródłowego, w którym wystąpił błąd.  
  
 `pichCharPosition`  
 [out] Adres zmiennej, która odbiera pozycja znaku w wierszu, w którym wystąpił błąd.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` w przypadku powodzenia lub `E_FAIL` Jeśli lokalizacja nie została pobrana.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)