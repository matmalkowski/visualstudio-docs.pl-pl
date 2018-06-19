---
title: Wyliczenia Visual C++ w Projektancie klas
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: a42dfb65cc70704bbed662e35b2e2eb0e9c237c4
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31922023"
---
# <a name="visual-c-enumerations-in-class-designer"></a>Visual C++ wyliczenia w Projektancie klas

**Projektant klas** obsługuje C++ `enum` i zakresami `enum class` typów. Poniżej przedstawiono przykładowy:

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

- [Praca z kodem Visual C++](working-with-visual-cpp-code.md)
- [Wyliczenia](/cpp/cpp/enumerations-cpp)