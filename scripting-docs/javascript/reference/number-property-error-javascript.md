---
title: "Liczba właściwość (błąd) (JavaScript) | Dokumentacja firmy Microsoft"
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
- Number
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Number property
ms.assetid: 8697e20b-a2b0-4e26-85c0-ab07ddfe8281
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bbc229e7d0572e1a3dbed056b344da7ff9ce7292
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="number-property-error-javascript"></a>number — Właściwość (Błąd) (JavaScript)
Zwraca lub ustawia wartość liczbową skojarzone z określonego błędu. `Error` Obiektu właściwości domyślnej jest **numer**.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
object  
.number [= errorNumber]  
```  
  
## <a name="parameters"></a>Parametry  
 *Obiekt*  
 Wszystkie wystąpienia `Error` obiektu.  
  
 *Numer_błędu*  
 Liczba całkowita reprezentująca wystąpił błąd.  
  
## <a name="remarks"></a>Uwagi  
 Numer błędu jest wartością 32-bitową. Górny word 16-bitowych jest kod obiektu, a niższe word to kod błędu. Aby określić kod błędu, użyj `&` (bitowe i) operatora łączenia właściwość numeru z liczbą szesnastkową `0xFFFF`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład powoduje wyjątków i wyświetla kod błędu, który jest pochodną numer błędu.  
  
```JavaScript  
try  
    {  
    // Cause an error.  
    var x = y;  
    }  
catch(e)  
    {  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
  
    document.write ("Facility Code: ")  
    document.write(e.number>>16 & 0x1FFF)  
    document.write ("<br />");  
  
    document.write ("Error Message: ")  
    document.write (e.message)  
    }  
```  
  
## <a name="example"></a>Przykład  
 Poniżej przedstawiono dane wyjściowe tego kodu.  
  
```JavaScript  
Error Code: 5009  
Facility Code: 10  
Error Message: 'y' is undefined  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
 **Dotyczy**: [Error — obiekt](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Description — właściwość (błąd)](../../javascript/reference/description-property-error-javascript.md)   
 [Message — właściwość (błąd)](../../javascript/reference/message-property-error-javascript.md)   
 [name — właściwość (błąd)](../../javascript/reference/name-property-error-javascript.md)