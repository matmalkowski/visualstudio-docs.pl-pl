---
title: in — Operator (JavaScript) | Dokumentacja firmy Microsoft
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
- in_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- in operator
ms.assetid: dcd8f901-96b8-4c91-848b-b1ec0ab1c11c
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eefcd4c53d2e3366a26f0d8dfb099f59038507ae
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790744"
---
# <a name="in-operator-javascript"></a>in — Operator (JavaScript)
Testy istnienia właściwości w obiekcie.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
result = property in object  
```  
  
## <a name="parameters"></a>Parametry  
 `result`  
 Wymagany. Dowolnej zmiennej.  
  
 `property`  
 Wymagany. Wyrażenie, którego wynikiem jest wyrażenie ciągu.  
  
 `object`  
 Wymagany. Dowolny obiekt.  
  
## <a name="remarks"></a>Uwagi  
 `in` Operator określa, czy obiekt nie ma właściwości o nazwie `property`. Określa również, czy właściwość jest częścią łańcucha prototypu obiektu. Aby uzyskać więcej informacji na temat obiektu prototypy zobacz [prototypy i dziedziczenie](../../javascript/advanced/prototypes-and-prototype-inheritance.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `in` operator:  
  
```JavaScript  
// Create an object that has some properties.  
var myObject = new Object();  
myObject.name = "James";  
myObject.age = "22";  
myObject.phone = "555 0234";  
  
if ("phone" in myObject)  
   document.write ("property is present");  
else  
   document.write ("property is not present");  
  
// Output: property is present  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kolejność wykonywania działań](../../javascript/operator-subtractprecedence-javascript.md)   
 [Podsumowanie dla operatorów (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)