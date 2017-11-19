---
title: "Description — właściwość (błąd) (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Description
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- error handling, error description
- Description property
- errors, description
ms.assetid: ea727f1e-2041-4400-965c-67e6d47a1ff0
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6135951fdf65698ed48b9bbacdcc55c1aac22d41
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="description-property-error-javascript"></a>description — Właściwość (Błąd) (JavaScript)
Zwraca lub ustawia ciąg opisujący skojarzone z określonego błędu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
object  
.description [= stringExpression]  
```  
  
## <a name="parameters"></a>Parametry  
 *obiekt*  
 Wymagany. Wszystkie wystąpienia `Error` obiektu.  
  
 `stringExpression`  
 Opcjonalny. Wyrażenia ciągu zawierającego opis błędu.  
  
## <a name="remarks"></a>Uwagi  
 **Opis** właściwość zawiera ciąg z komunikatem o skojarzone z określonego błędu. Aby ostrzec użytkownika wystąpił błąd, należy użyć wartości zawartych w tej właściwości.  
  
 **Opis** i **komunikat** właściwości mają te same funkcje; **opis** właściwość zapewnia zgodność z poprzednimi wersjami;  **komunikat** właściwości jest zgodny ze standardem ECMA.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie **opis** właściwości.  
  
```JavaScript  
try  
{  
// Cause an error:  
    x = y     
}  
catch(e)  
{  
// Prints "[object Error]":  
    document.write(e)  
    document.write (" ");  
// Prints 5009:  
    document.write((e.number & 0xFFFF))    
    document.write (" ");  
// Prints "'y' is undefined":  
    document.write(e.description);  
    document.write (" ");  
// Prints "'y' is undefined":  
    document.write(e.message)  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **Dotyczy**: [Error — obiekt](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Number — właściwość (błąd)](../../javascript/reference/number-property-error-javascript.md)   
 [Message — właściwość (błąd)](../../javascript/reference/message-property-error-javascript.md)   
 [name — właściwość (błąd)](../../javascript/reference/name-property-error-javascript.md)