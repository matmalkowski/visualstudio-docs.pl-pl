---
title: '&lt;Zwraca&gt; (JavaScript) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- returns JavaScript XML tag
- <returns> JavaScript XML tag
ms.assetid: 10d97829-c0ae-40a5-b04c-d8b538cdefbc
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: dfe2c3d8e9c91927f7f4d0848b8d180132646614
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42677097"
---
# <a name="ltreturnsgt-javascript"></a>&lt;Zwraca&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [dokumentacja programu Visual Studio 2017](https://docs.microsoft.com/en-us/visualstudio/).  
  
Określa informacje o dokumentacji dla wyniku wywołania funkcji lub metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
<returns type="ValueType" integer="true|false"  
    domElement="true|false" mayBeNull="true|false"  
    elementType="ArrayElementType" elementInteger="true|false"  
    elementDomElement="true|false" elementMayBeNull="true|false"  
    locid="descriptionID" value="code">description  
</returns>  
```  
  
#### <a name="parameters"></a>Parametry  
 `type`  
 Opcjonalna. Typ danych wartości zwracanej. Typ może być jednym z następujących czynności:  
  
-   Wpisz w specyfikacji ECMAScript 5, takie jak z językiem ECMAScript `Number` i `Object`.  
  
-   Obiekt modelu DOM, takich jak `HTMLElement`, `Window`, i `Document`.  
  
-   Funkcja konstruktora języka JavaScript.  
  
 `integer`  
 Opcjonalna. Jeśli `type` jest `Number`, określa, czy zwracana wartość jest liczbą całkowitą. Ustaw `true` do wskazania, że wartość zwracana jest liczba całkowita; w przeciwnym wypadku ustaw `false`. Ten atrybut nie jest używany przez program Visual Studio zapewnienie informacji IntelliSense.  
  
 `domElement`  
 Opcjonalna. Ten atrybut jest przestarzała; `type` atrybut mają pierwszeństwo przed tego atrybutu. Ten atrybut określa, czy udokumentowanego wartość zwracana jest DOM element. Ustaw `true` do wskazania, że wartość zwracana jest element DOM w LICZBIE; w przeciwnym wypadku ustaw `false`. Jeśli `type` atrybut nie jest ustawiony i `domElement` ustawiono `true`, IntelliSense traktuje udokumentowanego wartości zwracanej jako `HTMLElement` podczas wykonywania instrukcji.  
  
 `mayBeNull`  
 Opcjonalna. Określa, czy zastosowaniu zwracać wartość można ustawić na wartość null. Ustaw `true` aby wskazać, że zwracana wartość można ustawić na wartość null; w przeciwnym razie, należy ustawić na `false`. Wartość domyślna to `false`. Ten atrybut nie jest używany przez program Visual Studio zapewnienie informacji IntelliSense.  
  
 `elementType`  
 Opcjonalna. Jeśli `type` jest `Array`, ten atrybut określa typ elementów w tablicy.  
  
 `elementInteger`  
 Opcjonalna. Jeśli `type` jest `Array` i `elementType` jest `Number`, ten atrybut określa, czy elementy w tablicy są liczbami całkowitymi. Ustaw `true` do wskazania elementów w tablicy są liczbami całkowitymi; w przeciwnym wypadku ustaw `false`. Ten atrybut nie jest używany przez program Visual Studio zapewnienie informacji IntelliSense.  
  
 `elementDomElement`  
 Opcjonalna. Ten atrybut jest przestarzała; `elementType` atrybut mają pierwszeństwo przed tego atrybutu. Jeśli `type` jest `Array`, ten atrybut określa, czy elementy w tablicy elementów DOM w LICZBIE. Ustaw `true` określić elementy są elementów DOM; w przeciwnym wypadku ustaw `false`. Jeśli `elementType` atrybut nie jest ustawiony i `elementDomElement` ustawiono `true`, IntelliSense traktuje każdy element w tablicy jako `HTMLElement` podczas wykonywania instrukcji.  
  
 `elementMayBeNull`  
 Opcjonalna. Jeśli `type` jest `Array`, określa, czy elementy w tablicy może być ustawiona na wartość null. Ustaw `true` aby wskazać, że elementy w tablicy można ustawić na wartość null; w przeciwnym razie, należy ustawić na `false`. Wartość domyślna to `false`. Ten atrybut nie jest używany przez program Visual Studio zapewnienie informacji IntelliSense.  
  
 `locid`  
 Opcjonalna. Identyfikator informacji o lokalizacji na temat wartości zwracanej. Identyfikator jest albo identyfikatorem elementu członkowskiego albo odpowiada wartości atrybutu `name` w wiązce wiadomości zdefiniowanej przez metadane OpenAjax. Identyfikator typu zależy od formatu określonego w [ \<lokalizacja >](../ide/loc-javascript.md) tagu.  
  
 `value`  
 Opcjonalna. Określa kod, który ma zostać obliczona dla użycia przez funkcję IntelliSense zamiast sam kod funkcji. Na przykład można użyć tego atrybutu, aby dostarczyć IntelliSense dla asynchronicznymi wywołaniami zwrotnymi, takich jak `Promise`. Za pomocą `value` atrybutem `<returns>` elementu może poprawić wydajność funkcji IntelliSense, pomijając wykonywania długich kodu.  
  
 `description`  
 Opcjonalna. Opis wartość zwracaną.  
  
## <a name="remarks"></a>Uwagi  
 Element `<returns>` musi być umieszczony w ciele funkcji przed wszystkimi instrukcjami.  
  
## <a name="example"></a>Przykład  
 Poniższy kod ilustruje przykład użycia elementu `<returns>`.  
  
```javascript  
function areaFunction(radiusParam)  
{  
    /// <summary>Determines the area of a circle when provided a radius parameter.</summary>  
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>  
    /// <returns type="Number">The area.</returns>  
    var areaVal;  
    areaVal = Math.PI * radiusParam * radiusParam;  
    return areaVal;  
}  
  
// The following examples use the <remarks> element with a value attribute.  
  
function getJson(complete) {   
    /// <returns value='complete("")' ></returns>  
    var r = new XMLHttpRequest();   
    // . . .   
}   
  
getJson(function (json) {   
    json.  // IntelliSense for a String object is   
           // available here.  
});  
  
function calculate(x) {  
    /// <returns value='1'/>  
}  
calculate().  // Completion list for a Number.  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Komentarze dokumentacji XML](../ide/xml-documentation-comments-javascript.md)



