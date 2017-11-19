---
title: IDebugEnumField::GetValueFromString | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEnumField::GetValueFromString
helpviewer_keywords: IDebugEnumField::GetValueFromString method
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d88956f9ccdfef82f98de0b93d33c39b12955286
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugenumfieldgetvaluefromstring"></a>IDebugEnumField::GetValueFromString
Ta metoda zwraca wartość skojarzoną z nazwą stała wyliczenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetValueFromString(  
   LPCOLESTR  pszValue,  
   ULONGLONG* pvalue  
);  
```  
  
```csharp  
int GetValueFromString(  
   string    pszValue,  
   out ulong pValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszValue`  
 [in] Ciąg określający nazwę, dla którego można uzyskać wartość. Należy pamiętać, że dla języka C++, jest to ciąg znaków dwubajtowych.  
  
 `pValue`  
 [out] Zwraca wartość skojarzoną wartość liczbową.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE`, jeśli nazwa nie jest częścią wyliczenia lub kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest rozróżniana wielkość liter. Jeśli wymagane jest wyszukiwania bez uwzględniania wielkości liter (na przykład w języku takich jak Visual Basic, których nazwy nie są z uwzględnieniem wielkości liter), użyj [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md).  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)