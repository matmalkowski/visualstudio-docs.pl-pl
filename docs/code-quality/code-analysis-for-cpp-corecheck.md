---
title: Visual Studio C++ podstawowe wskazówki sprawdzania odwołania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/22/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code analysis, C++ core check
ms.assetid: f1429463-136e-41ed-8a75-a8dbf0b4fd89
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0825ea42ca74b224574299846504dfde7dd6f809
ms.sourcegitcommit: 67374acb6d24019a434d96bf705efdab99d335ee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="c-core-guidelines-checker-reference"></a>C++ podstawowe wskazówki dotyczące sprawdzania odwołania

Ta sekcja zawiera ostrzeżenia C++ podstawowe wskazówki. Informacje dotyczące analizy kodu, zobacz [/ analyze (analiza kodu)](/cpp/build/reference/analyze-code-analysis) i [Szybki Start: analiza kodu dla C/C++](../code-quality/quick-start-code-analysis-for-c-cpp.md).

> [!NOTE]
> Ostrzeżenia należeć do więcej niż jednej grupy, a nie wszystkie ostrzeżenia ma tematu pełną dokumentację.

## <a name="ownerpointer-group"></a>OWNER_POINTER grupy

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md) zwraca obiekt zakresie zamiast przydzielone sterty, jeśli ma ona Konstruktor przenoszenia. Zobacz [C++ podstawowe wskazówki dotyczące R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26403 RESET_OR_DELETE_OWNER](C26403.md) resetowania lub jawnie usunąć właściciela\<T > wskaźnika "% Zmienna %". Zobacz [C++ podstawowe wskazówki dotyczące R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26404 DONT_DELETE_INVALID](C26404.md) nie należy usuwać właściciela\<T > może to być w nieprawidłowym stanie. Zobacz [C++ podstawowe wskazówki dotyczące R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26405 DONT_ASSIGN_TO_VALID](C26405.md) nie należy przypisywać do właściciela\<T > może to być w nieprawidłowym stanie. Zobacz [C++ podstawowe wskazówki dotyczące R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26406 DONT_ASSIGN_RAW_TO_OWNER](C26406.md) nie należy przypisywać raw wskaźnika do właściciela\<T >. Zobacz [C++ podstawowe wskazówki dotyczące R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26407 DONT_HEAP_ALLOCATE_UNNECESSARILY](C26407.md) preferowane obiektów dodanych do zakresu, nie-Alokacja sterty niepotrzebnie. Zobacz [C++ podstawowe wskazówki dotyczące R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26429 USE_NOTNULL](C26429.md) Symbol "% % symbol" nigdy nie jest sprawdzane pod kątem nullness, może być oznaczony jako not_null. Zobacz [C++ podstawowe wskazówki dotyczące F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26430 TEST_ON_ALL_PATHS](C26430.md) Symbol "% % symbolu" nie jest sprawdzane pod kątem nullness we wszystkich ścieżkach. Zobacz [C++ podstawowe wskazówki dotyczące F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26431 DONT_TEST_NOTNULL](C26431.md) typ wyrażenia "% wyrażenie %" jest już gsl::not_null. Testuj go nullness. Zobacz [C++ podstawowe wskazówki dotyczące F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

## <a name="rawpointer-group"></a>RAW_POINTER grupy

[C26400 NO_RAW_POINTER_ASSIGNMENT](c26400.md) nie należy przypisywać wynik alokacji lub wywołanie funkcji z użyciem właściciela\<T > zwrócić wartość do nieprzetworzonej wskaźnika; Użyj właściciela\<T > zamiast tego. Zobacz [C++ podstawowe wskazówki dotyczące I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[C26401 DONT_DELETE_NON_OWNER](c26401.md) nie należy usuwać raw wskaźnika, który nie jest właścicielem\<T >. Zobacz [C++ podstawowe wskazówki dotyczące I.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)   zwraca obiekt zakresie zamiast przydzielone sterty, jeśli ma ona Konstruktor przenoszenia. Zobacz [C++ podstawowe wskazówki dotyczące R.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26408 NO_MALLOC_FREE](C26408.md) uniknąć malloc() i free() tak, wersja nothrow nowych z delete. Zobacz [C++ podstawowe wskazówki dotyczące R.10](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-mallocfree).

[C26409 NO_NEW_DELETE](C26409.md) Unikaj wywoływania nowy i Usuń jawnie, użyj std::make_unique\<T > zamiast tego. Zobacz [C++ podstawowe wskazówki dotyczące R.11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-newdelete).

[C26429 USE_NOTNULL](C26429.md) Symbol "% % symbol" nigdy nie jest sprawdzane pod kątem nullness, może być oznaczony jako not_null. Zobacz [C++ podstawowe wskazówki dotyczące F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26430 TEST_ON_ALL_PATHS](C26430.md) Symbol "% % symbolu" nie jest sprawdzane pod kątem nullness we wszystkich ścieżkach. Zobacz [C++ podstawowe wskazówki dotyczące F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26431 DONT_TEST_NOTNULL](C26431.md) typ wyrażenia "% wyrażenie %" jest już gsl::not_null. Testuj go nullness. Zobacz [C++ podstawowe wskazówki dotyczące F.23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26481 NO_POINTER_ARITHMETIC](C26481.md) nie używaj arytmetyki wskaźnika. Zamiast tego użyj zakresu. Zobacz [C++ podstawowe wskazówki dotyczące Bounds.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md).
Wyrażenie "% wyrażenie %": nie tablicy na wskaźnik zniszczenie. Zobacz [C++ podstawowe wskazówki dotyczące Bounds.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

## <a name="uniquepointer-group"></a>UNIQUE_POINTER grupy

[C26410 NO_REF_TO_CONST_UNIQUE_PTR](C26410.md) parametru % parametru % jest odwołaniem do `const` unikatowy wskaźnika, użyj T const * lub const T & zamiast tego. Zobacz [C++ podstawowe wskazówki dotyczące R.32](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-uniqueptrparam).

[C26411 NO_REF_TO_UNIQUE_PTR](C26411.md) parametr % parametru % jest odwołanie do wskaźnika unikatowy i nigdy nie jest ponownie przypisywane lub zresetować, użyj T * lub T & zamiast tego. Zobacz [C++ podstawowe wskazówki dotyczące R.33](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-reseat).

[C26414 RESET_LOCAL_SMART_PTR](C26414.md) przenieść, skopiować, ponowne przypisanie lub resetowanie wskaźnika inteligentnego lokalnego "% % symbol". Zobacz [C++ podstawowe wskazówki dotyczące R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26415 SMART_PTR_NOT_NEEDED](C26415.md) wskaźnika inteligentnego parametr "% symbol %" jest używany do zawartych w niej wskaźnika. Użyj T * lub T & zamiast tego. Zobacz [C++ podstawowe wskazówki dotyczące R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

## <a name="sharedpointer-group"></a>SHARED_POINTER grupy

[C26414 RESET_LOCAL_SMART_PTR](C26414.md) przenieść, skopiować, ponowne przypisanie lub resetowanie wskaźnika inteligentnego lokalnego "% % symbol". Zobacz [C++ podstawowe wskazówki dotyczące R.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26415 SMART_PTR_NOT_NEEDED](C26415.md) wskaźnika inteligentnego parametr "% symbol %" jest używany do zawartych w niej wskaźnika. Użyj T * lub T & zamiast tego. Zobacz [C++ podstawowe wskazówki dotyczące R.30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

[C26416 NO_RVALUE_REF_SHARED_PTR](C26416.md) parametr wskaźnika Shared "% symbol %" jest przekazywana przez odwołanie do r-wartości. Zamiast tego przekazanie przez wartość. Zobacz [C++ podstawowe wskazówki dotyczące R.34](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-owner).

[C26417 NO_LVALUE_REF_SHARED_PTR](C26417.md) parametr wskaźnika Shared "% symbol %" jest przekazywana przez odwołanie i nie Resetuj lub przypisane. Użyj T * lub T & zamiast tego. Zobacz [C++ podstawowe wskazówki dotyczące R.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam).

[C26418 NO_VALUE_OR_CONST_REF_SHARED_PTR](C26418.md) parametr wskaźnika Shared "% % symbolu" nie jest skopiować lub przenieść. Użyj T * lub T & zamiast tego. Zobacz [C++ podstawowe wskazówki dotyczące R.36](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-const).

## <a name="declaration-group"></a>Deklaracja grupy

[C26426 NO_GLOBAL_INIT_CALLS](C26426.md) globalne inicjatora wywołuje funkcję z systemem innym niż constexpr "% % symbol". Zobacz [C++ podstawowe wskazówki dotyczące I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[C26427 NO_GLOBAL_INIT_EXTERNS](C26427.md) inicjatora globalnych uzyskuje dostęp do obiektu zewnętrzny "% % symbol". Zobacz [C++ podstawowe wskazówki dotyczące I.22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[C26444 NO_UNNAMED_RAII_OBJECTS](c26444.md) należy unikać bez nazwy obiektów z konstrukcji niestandardowych oraz zniszczenia. Zobacz [ES.84: nie (spróbuj) zadeklarować zmiennej lokalnej bez nazwy](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="class-group"></a>Klasa grupy

[C26432 DEFINE_OR_DELETE_SPECIAL_OPS](C26432.md) zdefiniuj lub usunąć wszelkie operacje domyślną w typie '% symbol %', zdefiniuj lub usunąć je wszystkie. Zobacz [C++ podstawowe wskazówki dotyczące C.21](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c21-if-you-define-or-delete-any-default-operation-define-or-delete-them-all).

[C26433 OVERRIDE_EXPLICITLY](c26433.md) funkcja "% % symbol" powinna być oznaczona jako "override". Zobacz [C.128: funkcji wirtualnych należy określić dokładnie jeden wirtualny, zastępowanie lub końcowego](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).

[C26434 DONT_HIDE_METHODS](C26434.md) funkcja "% symbol_1%" ukrywa-wirtualna funkcja "% symbol_2%". Zobacz [C++ podstawowe wskazówki dotyczące C.128](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).

[C26435 SINGLE_VIRTUAL_SPECIFICATION](c26435.md) funkcja "% % symbol" należy określić dokładnie jedną "virtual", "override" lub "final". Zobacz [C.128: funkcji wirtualnych należy określić dokładnie jeden wirtualny, zastępowanie lub końcowego](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).


[C26436 NEED_VIRTUAL_DTOR](C26436.md) typu '% symbol %' z funkcją wirtualną musi albo publiczny wirtualny lub chronionych niewirtualne — destruktor. Zobacz [C++ podstawowe wskazówki dotyczące C.35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c35-a-base-class-destructor-should-be-either-public-and-virtual-or-protected-and-nonvirtual).


[C26443 NO_EXPLICIT_DTOR_OVERRIDE](c26443.md) zastąpiona destruktor nie należy używać jawnego przesłaniania lub specyfikatory "virtual". Zobacz [C.128: funkcji wirtualnych należy określić dokładnie jeden wirtualny, zastępowanie lub końcowego](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).


## <a name="type-group"></a>Typ grupy

[C26437 DONT_SLICE](C26437.md) nie wycinka. Zobacz [C++ podstawowe wskazówki dotyczące ES.63](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es63-dont-slice).

## <a name="style-group"></a>Styl grupy

[C26438 NO_GOTO](C26438.md) uniknąć `goto`. Zobacz [C++ podstawowe wskazówki dotyczące ES.76](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es76-avoid-goto).

## <a name="function-group"></a>Grupy — funkcja

[C26439 SPECIAL_NOEXCEPT](C26439.md) tego typu funkcji nie może zgłaszać. Zadeklaruj `noexcept`. Zobacz [C++ podstawowe wskazówki dotyczące F.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[C26440 DECLARE_NOEXCEPT](C26440.md) funkcja "% % symbol" mogą być deklarowane `noexcept`. Zobacz [C++ podstawowe wskazówki dotyczące F.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[C26447 DONT_THROW_IN_NOEXCEPT](c26447.md) zadeklarowano funkcji **noexcept** , ale wywołuje funkcję, która może zgłaszać wyjątków.
Zobacz [C++ podstawowe wskazówki: F.6: Jeśli funkcja nie może zgłosić, Zadeklaruj ją noexcept](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

## <a name="concurrency-group"></a>Grupy WSPÓŁBIEŻNOŚCI

[C26441 NO_UNNAMED_GUARDS](C26441.md) obiektów strażnik musi mieć nazwę. Zobacz [C++ podstawowe wskazówki dotyczące cp.44](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cp44-remember-to-name-your-lock_guards-and-unique_locks).

## <a name="const-group"></a>CONST grupy

[C26460 USE_CONST_REFERENCE_ARGUMENTS](c26460.md) argument odwołania "% argumentu %" dla funkcji "% funkcji %" może być oznaczony jako `const`. Zobacz [C++ podstawowe wskazówki dotyczące con.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[C26461 USE_CONST_POINTER_ARGUMENTS](c26461.md): argument wskaźnika "% argumentu %" dla funkcji "% funkcji %" może być oznaczony jako wskaźnik do `const`. Zobacz [C++ podstawowe wskazówki dotyczące con.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[C26462 USE_CONST_POINTER_FOR_VARIABLE](c26462.md) wartość wskazywana przez "% Zmienna %" jest przypisane tylko raz, oznacz go jako wskaźnik do `const`. Zobacz [C++ podstawowe wskazówki dotyczące con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26463 USE_CONST_FOR_ELEMENTS](c26463.md) elementów tablicy % tablicy % przypisanych tylko raz, Oznacz elementy `const`. Zobacz [C++ podstawowe wskazówki dotyczące con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26464 USE_CONST_POINTER_FOR_ELEMENTS](c26464.md) wskazywana przez elementy tablicy % tablicy % są przypisane wartości tylko raz, elementy Oznacz jako wskaźnik do `const`. Zobacz [C++ podstawowe wskazówki dotyczące con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26496 USE_CONST_FOR_VARIABLE](c26496.md) zmiennej "% Zmienna %" jest przypisane tylko raz, oznacz go jako `const`. Zobacz [C++ podstawowe wskazówki dotyczące con.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26497 USE_CONSTEXPR_FOR_FUNCTION](c26497.md) tej funkcji % funkcji można oznaczyć `constexpr` w razie potrzeby jest ocena kompilacji. Zobacz [C++ podstawowe wskazówki dotyczące F.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rf-constexpr).

[C26498 USE_CONSTEXPR_FOR_FUNCTIONCALL](c26498.md) można użyć tej funkcji wywołania % funkcji % `constexpr` w razie potrzeby jest ocena kompilacji. Zobacz [C++ podstawowe wskazówki dotyczące con.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-constexpr).

## <a name="type-group"></a>Typ grupy

[C26465 NO_CONST_CAST_UNNECESSARY](c26465.md) nie używaj `const_cast` do rzutowania z usuwaniem `const`. `const_cast` nie jest wymagana. constness lub zmienności nie jest usuwany przez tę konwersję. Zobacz [C++ podstawowe wskazówki dotyczące Type.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-constcast).

[C26466 NO_STATIC_DOWNCAST_POLYMORPHIC](c26466.md) nie używaj `static_cast` downcasts. Rzutowanie z typem polimorficznym należy używać dynamic_cast. Zobacz [C++ podstawowe wskazówki dotyczące Type.2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-downcast).

[C26471 NO_REINTERPRET_CAST_FROM_VOID_PTR](c26471.md) nie używaj `reinterpret_cast`. Rzutowanie z void * można użyć `static_cast`. Zobacz [C++ podstawowe wskazówki dotyczące Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26472 NO_CASTS_FOR_ARITHMETIC_CONVERSION](C26472.md) nie używaj `static_cast` dla konwersje arytmetyczne. Użyj nawiasów klamrowych inicjowania, gsl::narrow_cast lub gsl::narow. Zobacz [C++ podstawowe wskazówki dotyczące Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26473 NO_IDENTITY_CAST](C26473.md) nie rzutowanie pomiędzy typami wskaźnika, gdy typu źródłowego i docelowego są takie same. Zobacz [C++ podstawowe wskazówki dotyczące Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26474 NO_IMPLICIT_CAST](C26474.md) nie rzutowanie pomiędzy typami wskaźnika podczas konwersji może być niejawnej. Zobacz [C++ podstawowe wskazówki dotyczące Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26475 NO_FUNCTION_STYLE_CASTS](C26475.md) nie należy używać funkcji stylu C rzutowania. Zobacz [C++ podstawowe wskazówki dotyczące ES.49](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es49-if-you-must-use-a-cast-use-a-named-cast).
 
[C26490 NO_REINTERPRET_CAST](c26490.md) nie używaj `reinterpret_cast`. Zobacz [C++ podstawowe wskazówki dotyczące Type.1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26491 NO_STATIC_DOWNCAST](c26490.md) nie używaj `static_cast` downcasts. Zobacz [C++ podstawowe wskazówki dotyczące Type.2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26492 NO_CONST_CAST](c26492.md) nie używaj `const_cast` do rzutowania z usuwaniem `const`. Zobacz [C++ podstawowe wskazówki dotyczące Type.3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26493 NO_CSTYLE_CAST](c26493.md) rzutowania w stylu języka C nie jest używany. Zobacz [C++ podstawowe wskazówki dotyczące Type.4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).
 
[C26494 VAR_USE_BEFORE_INIT](c26494.md) zmiennej "% Zmienna %" nie jest zainicjowany. Zawsze można zainicjować obiektu. Zobacz [C++ podstawowe wskazówki dotyczące Type.5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26495 MEMBER_UNINIT](c26495.md) zmiennej "% Zmienna %" nie jest zainicjowany. Zawsze można zainicjować zmiennej członkowskiej. Zobacz [C++ podstawowe wskazówki dotyczące Type.6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

## <a name="bounds-group"></a>Grupy granic

[C26446 USE_GSL_AT](c26446.md) wolą używać `gsl::at()` zamiast operatora indeksu dolnego niezaznaczone. Zobacz [C++ podstawowe wskazówki: Bounds.4: nie używaj funkcji biblioteki standardowe i typy, które nie są sprawdzane granice](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

[C26481 NO_POINTER_ARITHMETIC](C26481.md).
Nie używaj arytmetyki wskaźnika. Zamiast tego użyj zakresu. Zobacz [Bounds.1 wytyczne C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26482 NO_DYNAMIC_ARRAY_INDEXING](c26482.md) tylko indeksowanie tablic za pomocą wyrażenia stałe. Zobacz [Bounds.2 wytyczne C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26483 STATIC_INDEX_OUT_OF_RANGE](c26483.md) wartość % wartość jest poza zakresem (0, powiązane %) zmiennej "% Zmienna %". Tylko indeks do tablic za pomocą wyrażenia stałe, które znajdują się w granice tablicy. Zobacz [Bounds.2 wytyczne C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md) wyrażenie "% wyrażenie %": nie tablicy na wskaźnik zniszczenie. Zobacz [Bounds.3 wytyczne C++ Core](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

## <a name="gsl-group"></a>GSL grupy

[C26445 NO_SPAN_REF](c26445.md) odwołania do `gsl::span` lub `std::string_view` może wskazywać na problem okres istnienia.
Zobacz [C++ podstawowe wskazówki dotyczące GSL.view: widoków](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views)

[C26446 USE_GSL_AT](c26446.md) wolą używać `gsl::at()` zamiast operatora indeksu dolnego niezaznaczone. Zobacz [C++ podstawowe wskazówki: Bounds.4: nie używaj funkcji biblioteki standardowe i typy, które nie są sprawdzane granice](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

[C26448 USE_GSL_FINALLY ](c26448.md) Rozważ użycie `gsl::finally` Jeśli końcowego Akcja. Zobacz [wytyczne C++ Core: GSL.util: narzędzia](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-utilities).

[C26449 NO_SPAN_FROM_TEMPORARY](c26449.md) 
 `gsl::span` lub `std::string_view` utworzone na podstawie tymczasowej jest nieprawidłowy gdy tymczasowy zostało unieważnione. Zobacz [wytyczne C++ Core: GSL.view: widoki](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views).


## <a name="deprecated-warnings"></a>Przestarzałe ostrzeżenia

Następujące ostrzeżenia są obecne w wczesne zestaw reguł eksperymentalne core sprawdzania wytyczne, ale obecnie są przestarzałe i można zignorować. W przypadku ostrzeżenia są ostrzeżenia z listy powyżej.

- 26412 DEREF_INVALID_POINTER
- 26413 DEREF_NULLPTR
- 26420 ASSIGN_NONOWNER_TO_EXPLICIT_OWNER
- 26421 ASSIGN_VALID_OWNER
- 26422 VALID_OWNER_LEAVING_SCOPE
- 26423 ALLOCATION_NOT_ASSIGNED_TO_OWNER
- 26424 VALID_ALLOCATION_LEAVING_SCOPE
- 26425 ASSIGNING_TO_STATIC
- 26499 NO_LIFETIME_TRACKING

## <a name="see-also"></a>Zobacz też
[Przy użyciu programy wytyczne C++ Core](using-the-cpp-core-guidelines-checkers.md)
