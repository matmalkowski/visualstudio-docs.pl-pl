---
title: "moveNext — metoda (moduł wyliczający) (JavaScript) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: moveNext
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: MoveNext method
ms.assetid: 59aa339b-f375-450a-8276-37896a55a824
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab9b07a9a9c4640407cff0eaf21a6e8cd65dac11
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="movenext-method-enumerator-javascript"></a>moveNext — Metoda (Moduł wyliczający) (JavaScript)
Przenosi bieżący element do następnego elementu w kolekcji.  
  
> [!WARNING]
>  Ten obiekt jest obsługiwany tylko w programie Internet Explorer.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
enumObj.moveNext( )   
```  
  
## <a name="remarks"></a>Uwagi  
 Wymagane *enumObj* odwołanie jest dowolne `Enumerator` obiektu.  
  
 Jeśli moduł wyliczający znajduje się na końcu kolekcji lub kolekcja jest pusta, bieżący element ustawiono niezdefiniowaną.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie **moveNext** metoda służy do przenoszenia do następnego dysku w `Drives` kolekcji:  
  
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
 [atEnd — metoda (moduł wyliczający)](../../javascript/reference/atend-method-enumerator-javascript.md)   
 [Item — metoda (moduł wyliczający)](../../javascript/reference/item-method-enumerator-javascript.md)   
 [moveFirst — metoda (moduł wyliczający)](../../javascript/reference/movefirst-method-enumerator-javascript.md)