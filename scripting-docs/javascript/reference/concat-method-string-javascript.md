---
title: "Metoda concat (ciąg) (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- concat
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- concat method (String)
- Concat method
ms.assetid: 5d28ebb2-d534-4179-9297-a4c821ee9f24
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b6419cc6404e06fc780802a30a3b4add8320881
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="concat-method-string-javascript"></a>concat — Metoda (Ciąg) (JavaScript)
Zwraca ciąg zawierający łączenia dwóch lub więcej ciągów.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
string1. concat([string2[, string3[, . . . [, stringN]]]])  
```  
  
## <a name="parameters"></a>Parametry  
 `string1`  
 Wymagany. `String` Obiektu lub literału ciągu na której wszystkie inne określone parametry są łączone.  
  
 `string2,. . ., stringN`  
 Opcjonalny. Ciągi, które mają zostać dołączone do końca `string1`.  
  
## <a name="remarks"></a>Uwagi  
 Wynik `concat` metoda jest odpowiednikiem: `result`  =  `string1`  +  `string2`  +  `string3`  +  `stringN`. Zmień wartości w ciągu źródłowego lub wynik nie ma wpływu na wartość w innym ciągu. Jeśli dowolny argument nie są ciągami, najpierw są konwertowane na ciągi przed jest połączony do `string1`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `concat` metody, gdy jest używany z ciągiem:  
  
```JavaScript  
var str1 = "ABCD"  
var str2 = "EFGH";  
var str3 = "1234";  
var str4 = "5678";  
document.write(str1.concat(str2, str3, str4));  
  
// Output: "ABCDEFGH12345678"  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Dotyczy**: [ciągu obiektu](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Operator dodawania (+)](../../javascript/reference/addition-operator-decrement-javascript.md)