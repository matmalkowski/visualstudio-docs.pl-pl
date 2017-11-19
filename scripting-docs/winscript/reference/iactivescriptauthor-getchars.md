---
title: IActiveScriptAuthor::GetChars | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthor.GetChars
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthor::GetChars
ms.assetid: a73ba263-12f7-4d5f-b4c8-9ad7e2d5d3cb
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: abc9c819c2dd4a75d6223af86b4fe89baebc186b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorgetchars"></a>IActiveScriptAuthor::GetChars
Zwraca zestaw znaków wykonania dla kontekstu żądanego ukończenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetChars(  
   DWORD            fRequestedList,  
   BSTR             *pbstrChars  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fRequestedList`  
 [in] Kontekst wykonania żądanej.  
  
|Stała|Wartość|Opis|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|0X0001|Żądania wyliczenia po lewej stronie.|  
|SCRIPT_CMPL_MEMBER_TRIGGER|0X0002|Żądania w kontekście zakończenia elementu członkowskiego.|  
|SCRIPT_CMPL_PARAM_TRIGGER|0x0003|Żąda listy parametrów.|  
|SCRIPT_CMPL_COMMIT|0X0004|Zakończenie żądania listy parametrów.|  
  
 `pbstrChars`  
 [out] Znaki, które odpowiadają kontekst wykonania żądanej.  
  
|`fRequestedList`Parametr|Znaki zwrócone|  
|--------------------------------|-------------------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|"."|  
|SCRIPT_CMPL_MEMBER_TRIGGER|"="|  
|SCRIPT_CMPL_PARAM_TRIGGER|"(,"|  
|SCRIPT_CMPL_COMMIT|"()"|  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)