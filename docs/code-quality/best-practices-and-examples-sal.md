---
title: Najlepsze praktyki i przykłady (SAL) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d8910c9b5d36cecec82bf0e386e294759113c76e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="best-practices-and-examples-sal"></a>Najlepsze praktyki i przykłady (SAL)
Poniżej przedstawiono kilka sposobów maksymalne poza języka adnotacji kodu źródłowego (SAL) i uniknąć niektórych typowych problemów.

## <a name="in"></a>\_In\_

Jeśli funkcja powinien zapisać do elementu, użyj `_Inout_` zamiast `_In_`. Jest to szczególnie istotne w przypadku zautomatyzowanych konwersji starsze makra na SAL. Przed SAL, wielu programistów użyć makra jako komentarze — makra, które zostały o nazwie `IN`, `OUT`, `IN_OUT`, lub wariantów te nazwy. Mimo że firma Microsoft zaleca przekonwertowanie tych makr SAL, również zalecamy należy zachować ostrożność podczas konwertowania ich ponieważ kod może zmieniły się od oryginalnej prototypu zostało zapisane, a stare makro może nie odzwierciedlają, co oznacza kod. Należy zachować szczególną ostrożność o `OPTIONAL` komentarz makro ponieważ często jest niepoprawnie umieszczona — na przykład po stronie niewłaściwy przecinkami.

```cpp

// Incorrect
void Func1(_In_ int *p1)
{
    if (p1 == NULL)
        return;

    *p1 = 1;
}

// Correct
void Func2(_Inout_ PCHAR p1)
{
    if (p1 == NULL)
        return;

    *p1 = 1;
}
```

## <a name="opt"></a>\_opt\_

Jeśli element wywołujący nie może przekazać wskaźnika o wartości null, użyj `_In_` lub `_Out_` zamiast `_In_opt_` lub `_Out_opt_`. Dotyczy to nawet funkcję, która sprawdza jego parametrów i zwraca błąd, jeśli ma wartość NULL, gdy nie ma. Mimo że pełniących funkcję Sprawdź jej parametr Nieoczekiwana wartość NULL, a zwracany bezpiecznie dobrych praktyk kodowania obrony, nie oznacza to, że adnotacja parametru może być opcjonalny typu (`_*Xxx*_opt_`).

```cpp

// Incorrect
void Func1(_Out_opt_ int *p1)
{
    *p = 1;
}

// Correct
void Func2(_Out_ int *p1)
{
    *p = 1;
}

```

## <a name="predefensive-and-postdefensive"></a>\_Wstępnie\_obrony\_ i \_Post\_obrony\_

Jeśli funkcja znajduje się w granicy zaufania i firma Microsoft zaleca użycie `_Pre_defensive_` adnotacji.  Modyfikator "obrony" modyfikuje niektórych adnotacje wskazanie, że w punkcie połączenia, ściśle powinna być sprawdzana interfejsu, ale w treści implementacji go powinien zakłada, niepoprawne parametry mogą być przekazywane. W takim przypadku `_In_ _Pre_defensive_` jest preferowana w granicy zaufania, aby wskazać, że chociaż obiekt wywołujący spowoduje błąd, gdy podejmowana jest próba przekazania wartości NULL, treść funkcji będzie analizować tak, jakby parametru może być NULL, a wszelkie próby odwołania do wskaźnika bez uprzedniego zostaną oflagowane sprawdzanie wartości NULL.  A `_Post_defensive_` adnotacji jest również dostępny do użycia w wywołań zwrotnych, gdzie zaufaną stronę zakłada, że obiekt wywołujący, a kodzie niezaufanym wywoływanego kodu.

## <a name="outwrites"></a>\_Limit\_zapisuje\_

W poniższym przykładzie pokazano wspólnej nadużycie `_Out_writes_`.

```cpp

// Incorrect
void Func1(_Out_writes_(size) CHAR *pb,
    DWORD size
);

```

Adnotacja `_Out_writes_` oznacza, że masz buforu. Ma ona `cb` bajtów przydzielonych z pierwszego bajtu zainicjowana na wyjściu. Ta adnotacja nie jest ściśle niewłaściwy i warto express przydzielony rozmiar. Ile elementów są inicjowane przez funkcję nie jednak sprawdzić.

W kolejnym przykładzie pokazano trzy sposoby poprawne, aby w pełni określić rozmiarze zainicjowane część buforu.

```cpp

// Correct
void Func1(_Out_writes_to_(size, *pCount) CHAR *pb,
    DWORD size,
    PDWORD pCount
);

void Func2(_Out_writes_all_(size) CHAR *pb,
    DWORD size
);

void Func3(_Out_writes_(size) PSTR pb,
    DWORD size
);

```

## <a name="out-pstr"></a>\_Limit\_ PSTR

Korzystanie z `_Out_ PSTR` prawie zawsze jest nieprawidłowy. To jest interpretowany jako mający parametru wyjściowego wskazujące buforu znaków i jest zerem.

```cpp

// Incorrect
void Func1(_Out_ PSTR pFileName, size_t n);

// Correct
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);

```

Adnotacja, takich jak `_In_ PCSTR` jest typowe i przydatne. Wskazuje ciąg wejściowy, który ma zakończenia o wartości NULL, ponieważ warunek wstępny programu `_In_` umożliwia rozpoznawania ciąg znaków zakończony znakiem NULL.

## <a name="in-wchar-p"></a>\_W\_ WCHAR * p

`_In_ WCHAR* p` jest wejściowe wskaźnika `p` wskazującego na jeden znak. Jednak w większości przypadków, to prawdopodobnie nie jest specyfikacji, którego dotyczy. Zamiast tego co prawdopodobnie jest przeznaczona jest specyfikacji tablicy zerem; Aby to zrobić, należy użyć `_In_ PWSTR`.

