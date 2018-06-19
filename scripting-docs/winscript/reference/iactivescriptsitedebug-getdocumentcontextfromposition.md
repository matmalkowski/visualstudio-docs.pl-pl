---
title: IActiveScriptSiteDebug::GetDocumentContextFromPosition | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.GetDocumentContextFromPosition
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::GetDocumentContextFromPosition
ms.assetid: ba5f7348-0107-4b12-b949-79a012476cf7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25ce03a124f246443afd0f5a8540a93e7d474f9a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793531"
---
# <a name="iactivescriptsitedebuggetdocumentcontextfromposition"></a>IActiveScriptSiteDebug::GetDocumentContextFromPosition
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
 [Interfejs IActiveScriptSiteDebug](../../winscript/reference/iactivescriptsitedebug-interface.md)