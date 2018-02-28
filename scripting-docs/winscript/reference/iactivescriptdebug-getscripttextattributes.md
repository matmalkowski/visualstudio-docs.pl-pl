---
title: IActiveScriptDebug::GetScriptTextAttributes | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptDebug.GetScriptTextAttributes
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptDebug::GetScriptTextAttributes
ms.assetid: 2e8bda34-db0c-4b2e-a17f-82c4e0dbbc8c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c8e9cd76da3e754eabce836b386893043dcd0622
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptdebuggetscripttextattributes"></a>IActiveScriptDebug::GetScriptTextAttributes
Zwraca atrybuty tekstu dla dowolnego bloku skryptu tekstu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetScriptTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrCode`  
 [in] Tekst bloku skryptu. Ten ciąg nie muszą być zakończone znakiem null.  
  
 `uNumCodeChars`  
 [in] Liczba znaków w tekście blok skryptu.  
  
 `pstrDelimiter`  
 [in] Adres ogranicznik zakończenia elementu skryptu bloku. Gdy `pstrCode` analizy strumienia tekstu host zazwyczaj używa ogranicznik, takie jak dwa pojedynczy znaki cudzysłowu ("), aby wykryć koniec bloku skryptu. Ten parametr określa ogranicznik używany hosta, dzięki czemu aparat skryptów w celu zapewnienia przetworzenia warunkowego wstępnego pierwotnych (na przykład, zastępując pojedynczego cudzysłowu ['] dwa znaki pojedynczego cudzysłowu do użycia jako ogranicznik). Dokładnie, jak (i jeśli) skryptów używa aparatu tych informacji jest zależna od aparatu skryptów. Ustaw ten parametr na wartość NULL, jeśli host nie użyto ogranicznik można oznaczyć końca bloku skryptu.  
  
 `dwFlags`  
 [in] Flagi skojarzone z bloku skryptu. Może być kombinacją tych wartości:  
  
|Stała|Wartość|Opis|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0X0001|Wskazuje, że identyfikatorów i operatory kropka należy zidentyfikować flag SOURCETEXT_ATTR_IDENTIFIER i SOURCETEXT_ATTR_MEMBERLOOKUP, odpowiednio.|  
|GETATTRFLAG_THIS|0x0100|Wskazuje, że z flagą SOURCETEXT_ATTR_THIS należy zidentyfikować identyfikator dla bieżącego obiektu.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Wskazuje, czy tekst zawartości i komentarza należy zidentyfikować przy użyciu flagi SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [w, out] Bufor do zawierają atrybuty zwracane.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Hosta inteligentnego, który implementuje `IDebugDocumentText` interfejsu użyć tej metody w celu delegowania wywołań `IDebugDocumentText::GetText` metody.  
  
 Ta metoda blokach skryptu; `GetScriptletTextAttributes` metoda jest przeznaczona dla skryptlety.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IActiveScriptDebug](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)   
 [Interfejs IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)   
 [Wyliczenie SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)