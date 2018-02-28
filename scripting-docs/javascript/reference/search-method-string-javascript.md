---
title: "Search — metoda (ciąg) (JavaScript) | Dokumentacja firmy Microsoft"
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
- search
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- search method
ms.assetid: 1cae0fbc-3319-4327-ba4e-d5fa2c4a9ba0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 730fb1604147b56fc5ab1e312bf7a6dfb5487a5a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="search-method-string-javascript"></a>search — Metoda (Ciąg) (JavaScript)
Znajduje pierwsze dopasowanie podciąg podczas wyszukiwania wyrażenia regularnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
stringObj.search(rgExp)   
```  
  
## <a name="parameters"></a>Parametry  
 `stringObj`  
 Wymagany. `String` Obiektu lub na którym należy wykonać wyszukiwanie literału ciągu.  
  
 `rgExp`  
 Wymagany. Wystąpienie **wyrażenia regularnego** obiektu zawierającego odpowiednie flagi i wzorzec wyrażenia regularnego.  
  
## <a name="return-value"></a>Wartość zwracana  
 W przypadku odnalezienia pasującego **wyszukiwania** metoda zwraca wartość całkowitą, która wskazuje przesunięcie od początku ciągu których wystąpiła pierwsze dopasowanie. Jeśli nie znaleziono, zwraca -1.  
  
## <a name="remarks"></a>Uwagi  
 Można również ustawić `i` Flaga, która powoduje, że wyszukiwanie zakończyło się bez uwzględniania wielkości liter.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie **wyszukiwania** metody.  
  
```JavaScript  
var src = "is but a Dream within a dream";  
var re = /dream/;  
var pos = src.search(re);  
document.write(pos);  
document.write("<br/>");  
  
re = /dream/i;  
pos = src.search(re);  
document.write(pos);  
  
// Output:   
// 24   
// 9  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Dotyczy**: [ciągu obiektu](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [exec — metoda (wyrażenie regularne)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [Match — metoda (ciąg)](../../javascript/reference/match-method-string-javascript.md)   
 [Obiekt będący wyrażeniem regularnym](../../javascript/reference/regular-expression-object-javascript.md)   
 [Składnia wyrażeń regularnych (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [replace — metoda (ciąg)](../../javascript/reference/replace-method-string-javascript.md)   
 [Test — metoda (wyrażenie regularne)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Programowanie wyrażeniem regularnym (JavaScript)](http://msdn.microsoft.com/en-us/3b62e27c-4f07-4726-a95b-6e841807bfaf)