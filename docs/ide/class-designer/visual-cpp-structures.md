---
title: Struktury Visual C++ w Projektancie klas | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: d0621b5a2a82786a41e8d566954f03341affa905
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="visual-c-structures-in-class-designer"></a>Struktury Visual C++ w Projektancie klas
Projektant klas obsługuje struktur C++, które są zadeklarowane ze słowem kluczowym `struct`. Poniżej przedstawiono przykładowy:  
  
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
[Praca z kodem Visual C++](working-with-visual-cpp-code.md)   
[Klasy i struktury](/cpp/cpp/classes-and-structs-cpp)   
[struct](/cpp/cpp/struct-cpp)