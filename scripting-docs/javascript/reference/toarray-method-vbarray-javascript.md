---
title: "toArray — metoda (VBArray) (JavaScript) | Dokumentacja firmy Microsoft"
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
- toArray
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toArray method
ms.assetid: 664de44c-2039-4289-82f6-948e9d744d80
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eeee8acad04125eb942089b4d8dacef6f0f5e6fb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="toarray-method-vbarray-javascript"></a>toArray — Metoda (VBArray) (JavaScript)
Zwraca standard [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] tablicy skonwertowane z VBArray.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
safeArray.toArray( )   
```  
  
## <a name="remarks"></a>Uwagi  
 Wymagane *safeArray* odwołanie jest obiekt VBArray.  
  
 Konwersja tłumaczy wielowymiarowe VBArray na pojedynczy wymiarów [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] tablicy. Każdy wymiar kolejnych jest dołączany na końcu poprzedniego. Na przykład VBArray z trzech wymiarów i trzy elementy w każdy wymiar jest konwertowany na [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] tablicy w następujący sposób:  
  
 Załóżmy, że zawiera VBArray: (1, 2, 3), (4, 5, 6) (7, 8, 9). Po translacji [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] tablica zawiera: 1, 2, 3, 4, 5, 6, 7, 8, 9.  
  
 Obecnie nie istnieje sposób przekonwertować [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] tablicy w VBArray.  
  
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
      document.writeln("<BR>")  
   Next  
   CreateVBArray = a  
End Function  
-->  
</script>  
  
<script type="text/javascript">  
<!--  
function VBArrayTest(vbarray)  
{  
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
  
## <a name="requirements"></a>Wymagania  
 Obsługiwane w następujących trybach dokumentu: Osobliwości, Standardy programu Internet Explorer 6, Standardy programu Internet Explorer 7, Standardy programu Internet Explorer 8, Standardy programu Internet Explorer 9 i standardy programu Internet Explorer 10. Nieobsługiwane w [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplikacji. Zobacz [Informacje o wersji](../../javascript/reference/javascript-version-information.md).  
  
 **Dotyczy**: [obiektu VBArray](../../javascript/reference/vbarray-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Dimensions — metoda (VBArray)](../../javascript/reference/dimensions-method-vbarray-javascript.md)   
 [getItem — metoda (VBArray)](../../javascript/reference/getitem-method-vbarray-javascript.md)   
 [LBound — metoda (VBArray)](../../javascript/reference/lbound-method-vbarray-javascript.md)   
 [UBound — metoda (VBArray)](../../javascript/reference/ubound-method-vbarray-javascript.md)