---
title: Wstawki kodu C#
ms.date: 06/05/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- snippets [C#]
- code snippets [C#]
- Code Snippet Inserter [C#]
- C#, code snippets
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: b9d494b1fb6465c1cf246f6becb9b812115e6076
ms.sourcegitcommit: a8e01952be5a539104e2c599e9b8945322118055
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="c-code-snippets"></a>Wstawki kodu C#

Wstawki kodu są gotowe do użycia wstawki kodu, który można szybko wstawić do kodu. Na przykład `for` fragment kodu tworzy pustą `for` pętli. Niektóre fragmenty kodu są Otocz wstawki kodu, które umożliwia wybór wierszy kodu, a następnie wybierz fragment kodu, który zawiera wybranych wierszy kodu. Na przykład, gdy należy wybrać wiersze kodu i aktywować `for` fragment kodu tworzy `for` pętli z tych wierszy kodu wewnątrz bloku pętli. Wstawki kodu można ustawić program pisania kodu, szybsze, łatwiejsze i bardziej niezawodny.

 Wstawianie wstawek kodu w lokalizacji kursora lub wstawić fragment kodu Otocz wokół aktualnie zaznaczonego kodu. Wstawianie wstawek kodu jest wywoływany przez **wstawianie fragmentu kodu** lub **z funkcji Otocz przez** polecenia w **IntelliSense** menu lub za pomocą skrótów klawiaturowych  **CTRL**+**K**,**X** lub **Ctrl**+**K**,**S** odpowiednio.

 **Wstawianie wstawek kodu** Wyświetla nazwę wstawki kodu dla wszystkich wstawki kodu dostępne. Wstawianie wstawek kodu zawiera również — okno dialogowe wejściowych wpisuje nazwę fragmentu kodu lub część nazwy fragment kodu. Wstawianie wstawek kodu prezentuje najlepiej pasuje do nazwy fragment kodu. Naciśnięcie przycisku **kartę** w dowolnym momencie spowoduje odrzucenie Wstawianie wstawek kodu i wstawianie fragmentu kodu aktualnie zaznaczonego. Naciśnięcie przycisku **Esc** lub kliknięcie przycisku myszy w edytorze kodu będzie odrzucać Wstawianie wstawek kodu bez wstawianie fragmentu kodu.

## <a name="default-code-snippets"></a>Domyślne wstawki kodu

Domyślnie poniższe fragmenty kodu są zawarte w programie Visual Studio dla C#.

|Nazwa (lub skrót)|Opis|Prawidłowe lokalizacje, aby wstawić fragment kodu|
|--------------------------|-----------------|---------------------------------------|
|#if|Tworzy [#if](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-if) dyrektywy i [#endif](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endif) dyrektywy.|W dowolnym miejscu.|
|#region|Tworzy [#region](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-region) dyrektywy i [#endregion](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endregion) dyrektywy.|W dowolnym miejscu.|
|~|Tworzy [finalizator](/dotnet/csharp/programming-guide/classes-and-structs/destructors) (destruktor) zawierające klasy.|Wewnątrz klasy.|
|— atrybut|Tworzy oświadczenie dla klasy, która jest pochodną <xref:System.Attribute>.|W przestrzeni nazw (w tym globalnej przestrzeni nazw), klasy lub struktury.|
|checked|Tworzy [zaznaczone](/dotnet/csharp/language-reference/keywords/checked) bloku.|Wewnątrz metody, indeksatora, Metoda dostępu do właściwości lub metody dostępu zdarzenia.|
|class|Tworzy deklaracji klasy.|W przestrzeni nazw (w tym globalnej przestrzeni nazw), klasy lub struktury.|
|ctor|Tworzy konstruktora dla klasy zawierającego.|Wewnątrz klasy.|
|cw|Tworzy wywołanie <xref:System.Console.WriteLine%2A>.|Wewnątrz metody, indeksatora, Metoda dostępu do właściwości lub metody dostępu zdarzenia.|
|do|Tworzy [czy](/dotnet/csharp/language-reference/keywords/do) `while` pętli.|Wewnątrz metody, indeksatora, Metoda dostępu do właściwości lub metody dostępu zdarzenia.|
|else|Tworzy [else](/dotnet/csharp/language-reference/keywords/if-else) bloku.|Wewnątrz metody, indeksatora, Metoda dostępu do właściwości lub metody dostępu zdarzenia.|
|enum|Tworzy [wyliczenia](/dotnet/csharp/language-reference/keywords/enum) deklaracji.|W przestrzeni nazw (w tym globalnej przestrzeni nazw), klasy lub struktury.|
|equals|Tworzy deklaracji metody, która zastępuje <xref:System.Object.Equals%2A> metody zdefiniowanej w <xref:System.Object> klasy.|Wewnątrz klasy lub struktury.|
|Wyjątek|Tworzy deklaracji klasy, która pochodzi z wyjątek (<xref:System.Exception> domyślnie).|W przestrzeni nazw (w tym globalnej przestrzeni nazw), klasy lub struktury.|
|dla|Tworzy [dla](/dotnet/csharp/language-reference/keywords/for) pętli.|Wewnątrz metody, indeksatora, Metoda dostępu do właściwości lub metody dostępu zdarzenia.|
|foreach|Tworzy [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) pętli.|Wewnątrz metody, indeksatora, Metoda dostępu do właściwości lub metody dostępu zdarzenia.|
|forr|Tworzy [dla](/dotnet/csharp/language-reference/keywords/for) pętli tego zmniejsza zmienna pętli for po każdej iteracji.|Wewnątrz metody, indeksatora, Metoda dostępu do właściwości lub metody dostępu zdarzenia.|
|if|Tworzy [Jeśli](/dotnet/csharp/language-reference/keywords/if-else) bloku.|Wewnątrz metody, indeksatora, Metoda dostępu do właściwości lub metody dostępu zdarzenia.|
|indeksator|Tworzy deklaracji indeksatora.|Wewnątrz klasy lub struktury.|
|interface|Tworzy [interfejsu](/dotnet/csharp/language-reference/keywords/interface) deklaracji.|W przestrzeni nazw (w tym globalnej przestrzeni nazw), klasy lub struktury.|
|Wywołania|Tworzy blok bezpiecznie wywołująca zdarzenie.|Wewnątrz metody, indeksatora, Metoda dostępu do właściwości lub metody dostępu zdarzenia.|
|iterator|Tworzy iteratora.|Wewnątrz klasy lub struktury.|
|iterindex|Tworzy parę "o nazwie" iterator i indeksatora przy użyciu klasy zagnieżdżonej.|Wewnątrz klasy lub struktury.|
|lock|Tworzy [blokady](/dotnet/csharp/language-reference/keywords/lock-statement) bloku.|Wewnątrz metody, indeksatora, Metoda dostępu do właściwości lub metody dostępu zdarzenia.|
|mbox|Tworzy wywołanie <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName>. Może być konieczne dodanie odwołania do *System.Windows.Forms.dll*.|Wewnątrz metody, indeksatora, Metoda dostępu do właściwości lub metody dostępu zdarzenia.|
|— przestrzeń nazw|Tworzy [przestrzeni nazw](/dotnet/csharp/language-reference/keywords/namespace) deklaracji.|W obszarze nazw (w tym globalnej przestrzeni nazw).|
|Prop|Tworzy [automatycznie implementowana właściwość](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties) deklaracji.|Wewnątrz klasy lub struktury.|
|propfull|Tworzy deklaracji właściwości z `get` i `set` metody dostępu.|Wewnątrz klasy lub struktury.|
|propg|Tworzy tylko do odczytu [automatycznie implementowanej właściwości](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties) z prywatnej `set` metody dostępu.|Wewnątrz klasy lub struktury.|
|SIM|Tworzy [statycznych](/dotnet/csharp/language-reference/keywords/static) [int](/dotnet/csharp/language-reference/keywords/int) deklaracji metody Main.|Wewnątrz klasy lub struktury.|
|struktura |Tworzy [struktury](/dotnet/csharp/language-reference/keywords/struct) deklaracji.|W przestrzeni nazw (w tym globalnej przestrzeni nazw), klasy lub struktury.|
|svm|Tworzy [statycznych](/dotnet/csharp/language-reference/keywords/static) [void](/dotnet/csharp/language-reference/keywords/void) deklaracji metody Main.|Wewnątrz klasy lub struktury.|
|— przełącznik|Tworzy [przełącznika](/dotnet/csharp/language-reference/keywords/switch) bloku.|Wewnątrz metody, indeksatora, Metoda dostępu do właściwości lub metody dostępu zdarzenia.|
|Spróbuj|Tworzy [try-catch](/dotnet/csharp/language-reference/keywords/try-catch) bloku.|Wewnątrz metody, indeksatora, Metoda dostępu do właściwości lub metody dostępu zdarzenia.|
|tryf|Tworzy [try-finally](/dotnet/csharp/language-reference/keywords/try-finally) bloku.|Wewnątrz metody, indeksatora, Metoda dostępu do właściwości lub metody dostępu zdarzenia.|
|unchecked|Tworzy [niezaznaczone](/dotnet/csharp/language-reference/keywords/unchecked) bloku.|Wewnątrz metody, indeksatora, Metoda dostępu do właściwości lub metody dostępu zdarzenia.|
|unsafe|Tworzy [niebezpieczne](/dotnet/csharp/language-reference/keywords/unsafe) bloku.|Wewnątrz metody, indeksatora, Metoda dostępu do właściwości lub metody dostępu zdarzenia.|
|korzystanie|Tworzy [przy użyciu](/dotnet/csharp/language-reference/keywords/using-directive) dyrektywy.|W obszarze nazw (w tym globalnej przestrzeni nazw).|
|while|Tworzy [podczas](/dotnet/csharp/language-reference/keywords/while) pętli.|Wewnątrz metody, indeksatora, Metoda dostępu do właściwości lub metody dostępu zdarzenia.|

## <a name="see-also"></a>Zobacz także

- [Funkcje wstawek kodu](../ide/code-snippet-functions.md)
- [Fragmenty kodu](../ide/code-snippets.md)
- [Parametry szablonu](../ide/template-parameters.md)
- [Porady: Użyj Otocz wstawki kodu](../ide/how-to-use-surround-with-code-snippets.md)