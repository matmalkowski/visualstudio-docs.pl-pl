---
title: IActiveScriptAuthor::AddScriptlet | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthor.AddScriptlet
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthor::AddScriptlet
ms.assetid: 879a6651-f187-4934-b130-c1247549900b
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b21f906a73a313bf775683ba63738adb25af0007
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthoraddscriptlet"></a>IActiveScriptAuthor::AddScriptlet
Dodaje skryptlet kodu jako element podrzędny elementu poziomu głównego `IScriptNode` obiektu. Na hoście w pełni kwalifikowanej nazwy skryptletu może mieć tylko dwa poziomy.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT AddScriptlet(  
   LPCOLESTR pszDefaultName,  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszSubItemName,  
   LPCOLESTR pszEventName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszDefaultName`  
 [in] Adres domyślną nazwę do skojarzenia z skryptlet.  
  
 `pszCode`  
 [in] Adres skryptlet tekstu.  
  
 `pszItemName`  
 [in] Adres buforu najwyższego poziomu identyfikatora nazwy skryptletu pełną na hoście.  
  
 `pszSubItemName`  
 [in] Adres buforu identyfikator drugiego poziomu nazwy skryptletu pełną na hoście. Wartość NULL, jeśli nazwa zawiera tylko jeden poziom.  
  
 `pszEventName`  
 [in] Adres buforu, który zawiera nazwę zdarzenia, dla którego skryptlet jest program obsługi zdarzeń.  
  
 `pszDelimiter`  
 [in] Adres ogranicznik zakończenia elementu skryptu bloku. Gdy `pszCode` analizy strumienia tekstu host zazwyczaj używa ogranicznik (na przykład dwa pojedynczy cudzysłów), aby wykryć koniec bloku skryptu. Ustaw ten parametr na wartość NULL, jeśli ogranicznik nie oznacza koniec bloku skryptu.  
  
 `dwCookie`  
 [in] Wartość zdefiniowanym przez aplikację, która jest używana do skojarzenia skryptlet z obiektu hosta.  
  
 `dwFlags`  
 [in] Nie jest używany.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)