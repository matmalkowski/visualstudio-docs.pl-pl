---
title: Ciągi szablonu (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f2e525a5-b0fc-49c3-95a0-641788e5c12a
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7b6aa430fd4f958c5519093b85d399060b6031a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788785"
---
# <a name="template-strings-javascript"></a>Ciągi szablonu (JavaScript)
W [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)], można utworzyć literałów ciągu zawierających wyrażenia osadzone ciągi szablonu. Ciągi szablonu stanowią Ponadto wbudowana obsługa ciągi wiele wierszy.  
  
 Aby skonstruować ciąg szablonu, użyj akcent (nazywanych również znaczników wstecz) ('), aby załączyć ciągu zamiast pojedynczym lub podwójnym cudzysłowie. Poniższy przykład kodu pokazuje ciąg prostego szablonu.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 Ciągi szablonu może zawierać podziałów wierszy bez konieczności użycia znaku wysuwu wiersza (\n).  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 Znak $ służy do określania symbole zastępcze w ciągu szablonu. Składnia jest ${*wyrażenie*}, gdzie *wyrażenie* jest dowolne wyrażenie JavaScript, takich jak zmienną lub funkcję, jak pokazano w poniższym przykładzie.  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
 Oznakowane szablonu funkcji, które umożliwiają zmodyfikowanie wartości ciągu szablonu przy użyciu funkcji, które jest wywoływane przy użyciu argumentów z ciąg szablonu. Pierwszy argument jest tablicą literałów ciągu, rozdzielone wyrażenia parametrów szablonu, zawartych w niej i drugi argument jest tablicą ( [parametru Rest](../../javascript/functions-javascript.md)) zawierający wartości wyrażenia parametrów szablonu.  
  
 W poniższym przykładzie funkcja szablonu oznakowanych buildURL jest używana do konstruowania adresu URL. Składnia jest do użycia natychmiast następuje ciąg szablonu nazwy funkcji.  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
 Aby uzyskać dostęp do wartości nieprzetworzony ciąg przekazany pierwszy argument przekazany do obsługuje funkcja szablonu oznakowanych `raw` właściwości, która zwraca formularza nieprzetworzony ciąg ciągów przekazana.  
  
```  
function buildURL(strArray, ...valArray) {  
    console.log(strArray.raw);  
}  
  
var lang = "en-us";  
var a = "library";  
var b = "dn771551.aspx";  
  
// Call the tagged template function.  
var url = buildURL`http://msdn.microsoft.com/${lang}/${a}/${b}`;  
  
// Ouput:  
// http://msdn.microsoft.com/  
// /  
// en-us  
// library  
```  
  
> [!NOTE]
>  Można również użyć [String.RAW —](../../javascript/reference/string-raw-function-javascript.md) funkcja zwracająca nieprzetworzony ciąg formę ciąg szablonu.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka JavaScript](../../javascript/javascript-language-reference.md)   
 [Zaawansowane JavaScript](../../javascript/advanced/advanced-javascript.md)