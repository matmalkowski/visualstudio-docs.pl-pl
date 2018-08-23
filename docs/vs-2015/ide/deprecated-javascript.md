---
title: '&lt;przestarzałe&gt; (JavaScript) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cf33d371-59da-4310-95ee-d7524fd9d58c
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9d62067b8bd888c40a8cbc0f67d209760d487cf5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681810"
---
# <a name="ltdeprecatedgt-javascript"></a>&lt;przestarzałe&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [dokumentacja programu Visual Studio 2017](https://docs.microsoft.com/en-us/visualstudio/).  
  
Określa zaniechanej funkcji lub metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
<deprecated  
    type="deprecate|remove"  
    locid="descriptionID">description  
</deprecated>  
```  
  
#### <a name="parameters"></a>Parametry  
 `type`  
 Opcjonalna. Określa, czy funkcja lub metoda zostanie usunięta w przyszłej wersji lub tego, czy funkcja lub metoda już została usunięta, a jej użycie może spowodować wystąpienie błędu. Ustaw `deprecate` do określenia, czy funkcja lub metoda zostanie usunięta w przyszłej wersji. Ustaw `remove` do określenia, czy funkcja lub metoda już została usunięta.  
  
 `locid`  
 Opcjonalna. Identyfikator informacji o lokalizacji na temat funkcji lub metody. Identyfikator jest albo identyfikatorem elementu członkowskiego albo odpowiada wartości atrybutu `name` w wiązce wiadomości zdefiniowanej przez metadane OpenAjax. Identyfikator typu zależy od formatu określonego w [ \<lokalizacja >](../ide/loc-javascript.md) elementu.  
  
 `description`  
 Opcjonalna. Opis funkcji lub metody, która jest on przestarzały.  
  
## <a name="remarks"></a>Uwagi  
 Elementy adnotować funkcje, które obejmują `<deprecated>`, musi być umieszczony w ciele funkcji przed wszystkimi instrukcjami. Gdy funkcja zostanie oznaczony jako przestarzały, zaleca się, zastąp jego [ \<podsumowania >](../ide/summary-javascript.md) element z `<deprecated>` elementu.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób użycia `<deprecated>` elementu.  
  
```javascript  
function areaFunction(radiusParam) {  
    /// <deprecated type="deprecate" >Determines the area of a circle when supplied a radius parameter.</deprecated>  
    /// <param name="radiusParam" type="Number">The radius of the circle.</param>  
    /// <returns type="Number">The area.</returns>  
    var areaVal;  
    areaVal = Math.PI * radiusParam * radiusParam;  
    return areaVal;  
}  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Komentarze dokumentacji XML](../ide/xml-documentation-comments-javascript.md)



