---
title: IActiveScriptDebug::GetScriptletTextAttributes | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptDebug.GetScriptletTextAttributes
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptDebug::GetScriptletTextAttributes
ms.assetid: b3990d86-5fdf-4c9f-9678-3f4b808c7ca8
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 909879030e5c6d26353d2003279d5c1ca7bacb74
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptdebuggetscriptlettextattributes"></a>IActiveScriptDebug::GetScriptletTextAttributes
Zwraca atrybuty tekstu dla dowolnego skryptlet.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrCode`  
 [in] Tekst skryptlet. Ten ciąg nie muszą być zakończone znakiem null.  
  
 `uNumCodeChars`  
 [in] Liczba znaków w tekście skryptlet.  
  
 `pstrDelimiter`  
 [in] Adres ogranicznika "end skryptlet". Gdy `pstrCode` analizy strumienia tekstu host zazwyczaj używa ogranicznik, takie jak dwa pojedynczy znaki cudzysłowu ("), aby wykryć koniec skryptlet. Ten parametr określa ogranicznik używany hosta, dzięki czemu aparat skryptów w celu zapewnienia przetworzenia warunkowego wstępnego pierwotnych (na przykład, zastępując pojedynczego cudzysłowu ['] dwa znaki pojedynczego cudzysłowu do użycia jako ogranicznik). Dokładnie, jak (i jeśli) skryptów używa aparatu tych informacji jest zależna od aparatu skryptów. Ustaw ten parametr na wartość NULL, jeśli host nie użyto ogranicznik można oznaczyć końca skryptlet.  
  
 `dwFlags`  
 [in] Flagi skojarzone z skryptlet. Może być kombinacją tych wartości:  
  
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
  
 To wywołanie jest dostępne, ponieważ skryptlety są wyrażeń i może mieć inną składnię niż blok skryptu. Jeśli dysponują takiej samej składni implementacja tej metody będzie taka sama jak implementacja `GetScriptTextAttributes` metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IActiveScriptDebug](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)   
 [Interfejs IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)   
 [Wyliczenie SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)