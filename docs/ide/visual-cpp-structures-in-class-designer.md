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
ms.openlocfilehash: 85e2068e00f2164b44feb9aae61a47de426be735
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="visual-c-structures-in-class-designer"></a>Struktury Visual C++ w Projektancie klas
Projektant klas obsługuje struktur C++, które są zadeklarowane ze słowem kluczowym `struct`. Poniżej przedstawiono przykładowy:  
  
```  
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
  
## <a name="see-also"></a>Zobacz też  
 [Praca z kodem Visual C++ (Projektant klas)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [Klasy i struktury](/cpp/cpp/classes-and-structs-cpp)   
 [— Struktura](/cpp/cpp/struct-cpp)