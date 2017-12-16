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
ms.openlocfilehash: f7f5ccb0bedd57b6b72d06e39e8829aa9d6b140d
ms.sourcegitcommit: 64c7682ec3a2cbea684e716803398d4278b591d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2017
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