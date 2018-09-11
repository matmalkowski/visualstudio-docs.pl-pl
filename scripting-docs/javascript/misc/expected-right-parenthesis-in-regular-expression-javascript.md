---
title: Oczekiwano &#39;)&#39; w wyrażeniu regularnym (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5020
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b5d1075a41d2b97d10166b1372e8df3a93dd9d8e
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279131"
---
# <a name="expected-3939-in-regular-expression-javascript"></a>Oczekiwano &#39;)&#39; w wyrażeniu regularnym (JavaScript)
Podjęto próbę utworzenia przechwytywania wyrażeń regularnych, potwierdzenie lub grupy, ale nie zawiera nawias zamykający. Nawiasy ma kilka celów w wyrażeniach regularnych. Przede wszystkim, są one używane do przechwytywania wyrażeń podrzędnych, określ potwierdzenia lub pogrupować wzorców, dzięki czemu elementy mogą być traktowane jako pojedyncza jednostka, *, +,?, i tak dalej.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Dodaj nawias zamykający po prawej stronie.  
  
    > [!NOTE]
    >  Jeśli chcesz dopasować nawiasy pojedynczy znak ucieczki znakiem kreski ułamkowej odwróconej - \\(— tak, aby nie jest interpretowany jako znak specjalny przez [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekt będący wyrażeniem regularnym](../../javascript/reference/regular-expression-object-javascript.md)   
 [Składnia wyrażeń regularnych (JavaScript)](https://msdn.microsoft.com/library/1400241x)