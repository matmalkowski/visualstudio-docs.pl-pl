---
title: Uzupełnianie składni dla identyfikatorów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IntelliSense [JavaScript], statement completion
- statement completion, JavaScript IntelliSense
ms.assetid: c2cd4945-c67e-471b-8057-96cfd25f7fb2
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9ad7a83ac3eb7f0af57eed382ace32fdb80ccef2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42694275"
---
# <a name="statement-completion-for-identifiers"></a>Uzupełnianie składni dla identyfikatorów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [dokumentacja programu Visual Studio 2017](https://docs.microsoft.com/en-us/visualstudio/).  
  
Język JavaScript nie zezwala na jawnych typowań wartości w celu deklaracje zmiennych. W rezultacie IntelliSense nie zawsze podawać listy uzupełniania dla obiektów. Taka sytuacja może wystąpić w różnych sytuacjach. Poniżej przedstawiono typowe kilka z nich.  
  
-   Parametr jest zadeklarowana, ale go nie została wywołana gdzie indziej w aktywnym dokumencie, jak pokazano w poniższym przykładzie.  
  
    ```javascript  
    function illuminate(light) {  
             light.  // Accurate statement completion is not available   
                     // unless illuminate is called elsewhere with a   
                     // parameter that has a value. If it is called only  
                     // in a function that is a sibling to   
                     // illuminate(light) in the call hierarchy, the   
                     // IntelliSense engine also cannot determine the   
                     // parameter type.  
         }  
  
    // Sibling function. No statement completion for light   
    // object in preceding code.  
    function lightLamp() {  
        var x = illuminate(1);  
    }  
  
    // Uncomment the next line to obtain statement completion for  
    // light object in preceding code.  
    // var x = illuminate(1);  
    ```  
  
-   Obiekt jest funkcją, która jest wywoływana w odpowiedzi na zdarzenie. W czasie projektowania aparat IntelliSense nie można określić typ obiektów używanych w tej sytuacji.  
  
     Jeśli aparat IntelliSense można określić, że zdarzenia powinna być wywoływana, zwykle korzystając ze `addEventListener` zdarzenia w aktywnym dokumencie znajduje się bardziej precyzyjne informacje IntelliSense.  
  
 Gdy IntelliSense nie może go zidentyfikować, aparat IntelliSense wypełnia lista uzupełniania z nazwanych obiektów lub identyfikatorów, które znajdują się w aktywnym dokumencie. Gdy na liście uzupełniania zawiera tych identyfikatorów, ikony informacji są wyświetlane obok nich. Ponadto etykietkę narzędzia dla każdego identyfikatora wskazuje, że wyrażenie jest nieznany. Na poniższej ilustracji przedstawiono instrukcję opcje uzupełniania dla obiektu typu `light` , nie można zidentyfikować, ponieważ obiekt i jego właściwości są niezdefiniowane. Jednak `intensity` właściwość jest dostępne na liście identyfikator, ponieważ jest on używany w `illuminate` funkcji.  
  
 **Opcje uzupełniania dla obiektu, który nie może zostać zidentyfikowany**  
  
 ![Technologia JavaScript IntelliSense dla identyfikatorów](../ide/media/js-intellisense-identifiers.png "js_intellisense_identifiers")  
  
 Na liście uzupełniania dla obiektu można zastąpić za pomocą komentarzy dokumentacji XML lub funkcje rozszerzalność JavaScript IntelliSense. Korzystając z tych funkcji, możesz podać informacje o typie i bardziej opisowe informacje IntelliSense po jej w przeciwnym razie będą niedostępne. Aby uzyskać więcej informacji, zobacz [rozszerzanie JavaScript IntelliSense](../ide/extending-javascript-intellisense.md) i [tworzyć komentarze dokumentacji XML](../ide/create-xml-documentation-comments-for-javascript-intellisense.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcja IntelliSense dla języka JavaScript](../ide/javascript-intellisense.md)



