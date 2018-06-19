---
title: UBound — metoda (VBArray) (JavaScript) | Dokumentacja firmy Microsoft
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
- ubound
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- ubound method
ms.assetid: 761811c5-9a3d-4cb3-bfe0-0a8749f34496
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dfb87cf3fd552c329635a3ca3e974c84a1324bfd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791983"
---
# <a name="ubound-method-vbarray-javascript"></a>ubound — Metoda (VBArray) (JavaScript)
Zwraca największą wartość indeksu używane w określonym wymiarze VBArray.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
safeArray.ubound(dimension)   
```  
  
## <a name="parameters"></a>Parametry  
 *safeArray*  
 Wymagany. Obiekt VBArray.  
  
 `dimension`  
 Opcjonalny. Wymiar VBArray, dla której wyznaczony wyższej powiązanej indeksu. Pominięcie `ubound` zachowuje się tak, jakby został przekazany przez wartość 1.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli VBArray jest pusta, `ubound` metoda zwraca niezdefiniowany. Jeśli `dim` jest większa niż liczba wymiarów w VBArray lub jest ujemna, z nich metoda generuje błąd "Indeks dolny spoza zakresu".  
  
## <a name="example"></a>Przykład  
 Poniższy przykład składa się z trzech części. Pierwsza część jest kod VBScript w celu utworzenia bezpieczną tablicą Visual Basic. Druga część to [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] kod, który określa liczbę wymiarów tablicy bezpieczne i górną granicę każdego wymiaru. Oba te elementy są przekazywane do \<HEAD > części strony HTML. Trzeci części [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] kodu, który jest przesyłany w \<treści >, aby uruchomić z dwóch części.  
  
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
         a(j, i) = k  
         k = k + 1  
      Next  
   Next  
   CreateVBArray = a  
End Function  
-->  
</script>  
  
<script type="text/javascript">  
<!--  
function VBArrayTest(vba)  
{  
   var i;  
   var a = new VBArray(vba);  
   var s = "";  
   for (i = 1; i <= a.dimensions(); i++)  
   {  
      s += "The upper bound of dimension ";  
      s += i + " is ";  
      s += a.ubound(i);  
      s += ".<br />";  
   }  
   return (s);  
}  
-->  
</script>  
</head>  
  
<body>  
<script type="text/javascript">  
   document.write(VBArrayTest(CreateVBArray()));  
</script>  
</body>  
```  
  
## <a name="requirements"></a>Wymagania  
 Obsługiwane w następujących trybach dokumentu: Osobliwości, Standardy programu Internet Explorer 6, Standardy programu Internet Explorer 7, Standardy programu Internet Explorer 8, Standardy programu Internet Explorer 9 i standardy programu Internet Explorer 10. Nieobsługiwane w [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplikacji. Zobacz [Informacje o wersji](../../javascript/reference/javascript-version-information.md).  
  
 **Dotyczy**: [obiektu VBArray](../../javascript/reference/vbarray-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Dimensions — metoda (VBArray)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [getItem — metoda (VBArray)](../../javascript/reference/getitem-method-vbarray-javascript.md)   
 [LBound — metoda (VBArray)](../../javascript/reference/lbound-method-vbarray-javascript.md)   
 [toArray — metoda (VBArray)](../../javascript/reference/toarray-method-vbarray-javascript.md)