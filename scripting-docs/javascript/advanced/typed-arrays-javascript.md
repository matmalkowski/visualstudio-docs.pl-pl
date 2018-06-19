---
title: Wpisane tablice (JavaScript) | Dokumentacja firmy Microsoft
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
ms.assetid: fa82c562-0ebf-4559-aecc-166e59f7fb64
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5fc3b29a4593e7c627a6e606242229e87fa5be54
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24789139"
---
# <a name="typed-arrays-javascript"></a>Tablice o określonym typie (JavaScript)
Tablice o określonym typie służy do obsługi danych binarnych ze źródeł, takich jak protokołów sieciowych, formatów pliku binarnego i buforów raw grafiki. Wpisane tablice mogą służyć do zarządzania w pamięci danych binarnych o układach dobrze znanego typu byte.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób użycia [arraybuffer — obiekt](../../javascript/reference/arraybuffer-object.md) jako odpowiedzi [XMLHttpRequest](http://msdn.microsoft.com/library/ie/ms535874\(v=vs.85\).aspx). Bajty w odpowiedzi można manipulować przy użyciu różnych metod [obiektu DataView](../../javascript/reference/dataview-object.md), lub przez skopiowanie do odpowiedniego typu tablicy bajtów.  
  
> [!TIP]
>  Aby uzyskać więcej informacji o używaniu różne typy odpowiedzi z `XmlHttpRequest`, zobacz [XMLHttpRequest.responseType](http://msdn.microsoft.com/en-us/8d7738d1-4bfd-4cf1-8015-174def089556), [ulepszenia XMLHttpRequest](http://msdn.microsoft.com/en-us/be09137c-6546-441b-b953-dcbf72b77069), i [pobierania różnych typy zawartości (aplikacje ze Sklepu Windows)](http://msdn.microsoft.com/en-us/c0006bbd-17f9-4c6a-af81-2acaf109111d).  
  
```JavaScript  
...  
<div id="xhrDiv"></div>  
...  
var name = "http://www.microsoft.com";  
var xhrDiv = document.getElementById("xhrDiv");  
  
var req = new XMLHttpRequest();  
req.open("GET", name, true);  
req.responseType = "arraybuffer";  
req.onreadystatechange = function () {  
if (req.readyState == req.DONE) {  
    var arrayResponse = req.response;  
    var dataView = new DataView(arrayResponse);  
    var ints = new Uint32Array(dataView.byteLength / 4);  
  
    xhrDiv.style.backgroundColor = "#00FF00";  
    xhrDiv.innerText = "Array is " + ints.length + "uints long";  
    }  
}  
req.send();  
```  
  
## <a name="arraybuffer"></a>ArrayBuffer  
 [Arraybuffer — obiekt](../../javascript/reference/arraybuffer-object.md) reprezentuje buforu danych pierwotnych, który jest używany do przechowywania danych dla różnych tablice o określonym typie. Nie można odczytać lub zapisać `ArrayBuffer`, ale można go przekazać do typu tablicy lub [obiektu DataView](../../javascript/reference/dataview-object.md) interpretować raw buforu. Można użyć `ArrayBuffer` do przechowywania dowolny rodzaj danych (lub mieszane typy danych).  
  
## <a name="dataview"></a>DataView  
 Można użyć [obiektu DataView](../../javascript/reference/dataview-object.md) do odczytu i zapisu do dowolnej lokalizacji w różnych rodzajów danych binarnych `ArrayBuffer`.  
  
## <a name="typed-arrays"></a>Tablice o określonym typie  
 Typy tablic typu przedstawiają widoki [arraybuffer — obiekt](../../javascript/reference/arraybuffer-object.md) czy indeksowane i wykonywać na nich operacji. Wszystkie typy tablic mają stałą długość.  
  
||||  
|-|-|-|  
|Nazwa|Rozmiar (w bajtach)|Opis|  
|[Int8array — obiekt](../../javascript/reference/int8array-object.md)|1|8 bitowych uzupełniają dwa na liczbę całkowitą ze znakiem|  
|[Uint8array — obiekt](../../javascript/reference/uint8array-object.md)|1|8 bitowej liczby całkowitej bez znaku|  
|[Int16array — obiekt](../../javascript/reference/int16array-object.md)|2|Bit szesnastu uzupełniają dwa na liczbę całkowitą ze znakiem|  
|[Uint16array — obiekt](../../javascript/reference/uint16array-object.md)|2|Szesnastu bitowej liczby całkowitej bez znaku|  
|[Int32array — obiekt](../../javascript/reference/int32array-object.md)|4|30 2 bitowych uzupełniają dwa na liczbę całkowitą ze znakiem|  
|[Uint32array — obiekt](../../javascript/reference/uint32array-object.md)|4|30 2 bitową nieznakowaną liczbą całkowitą|  
|[Float32array — obiekt](../../javascript/reference/float32array-object.md)|4|IEEE 30 2 bitowych liczba zmiennoprzecinkowa|  
|[Float64array — obiekt](../../javascript/reference/float64array-object.md)|8|IEEE sześćdziesiąt 4 bitowych liczba zmiennoprzecinkowa|