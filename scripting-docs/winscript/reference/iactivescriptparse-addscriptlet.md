---
title: IActiveScriptParse::AddScriptlet | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptParse.AddScriptlet
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParse_AddScriptlet
ms.assetid: 824929f4-4dd3-473a-92d9-0b96acea2f14
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e854ac71dc36263d805160f9336e049856076ce5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparseaddscriptlet"></a>IActiveScriptParse::AddScriptlet
Dodaje skryptlet kodu do skryptu. Ta metoda jest używana w środowiskach, gdzie trwały stan skryptu jest sprzężony z dokumentem hosta, a host jest odpowiedzialny za Przywracanie skryptu, a nie za pomocą `IPersist*` interfejsu. Podstawowe przykłady są języki skryptów HTML umożliwiających skryptlety kodu osadzony w dokumencie HTML, który jest dołączony do zdarzenia wewnętrzne (na przykład ONCLICK="button1.text='Exit" ").  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT AddScriptlet(  
    LPCOLESTR pstrDefaultName,       // address of default name of scriptlet  
    LPCOLESTR pstrCode,              // address of scriptlet text  
    LPCOLESTR pstrItemName,          // address of item name  
    LPCOLESTR pstrSubItemName,       // address of subitem name  
    LPCOLESTR pstrEventName,         // address of event name  
    LPCOLESTR pstrDelimiter,         // address of end-of-scriptlet delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // scriptlet flags  
    BSTR *pbstrName,                 // address of actual name of scriptlet  
    EXCEPINFO *pexcepinfo            // address of exception information  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrDefaultName`  
 [in] Adres do skojarzenia z skryptlet nazwa domyślna. Jeśli skryptlet nie zawiera informacji o nazewnictwie (jak w powyższym przykładzie ONCLICK), ta nazwa będzie używana do identyfikowania skryptlet. Jeśli ten parametr ma `NULL`, aparat skryptów wytwarza unikatową nazwę, jeśli to konieczne.  
  
 `pstrCode`  
 [in] Adres tekst skryptlety do dodania. Interpretacja ten ciąg jest zależna od język skryptów.  
  
 `pstrItemName`  
 [in] Adres buforu, który zawiera nazwę elementu skojarzone z tym skryptlet. Ten parametr, oprócz `pstrSubItemName`, określa obiekt, dla którego skryptlet jest obsługą zdarzeń.  
  
 `pstrSubItemName`  
 [in] Adres buforu, który zawiera nazwę `subobject` nazwanego elementu z którą ten skryptlet jest skojarzony; ta nazwa musi zostać znaleziony w informacji o typie nazwanego elementu. Ten parametr ma wartość NULL, jeśli skryptlet ma być skojarzona z element o nazwie, a nie `subitem`. Ten parametr, oprócz `pstrItemName`, identyfikuje określonego obiektu, dla którego skryptlet jest obsługą zdarzeń.  
  
 `pstrEventName`  
 [in] Adres buforu, który zawiera nazwę zdarzenia, dla którego skryptlet jest obsługą zdarzeń.  
  
 `pstrDelimiter`  
 [in] Adres ogranicznika "end skryptlet". Gdy `pstrCode` parametru jest analizowana ze strumienia tekstu, host zazwyczaj używa ogranicznik, takie jak dwa pojedynczy znaki cudzysłowu ("), aby wykryć koniec skryptlet. Ten parametr określa ogranicznik używany hosta, dzięki czemu aparat skryptów w celu zapewnienia przetworzenia warunkowego wstępnego pierwotnych (na przykład, zastępując pojedynczego cudzysłowu ['] dwa znaki pojedynczego cudzysłowu do użycia jako ogranicznik). Dokładnie, jak (i jeśli) skryptów aparatu sprawia, że korzystanie z tych informacji jest zależna od aparatu skryptów. Ustaw ten parametr na wartość NULL, jeśli host nie użyto ogranicznik można oznaczyć końca skryptlet.  
  
 `dwSourceContextCookie`  
 [in] Wartość zdefiniowanym przez aplikację, która jest używana na potrzeby debugowania.  
  
 `ulStartingLineNumber`  
 [in] Liczony od zera wartość, która określa, która linia analiza rozpocznie się na.  
  
 `dwFlags`  
 [in] Flagi skojarzone z skryptlet. Może być kombinacją następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|SCRIPTTEXT_ISVISIBLE|Wskazuje, że w skrypcie powinny być widoczne (i w związku z tym wywołane przez nazwę) jako metoda globalna w obszarze nazw skryptu.|  
|SCRIPTTEXT_ISPERSISTENT|Wskazuje, czy kod dodane podczas tego wywołania ma zostać zapisany po zapisaniu aparat skryptów (na przykład za pomocą wywołania `IPersist*::Save`), lub jeśli aparat skryptów jest resetowany i przejście do stanu zainicjowane. Aby uzyskać więcej informacji o tym stanie Zobacz stany aparatu skryptu.|  
  
 `pbstrName` ,  
 [out] Rzeczywista nazwa używana do identyfikacji skryptlet. Ma to na celu w kolejności preferencji: w tekście skryptlet jawnie określić nazwę, domyślna nazwa podana w `pstrDefaultName`, lub unikatową nazwę syntezatora przez aparat skryptów.  
  
 `pexcepinfo` ,  
 [out] Adres struktury zawierający informacje o wyjątku. Ta struktura powinno być wypełnione przypadku jest zwracany DISP_E_EXCEPTION.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Powodzenie.|  
|`DISP_E_EXCEPTION`|Wystąpił wyjątek podczas analizowania skryptlet. `pexcepinfo` Parametr zawiera informacje o wyjątku.|  
|`E_INVALIDARG`|Argument był nieprawidłowy.|  
|`E_NOTIMPL`|Ta metoda nie jest obsługiwana; aparat skryptów nie obsługuje dodawania skryptlety wychwytywanie zdarzeń.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`E_UNEXPECTED`|Nie oczekiwano wywołania (na przykład aparatu skryptów jeszcze nie został załadowany lub zainicjować) i dlatego nie powiodła się.|  
|`OLESCRIPT_E_INVALIDNAME`|Podana nazwa domyślna jest nieprawidłowy w tym języku skryptów.|  
|`OLESCRIPT_E_SYNTAX`|Wystąpił błąd składni nieokreślony w skryptlet.|  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)