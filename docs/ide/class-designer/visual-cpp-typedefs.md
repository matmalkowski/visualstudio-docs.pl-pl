---
title: "Definicje typów Visual C++ w Projektancie klas | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.classdesigner.typedef
- vs.classdesigner.aliasofline
helpviewer_keywords:
- Class Designer [Visual Studio], typedefs
ms.assetid: c1984108-71fc-4d3a-b4d4-3eac2c6b4ebf
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 96d7e8cee6ce024040184aca50b5f5cb6facf388
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2018
---
# <a name="visual-c-typedefs-in-class-designer"></a>Definicje typów Visual C++ w Projektancie klas
Instrukcji TypeDef utworzyć jednej lub kilku warstw pośredników między nazwą jego typ podstawowy. Projektant klas obsługuje typy typedef języka C++, które są zadeklarowane ze słowem kluczowym `typedef`, na przykład:  
  
```cpp
typedef class coord  
{  
   void P(x,y);  
   unsigned x;  
   unsigned y;  
} COORD;  
```  
  
Tego typu można użyć do zadeklarowania wystąpienie:  
  
`COORD OriginPoint;`  
  
Mimo że można zadeklarować jako element typedef bez nazwy, Projektant klas nie będzie używać nazwa tagu, który określisz; Nazwa, która generuje widoku klasy zostanie użyty. Na przykład następujące oświadczenie jest prawidłowy, ale pojawia się w widoku klas i Projektant klas jako obiekt o nazwie **__unnamed**:  
  
```cpp
typedef class coord  
{  
   void P(x,y);  
   unsigned x;  
   unsigned y;  
};  
```

Aby uzyskać więcej informacji o korzystaniu z `typedef` typu, zobacz [definicje typów](/cpp/aliases-and-typedefs-cpp#typedefs).

Kształt C++ element typedef ma kształt z typem określonym w definicji typu. Na przykład, jeśli źródło deklaruje `typedef class`, kształt zaokrąglonymi narożnikami, a etykieta **klasy**. Aby uzyskać `typedef struct`, kształt ma narożniki i etykiety **struktury**.  
  
Klasy i struktury mogą mieć zagnieżdżonych definicje typów zadeklarowana wewnątrz. w związku z tym kształty klasy i struktury można wyświetlić deklaracje typedef zagnieżdżonych jako kształtów zagnieżdżonych.  
  
Element TypeDef shapes pomocy technicznej **Pokaż jako skojarzenie** i **wyświetlić jako kolekcję skojarzeń** polecenia w menu kontekstowym.  
  
Poniżej przedstawiono kilka przykładów typdef typów, które obsługuje Projektant klas:  
  
`typedef type name`  
  
*Nazwa* : *typu*  
  
— klasa typedef  
  
Rysuje skojarzenia nawiązywania wpisz *nazwa*, jeśli to możliwe.  
  
`typedef void (*func)(int)`  
  
`func: void (*)(int)`  
  
— klasa typedef  
  
Element TypeDef dla wskaźników funkcji. Brak wiersza skojarzenie jest rysowane.  
  
Projektant klas nie jest wyświetlany jako element typedef, jeśli jej typ źródła jest wskaźnik funkcji.  
  
```cpp
typedef int MyInt;  
class A {  
   MyInt I;  
};  
```  
  
`MyInt: int`  
  
— klasa typedef  
  
`A`  
  
Class  
  
Rysuje linię skojarzenia wskazujący z kształtu typu źródłowego kształtu typu docelowego.  
  
`Class B {};`  
  
`typedef B MyB;`  
  
`B`  
  
Class  
  
`MyB : B`  
  
— klasa typedef  
  
Prawym przyciskiem myszy kształt element typedef, a następnie klikając polecenie **Pokaż jako skojarzenie** Wyświetla typedef lub klasy i **Alias** linia łącząca dwa kształty (podobnie jak linia asocjacji).  
  
`typedef B MyB;`  
  
`typedef MyB A;`  
  
`MyBar : Bar`  
  
— klasa typedef  
  
Taka sama jak powyżej.  
  
```cpp
Class B {};  
typedef B MyB;  
  
class A {  
   MyB B;  
};  
```  
  
`B`  
  
Class  
  
`MyB : B`  
  
— klasa typedef  
  
`A`  
  
Class  
  
`MyB`jest zagnieżdżony element typedef.  
  
`#include <vector>`  
  
`...`  
  
`using namespace std;`  
  
`...`  
  
`typedef vector<int> MyIntVect;`  
  
`vector<T>`Klasy  
  
`MyIntVect : vector<int>`  
  
— klasa typedef  
  
`class B {};`  
  
`typedef B MyB;`  
  
`class A : MyB {};`  
  
`MyB : B`  
  
— klasa typedef  
  
-> B  
  
`B`  
  
`A`  
  
Class  
  
-> MyB  
  
Projektant klas nie obsługuje wyświetlania tego rodzaju relacji za pomocą polecenia menu kontekstowego.  
  
`#include <vector>`  
  
`Typedef MyIntVect std::vector<int>;`  
  
`Class MyVect : MyIntVect {};`  
  
`std::vector<T>`  
  
Class  
  
`MyIntVect : std::vector<int>`  
  
— klasa typedef  
  
`MyVect`  
  
Class  
  
-> MyIntVect  
  
## <a name="see-also"></a>Zobacz także

[Praca z kodem Visual C++](working-with-visual-cpp-code.md)  
[Definicje typów](/cpp/aliases-and-typedefs-cpp#typedefs)