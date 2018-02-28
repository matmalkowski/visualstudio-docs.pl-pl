---
title: "Enumerator — obiekt (JavaScript) | Dokumentacja firmy Microsoft"
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
- Enumerator
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Enumerator object
ms.assetid: 63f03c21-d58c-47db-a728-4d8d88b0a422
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 50b1ebfb6e24ed734f008b3c05f10a1687c4aff5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="enumerator-object-javascript"></a>Enumerator — Obiekt (JavaScript)
Umożliwia wyliczenie elementów w kolekcji.  
  
> [!WARNING]
>  Ten obiekt jest obsługiwany w programie Internet Explorer, nie [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
enumObj = new Enumerator([collection])   
```  
  
## <a name="parameters"></a>Parametry  
 `enumObj`  
 Wymagany. Nazwa zmiennej, do której `Enumerator` obiekt jest przypisany.  
  
 `collection`  
 Opcjonalny. Dowolny obiekt kolekcji.  
  
## <a name="remarks"></a>Uwagi  
 Kolekcje różnią się od tablice elementów członkowskich kolekcji nie ma bezpośredniego połączenia. Zamiast używać indeksów, jak w przypadku tablic, można przenieść bieżący wskaźnik elementu tylko do pierwszego lub następnego elementu kolekcji.  
  
 `Enumerator` Obiektu umożliwia dostęp do członków kolekcji i działa podobnie do `For...Each` instrukcji w języku VBScript.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia użycie `Enumerator` obiektu:  
  
```JavaScript  
var bytesPerGB = 1024 * 1024 * 1024;  
  
var fso = new ActiveXObject("Scripting.FileSystemObject");  
  
document.write(fso.Drives);  
var e = new Enumerator(fso.Drives);  
  
var driveString = "";  
  
e.moveFirst();  
while (e.atEnd() == false)  
{  
    var drv = e.item();  
  
    driveString += drv.Path + " - ";  
  
    if (drv.IsReady){  
        var freeGB = drv.FreeSpace / bytesPerGB;  
        var totalGB = drv.TotalSize / bytesPerGB;  
  
        driveString += freeGB.toFixed(3) + " GB free of ";  
        driveString += totalGB.toFixed(3) + " GB";  
    }  
    else{  
        driveString += "Not Ready";  
    }  
  
    driveString += "<br />";;  
  
    e.moveNext();  
}  
document.write(driveString);  
  
// Output: <drive information  
  
```  
  
## <a name="properties"></a>Właściwości  
 `Enumerator` Obiekt nie ma właściwości.  
  
## <a name="methods"></a>Metody  
 [atEnd — metoda](../../javascript/reference/atend-method-enumerator-javascript.md) &#124; [elementu metody](../../javascript/reference/item-method-enumerator-javascript.md) &#124; [moveFirst — metoda](../../javascript/reference/movefirst-method-enumerator-javascript.md) &#124; [moveNext — metoda](../../javascript/reference/movenext-method-enumerator-javascript.md)  
  
## <a name="requirements"></a>Wymagania  
 Obsługiwane w następujących trybach dokumentu: Osobliwości, Standardy programu Internet Explorer 6, Standardy programu Internet Explorer 7, Standardy programu Internet Explorer 8, Standardy programu Internet Explorer 9 i standardy programu Internet Explorer 10. Nieobsługiwane w [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplikacji. Zobacz [Informacje o wersji](../../javascript/reference/javascript-version-information.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Boolean — obiekt](../../javascript/reference/boolean-object-javascript.md)