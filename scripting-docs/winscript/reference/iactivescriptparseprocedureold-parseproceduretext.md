---
title: IActiveScriptParseProcedureOld::ParseProcedureText | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParseProcedureOld.ParseProcedureText
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptParseProcedureOld::ParseProcedureText
ms.assetid: 21a21313-35ce-432d-b9a6-7999065f19ac
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cab546deb390535fa8ff71e116a0ad42d33cc104
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793609"
---
# <a name="iactivescriptparseprocedureoldparseproceduretext"></a>IActiveScriptParseProcedureOld::ParseProcedureText
Analizuje procedury podanego kodu i dodaje procedurę anonimowego z przestrzenią nazw.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ParseProcedureText(  
   LPCOLESTR    pstrCode,  
   LPCOLESTR    pstrFormalParams,  
   LPCOLESTR    pstrItemName,  
   IUnknown*    punkContext,  
   LPCOLESTR    pstrDelimiter,  
   DWORD_PTR    dwSourceContextCookie,  
   ULONG        ulStartingLineNumber,  
   DWORD        dwFlags,  
   IDispatch**  ppdisp  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrCode`  
 [in] Tekst procedury do oceny. Interpretacja ten ciąg jest zależna od język skryptów.  
  
 `pstrFormalParams`  
 [in] Nazwy parametrów formalnych w procedurze. Nazwy parametrów muszą być rozdzielane ogranicznikami odpowiednie dla aparatu skryptów. Nazwy nie powinny być ujęte w nawiasy.  
  
 `pstrItemName`  
 [in] Nazwa elementu o nazwie, który udostępnia kontekst procedura ma zostać obliczone. Jeśli ten parametr ma `NULL`, kod jest obliczane w kontekście globalnym aparatu skryptów.  
  
 `punkContext`  
 [in] Obiekt kontekstu. Ten obiekt jest zarezerwowana do użycia w środowisku debugowania, w którym takiej sytuacji można podać przez debuger do reprezentowania aktywny kontekst środowiska wykonawczego. Jeśli ten parametr ma `NULL`, korzysta z aparatu `pstrItemName` do identyfikowania kontekstu.  
  
 `pstrDelimiter`  
 [in] Ogranicznik — wewnętrzny. Gdy `pstrCode` analizy strumienia tekstu host zazwyczaj używa ogranicznik, takie jak dwa pojedynczy znaki cudzysłowu ("), aby wykryć koniec procedury. Ten parametr określa ogranicznik używany host, umożliwiając aparat skryptów zapewnić niektórych warunkowego pierwotnych przetwarzania wstępnego (na przykład, zastępując dwa znaki pojedynczego cudzysłowu do użycia jako ogranicznik pojedynczego cudzysłowu [']). Dokładnie, jak (i jeśli) skryptów używa aparatu tych informacji jest zależna od aparatu skryptów. Ustaw ten parametr, `NULL` Jeśli host nie użyto ogranicznik można oznaczyć końca procedury.  
  
 `dwSourceContextCookie`  
 [in] Wartość zdefiniowanym przez aplikację, która jest używana na potrzeby debugowania.  
  
 `ulStartingLineNumber`  
 [in] Rozpocznie się od zera wartość, która określa, jaką wiersz analizy.  
  
 `dwFlags`  
 [in] Flagi skojarzone z tą procedurą. Może być kombinacją tych wartości.  
  
|Stała|Wartość|Znaczenie|  
|--------------|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|0x00000020|Oznacza to, że kod w `pstrCode` wyrażenie reprezentuje wartość zwracaną przez procedurę.|  
|SCRIPTPROC_IMPLICIT_THIS|0x00000100|Oznacza to, że `this` wskaźnik myszy znajduje się w zakresie procedury.|  
|SCRIPTPROC_IMPLICIT_PARENTS|0x00000200|Oznacza to, że nadrzędne `this` wskaźnika znajdują się w zakresie procedury.|  
  
 `ppdisp`  
 [out] Zwraca otoki wysyłania, domyślną metodą w przypadku procedury przeanalizowana przez tę metodę.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_INVALIDARG`|Argument był nieprawidłowy.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`E_NOTIMPL`|Ta metoda nie jest obsługiwana. Aparat skryptów nie obsługuje dodawania czasu wykonywania procedur z przestrzenią nazw.|  
|`E_UNEXPECTED`|Nie oczekiwano wywołania (na przykład aparatu skryptów jest w stanie niezainicjowaną bądź zamknięte).|  
|`OLESCRIPT_E_SYNTAX`|Wystąpił błąd składni nieokreślony w procedurze.|  
|`S_FALSE`|Aparat skryptów nie obsługuje obiektu dyspozytora; `ppdisp`ustawiono parametr `NULL`.|  
  
## <a name="remarks"></a>Uwagi  
 Brak kodu skryptu jest oceniane podczas tego wywołania; zamiast procedura jest kompilowany do metody na `ppdisp` gdzie może ona zostać wywołana przez skrypt później.  
  
 Ten interfejs jest przestarzały uzyskać `IActiveScriptParseProcedure` interfejsu. `IActiveScriptParseProcedure::ParseProcedureText` Metoda jest podobna do tej metody, ale pozwala należy określić nazwę procedury. We wszystkich przypadkach `IActiveScriptParseProcedure::ParseProcedureText` powinien być używany.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IActiveScriptParseProcedureOld](../../winscript/reference/iactivescriptparseprocedureold-interface.md)   
 [IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)