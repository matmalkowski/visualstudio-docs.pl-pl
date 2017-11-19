---
title: "Obiekt będący wyrażeniem regularnym (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: RegularExpression_JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Regular Expression object
- regular expressions, RegExp object
- RegExp object, overview
ms.assetid: 346aa83e-a045-47ea-acae-b42c7b121534
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df2d07e3b47e315ec804e5a7f20024dc2184eef0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="regular-expression-object-javascript"></a>Obiekt będący wyrażeniem regularnym (JavaScript)
Obiekt, który zawiera wzorzec wyrażenia regularnego, wraz z flag określających sposób stosowania ze wzorcem.  
  
## <a name="syntax"></a>Składnia  
  
```  
re = /pattern/[flags]  
```  
  
## <a name="syntax"></a>Składnia  
  
```  
re = new RegExp("pattern"[,"flags"])   
```  
  
## <a name="parameters"></a>Parametry  
 *Ponowna*  
 Wymagany. Nazwa zmiennej, do której przypisano wzorzec wyrażenia regularnego.  
  
 *wzorzec*  
 Wymagany. Wzorzec wyrażenia regularnego do użycia. Jeśli używasz składni 1 ograniczania wzorzec przez "/" znaków. Jeśli używasz składni 2 wzorzec należy ująć w cudzysłowy.  
  
 `flags`  
 Opcjonalny. Należy ująć w cudzysłów flagi, użycie składni 2. Dostępne flagi, które mogą być łączone, są:  
  
-   g (wyszukiwanie globalne dla wszystkich wystąpień elementu *wzorzec*)  
  
-   i (ignorowanie wielkości liter)  
  
-   m (wielowierszowy wyszukiwania)  
  
-   u (unicode), umożliwia EcmaScript 6 [funkcje Unicode](../../javascript/advanced/special-characters-javascript.md). Obsługiwana tylko w programie [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)].  
  
-   y (dopasowanie jego umocowania), wyszukuje dopasowuje `lastIndex` właściwości wyrażeń regularnych (i nie Szukaj w późniejszym indeksy). Obsługiwane w [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)].  
  
## <a name="remarks"></a>Uwagi  
 **Wyrażenia regularnego** obiekt nie należy mylić z globalnej `RegExp` obiektu. Mimo że dźwiękowej są takie same, są one oddzielne. Właściwości **wyrażenia regularnego** obiektu zawierają tylko informacje dotyczące jednego określonego **wyrażenia regularnego** wystąpienia podczas właściwości globalne `RegExp` obiekt zawiera stale zaktualizowane informacje o każdym dopasowaniu po jego wystąpieniu.  
  
 **Wyrażenie regularne** wzorce używane podczas wyszukiwania ciągów dla kombinacji znaków przechowywania obiektów. Po **wyrażenia regularnego** obiekt jest tworzony, albo jest przekazywany do metody ciągu lub ciągu jest przekazywana do jednej z metod wyrażenia regularnego. Informacje o najnowszych wyszukiwania, wykonywane są przechowywane w globalnej `RegExp` obiektu.  
  
 Składnia 1 należy użyć, gdy wiesz, ciąg wyszukiwania wcześniejsze. Gdy często zmienia się ciąg wyszukiwania lub jest nieznany, na przykład ciągi jest pobierana z danych wejściowych użytkownika za pomocą składni 2.  
  
 *Wzorzec* argument jest skompilowany w wewnętrznym formacie przed użyciem. W składni 1 *wzorzec* jest skompilowany, ponieważ skrypt został załadowany. W składni 2 *wzorzec* jest kompilowane bezpośrednio przed użyciem, lub gdy **skompilować** metoda jest wywoływana.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie **wyrażenia regularnego** obiektu przez utworzenie obiektu (ponownego) zawierają wzorzec wyrażenia regularnego z jego flag skojarzone. W tym przypadku powstałe w ten sposób **wyrażenia regularnego** obiekt jest następnie używany przez `match` metody:  
  
```JavaScript  
var s = "through the pages of the book";  
  
// Create regular expression pattern.  
var re = new RegExp("the", "i");  
  
// Attempt match on search string.  
var r = s.match(re);     
  
// Return first occurrence of "the".  
if(console && console.log) {  
    console.log(r);  
}  
  
// Output:  
//   
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład aktualizuje wzorzec wyrażenia regularnego, aby wyszukać wielu wystąpień.  
  
```JavaScript  
// Create regular expression pattern using the i and g flags.  
var re = new RegExp("the", "ig");  
  
// Attempt match on search string.  
var r = s.match(re);     
  
// Return the two occurrences of "the".  
if(console && console.log) {  
    console.log(r.length);  
    console.log(r);  
}  
  
// Output:  
// 2  
// [object Array] ["the", "the"]  
```  
  
## <a name="example"></a>Przykład  
 Jeśli flagi /y dopasowanie zakończy się powodzeniem, aktualizuje `lastindex` do indeksu następny znak po ostatnim dopasowania. W przypadku niepowodzenia dopasowania resetuje `lastindex` na 0.  
  
 Poniższy przykład wyszukuje dopasowanie od określonego indeksu przy użyciu flagi /y i `lastIndex` właściwości.  
  
```JavaScript  
// Create regular expression pattern using the i and y flags.  
var re = new RegExp("the", "iy");  
  
// Set the lastIndex property and attempt a match  
// at the specified index.  
re.lastIndex = 20;  
var r = s.match(re);     
  
// No matches returned.  
if(console && console.log) {  
    console.log(r);  
}  
// Reset the lastIndex property and attempt a match.  
re.lastIndex = 21;  
var r = s.match(re);  
  
// Return occurrence of "the" starting at index 21.  
if(console && console.log) {  
    console.log(r);  
}  
  
// Output:  
// null  
// [object Array] ["the"]  
```  
  
<a name="js56jsobjregexpressionprop"></a>   
## <a name="properties"></a>Właściwości  
 [Global — właściwość](../../javascript/reference/global-property-regular-expression-javascript.md) &#124; [ignoreCase właściwość](../../javascript/reference/ignorecase-property-regular-expression-javascript.md) &#124; [właściwość multiline](../../javascript/reference/multiline-property-regular-expression-javascript.md) &#124; [właściwość źródła](../../javascript/reference/source-property-regular-expression-javascript.md)  
  
<a name="js56jsobjregexpressionmeth"></a>   
## <a name="methods"></a>Metody  
 [Compile — metoda](../../javascript/reference/compile-method-regular-expression-javascript.md) &#124; [exec — metoda](../../javascript/reference/exec-method-regular-expression-javascript.md) &#124; [test — metoda](../../javascript/reference/test-method-regular-expression-javascript.md)  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 Flaga u jest obsługiwana w [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)].  
  
 Flaga y jest obsługiwana w [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)].  
  
## <a name="see-also"></a>Zobacz też  
 [RegExp — obiekt](../../javascript/reference/regexp-object-javascript.md)   
 [Składnia wyrażeń regularnych (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [String — obiekt](../../javascript/reference/string-object-javascript.md)