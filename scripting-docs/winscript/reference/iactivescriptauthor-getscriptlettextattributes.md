---
title: IActiveScriptAuthor::GetScriptletTextAttributes | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetScriptletTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetScriptletTextAttributes
ms.assetid: 082edfce-6c5b-4e5e-b942-31b423a4fa1d
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b01fba7d0e8eb80fed51b1ff0ebd3a8816bacb01
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793300"
---
# <a name="iactivescriptauthorgetscriptlettextattributes"></a>IActiveScriptAuthor::GetScriptletTextAttributes
Zwraca atrybuty tekstu skryptlet.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR pszCode,  
   ULONG cch,  
   LPCOLESTR pszDelimiter,  
   DWORD dwFlags,  
   SOURCE_TEXT_ATTR *pattr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszCode`  
 [w size_is (`cch`)] skryptlet tekstu. Ten ciąg ma być zakończone znakiem null.  
  
 `cch`  
 [in] Rozmiar używany `pszCode` i `pattr` parametrów.  
  
 `pszDelimiter`  
 [in] Adres ogranicznika "end skryptlet". Gdy `pszCode` analizy strumienia tekstu host zazwyczaj używa ogranicznik (na przykład dwa pojedynczy cudzysłów), aby wykryć koniec skryptlet. Ustaw ten parametr na wartość NULL, jeśli nie ogranicznika służy do identyfikowania koniec skryptlet.  
  
 `dwFlags`  
 [in] Flagi, które są skojarzone z atrybutów tekstu skryptlet. Może być kombinacją następujących wartości.  
  
|Stała|Wartość|Opis|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0X0001|Identyfikowanie identyfikatorów, które mają atrybut SOURCETEXT_ATTR_IDENTIFIER i zidentyfikować kropka operatory, które mają atrybut SOURCETEXT_ATTR_MEMBERLOOKUP.|  
|GETATTRFLAG_THIS|0x0100|Zidentyfikuj bieżącego obiektu, który ma atrybut SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Określ tekst zawartości i komentarza ciąg, który ma atrybut SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [w, out, size_is (`cch`)] informacji o kolorze do kodu skryptlet.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)   
 [Wyliczenie SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)