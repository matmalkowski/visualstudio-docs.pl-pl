---
title: IActiveScriptParseProcedure32::ParseProcedureText | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ede37171-2f1e-4467-a358-17bd4a4f1869
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 2f36160ab9dca3ccc99aed1068b7e94fe1b7675d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparseprocedure32parseproceduretext"></a>IActiveScriptParseProcedure32::ParseProcedureText
Analizuje procedury podanego kodu i dodaje procedurę do przestrzeń nazw.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ParseProcedureText(  
    LPCOLESTR pstrCode,              // address of procedure text  
    LPCOLESTR pstrFormalParams,      // address of formal parameter names  
    LPCOLESTR pstrProcedureName,     // address of procedure name  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-procedure delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // procedure flags  
    IDispatch **ppdisp               // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrCode`  
 [in] Adres tekst procedury do oceny. Interpretacja ten ciąg jest zależna od język skryptów.  
  
 `pstrFormalParams`  
 [in] Adres nazwy parametrów formalnych w procedurze. Nazwy parametrów muszą być rozdzielane ogranicznikami odpowiednie dla aparatu skryptów. Nazwy nie powinny być ujęte w nawiasy.  
  
 `pstrProcedureName`  
 [in] Adres nazwę procedury do przeanalizowania.  
  
 `pstrItemName`  
 [in] Adres nazwa elementu zapewniająca kontekstu, w którym ma zostać obliczone procedury. Jeśli ten parametr ma `NULL`, kod jest obliczane w kontekście globalnym aparatu skryptów.  
  
 `punkContext`  
 [in] Adres obiektu kontekstu. Ten obiekt jest zarezerwowana do użycia w środowisku debugowania, w którym takiej sytuacji można podać przez debuger do reprezentowania aktywny kontekst środowiska wykonawczego. Jeśli ten parametr ma `NULL`, korzysta z aparatu `pstrItemName` do identyfikowania kontekstu.  
  
 `pstrDelimiter`  
 [in] Adres ogranicznika — wewnętrzny. Gdy `pstrCode` analizy strumienia tekstu host zazwyczaj używa ogranicznik, takie jak dwa pojedynczy znaki cudzysłowu ("), aby wykryć koniec procedury. Ten parametr określa ogranicznik używany hosta, dzięki czemu aparat skryptów w celu zapewnienia przetworzenia warunkowego wstępnego pierwotnych (na przykład, zastępując pojedynczego cudzysłowu ['] dwa znaki pojedynczego cudzysłowu do użycia jako ogranicznik). Dokładnie, jak (i jeśli) skryptów aparatu sprawia, że korzystanie z tych informacji jest zależna od aparatu skryptów. Ustaw ten parametr, `NULL` Jeśli host nie użyto ogranicznik można oznaczyć końca procedury.  
  
 `dwSourceContextCookie`  
 [in] Wartość zdefiniowanym przez aplikację, która jest używana na potrzeby debugowania.  
  
 `ulStartingLineNumber`  
 [in] Liczony od zera wartość, która określa, która linia analiza rozpocznie się na.  
  
 `dwFlags`  
 [in] Flagi skojarzone z tą procedurą. Może być kombinacją tych wartości:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|Oznacza to, że kod w `pstrCode` wyrażenie reprezentuje wartość zwracaną przez procedurę. Domyślnie ten kod może zawierać wyrażenia, listę instrukcji lub jakikolwiek else dozwoloną w procedurze język skryptów.|  
|SCRIPTPROC_IMPLICIT_THIS|Oznacza to, że `this` wskaźnik myszy znajduje się w zakresie procedury.|  
|SCRIPTPROC_IMPLICIT_PARENTS|Oznacza to, że nadrzędne `this` wskaźnika znajdują się w zakresie procedury.|  
  
 `ppdisp`  
 [out] Adres wskaźnika do obiektu zawierającego właściwości i metody globalne skryptu. Jeśli aparat skryptów nie obsługuje takiego obiektu `NULL` jest zwracany.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Powodzenie.|  
|`E_INVALIDARG`|Argument był nieprawidłowy.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`E_NOTIMPL`|Ta metoda nie jest obsługiwana. Aparat skryptów nie obsługuje dodawania czasu wykonywania procedur z przestrzenią nazw.|  
|`E_UNEXPECTED`|Nie oczekiwano wywołania (na przykład aparatu skryptów jest w stanie niezainicjowaną bądź zamknięte).|  
|`OLESCRIPT_E_SYNTAX`|Wystąpił błąd składni nieokreślony w procedurze.|  
|`S_FALSE`|Aparat skryptów nie obsługuje obiektu dyspozytora; `ppdisp` ustawiono parametr `NULL`.|  
  
## <a name="remarks"></a>Uwagi  
 Brak kodu skryptu jest oceniane podczas tego wywołania; zamiast procedura jest kompilowany do stanu skryptu, gdzie może ona zostać wywołana przez skrypt później.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptParseProcedure32](../../winscript/reference/iactivescriptparseprocedure32.md)