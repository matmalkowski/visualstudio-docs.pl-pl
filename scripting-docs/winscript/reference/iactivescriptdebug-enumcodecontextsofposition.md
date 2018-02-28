---
title: IActiveScriptDebug::EnumCodeContextsOfPosition | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptDebug.EnumCodeContextsOfPosition
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptDebug::EnumCodeContextsOfPosition
ms.assetid: 19f44420-bcc8-4c10-8c38-378d96044117
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 40fd8e2d19d3949ff26811956ae3d203871e5510
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptdebugenumcodecontextsofposition"></a>IActiveScriptDebug::EnumCodeContextsOfPosition
Używany przez hosta inteligentnego, aby delegować `IDebugDocumentContext::EnumCodeContexts` metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumCodeContextsOfPosition(  
   DWORD_PTR                 dwSourceContext,  
   ULONG                     uCharacterOffset,  
   ULONG                     uNumChars,  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwSourceContext`  
 [in] Kontekst źródła przewidzianych do `IActiveScriptParse::ParseScriptText` lub `IActiveScriptParse::AddScriptlet`.  
  
 `uCharacterOffset`  
 [in] Znak przesuwane względem początku skryptu tekstu.  
  
 `uNumChars`  
 [in] Liczba znaków w tym kontekście.  
  
 `ppescc`  
 [out] Moduł wyliczający kontekstów kodu w określonym zakresie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Hosty inteligentne ta metoda umożliwia delegowanie `IDebugDocumentContext::EnumCodeContexts` metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IActiveScriptDebug](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)