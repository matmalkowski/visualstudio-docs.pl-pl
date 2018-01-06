---
title: Struktury Visual C++ w Projektancie klas | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d6f2aa3893a230abd52dd5cf19ed9d751e56e50c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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