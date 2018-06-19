---
title: Struktury Visual C++ w Projektancie klas
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 36d9e78a1944817d9384d0c55b9584e58a758ccc
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31925084"
---
# <a name="visual-c-structures-in-class-designer"></a>Visual C++ struktur w Projektancie klas

**Projektant klas** obsługuje struktury języka C++, które są zadeklarowane ze słowem kluczowym `struct`. Poniżej przedstawiono przykładowy:

```cpp
struct MyStructure
{
   char a;
   int i;
   long j;
};
```

Aby uzyskać więcej informacji o korzystaniu z `struct` typu, zobacz [struktury](/cpp/cpp/struct-cpp).

Struktura C++ kształt na diagramie klas wyglądu i działania takie jak kształt klasy, z tą różnicą, że etykieta odczytuje **struktury** i ma narożniki zamiast zaokrąglone narożniki.

|Element Code|Widok projektanta klas|
|------------------|-------------------------|
|`struct StructureName {};`|**StructureName**<br /><br /> Struct|

## <a name="see-also"></a>Zobacz także

- [Praca z kodem Visual C++](working-with-visual-cpp-code.md)
- [Klasy i struktury](/cpp/cpp/classes-and-structs-cpp)
- [struct](/cpp/cpp/struct-cpp)