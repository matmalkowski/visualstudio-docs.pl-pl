---
title: IActiveScriptSiteDebug32::GetDocumentContextFromPosition | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53348dff-35a6-4303-b263-90c10af06bf3
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 71136a1b3cb136cbc0a97cf39f59f1f4e950048b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebug32getdocumentcontextfromposition"></a>IActiveScriptSiteDebug32::GetDocumentContextFromPosition
Używane przez aparat języka Aby delegować `IDebugCodeContext::GetSourceContext`.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetDocumentContextFromPosition(  
   DWORD_PTR                dwSourceContext,  
   ULONG                    uCharacterOffset,  
   ULONG                    uNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwSourceContext`  
 [in] Zawartość źródłową przewidzianych do `ParseScriptText` lub `AddScriptlet`.  
  
 `uCharacterOffset`  
 [in] Znak przesuwane względem początku bloku skryptu lub skryptlet.  
  
 `uNumChars`  
 [in] Liczba znaków w tym kontekście.  
  
 `ppsc`  
 [out] Kontekstu dokumentu odpowiadającego tej pozycji znaku zakresu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Aparaty języka ta metoda umożliwia delegowanie `IDebugCodeContext::GetSourceContext`.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IActiveScriptSiteDebug32](../../winscript/reference/iactivescriptsitedebug32-interface.md)