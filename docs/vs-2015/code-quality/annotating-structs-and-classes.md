---
title: Dodawanie adnotacji do struktur i klas | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 11
author: corob-msft
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 24ed559321bb63d5f9871193f312356466756429
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42679153"
---
# <a name="annotating-structs-and-classes"></a>Dodawanie adnotacji struktur i klas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [Dodawanie adnotacji do struktur i klas](https://docs.microsoft.com/visualstudio/code-quality/annotating-structs-and-classes).  
  
Elementy członkowskie struktury i klasy może dodawać adnotacje, za pomocą funkcji adnotacje, przypominają invariants — jest uznawana za tę prawdziwe dowolnego wywołania funkcji i funkcji wejścia/wyjścia, która obejmuje otaczającej strukturze jako parametr lub wartość wyniku.  
  
## <a name="struct-and-class-annotations"></a>Struktury i klasy adnotacji  
  
-   `_Field_range_(low, high)`  
  
     To pole jest z zakresu (włącznie) z `low` do `high`.  Odpowiednikiem `_Satisfies_(_Curr_ >= low && _Curr_ <= high)` zastosowany do obiektu adnotacjami przy użyciu odpowiednich warunków pre lub post.  
  
-   `_Field_size_(size)`, `_Field_size_opt_(size)`, `_Field_size_bytes_(size)`, `_Field_size_bytes_opt_(size)`  
  
     Pola, które ma rozmiar obszaru do zapisu w elementy (lub w bajtach) jako określony przez `size`.  
  
-   `_Field_size_part_(size, count)`, `_Field_size_part_opt_(size, count)`,         `_Field_size_bytes_part_(size, count)`, `_Field_size_bytes_part_opt_(size, count)`  
  
     Pola, które ma rozmiar obszaru do zapisu w elementy (lub w bajtach) jako określony przez `size`i `count` tych elementów (w bajtach), które są do odczytu.  
  
-   `_Field_size_full_(size)`, `_Field_size_full_opt_(size)`, `_Field_size_bytes_full_(size)`, `_Field_size_bytes_full_opt_(size)`  
  
     Pola, które ma elementy readable i writable rozmiar elementów (lub w bajtach) jako określony przez `size`.  
  
-   `_Struct_size_bytes_(size)`  
  
     Pola, które ma elementy readable i writable rozmiar elementów (lub w bajtach) jako określony przez `size`.  
  
     Ma zastosowanie do deklaracji struktury lub klasy.  Wskazuje, że prawidłowy obiekt tego typu mogą być większe niż zadeklarowanym typem z liczbą bajtów jest określona przez `size`.  Na przykład:  
  
    ```cpp  
  
    typedef _Struct_size_bytes_(nSize)  
    struct MyStruct {  
        size_t nSize;  
        …  
    };  
  
    ```  
  
     Rozmiar buforu w bajtach parametr `pM` typu `MyStruct *` zostaje następnie przeniesiony za:  
  
    ```cpp  
    min(pM->nSize, sizeof(MyStruct))  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z adnotacji SAL w celu zmniejszenia liczby błędów kodu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Informacje o języku SAL](../code-quality/understanding-sal.md)   
 [Dodawanie adnotacji do parametrów funkcji i zwracanych wartości](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Zachowanie funkcji dodawania adnotacji](../code-quality/annotating-function-behavior.md)   
 [Dodawanie adnotacji do zachowania blokującego](../code-quality/annotating-locking-behavior.md)   
 [Określanie miejsca i warunków stosowania adnotacji](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Funkcje wewnętrzne](../code-quality/intrinsic-functions.md)   
 [Najlepsze praktyki i przykłady](../code-quality/best-practices-and-examples-sal.md)



