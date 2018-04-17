---
title: Wyliczenia Visual C++ w Projektancie klas | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: ac804f35c2d917e5443e61d4f2e53cde81165070
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
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