---
title: DataView — obiekt | Dokumentacja firmy Microsoft
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
ms.assetid: 250ec067-7505-4ee0-82ab-bfd3c2820afa
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 370ee1afbdf7fe1d87843c4979833d54a575a4fd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24790690"
---
# <a name="dataview-object"></a>DataView — Obiekt
Obiekt DataView umożliwia odczytywanie i zapisywanie do dowolnej lokalizacji w ArrayBuffer różne rodzaje danych binarnych.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
dataView = new DataView(buffer, byteOffset, byteLength);  
```  
  
## <a name="parameters"></a>Parametry  
 `dataView`  
 Wymagany. Nazwa zmiennej, do której **DataView** obiekt jest przypisany.  
  
 `buffer`  
 ArrayBuffer, który reprezentuje widoku danych.  
  
 `byteOffset`  
 Opcjonalny. Określa przesunięcie w bajtach od początku buforu, w którym powinny one zacząć widoku danych.  
  
 `byteLength`  
 Opcjonalny. Określa długość (w bajtach) w sekcji buforu reprezentujące widoku danych.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli zarówno byteOffset i byteLength zostaną pominięte, w widoku danych obejmuje cały zakres ArrayBuffer. W przypadku pominięcia byteLength widoku danych rozciąga się od danego byteOffset aż do zakończenia ArrayBuffer. Jeśli dany byteOffset i byteLength odwołuje się do obszaru poza koniec ArrayBuffer, wyjątek.  
  
## <a name="properties"></a>Właściwości  
 W poniższej tabeli wymieniono właściwości `DataView` obiektu.  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|[Właściwość Buffer](../../javascript/reference/buffer-property-dataview.md)|Tylko do odczytu. Pobiera ArrayBuffer, do której odwołuje się ten widok.|  
|[byteLength właściwość](../../javascript/reference/bytelength-property-dataview.md)|Tylko do odczytu. Długość tego widoku od początku jego buforu ArrayBuffer, w bajtach, ustalona podczas tworzenia.|  
|[byteOffset właściwość](../../javascript/reference/byteoffset-property-dataview.md)|Tylko do odczytu. Przesunięcie od początku jego ArrayBuffer w bajtach, jak określono w czasie tworzenia widoku.|  
  
## <a name="methods"></a>Metody  
 W poniższej tabeli przedstawiono metody `DataView`obiektu.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[getInt8 — metoda](../../javascript/reference/getint8-method-dataview.md)|Pobiera wartość Int8 na określone przesunięcie bajtów od początku widoku.|  
|[getUint8 — metoda (DataView)](../../javascript/reference/getuint8-method-dataview.md)|Pobiera wartość Uint8 na określone przesunięcie bajtów od początku widoku.|  
|[getInt16 — metoda (DataView)](../../javascript/reference/getint16-method-dataview.md)|Pobiera wartość Int16 na określone przesunięcie bajtów od początku widoku.|  
|[getUint16 — metoda (DataView)](../../javascript/reference/getuint16-method-dataview.md)|Pobiera wartość Uint16 na określone przesunięcie bajtów od początku widoku.|  
|[getInt32 — metoda (DataView)](../../javascript/reference/getint32-method-dataview.md)|Pobiera wartość Int32 na określone przesunięcie bajtów od początku widoku.|  
|[getUint32 — metoda (DataView)](../../javascript/reference/getuint32-method-dataview.md)|Pobiera wartość Uint32 na określone przesunięcie bajtów od początku widoku.|  
|[getFloat32 — metoda (DataView)](../../javascript/reference/getfloat32-method-dataview.md)|Pobiera wartość Float32 na określone przesunięcie bajtów od początku widoku.|  
|[getFloat64 — metoda (DataView)](../../javascript/reference/getfloat64-method-dataview.md)|Pobiera wartość Float64 na określone przesunięcie bajtów od początku widoku.|  
|[setInt8 — metoda (DataView)](../../javascript/reference/setint8-method-dataview.md)|Przechowuje wartość Int8 na określone przesunięcie bajtów od początku widoku.|  
|[setUint8 — metoda (DataView)](../../javascript/reference/setuint8-method-dataview.md)|Przechowuje wartość Uint8 na określone przesunięcie bajtów od początku widoku.|  
|[setInt16 — metoda (DataView)](../../javascript/reference/setint16-method-dataview.md)|Przechowuje wartość Int16 na określone przesunięcie bajtów od początku widoku.|  
|[setUint16 — metoda (DataView)](../../javascript/reference/setuint16-method-dataview.md)|Przechowuje wartość Uint16 na określone przesunięcie bajtów od początku widoku.|  
|[setInt32 — metoda (DataView)](../../javascript/reference/setint32-method-dataview.md)|Przechowuje wartość Int32 na określone przesunięcie bajtów od początku widoku.|  
|[setUint32 — metoda (DataView)](../../javascript/reference/setuint32-method-dataview.md)|Przechowuje wartość Uint32 na określone przesunięcie bajtów od początku widoku.|  
|[setFloat32 — metoda (DataView)](../../javascript/reference/setfloat32-method-dataview.md)|Przechowuje wartość Float32 na określone przesunięcie bajtów od początku widoku.|  
|[setFloat64 — metoda (DataView)](../../javascript/reference/setfloat64-method-dataview.md)|Przechowuje wartość Float64 na określone przesunięcie bajtów od początku widoku.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób użycia obiektu DataView do przetwarzania danych binarnych z XmlHttpRequest:  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var ints = new Int32Array(dataView.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Wymagania  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]