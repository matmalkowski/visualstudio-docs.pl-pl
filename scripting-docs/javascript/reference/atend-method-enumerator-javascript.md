---
title: "atEnd — metoda (moduł wyliczający) (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: atEnd
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: atEnd method
ms.assetid: 326808fb-9a0f-428e-aff1-b11b237913f1
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7b5097d00c11ffafc314264f134aedda3981c8e2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="atend-method-enumerator-javascript"></a>atEnd — Metoda (Moduł wyliczający) (JavaScript)
Zwraca wartość logiczną wskazującą, czy moduł wyliczający znajduje się na końcu kolekcji.  
  
> [!WARNING]
>  Ten obiekt jest obsługiwany tylko w programie Internet Explorer.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
myEnum.atEnd()  
```  
  
## <a name="remarks"></a>Uwagi  
 Wymagane *myEnum* odwołanie jest dowolne `Enumerator` obiektu.  
  
 `atEnd` Metoda zwraca **true** bieżący element jest ostatnim w kolekcji, Kolekcja jest pusta, czy bieżący element jest niezdefiniowana. W przeciwnym razie zwraca **false**.  
  
## <a name="example"></a>Przykład  
 W poniższym kodzie `atEnd` metoda jest używana do określenia, czy osiągnięto koniec listy dysków:  
  
```JavaScript  
function ShowDrives()  
{  
    var s = "";  
    var bytesPerGB = 1024 * 1024 * 1024;  
  
    var fso = new ActiveXObject("Scripting.FileSystemObject");  
    var e = new Enumerator(fso.Drives);  
  
    e.moveFirst();  
    while (e.atEnd() == false)  
    {  
        var drv = e.item();  
  
        s += drv.Path + " - ";  
  
        if (drv.IsReady)  
        {  
            var freeGB = drv.FreeSpace / bytesPerGB;  
            var totalGB = drv.TotalSize / bytesPerGB;  
  
            s += freeGB.toFixed(3) + " GB free of ";  
            s += totalGB.toFixed(3) + " GB";  
        }  
        else  
        {  
            s += "Not Ready";  
        }  
  
        s += "<br />";  
  
        e.moveNext();  
    }  
    return(s);  
}  
```  
  
## <a name="requirements"></a>Wymagania  
 Obsługiwane w następujących trybach dokumentu: Osobliwości, Standardy programu Internet Explorer 6, Standardy programu Internet Explorer 7, Standardy programu Internet Explorer 8, Standardy programu Internet Explorer 9 i standardy programu Internet Explorer 10. Nieobsługiwane w [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplikacji. Zobacz [Informacje o wersji](../../javascript/reference/javascript-version-information.md).  
  
 **Dotyczy**: [Enumerator — obiekt](../../javascript/reference/enumerator-object-javascript.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Item — metoda (moduł wyliczający)](../../javascript/reference/item-method-enumerator-javascript.md)   
 [moveFirst — metoda (moduł wyliczający)](../../javascript/reference/movefirst-method-enumerator-javascript.md)   
 [moveNext — metoda (moduł wyliczający)](../../javascript/reference/movenext-method-enumerator-javascript.md)   
 [Enumerator — obiekt](../../javascript/reference/enumerator-object-javascript.md)