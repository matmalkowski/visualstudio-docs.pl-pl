---
title: Definicje typów Visual C++ w Projektancie klas
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.typedef
- vs.classdesigner.aliasofline
helpviewer_keywords:
- Class Designer [Visual Studio], typedefs
ms.assetid: c1984108-71fc-4d3a-b4d4-3eac2c6b4ebf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 6eb831422df42a246a5d5c23ccdd480bce47a0e6
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
---
# <a name="visual-c-typedefs-in-class-designer"></a>Definicje typów Visual C++ w Projektancie klas

[Element TypeDef](/cpp/cpp/aliases-and-typedefs-cpp#typedefs) instrukcje tworzenia jednej lub kilku warstw pośredników między nazwą jego typ podstawowy. **Projektant klas** obsługuje typy typedef języka C++, które są zadeklarowane ze słowem kluczowym `typedef`, na przykład:

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

## <a name="class-and-struct-shapes"></a>Kształty klasy i struktury

W **Projektant klas**, C++ typedef ma kształt z typem określonym w definicji typu. Jeśli źródło deklaruje `typedef class`, kształt zaokrąglonymi narożnikami, a etykieta **klasy**. Aby uzyskać `typedef struct`, kształt ma narożniki i etykiety **struktury**.

Klasy i struktury może mieć zagnieżdżonych definicje typów zadeklarowany w nich. W **Projektant klas**, klasy i struktury kształtów mogą być prezentowane w deklaracji typedef zagnieżdżonych kształtów w zagnieżdżonych.

Element TypeDef shapes pomocy technicznej **Pokaż jako skojarzenie** i **wyświetlić jako kolekcję skojarzeń** polecenia w menu kontekstowym.

### <a name="class-typedef-example"></a>Przykład klasy — typedef

```cpp
class B {};
typedef B MyB;
```

![Element typedef klasy C++ w Projektancie klas](media/cpp-class-typedef.png)

### <a name="struct-typedef-example"></a>Przykład typedef — struktura

```cpp
typedef struct mystructtag
{
    int   i;
    double f;
} mystruct;
```

![Element typedef struktury języka C++ w Projektancie klas](media/cpp-struct-typedef.png)

## <a name="unnamed-typedefs"></a>Nienazwane definicje typów

Mimo że można zadeklarować jako element typedef nie zawiera nazwy **Projektant klas** nie są używane przez Ciebie nazwą tagu. **Projektant klas** używa nazwy który **widoku klasy** generuje. Na przykład następujące oświadczenie jest prawidłowy, ale wygląda na to w **widoku klasy** i **Projektant klas** jako obiekt o nazwie **__unnamed**:

```cpp
typedef class coord
{
   void P(x,y);
   unsigned x;
   unsigned y;
};
```

> [!NOTE]
> **Projektant klas** definicje typów, których typ źródła jest wskaźnik funkcji nie są wyświetlane.

## <a name="see-also"></a>Zobacz także

- [Praca z kodem Visual C++](working-with-visual-cpp-code.md)
- [Definicje typów](/cpp/cpp/aliases-and-typedefs-cpp#typedefs)