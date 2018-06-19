---
title: Dodawanie adnotacji struktur i klas
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Field_size_bytes_part_
- _Field_size_bytes_full_opt_
- _Field_size_bytes_
- _Field_size_opt_
- _Field_size_part_
- _Field_size_bytes_part_opt_
- _Field_range_
- _Field_size_part_opt_
- _Field_size_
- _Field_size_bytes_opt_
- _Struct_size_bytes_
- _Field_size_bytes_full_
- _Field_size_full_
- _Field_size_full_opt_
ms.assetid: b8278a4a-c86e-4845-aa2a-70da21a1dd52
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 076631860035e41451741d49843d9282ec4c15f7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31894351"
---
# <a name="annotating-structs-and-classes"></a>Dodawanie adnotacji struktur i klas
Elementy członkowskie struktury i klasy może dodawać adnotacje, za pomocą adnotacji przypominają invariants — są one domniemania PRAWDA dowolnego wywołanie funkcji i funkcji wejścia/wyjścia, który obejmuje otaczającej strukturę jako parametr lub wartość wyniku.

## <a name="struct-and-class-annotations"></a>Struktury i klasy adnotacji

-   `_Field_range_(low, high)`

     Pole znajduje się w zakresie (włącznie) z `low` do `high`.  Odpowiednikiem `_Satisfies_(_Curr_ >= low && _Curr_ <= high)` zastosowane do obiektu adnotacjami przy użyciu odpowiednich warunków pre lub post.

-   `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)`, `_Field_size_bytes_opt_(size)`

     Pola, którego rozmiar zapisu w elementy (lub bajtów) jako określony przez `size`.

-   `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)`,         `_Field_size_bytes_part_(size, count)`, `_Field_size_bytes_part_opt_(size, count)`

     Pola, którego rozmiar zapisu w elementy (lub bajtów) jako określony przez `size`i `count` tych elementów (w bajtach), które są do odczytu.

-   `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)`, `_Field_size_bytes_full_opt_(size)`

     Pola, które ma rozmiar elementy readable i writable elementy (lub bajtów) jako określony przez `size`.

-   `_Struct_size_bytes_(size)`

     Pola, które ma rozmiar elementy readable i writable elementy (lub bajtów) jako określony przez `size`.

     Ma zastosowanie do deklaracji struktury lub klasy.  Wskazuje, że prawidłowy obiekt tego typu może być większa niż deklarowany typ, liczbę bajtów jest określona przez `size`.  Na przykład:

    ```cpp

    typedef _Struct_size_bytes_(nSize)
    struct MyStruct {
        size_t nSize;
        ...
    };

    ```

     Rozmiar buforu w bajtach parametru `pM` typu `MyStruct *` następnie przyjmuje się:

    ```cpp
    min(pM->nSize, sizeof(MyStruct))
    ```

## <a name="see-also"></a>Zobacz też
 [Korzystanie z adnotacji SAL w celu redukowanie defektów kodu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md) [opis SAL](../code-quality/understanding-sal.md) [Dodawanie adnotacji do parametrów funkcji i zwracanych wartości](../code-quality/annotating-function-parameters-and-return-values.md) [.zachowaniefunkcjidodawaniaadnotacji](../code-quality/annotating-function-behavior.md) [Dodawanie adnotacji do zachowania blokującego](../code-quality/annotating-locking-behavior.md) [określenie, kiedy i gdzie dotyczy adnotacji](../code-quality/specifying-when-and-where-an-annotation-applies.md) [funkcje wewnętrzne](../code-quality/intrinsic-functions.md) [najlepsze rozwiązania i Przykłady](../code-quality/best-practices-and-examples-sal.md)