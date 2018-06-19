---
title: constructor — właściwość (obiekt) (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- constructor
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- constructor property
ms.assetid: 6f5d0e9d-e85f-4fde-b558-744510483d69
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 569dab69906aa167ef486923bd7ceb7455ac243e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790387"
---
# <a name="constructor-property-object-javascript"></a>constructor — Właściwość (Obiekt) (JavaScript)
Określa funkcję, która tworzy obiekt.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
object.constructor  
```  
  
## <a name="remarks"></a>Uwagi  
 Wymagane `object` to nazwa obiektu lub funkcji.  
  
 `constructor` Właściwości jest elementem członkowskim prototypu każdy obiekt, który ma prototypu. Dotyczy to również wszystkich wewnętrzne [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] obiekty z wyjątkiem `Global` i `Math` obiektów. `constructor` Właściwość zawiera odwołanie do funkcji, która tworzy wystąpienie określonego obiektu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie właściwości konstruktora.  
  
```JavaScript  
// A constructor function.  
function MyObj() {  
    this.number = 1;  
}  
  
var x = new String("Hi");  
  
if (x.constructor == String)  
    document.write("Object is a String.");  
document.write ("<br />");  
  
var y = new MyObj;  
if (y.constructor == MyObj)  
    document.write("Object constructor is MyObj.");  
  
// Output:  
// Object is a String.  
// Object constructor is MyObj.  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [prototype — właściwość (obiekt)](../../javascript/reference/prototype-property-object-javascript.md)