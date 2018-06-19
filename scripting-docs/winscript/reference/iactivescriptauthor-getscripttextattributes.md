---
title: IActiveScriptAuthor::GetScriptTextAttributes | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetScriptTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetScriptTextAttributes
ms.assetid: a53451de-cc5c-4b53-8e5f-81e196364caf
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6aa96623b4356f0a3d17c8b2631840953dac2d51
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793249"
---
# <a name="iactivescriptauthorgetscripttextattributes"></a>IActiveScriptAuthor::GetScriptTextAttributes
Zwraca atrybuty tekstu w bloku skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetScriptTextAttributes(  
    LPCOLESTR        pszCode,  
    ULONG            cch,  
    LPCOLESTR        pszDelimiter,  
    DWORD            dwFlags,  
    SOURCE_TEXT_ATTR *pattr);  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszCode`  
 [w size_is (`cch`)] tekst bloku skryptu. Ten ciąg ma być zakończone znakiem null.  
  
 `cch`  
 [in] Rozmiar używany `pszCode` i `pattr` parametrów.  
  
 `pszDelimiter`  
 [in] Adres ogranicznik zakończenia elementu skryptu. Gdy `pszCode` analizy strumienia tekstu host zazwyczaj używa ogranicznik (na przykład dwa pojedynczy cudzysłów), aby wykryć koniec skryptlet. Ustaw ten parametr na wartość NULL, jeśli nie istnieje żadne ogranicznik do identyfikowania koniec bloku skryptu.  
  
 `dwFlags`  
 [in] Flagi, które są skojarzone z atrybutów tekstu w bloku skryptu. Może być kombinacją następujących wartości:  
  
|Stała|Wartość|Opis|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0X0001|Identyfikowanie identyfikatorów, które mają atrybut SOURCETEXT_ATTR_IDENTIFIER i zidentyfikować kropka operatory, które mają atrybut SOURCETEXT_ATTR_MEMBERLOOKUP.|  
|GETATTRFLAG_THIS|0x0100|Zidentyfikuj bieżącego obiektu, który ma atrybut SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Określ tekst zawartości i komentarza ciąg, który ma atrybut SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [w, out, size_is (`cch`)] informacji o kolorze do kodu bloku skryptu.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)   
 [Wyliczenie SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)