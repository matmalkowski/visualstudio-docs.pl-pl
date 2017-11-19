---
title: "VBArray — obiekt (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: VBArray
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: VBArray object constant
ms.assetid: f0b767f1-ea8a-4726-962b-2708d4742518
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b86e261a0cef445f1e0e0ecd651d5eb283cffce1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="vbarray-object-javascript"></a>VBArray — Obiekt (JavaScript)
Zapewnia dostęp do macierzy bezpieczne Visual Basic.  
  
> [!WARNING]
>  Ten obiekt jest obsługiwany w programie Internet Explorer, nie [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
varName = new VBArray(safeArray)   
```  
  
## <a name="parameters"></a>Parametry  
 `varName`  
 Wymagany. Nazwa zmiennej, do której przypisano VBArray.  
  
 *safeArray*  
 Wymagany. Wartość VBArray.  
  
## <a name="remarks"></a>Uwagi  
 VBArrays są tylko do odczytu i nie można utworzyć bezpośrednio. *SafeArray* argumentu musi uzyskać wartość VBArray przed przesłaniem do konstruktora VBArray. To jest możliwe tylko przez pobieranie wartości z istniejących ActiveX lub innego obiektu.  
  
 VBArrays ma wiele wymiarów. Indeksy każdego wymiaru mogą być różne. **Wymiarów** metoda pobiera liczbę wymiarów tablicy; `lbound` i `ubound` metody pobrać zakres indeksy używane przez każdego wymiaru.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład składa się z trzech części. Pierwsza część jest kod VBScript w celu utworzenia bezpieczną tablicą Visual Basic. Druga część to [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] kod, który konwertuje Visual Basic bezpiecznej tablicy, tak aby [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] tablicy. Oba te elementy są przekazywane do \<HEAD > części strony HTML. Trzeci części [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] kodu, który jest przesyłany w \<treści >, aby uruchomić z dwóch części.  
  
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
         document.writeln(k)  
         k = k + 1  
      Next  
      document.writeln("<br />")  
   Next  
   CreateVBArray = a  
End Function  
-->  
</script>  
  
<script type="text/javascript">  
<!--  
function VBArrayTest(vbarray){  
   var a = new VBArray(vbarray);  
   var b = a.toArray();  
   var i;  
   for (i = 0; i < 9; i++)   
   {  
      document.writeln(b[i]);  
   }  
}  
-->  
</script>  
</head>  
  
<body>  
<script type="text/javascript">  
<!--  
   VBArrayTest(CreateVBArray());  
-->  
</script>  
</body>  
```  
  
## <a name="properties"></a>Właściwości  
 `VBArray` Obiekt nie ma właściwości.  
  
## <a name="methods"></a>Metody  
 [Dimensions — metoda](../../javascript/reference/dimensions-method-vbarray-javascript.md) &#124; [getItem — metoda](../../javascript/reference/getitem-method-vbarray-javascript.md) &#124; [lbound — metoda](../../javascript/reference/lbound-method-vbarray-javascript.md) &#124; [toArray — metoda](../../javascript/reference/toarray-method-vbarray-javascript.md) &#124; [ubound — metoda](../../javascript/reference/ubound-method-vbarray-javascript.md)  
  
## <a name="requirements"></a>Wymagania  
 Obsługiwane w następujących trybach dokumentu: Osobliwości, Standardy programu Internet Explorer 6, Standardy programu Internet Explorer 7, Standardy programu Internet Explorer 8, Standardy programu Internet Explorer 9 i standardy programu Internet Explorer 10. Nieobsługiwane w [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplikacji. Zobacz [Informacje o wersji](../../javascript/reference/javascript-version-information.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Array — obiekt](../../javascript/reference/array-object-javascript.md)