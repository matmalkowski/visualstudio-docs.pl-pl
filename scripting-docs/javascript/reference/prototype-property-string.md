---
title: "prototype — właściwość (ciąg) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 437ce478-9c45-45f7-8952-bd71856cfcd8
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df8c6abbd64fce9172d805c2e22dee51f4fbbee4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-string"></a>prototype — Właściwość (Ciąg)
Zwraca odwołanie do prototypu dla klasy ciągu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
string.prototype  
```  
  
## <a name="remarks"></a>Uwagi  
 `string` Argument jest nazwą ciągu.  
  
 Użyj `prototype` właściwości, aby zapewnić podstawowy zestaw funkcji do klasy obiektów. Nowe wystąpienia obiektu "dziedziczy" zachowanie prototypu przypisane do tego obiektu.  
  
 Na przykład, aby dodać metodę `String` obiekt, który zwraca wartość ostatniego elementu w ciągu, zadeklarować funkcję, dodaj go do `String.prototype`, a następnie użyć go.  
  
```JavaScript  
function string_last( ){  
    return this.charAt(this.length - 1);  
}  
String.prototype.last = string_last;  
var myString = new String("every good boy does fine");  
document.write(myString.last());  
  
// Output:  
// e  
```  
  
 Wszystkie wewnętrzne [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] obiekty mają `prototype` właściwość, która jest tylko do odczytu. Właściwości i metody, które mogą być dodawane do prototyp, ale obiekt nie może być przypisany inny prototypu. Jednak obiekty zdefiniowane przez użytkownika można przypisać nowe prototypu.  
  
 Listy metod i właściwości dla każdego obiektu wewnętrznego w niniejszej dokumentacji języka wskazać te, które są częścią prototypu obiektu, a które nie są.  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]