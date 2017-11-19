---
title: "Nie można przypisać do &#39; to &#39; | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5000
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba2b0a2b-f0f8-4698-b335-a4ab6c166671
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c164b9b7d2989076a9dc0ef0bafba6159bc08885
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="cannot-assign-to-39this39"></a>Nie można przypisać do &#39; to &#39;
Próbujesz przypisać wartości do **to**. **to** jest [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] — słowo kluczowe, która odwołuje się do jednego:  
  
-   obiekt aktualnie wykonywanych — metoda  
  
-   globalny obiekt nie istnieje Bieżąca metoda (lub metoda nie należy do innego obiektu).  
  
 Metoda jest [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] funkcji, które jest wywoływane za pośrednictwem obiektu. Wewnątrz metody **to** — słowo kluczowe jest odwołanie do obiektu metoda została wywołana za pomocą (która stanie się być obiekt utworzony przez wywołanie konstruktora klasy **nowe** operatora).  
  
 Wewnątrz metody, można użyć **to** do odwoływania się do bieżącego obiektu, ale nie można przypisać nową wartość do **to**.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Nie należy przypisywać **to**. Dostęp do właściwości lub metody wystąpień obiektu, należy użyć operatora kropki (np. koło**.** RADIUS).  
  
    > [!NOTE]
    >  Nie można nadać nazwy zmiennej utworzonych przez użytkownika **to**; jest [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] słowa zastrzeżone.  
  
## <a name="see-also"></a>Zobacz też  
 [Ta instrukcja](../../javascript/reference/this-statement-javascript.md)   
 [Rozwiązywanie problemów w skryptach](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)