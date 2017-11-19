---
title: IActiveScriptParse32::ParseScriptText | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f33e454c-69d8-4cab-9150-d1e7fd04786d
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: af1e3b6723b402263359719695aa1f57432c76e2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparse32parsescripttext"></a>IActiveScriptParse32::ParseScriptText
Analizuje skryptlet podanego kodu, dodawanie deklaracji w przestrzeni nazw i oceny kodu zależnie od potrzeb.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ParseScriptText(  
    LPCOLESTR pstrCode,              // address of scriptlet text  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-scriptlet delimiter  
    DWORD_PTR dwSourceContextCookie, // cookie for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // scriptlet flags  
    VARIANT *pvarResult,             // address of buffer for results  
    EXCEPINFO *pexcepinfo            // address of buffer for error data  
);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|`pstrCode`|[in] Adres tekst skryptlety do oceny. Interpretacja ten ciąg jest zależna od język skryptów.|  
|`pstrItemName`|[in] Nazwa elementu, który udostępnia kontekst, w którym ma zostać obliczone skryptlet adres. Jeśli ten parametr ma wartość NULL, kod jest obliczane w kontekście globalnym aparatu skryptów.|  
|`punkContext`|[in] Adres obiektu kontekstu. Ten obiekt jest zarezerwowana do użycia w środowisku debugowania, w którym takiej sytuacji można podać przez debuger do reprezentowania aktywny kontekst środowiska wykonawczego. Jeśli ten parametr ma wartość NULL, używa aparatu `pstrItemName` do identyfikowania kontekstu.|  
|`pstrDelimiter`|[in] Adres ogranicznika "end skryptlet". Gdy `pstrCode` analizy strumienia tekstu host zazwyczaj używa ogranicznik, takie jak dwa pojedynczy znaki cudzysłowu ("), aby wykryć koniec skryptlet. Ten parametr określa ogranicznik używany hosta, dzięki czemu aparat skryptów w celu zapewnienia przetworzenia warunkowego wstępnego pierwotnych (na przykład, zastępując pojedynczego cudzysłowu ['] dwa znaki pojedynczego cudzysłowu do użycia jako ogranicznik). Dokładnie, jak (i jeśli) skryptów aparatu sprawia, że korzystanie z tych informacji jest zależna od aparatu skryptów. Ustaw ten parametr, `NULL` Jeśli host nie użyto ogranicznik można oznaczyć końca skryptlet.|  
|`dwSourceContextCookie`|[in] Plik cookie używany do debugowania.|  
|`ulStartingLineNumber`|[in] Liczony od zera wartość, która określa, która linia analiza rozpocznie się na.|  
|`dwFlags`|[in] Flagi skojarzone z skryptlet. Może być kombinacją tych wartości:|  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|SCRIPTTEXT_ISEXPRESSION|Jeśli różnicy między obliczeniową wyrażenie instrukcji jest ważne, ale składniowo jest niejednoznaczny w język skryptów, ta flaga Określa, że skryptlet jest interpretowane jako wyrażenie, a nie jako instrukcji lub listy instrukcji. Domyślnie instrukcje są uznawane za chyba że odpowiedniego wyboru można ustalić na podstawie składni skryptlet tekstu.|  
|SCRIPTTEXT_ISPERSISTENT|Wskazuje, czy kod dodane podczas tego wywołania ma zostać zapisany po zapisaniu aparat skryptów (na przykład za pomocą wywołania `IPersist*::Save`), lub jeśli aparat skryptów jest resetowany i przejście do stanu zainicjowane.|  
|SCRIPTTEXT_ISVISIBLE|Wskazuje, że w skrypcie powinny być widoczne (i w związku z tym wywołane przez nazwę) jako metoda globalna w obszarze nazw skryptu.|  
  
|||  
|-|-|  
|`pvarResult`|[out] Adres buforu, który odbiera wyniki przetwarzania skryptlet lub `NULL` Jeśli element wywołujący oczekuje wyników (to znaczy SCRIPTTEXT_ISEXPRESSION nie określono wartości).|  
|`pexcepinfo`|[out] Adres struktury, która otrzymuje informacje o wyjątku. Ta struktura jest wypełniana, jeśli `IActiveScriptParse::ParseScriptText` zwraca DISP_E_EXCEPTION.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Powodzenie.|  
|`DISP_E_EXCEPTION`|Wystąpił wyjątek podczas przetwarzania skryptlet. `pexcepinfo` Parametr zawiera informacje o wyjątku.|  
|`E_INVALIDARG`|Argument był nieprawidłowy.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`E_NOTIMPL`|Ta metoda nie jest obsługiwana. Aparat skryptów nie obsługuje środowiska wykonawczego Szacowanie wyrażenia lub instrukcje.|  
|`E_UNEXPECTED`|Nie oczekiwano wywołania (na przykład aparatu skryptów jest w stanie niezainicjowanej lub zamkniętych lub została ustawiona flaga SCRIPTTEXT_ISEXPRESSION i aparat skryptów jest w stanie zainicjowania).|  
|`OLESCRIPT_E_SYNTAX`|Wystąpił błąd składni nieokreślony w skryptlet.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli aparat skryptów jest w stanie zainicjowania, żaden kod nie zostanie obliczone faktycznie podczas tego wywołania; zamiast taki kod jest w kolejce i wykonywać, gdy aparat skryptów jest są przenoszone do (lub za pośrednictwem) stan uruchomienia. Ponieważ nie jest dozwolone wykonywanie w stanie zainicjowania, występuje błąd aby wywołać tę metodę, przy użyciu flagi SCRIPTTEXT_ISEXPRESSION w stanie zainicjowania.  
  
 Skryptlet może być wyrażenie, listę instrukcji lub jakikolwiek dozwolone przez język skryptów. Na przykład, ta metoda jest używana podczas obliczania HTML \<skryptu > tagu, który zezwala na używanie instrukcji do wykonania jako strony HTML jest tworzona, a nie tylko kompilowanie ich do stanu skryptu.  
  
 Kod, który został przekazany do tej metody musi być prawidłową, pełną fragment kodu. Na przykład w języku VBScript jest niedozwolone wywołanie tej metody jeden raz z Sub Function(x) i następnie ponownie `End Sub`. Analizator nie trzeba poczekać, drugie wywołanie zakończyć procedurę, ale raczej należy wygenerować błąd analizy, ponieważ deklaracja podprocedury został uruchomiony, ale nie ukończony.  
  
 Aby uzyskać więcej informacji na temat stanów skryptu, zobacz sekcję stanów aparatu skryptu [aparaty skryptów systemu Windows](../../winscript/windows-script-engines.md).  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)