---
title: IActiveScriptError::GetExceptionInfo | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptError.GetExceptionInfo
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptError_GetExceptionInfo
ms.assetid: 528416cc-8468-4ad7-a6c2-fa1daf6ecf33
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8719d1a169c89d7b6cf712a125b6962b9c7a8839
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescripterrorgetexceptioninfo"></a>IActiveScriptError::GetExceptionInfo
Pobiera informacje o błędzie, który wystąpił w trakcie skryptu aparatu skryptów.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetExceptionInfo(  
    EXCEPINFO *pexcepinfo  // structure for exception information  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pexcepinfo`  
 [out] Adres `EXCEPINFO` struktury, która otrzymuje informacje o błędzie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` w przypadku powodzenia lub `E_FAIL` Jeśli wystąpił błąd.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)