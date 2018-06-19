---
title: IActiveScriptSiteDebug::OnScriptErrorDebug | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.OnScriptErrorDebug
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::OnScriptErrorDebug
ms.assetid: 87f201da-36eb-49a2-b000-e1e1e8c4cdb7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a669d435d84295b22af4298936babf8439eaefa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793606"
---
# <a name="iactivescriptsitedebugonscripterrordebug"></a>IActiveScriptSiteDebug::OnScriptErrorDebug
Umożliwia host inteligentny do określenia sposobu obsługi błędów czasu wykonywania.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT OnScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   BOOL*                     pfEnterDebugger,  
   BOOL*                     pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pErrorDebug`  
 [in] Wystąpił błąd czasu wykonywania  
  
 `pfEnterDebugger`  
 [out] Flaga wskazująca, czy do przekazania błąd do debugera w celu debugowanie JIT.  
  
 `pfCallOnScriptErrorWhenContinuing`  
 [out] Flaga wskazująca, czy wywołać `IActiveScriptSite::OnScriptError` gdy użytkownik decyduje o tym kontynuować bez debugowania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Możliwe wartości zawierają, ale nie są ograniczone do wartości w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Host inteligentny ta metoda służy do określenia sposobu obsługi błędów czasu wykonywania.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IActiveScriptSiteDebug](../../winscript/reference/iactivescriptsitedebug-interface.md)