---
title: "Kolejność wykonywania działań (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- operator precedence
- order of precedence
ms.assetid: cf3c510a-2214-4b47-b8fe-3521298efaab
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 82503a312a4a4996e3bd38f596eef3104af3f11b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="operator-precedence-javascript"></a>Kolejność wykonywania działań (JavaScript)
Kolejność wykonywania działań opisuje kolejność, w której operacje są wykonywane, gdy wyrażenie jest obliczane. Operacje o wyższym priorytecie są wykonywane przed operacjami o niższym priorytecie. Na przykład, mnożenie jest wykonywane przed dodawaniem.  
  
## <a name="includejavascriptjavascriptincludesjavascript-mdmd-operators"></a>[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] — Operatory  
 W poniższej tabeli wymieniono [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] operatory zamówić najwyższy priorytet. Operatory o tym samym priorytecie są obliczane od lewej do prawej.  
  
|Operator|Opis|  
|--------------|-----------------|  
|. [ ] ( )|Dostęp do pola, indeksowanie tablicy, wywołania funkcji i grupowanie wyrażeń|  
|++ -- - ~ ! Usuń nowe typeof void|Operatory jednoargumentowe, zwrot typu danych, tworzenie obiektu, niezdefiniowane wartości|  
|* / %|Mnożenie, dzielenie, dzielenie modulo|  
|+ - +|Dodawanie, odejmowanie, łączenie ciągów|  
|<\< >> >>>|Przesunięcie bitowe|  
|< \<= >> = instanceof|Mniejsze niż, mniejsze lub równe, większe niż, większe niż lub równe, wystąpienie|  
|== != === !==|Równość, nierówność, ścisła równość i ścisła nierówność|  
|&|Bitowe ORAZ|  
|^|Bitowe XOR|  
|&#124;|Bitowe LUB|  
|&&|AND logiczne|  
|&#124;&#124;|OR logiczne|  
|?:|Warunkowe|  
|= *OP*=|Przypisania, przypisania operacji (takich jak += i & =)|  
|,|Wielokrotne obliczenie|  
  
 Nawiasów używa się do zmiany kolejności obliczeń określonej przez priorytet operatorów. Oznacza to, że wyrażenie w nawiasach jest w pełni obliczane, zanim jego wartość zostanie użyta w pozostałej części wyrażenia.  
  
 Na przykład:  
  
```JavaScript  
var result = 78 * 96 + 3;  
document.write(result);  
document.write("<br/>");  
  
result = 78 * (9 + 3);  
document.write(result);  
  
// Output:  
// 7491  
// 936  
```  
  
 Istnieją trzy operatory w pierwszym wyrażeniu: =, * oraz +. Zgodnie z regułami kolejność wykonywania działań, są oceniane w następującej kolejności: \*, +, = (78 \* 96 = 7488, 7488 + 3 = 7491).  
  
 W drugim wyrażeniu operator ( ) jest obliczany jako pierwszy, tak aby wyrażenie dodawania było obliczone przed mnożeniem (9 + 3 = 12, 12 * 78 = 936).  
  
 W poniższym przykładzie pokazano instrukcję, która obejmuje różne operatory i jest rozpoznawana jako `true`.  
  
```JavaScript  
var num = 10;  
  
if(5 == num / 2 && (2 + 2 * num).toString() === "22") {  
    document.write(true);  
}  
    // Output:  
    // true  
```  
  
 Operatory są oceniane w następującej kolejności: () do grupowania, *, + (w ramach grupy), "." dla funkcji () dla funkcji, /, ==, ===, i & &.