```cpp

// Incorrect
void Func1(_In_ WCHAR* wszFileName);

// Correct
void Func2(_In_ PWSTR wszFileName);

```

Brak prawidłowego specyfikacji o wartości NULL jest często. Użyj odpowiedniej `STR` wersji, aby zastąpić ten typ, jak pokazano w poniższym przykładzie.

```cpp

// Incorrect
BOOL StrEquals1(_In_ PCHAR p1, _In_ PCHAR p2)
{
    return strcmp(p1, p2) == 0;
}

// Correct
BOOL StrEquals2(_In_ PSTR p1, _In_ PSTR p2)
{
    return strcmp(p1, p2) == 0;
}

```

## <a name="outrange"></a>\_Out_range\_

Jeśli parametr jest wskaźnik i chcesz express zakresie wartości elementu, który jest wskazywany przez wskaźnik, należy użyć `_Deref_out_range_` zamiast `_Out_range_`. W poniższym przykładzie zakres * pcbFilled jest wyrażona, nie pcbFilled.

```cpp

// Incorrect
void Func1(
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,
    DWORD cbSize,
    _Out_range_(0, cbSize) DWORD *pcbFilled
);

// Correct
void Func2(
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,
    DWORD cbSize,
    _Deref_out_range_(0, cbSize) _Out_ DWORD *pcbFilled
);

```

 `_Deref_out_range_(0, cbSize)` nie jest ścisłym wymogiem niektórych narzędzi, ponieważ nie można go wywnioskować z `_Out_writes_to_(cbSize,*pcbFilled)`, ale są wyświetlane tutaj aby informacje były kompletne.

## <a name="wrong-context-in-when"></a>Nieprawidłowy kontekst w \_po\_

Inny powszechnym błędem jest ocena po wprowadzeniu stanu na potrzeby warunków wstępnych. W poniższym przykładzie `_Requires_lock_held_` jest warunkiem wstępnym.

```cpp

// Incorrect
_When_(return == 0, _Requires_lock_held_(p->cs))
int Func1(_In_ MyData *p, int flag);

// Correct
_When_(flag == 0, _Requires_lock_held_(p->cs))
int Func2(_In_ MyData *p, int flag);

```

 Wyrażenie `result` odnosi się do wartości po stanu, który nie jest dostępny w stanie wstępnego.

## <a name="true-in-success"></a>Wartość TRUE w \_Powodzenie\_

Jeśli funkcja zakończy się powodzeniem, gdy zwracana wartość jest różna od zera, należy użyć `return != 0` warunkiem powodzenia zamiast `return == TRUE`. NonZero nie musi oznaczać równoważność, do rzeczywistych wartością udostępnioną przez kompilator dla `TRUE`. Parametr `_Success_` wyrażenie i następujących wyrażeń są oceniane jako równoważne: `return != 0`, `return != false`, `return != FALSE`, i `return` bez parametrów lub porównania.

```cpp

// Incorrect
_Success_(return == TRUE, _Acquires_lock_(*lpCriticalSection))
BOOL WINAPI TryEnterCriticalSection(
  _Inout_ LPCRITICAL_SECTION lpCriticalSection
);

// Correct
_Success_(return != 0, _Acquires_lock_(*lpCriticalSection))
BOOL WINAPI TryEnterCriticalSection(
  _Inout_ LPCRITICAL_SECTION lpCriticalSection
);

```

## <a name="reference-variable"></a>Odwołanie do zmiennej

Odwołanie do zmiennej, poprzedniej wersji SAL używany domniemanych wskaźnika jako element docelowy adnotacji i wymagane dodanie `__deref` do adnotacji, dołączone do zmiennej odwołania. Ta wersja używa samego obiektu i nie wymaga dodatkowych `_Deref_`.

```cpp

// Incorrect
void Func1(
    _Out_writes_bytes_all_(cbSize) BYTE *pb,
    _Deref_ _Out_range_(0, 2) _Out_ DWORD &cbSize
);

// Correct
void Func2(
    _Out_writes_bytes_all_(cbSize) BYTE *pb,
    _Out_range_(0, 2) _Out_ DWORD &cbSize
);

```

## <a name="annotations-on-return-values"></a>Adnotacje w zwracanych wartości

Poniższy przykład przedstawia to powszechny problem w adnotacjach zwracanej wartości.

```cpp

// Incorrect
_Out_opt_ void *MightReturnNullPtr1();

// Correct
_Ret_maybenull_ void *MightReturnNullPtr2();

```

W tym przykładzie `_Out_opt_` mówi wskaźnik może mieć wartości NULL jako część warunki wstępne. Jednak warunki wstępne nie można zastosować do wartości zwracanej. W tym przypadku jest poprawna adnotacji `_Ret_maybenull_`.

## <a name="see-also"></a>Zobacz także

[Korzystanie z adnotacji SAL w celu redukowanie defektów kodu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
[opis SAL](../code-quality/understanding-sal.md)
[Dodawanie adnotacji do parametrów funkcji i zwracanych wartości](../code-quality/annotating-function-parameters-and-return-values.md) 
 [Zachowanie funkcji dodawania adnotacji](../code-quality/annotating-function-behavior.md)
[Dodawanie adnotacji do struktur i klas](../code-quality/annotating-structs-and-classes.md)
[Dodawanie adnotacji do zachowania blokującego](../code-quality/annotating-locking-behavior.md) 
 [Określenie, kiedy i gdzie dotyczy adnotacji](../code-quality/specifying-when-and-where-an-annotation-applies.md)
[funkcje wewnętrzne](../code-quality/intrinsic-functions.md)