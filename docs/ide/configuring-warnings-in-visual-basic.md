---
title: 'Konfigurowanie ostrzeżeń w Visual Basic:'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Basic], warnings
- run-time errors, warnings
- warnings, configuring
ms.assetid: 99cf4781-bd4d-47b4-91b9-217933509f82
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fa98e9b9b66f863915e120c2c31b0ab508c9929f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="configuring-warnings-in-visual-basic"></a>Konfigurowanie ostrzeżeń w Visual Basic

[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Kompilatora zawiera zestaw ostrzeżenia dotyczące kodu, który może powodować błędy środowiska wykonawczego. Tych informacji umożliwia zapis czyszcząca, szybciej, lepiej kodu przy użyciu mniejszej liczby błędów. Na przykład kompilator spowoduje wygenerowanie ostrzeżenia, gdy użytkownik próbuje wywołać elementu członkowskiego zmiennej obiektu nieprzypisane zwrócone z funkcji bez ustawienia zwracanej wartości, lub wykonać `Try` bloku błędów w logice przechwytują wyjątki.

 Czasami kompilator zapewnia dodatkowe logiki w imieniu użytkownika, dzięki czemu użytkownik może skupić się na wykonywanego zadania, a nie na przewidywanie możliwych błędów. W poprzednich wersjach [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], **Option Strict** zostało użyte do ograniczania dodatkową logikę który [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] zapewnia kompilatora. Konfigurowanie ostrzeżeń umożliwia ograniczenie tę logikę w sposób bardziej szczegółowego, na poziomie ostrzeżeń indywidualnych.

 Można dostosować projekt i wyłączyć ostrzeżenia nie zapewnienie im dostępu do aplikacji, włączając inne ostrzeżenia błędy w. Ta strona wyjaśniono, jak włączyć ostrzeżeń indywidualnych i wyłączyć.

## <a name="turning-warnings-off-and-on"></a>Włączanie i Włącz ostrzeżenia
 Istnieją dwa różne sposoby konfigurowania ostrzeżenia: można skonfigurować przy użyciu **projektanta projektu**, albo użyć **/warnaserror** i **/nowarn** — opcje kompilatora .

 **Skompilować** karcie **projektanta projektu** strony można włączyć ostrzeżenia i wyłączyć. Wybierz **Wyłącz wszystkie ostrzeżenia** Sprawdź pole, aby wyłączyć wszystkie ostrzeżenia; wybierz **traktuje wszystkie ostrzeżenia jako błędy** na traktowanie wszystkich ostrzeżeń jako błędy. Niektóre ostrzeżeń indywidualnych można przełączać jako błąd lub ostrzeżenie pożądane w tabeli.

 Gdy **Option Strict** ustawiono **poza**, **Option Strict** powiązane ostrzeżenia nie może być traktowana niezależnie od siebie nawzajem. Gdy **Option Strict** ustawiono **na**, skojarzone ostrzeżenia są traktowane jako błędy, nie ma znaczenia ich stan jest. Gdy **Option Strict** ma ustawioną wartość **niestandardowy** , określając `/optionstrict:custom` kompilatora wiersza polecenia **Option Strict** ostrzeżenia mogą być włączone lub wyłączone niezależnie.

 **/Warnaserror** opcji wiersza polecenia kompilatora można również określić, czy ostrzeżenia są traktowane jako błędy. Lista rozdzielona przecinkami można dodać do tę opcję, aby określić, które ostrzeżenia powinny być traktowane jako błędy lub ostrzeżenia przy użyciu + lub -. W poniższej tabeli przedstawiono możliwe opcje.

|Opcja wiersza polecenia|Określa|
|--------------------------|---------------|
|`/warnaserror+`|Traktuje wszystkie ostrzeżenia jako błędy|
|`/warnsaserror`-|Traktuje jako ostrzeżenia jako błędy. Domyślnie włączone.|
|`/warnaserror+:<warning list``>`|Traktuj konkretne ostrzeżenia jako błędy wyświetlane według ich identyfikator błędu w lista rozdzielona przecinkami r.|
|`/warnaserror-:<warning list>`|Nie Traktuj konkretne ostrzeżenia jako błędy wyświetlane według ich identyfikator błąd na liście rozdzielone przecinkami.|
|`/nowarn`|Nie zgłaszaj ostrzeżenia.|
|`/nowarn:<warning list>`|Nie zgłaszaj określonych ostrzeżeń, wyświetlane według ich identyfikator błąd na liście rozdzielone przecinkami.|

 Lista ostrzeżenie zawiera błąd identyfikatorów, które powinny być traktowane jako błędy, które mogą być używane z opcjami wiersza polecenia do Włącz określone ostrzeżenia lub wyłącz ostrzeżenia. Jeśli na liście ostrzeżenie zawiera nieprawidłową liczbę, jest zgłaszany błąd.

## <a name="examples"></a>Przykłady
 Tej tabeli przedstawiono przykłady argumenty wiersza polecenia opisano, co oznacza każdy argument.

|Argument|Opis|
|--------------|-----------------|
|`vbc /warnaserror`|Określa, że wszystkie ostrzeżenia powinny być traktowane jako błędy.|
|`vbc /warnaserror:42024`|Określa, że ostrzeżenie 42024 powinny być traktowane jako błąd.|
|`vbc /warnaserror:42024,42025`|Określa, że ostrzeżenia 42024 i 42025 powinny być traktowane jako błędy.|
|`vbc /nowarn`|Określa, należy podać żadnych ostrzeżeń.|
|`vbc /nowarn:42024`|Określa, że ostrzeżenie 42024 nie powinny być zgłaszane.|
|`vbc /nowarn:42024,42025`|Określa, czy ostrzeżenia 42024 i 42025 nie powinny być raportowane.|

## <a name="types-of-warnings"></a>Typy ostrzeżenia
 Poniżej przedstawiono listę ostrzeżeń, które można traktować jako błędy.

### <a name="implicit-conversion-warning"></a>Ostrzeżenie niejawna konwersja
 Generowane w przypadku wystąpienia niejawnej konwersji. Obejmują one niejawną konwersję z typu liczbowego wewnętrznej na ciąg przy użyciu `&` operatora. Domyślne dla nowych projektów jest wyłączona.

 ID: 42016

### <a name="late-bound-method-invocation-and-overload-resolution-warning"></a>Powiązany wywołania metody i ostrzeżenie rozpoznawanie przeciążenia
 Wygenerowany dla wystąpień z późnym wiązaniem. Domyślne dla nowych projektów jest wyłączona.

 ID: 42017

### <a name="operands-of-type-object-warnings"></a>Argumenty operacji typu "Object" ostrzeżeń
 Generowane, gdy argumentów operacji typu `Object` wystąpić, który spowodować błąd **Option Strict On**. Domyślne dla nowych projektów jest na.

 Identyfikator: 42018 i 42019

### <a name="declarations-require-as-clause-warnings"></a>Deklaracje wymagają ostrzeżenia klauzuli "As"
 Generowane, gdy zmienna, funkcji lub Brak deklaracji właściwości `As` klauzuli czy utworzono błąd **Option Strict On**. Zmienne, które nie mają typu przypisanego są rozpatrywane typu `Object`. Domyślne dla nowych projektów jest na.

 Identyfikator: 42020 (deklaracji zmiennej), 42021 (deklaracji funkcji) i 42022 (deklaracji właściwości).

### <a name="possible-null-reference-exception-warnings"></a>Ostrzeżenia wyjątek możliwe odwołanie o wartości null
 Generowane, gdy zmienna jest używana, zanim została do niej przypisana wartość. Domyślne dla nowych projektów jest na.

 ID: 42104, 42030

### <a name="unused-local-variable-warning"></a>Nieużywane ostrzeżenie zmiennej lokalnej
 Generowane, gdy zmienna lokalna jest zadeklarowane, ale nigdy nie jest określone. Domyślnie jest na.

 ID: 42024

### <a name="access-of-shared-member-through-instance-variable-warning"></a>Dostęp do udostępnionego elementu członkowskiego za pomocą ostrzeżenie zmiennej wystąpienia
 Generowane, gdy dostęp do udostępnionego elementu członkowskiego za pośrednictwem wystąpienia może mieć efekty uboczne lub podczas uzyskiwania dostępu do udostępnionego elementu członkowskiego za pośrednictwem zmiennej wystąpienia nie jest prawa strona wyrażenia lub jest przekazywany jako parametr. Domyślne dla nowych projektów jest na.

 ID: 42025

### <a name="recursive-operator-or-property-access-warnings"></a>Ostrzeżenia dostępu operatora lub właściwość cykliczne
 Generowane, gdy treść procedury używa tego samego operator lub właściwości, który jest zdefiniowany w. Domyślne dla nowych projektów jest na.

 Identyfikator: 42004 (operator), 42026 (właściwość)

### <a name="function-or-operator-without-return-value-warning"></a>Funkcja lub operator bez zwracają wartość Ostrzeżenie
 Generowane, gdy funkcja lub operator nie ma określonej wartości zwracanej. Dotyczy to również pominięcie `Set` do niejawnego zmiennej lokalnej o takiej samej nazwie jak funkcja. Domyślne dla nowych projektów jest na.

 Identyfikator: 42105 (funkcja), 42016 (operator)

### <a name="overloads-modifier-used-in-a-module-warning"></a>Modyfikator przeciążenia używany w module ostrzeżenie
 Generowane, gdy `Overloads` jest używany w `Module`. Domyślne dla nowych projektów jest na.

 ID: 42028

### <a name="duplicate-or-overlapping-catch-blocks-warnings"></a>Zduplikowany lub nakładający się ostrzeżenia bloki catch
 Generowane, gdy `Catch` bloku nigdy nie został osiągnięty z powodu jego relacji z innymi `Catch` bloków, które zostały zdefiniowane. Domyślne dla nowych projektów jest na.

 ID: 42029, 42031

## <a name="see-also"></a>Zobacz także

- [Error — typy](/dotnet/visual-basic/programming-guide/language-features/error-types)
- [Try... CATCH... Finally — instrukcja](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)
- [/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn)
- [/ warnaserror (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/warnaserror)
- [Strona kompilowania, Projektant projektu (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md)
- [Są domyślnie wyłączone ostrzeżenia kompilatora](/cpp/preprocessor/compiler-warnings-that-are-off-by-default)