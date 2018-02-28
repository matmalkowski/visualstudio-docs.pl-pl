---
title: "Message — właściwość (błąd) (JavaScript) | Dokumentacja firmy Microsoft"
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
- message
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Message property
ms.assetid: 8cab0392-e0db-4714-827c-47ab04e8b4f2
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9dbd2db6c6d31dc48d90c3b07d2388eacf73ae7a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="message-property-error-javascript"></a>message — Właściwość (Błąd) (JavaScript)
Zwraca ciąg z komunikatem o.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
errorObj.message  
```  
  
## <a name="parameters"></a>Parametry  
 `errorObj`  
 Wymagany. Wystąpienie `Error` obiektu.  
  
## <a name="remarks"></a>Uwagi  
 `message` Właściwość zwraca ciąg zawierający komunikat o błędzie skojarzony z określonego błędu.  
  
 `description` i `message` właściwości mają te same funkcje. `description` Właściwości wstecz zapewnia zgodność; `message` właściwości jest zgodny ze standardem ECMA.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład powoduje, że zostanie wygenerowany wyjątek TypeError i wyświetla nazwę błędu i komunikatu.  
  
```JavaScript  
try  
{  
    // Cause an error.  
    var x = y;  
}  
catch(e)  
{  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
```  
  
## <a name="example"></a>Przykład  
 Poniżej przedstawiono dane wyjściowe tego kodu.  
  
```JavaScript  
Error Message: 'y' is undefined  
Error Code: 5009  
Error Name: TypeError  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **Dotyczy**: [Error — obiekt](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Description — właściwość (błąd)](../../javascript/reference/description-property-error-javascript.md)   
 [name — właściwość (błąd)](../../javascript/reference/name-property-error-javascript.md)