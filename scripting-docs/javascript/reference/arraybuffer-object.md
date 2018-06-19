---
title: Arraybuffer — obiekt | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 9fda1261-f450-493b-b3db-ecfa9ca93cd7
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c253d63d12a4a5e71d1661aae560b74debecdd62
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24789238"
---
# <a name="arraybuffer-object"></a>ArrayBuffer — Obiekt
Reprezentuje nieprzetworzone buforu danych binarnych, który jest używany do przechowywania danych dla różnych tablice o określonym typie. `ArrayBuffers`Nie można odczytać lub zapisywane bezpośrednio, ale mogą zostać przekazane do typu tablicy lub [obiektu DataView](../../javascript/reference/dataview-object.md) interpretować raw buforu, zgodnie z potrzebami.  
  
 Aby uzyskać więcej informacji na temat tablice o określonym typie, zobacz [wpisane tablice](../../javascript/advanced/typed-arrays-javascript.md).  
  
## <a name="syntax"></a>Składnia  
  
```JavaScript  
  
arrayBuffer = new ArrayBuffer(length);  
```  
  
## <a name="parameters"></a>Parametry  
 `arrayBuffer`  
 Wymagany. Nazwa zmiennej, do której `ArrayBuffer` obiekt jest przypisany.  
  
 `length`  
 Długość buforu. Zawartość ArrayBuffer są inicjowane na 0. Jeśli żądanej liczby bajtów nie można przydzielić, zgłaszany jest wyjątek.  
  
## <a name="properties"></a>Właściwości  
 W poniższej tabeli wymieniono właściwości `ArrayBuffer` obiektu.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|[byteLength właściwość](../../javascript/reference/bytelength-property-arraybuffer.md)|Tylko do odczytu. Długość ArrayBuffer (w bajtach).|  
  
## <a name="functions"></a>Funkcje  
 W poniższej tabeli wymieniono funkcje `ArrayBuffer` obiektu.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|[Funkcja ArrayBuffer.isView](../../javascript/reference/arraybuffer-isview-function-arraybuffer.md)|Określa, czy obiekt zawiera widok buforu.|  
  
## <a name="methods"></a>Metody  
 W poniższej tabeli przedstawiono metody `ArrayBuffer` obiektu.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|[Slice — metoda](../../javascript/reference/slice-method-arraybuffer.md)|Zwraca część `ArrayBuffer`.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia do przetwarzania danych binarnych z obiektu ArrayBuffer [XMLHttpRequest](http://msdn.microsoft.com/library/ie/ms535874\(v=vs.85\).aspx). Można użyć [obiektu DataView](../../javascript/reference/dataview-object.md) uzyskać poszczególnych wartości.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Int32Array(buffer.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji o korzystaniu z `XmlHttpRequest`, zobacz [ulepszenia XMLHttpRequest](http://msdn.microsoft.com/en-us/be09137c-6546-441b-b953-dcbf72b77069).  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]