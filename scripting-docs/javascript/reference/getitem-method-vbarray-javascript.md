---
title: "getItem — metoda (VBArray) (JavaScript) | Dokumentacja firmy Microsoft"
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
- getItem
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- getItem method
- Item property
ms.assetid: f62964ad-8b2f-4596-95d0-b20e587ecea5
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6457435d047f2780a19fa8ce26fc2bb86f7ae0e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="getitem-method-vbarray-javascript"></a>getItem — Metoda (VBArray) (JavaScript)
Zwraca element w określonej lokalizacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
safeArray.getItem(dimension1[, dimension2, ...], dimensionN)   
```  
  
## <a name="parameters"></a>Parametry  
 *safeArray*  
 Wymagany. Obiekt VBArray.  
  
 *dimension1,..., dimensionN*  
 Określa dokładnej lokalizacji elementu żądanego obiektu VBArray. *n*jest równa liczbie wymiarów w VBArray.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład składa się z trzech części. Pierwsza część jest kod VBScript w celu utworzenia bezpieczną tablicą Visual Basic. Druga część to [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] kod, który iteruje po bezpiecznej tablicy Visual Basic i do drukowania zawartości każdego elementu. Oba te elementy są przekazywane do \<HEAD > części strony HTML. Trzeci części [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] kodu, który jest przesyłany w \<treści >, aby uruchomić z dwóch części.  
  
```JavaScript  
<head>  
<script type="text/vbscript">  
<!--  
Function CreateVBArray()  
   Dim i, j, k  
   Dim a(2, 2)  
   k = 1  
   For i = 0 To 2  
      For j = 0 To 2  
         a(i, j) = k  
         document.writeln(k)  
         k = k + 1  
      Next  
      document.writeln("<BR>")  
   Next  
   CreateVBArray = a  
End Function  
-->  
</script>  
<script type="text/javascript">  
<!--  
function GetItemTest(vbarray)  
{  
   var i, j;  
   var a = new VBArray(vbarray);  
   for (i = 0; i <= 2; i++)  
   {  
      for (j =0; j <= 2; j++)  
      {  
         document.writeln(a.getItem(i, j));  
      }  
   }  
}  
-->  
</script>  
</head>  
<body>  
<script type="text/javascript">  
<!--  
   GetItemTest(CreateVBArray());  
-->  
</script>  
</body>  
```  
  
## <a name="requirements"></a>Wymagania  
 Obsługiwane w następujących trybach dokumentu: Osobliwości, Standardy programu Internet Explorer 6, Standardy programu Internet Explorer 7, Standardy programu Internet Explorer 8, Standardy programu Internet Explorer 9 i standardy programu Internet Explorer 10. Nieobsługiwane w [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplikacji. Zobacz [Informacje o wersji](../../javascript/reference/javascript-version-information.md).  
  
 **Dotyczy**: [obiektu VBArray](../../javascript/reference/vbarray-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Dimensions — metoda (VBArray)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [LBound — metoda (VBArray)](../../javascript/reference/lbound-method-vbarray-javascript.md)   
 [toArray — metoda (VBArray)](../../javascript/reference/toarray-method-vbarray-javascript.md)   
 [UBound — metoda (VBArray)](../../javascript/reference/ubound-method-vbarray-javascript.md)