---
title: IActiveScriptAuthor::IsCommitChar | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthor.IsCommitChar
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthor::IsCommitChar
ms.assetid: 7857c6f9-61e6-41e5-8e01-f56588c10421
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67dcdd7107372ee2766d59374a1d5aa9eb98576d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthoriscommitchar"></a>IActiveScriptAuthor::IsCommitChar
Zwraca wartość wskazującą, czy znak danego zdarzenia powinny wywoływać zatwierdzania uzupełniania instrukcji przez aplikację.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT IsCommitChar(  
   OLECHAR    ch,  
   BOOL       *pfcommit  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ch`  
 [in] Znak do testowania.  
  
 `pfcommit`  
 [out] `True` Jeśli znak jest zatwierdzenia znaku; w przeciwnym razie `False`.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)