---
title: "toString — metoda (obiekt) (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toString
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: ToString method
ms.assetid: c4ae9da2-60c9-486f-b00a-9df03fda4a35
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 518f988486bb527220884052768e61d099dbd716
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="tostring-method-object-javascript"></a>toString — Metoda (Obiekt) (JavaScript)
Zwraca reprezentację ciągu obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
objectname.toString([radix])  
```  
  
## <a name="parameters"></a>Parametry  
 `objectname`  
 Wymagany. Obiekt, dla którego ma być uzyskane reprezentacji w postaci ciągu.  
  
 `radix`  
 Opcjonalny. Określa podstawa dla konwertowanie na ciągi wartości liczbowych. Ta wartość jest używana tylko w przypadku numerów.  
  
## <a name="remarks"></a>Uwagi  
 **ToString** metody jest członkiem wszystkich wbudowanych [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] obiektów. Jak działa zależy od typu obiektu:  
  
|Obiekt|Zachowanie|  
|------------|--------------|  
|Tablica|Elementy `Array` są konwertowane na ciągi. Są połączone wynikowy ciągów rozdzielonych przecinkami.|  
|Boolean|Jeśli jest wartość logiczna **true**, zwraca "`true`". W przeciwnym razie zwraca wartość "`false`".|  
|Data|Zwraca tekstową reprezentację wartości daty.|  
|Błąd|Zwraca ciąg zawierający powiązane komunikaty o błędach.|  
|Funkcja|Zwraca ciąg następującą postać gdzie *functionname* jest nazwą funkcji, których **toString** wywołano metodę:<br /><br /> `function functionname( ) { [native code] }`|  
|Wartość liczbowa|Zwraca tekstową reprezentację liczby.|  
|String|Zwraca wartość `String` obiektu.|  
|Domyślny|Zwraca `"[object objectname]"`, gdzie `objectname` jest nazwą typu obiektu.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie **toString** metody z argumentem podstawę systemu liczbowego. Wartość zwracana funkcji pokazano poniżej znajduje się tabela podstawa konwersji.  
  
```JavaScript  
function CreateRadixTable (){  
   var s = "";  
  
   // Create table heading.  
   s += "Hex  Dec  Bin \n";  
  
   for (x = 0; x < 16; x++)  
   {  
      s += "   ";  
  
      // Convert to hexidecimal.  
      s += x.toString(16);  
      s += "     ";  
      if (x < 10) s += "  ";  
  
      // Convert to decimal.  
      s += x.toString(10);  
      s += "     ";  
  
      // Convert to binary.  
      s += x.toString(2);  
      s += "\n";  
   }  
  
   return(s);  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 **Ma zastosowanie do**: [obiekt Array](../../javascript/reference/array-object-javascript.md)&#124; [Boolean — obiekt](../../javascript/reference/boolean-object-javascript.md)&#124; [Data obiektu](../../javascript/reference/date-object-javascript.md)&#124; [Obiektu error](../../javascript/reference/error-object-javascript.md)&#124; [Funkcji obiektu](../../javascript/reference/function-object-javascript.md)&#124; [Number obiektu](../../javascript/reference/number-object-javascript.md)&#124; [Obiekt obiektu](../../javascript/reference/object-object-javascript.md)&#124; [Ciągu obiektu](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Function — instrukcja](../../javascript/reference/function-statement-javascript.md)