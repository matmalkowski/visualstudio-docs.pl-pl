---
title: name — właściwość (błąd) (JavaScript) | Dokumentacja firmy Microsoft
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
- name
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Name property
- name property, error name
ms.assetid: 94df2d6b-f1a1-4931-a956-0a930cb87f76
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1a12157b4c467499fab23f7c4cb1be91e9ac5440
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791767"
---
# <a name="name-property-error-javascript"></a>name — Właściwość (Błąd) (JavaScript)
Zwraca nazwę wystąpił błąd.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
errorObj.  
name  
  
```  
  
## <a name="parameters"></a>Parametry  
 `errorObj`  
 Wymagany. Wystąpienie `Error` obiektu.  
  
## <a name="remarks"></a>Uwagi  
 **Nazwa** właściwość zwraca typ nazwy lub wyjątek błędu. Gdy wystąpi błąd wykonania, właściwość name ustawiono na jedną z następujących typów natywnych wyjątek:  
  
|Typ wyjątku|Znaczenie|  
|--------------------|-------------|  
|ConversionError|Ten błąd występuje zawsze, gdy jest próba konwersji obiektu na coś, do którego nie można przekonwertować.|  
|RangeError|Ten błąd występuje, gdy funkcja podana jest z argumentem przekroczyła jego dozwolonego zakresu. Na przykład ten błąd występuje, jeśli podjęto próbę stworzenia `Array` obiektów o długości, która nie jest prawidłową dodatnią liczbą całkowitą.|  
|ReferenceError|Ten błąd występuje, gdy wykryto nieprawidłowe odwołanie. Ten błąd wystąpi, na przykład, jeśli oczekiwane odwołanie ma `null`.|  
|RegExpError|Ten błąd występuje, gdy wystąpi błąd kompilacji z wyrażeniem regularnym. Po wyrażenie regularne jest kompilowana, jednak nie może wystąpić błąd. W tym przykładzie zostanie przeprowadzona, na przykład, gdy wyrażenie regularne jest zadeklarowane ze wzorcem ma nieprawidłową składnię lub innych niż flagi **i**, **g**, lub **m**, lub zawiera tę samą flagę więcej niż raz.|  
|SyntaxError|Ten błąd występuje, gdy zostanie przeanalizowany tekst źródłowy i tekst źródłowy nie jest zgodna z prawidłową składnię. Ten błąd wystąpi, na przykład, jeśli `eval` funkcja jest wywoływana z argumentem, który nie jest wartością tekstową prawidłowy program.|  
|TypeError|Ten błąd występuje, gdy rzeczywisty typ argumentu jest niezgodny z oczekiwanym typem. Przykładem po wystąpieniu tego błędu jest wywołanie funkcji elementu, który nie jest obiektem lub nie obsługuje tego wywołania.|  
|URIError|Ten błąd występuje, gdy zostanie wykryty niedozwolony Uniform Resource Indicator (URI). Na przykład jest to błąd występuje, gdy niedozwolony znak znajduje się w ciągu zostanie lub dekodowanym.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład powoduje, że zostanie wygenerowany wyjątek TypeError i wyświetla nazwę błędu i komunikatu.  
  
```JavaScript  
try  
{  
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
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Dotyczy**: [Error — obiekt](../../javascript/reference/error-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Description — właściwość (błąd)](../../javascript/reference/description-property-error-javascript.md)   
 [Message — właściwość (błąd)](../../javascript/reference/message-property-error-javascript.md)   
 [Number — właściwość (błąd)](../../javascript/reference/number-property-error-javascript.md)