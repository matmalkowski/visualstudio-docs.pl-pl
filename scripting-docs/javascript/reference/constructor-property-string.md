---
title: "constructor — właściwość (ciąg) | Dokumentacja firmy Microsoft"
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
ms.assetid: ef0e9c82-4651-4404-87b1-d00cad38c6f9
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7f1942073a9950a77c7e0cae759a9653318d8a18
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="constructor-property-string"></a>constructor — Właściwość (Ciąg)
Określa funkcję, która tworzy ciąg.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
string.constructor  
```  
  
## <a name="remarks"></a>Uwagi  
 Wymagane `string` jest nazwą ciągu.  
  
 `constructor` Właściwości jest elementem członkowskim prototypu każdy obiekt, który ma prototypu. Dotyczy to również wszystkich wewnętrzne [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] obiekty z wyjątkiem `Global` i `Math` obiektów. `constructor` Właściwość zawiera odwołanie do funkcji, która tworzy wystąpienie określonego obiektu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie właściwości konstruktora.  
  
```JavaScript  
var x = new String();  
  
if (x.constructor == String)  
    document.write("Object is a String.");  
else  
    document.write("Object is not a String.");  
  
// Output:  
// Object is a String.  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]