---
title: Wyliczenia Visual C++ w Projektancie klas | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ad55c68e16fcd340d69178dc24a4b92cada9e2f3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="visual-c-enumerations-in-class-designer"></a>Wyliczenia Visual C++ w Projektancie klas
Projektant klas obsługuje C++ `enum` i zakresami `enum class` typów. Poniżej przedstawiono przykładowy:  
  
```cpp
enum CardSuit {  
   Diamonds = 1,  
   Hearts = 2,  
   Clubs = 3,  
   Spades = 4  
};  
  
// or...  
enum class CardSuit {  
   Diamonds = 1,  
   Hearts = 2,  
   Clubs = 3,  
   Spades = 4  
};
```  
  
Wyliczenie C++ kształt na diagramie klas wyglądu i działania takie jak kształt struktura, z tą różnicą, że etykieta odczytuje **wyliczenia** lub **Enum class**, jest różowy zamiast niebieska i ma kolorowe krawędź w lewo i w górnej marginesy. Zarówno wyliczenie kształtów i struktura ma narożniki.  
  
Aby uzyskać więcej informacji o korzystaniu z `enum` typu, zobacz [wyliczenia](/cpp/cpp/enumerations-cpp).  
  
## <a name="see-also"></a>Zobacz także
[Praca z kodem Visual C++](working-with-visual-cpp-code.md)   
[Wyliczenia](/cpp/cpp/enumerations-cpp)