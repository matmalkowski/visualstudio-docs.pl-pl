---
title: IActiveScriptErrorDebug::GetDocumentContext | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptErrorDebug.GetDocumentContext
apilocation: jscript.dll
helpviewer_keywords: IActiveScriptErrorDebug::GetDocumentContext
ms.assetid: 567601a1-551a-4905-bda1-1f54610174f4
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1342465ed306f43d07248f8e3c776e9e9af2c774
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescripterrordebuggetdocumentcontext"></a>IActiveScriptErrorDebug::GetDocumentContext
Udostępnia kontekst dokumentu dla tego błędu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetDocumentContext(  
   IDebugDocumentContext**  ppssc  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppssc`  
 [out] Kontekstu dokumentu dla tego błędu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Zakres znaku na pozycji kontekstu dokumentu powinny zawierać wszystkie znaki odpowiadający błąd.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IActiveScriptErrorDebug](../../winscript/reference/iactivescripterrordebug-interface.md)