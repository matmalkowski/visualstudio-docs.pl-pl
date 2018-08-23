---
title: Tworzenie komentarzy JSDoc dla funkcji IntelliSense języka JavaScript | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0dadc81-3755-4a47-bcee-c1010819ff2a
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 10e5db2b81df20ab4b3002f367104fce61631faf
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42685350"
---
# <a name="create-jsdoc-comments-for-javascript-intellisense"></a>Tworzenie komentarzy JSDoc na potrzeby funkcji IntelliSense języka JavaScript
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [dokumentacja programu Visual Studio 2017](https://docs.microsoft.com/en-us/visualstudio/).  
  
Funkcja IntelliSense w programie Visual Studio Wyświetla informacje, które można dodać do skryptu, używając standardowych komentarzy JSDoc. Komentarze JSDoc służy do dostarczania informacji dotyczących elementów kodu, takich jak functions, pól i zmiennych.  
  
## <a name="jsdoc-comment-tags"></a>Tagi komentarza JSDoc  
 Następujących standardowych tagów komentarzy JSDoc są używane przez funkcję IntelliSense, aby wyświetlić informacje o swoim kodzie.  
  
|JSDoc tag|Składnia|Uwagi|  
|---------------|------------|-----------|  
|@deprecated|@deprecated *Opis elementu*|Określa zaniechanej funkcji lub metody.|  
|@description|@description *Opis elementu*|Określa opis funkcji lub metody.|  
|@param|@param {*typu*} *parameterName ** opis*|Określa informacje dla parametru w funkcji lub metody.<br /><br /> Obsługuje również TypeScript @paramTag.|  
|@property|@property {*typu*} *propertyName*|Określa informacje, w tym opis, pola lub elementu członkowskiego, który jest zdefiniowany w obiekcie.|  
|@returns|@returns {*typu*}|Określa wartość zwracaną.<br /><br /> TypeScript, można użyć @returnType zamiast @returns.|  
|@summary|@summary *Opis elementu*|Określa opis funkcji lub metody (taka sama jak @description).|  
|@type|@type {*typu*}|Określa typ stałą lub zmienną.|  
|@typedef|@typedef {*typu*} *customTypeName*|Określa typ niestandardowy.|  
  
### <a name="examples"></a>Przykłady  
 Poniższy przykład pokazuje użycie @description, @param, i @return JSDoc tagów dla funkcji o nazwie `getArea`.  
  
```javascript  
/** @description Determines the area of a circle that has the specified radius parameter.  
 * @param {number} radius The radius of the circle.  
 * @return {number}  
 */  
function getArea(radius) {  
    var areaVal;  
    areaVal = Math.PI * radius * radius;  
    return areaVal;  
}  
```  
  
 W poprzednim przykładzie, funkcja IntelliSense wyświetla opis parametru i informacje zwrotne po wpisaniu nawiasu otwierającego dla `getArea`.  
  
 ![Informacje o technologii IntelliSense dla funkcji](../ide/media/js-intellisense-jsdoc-comments.png "JS_IntelliSense_JSDoc_Comments")  
  
 Poniższy przykład pokazuje, jak używać @typedef oznaczyć za pomocą @property tagu.  
  
```javascript  
/**  
  * @typedef {object} Weather  
  * @property {string} current The current weather.  
  */  
function getForecast(Weather) {  
}  
  
var w = new Weather();  
```  
  
 Poniższy przykład pokazuje użycie @type JSDoc tagów. Jak pokazano w tym przykładzie, pojedyncza gwiazdka (*), które należy wykonać parę początkowej gwiazdki (\*\*) nie są wymagane.  
  
```javascript  
/**  
    @type {string}  
*/  
const RED = 'FF0000';  
  
```  
  
 Poniższy przykład pokazuje, jak używać @deprecated JSDoc tag.  
  
```javascript  
/**  
 * @deprecated since version 2.0  
 */  
function old() {  
}  
```



