---
title: Error — obiekt (JavaScript) | Dokumentacja firmy Microsoft
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
- Error
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Error object
ms.assetid: 0b27d6ec-3997-4e91-a6c0-5afbaf494db7
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: efc03f13a501a1a13a2e7f3eea000b406559f30b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790639"
---
# <a name="error-object-javascript"></a>Error — Obiekt (JavaScript)
Zawiera informacje o błędach.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      errorObj = new Error()  
errorObj = new Error([number])  
errorObj = new Error([number[, description]])  
```  
  
## <a name="parameters"></a>Parametry  
 `errorObj`  
 Wymagany. Nazwa zmiennej, do której `Error` obiekt jest przypisany. Przypisanie zmiennej zostanie pominięty podczas tworzenia przy użyciu błąd `throw` instrukcji.  
  
 `number`  
 Opcjonalny. Wartość liczbowa przypisana do błędu. Zero w przypadku pominięcia.  
  
 `description`  
 Opcjonalny. Krótki ciąg znakowy opisujący błąd. Pusty ciąg w przypadku pominięcia.  
  
## <a name="remarks"></a>Uwagi  
 Zawsze, gdy wystąpi błąd czasu wykonywania, wystąpienie `Error` obiekt jest tworzony do opisu błędu. To wystąpienie ma dwie właściwości wewnętrzne, które zawierają opis błędu (`description` właściwości) i kod błędu (`number` właściwości). Aby uzyskać więcej informacji, zobacz [błędy środowiska wykonawczego języka JavaScript](../../javascript/reference/javascript-run-time-errors.md).  
  
 Numer błędu jest wartością 32-bitową. Wyższe 16-bitowe słowo to kod funkcji, a niższe słowo to rzeczywisty kod błędu.  
  
 `Error`obiekty można również jawnie tworzyć, przy użyciu składni pokazanym powyżej lub zgłoszony przy użyciu `throw` instrukcji. W obu przypadkach można dodać właściwości chcesz rozszerzyć możliwości `Error` obiektu.  
  
 Zazwyczaj zmiennej lokalnej, która jest tworzona w **try... catch** odwołuje się do niejawnie tworzonych `Error` obiektu. W rezultacie można w dowolny sposób użyć numeru błędu i opisu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `Error` obiektu.  
  
```  
function checkInput(x) {  
    try  
    {  
        if (isNaN(parseInt(x))) {  
            throw new Error("Input is not a number.");  
        }  
    }  
    catch(e)  
    {  
        document.write(e.description);  
    }  
}  
  
checkInput("not a number");  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie niejawnie tworzonych `Error` obiektu.  
  
```JavaScript  
try  
   {  
   // Cause an error.  
   x = y;  
   }  
catch(e)  
   {  
      document.write(e);  
      document.write ("<br />");  
  
      document.write ("Number: ");  
      document.write (e.number & 0xFFFF);  
      document.write ("<br />");  
  
      document.write ("Facility Code: ");  
      document.write(e.number>>16 & 0x1FFF);  
      document.write ("<br />");  
  
      document.write ("Description: ");  
      document.write (e.description);  
   }  
  
// Output:  
// ReferenceError: 'y' is undefined  
// Number: 5009  
// Facility Code: 10  
// Description: 'y' is undefined  
  
```  
  
## <a name="methods"></a>Metody  
 [toString — metoda (błąd)](../../javascript/reference/tostring-method-error.md) &#124; [valueOf — metoda (Data)](../../javascript/reference/valueof-method-date.md)  
  
## <a name="properties"></a>Właściwości  
 [constructor — właściwość (błąd)](../../javascript/reference/constructor-property-error.md) &#124; [opis właściwości](../../javascript/reference/description-property-error-javascript.md) &#124; [message — właściwość](../../javascript/reference/message-property-error-javascript.md) &#124; [name — właściwość](../../javascript/reference/name-property-error-javascript.md) &#124; [number właściwości](../../javascript/reference/number-property-error-javascript.md) &#124; [prototype — właściwość (błąd)](../../javascript/reference/prototype-property-error.md) &#124; [stack — właściwość (błąd)](../../javascript/reference/stack-property-error-javascript.md) &#124; [stackTraceLimit właściwość (błąd)](../../javascript/reference/stacktracelimit-property-error-javascript.md)  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [New — Operator](../../javascript/reference/new-operator-decrementjavascript.md)   
 [throw — instrukcja](../../javascript/reference/throw-statement-javascript.md)   
 [try... catch... finally — instrukcja](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [var — instrukcja](../../javascript/reference/var-statement-javascript.md)   
 [Hilo JavaScript przykładowej aplikacji (w Sklepie Windows)](http://hilojs.codeplex.com/SourceControl/latest)