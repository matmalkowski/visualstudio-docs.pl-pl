---
title: Wstawki kodu Visual C# | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 06/05/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- snippets [C#], default snippets
- snippets [C#], Code Snippet Inserter
- Code Snippet Inserter [J#]
- Code Snippet Inserter [C#]
- Visual C#, default snippets
ms.assetid: dbea3dd6-e650-4190-b874-c9f097d7de6e
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 72e0e00fb5495946adcd7f47de8cdc2d6e0d32dc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="visual-c-code-snippets"></a>Wstawki kodu Visual C#
Wstawki kodu są gotowe do użycia wstawki kodu, który można szybko wstawić do kodu. Na przykład `for` fragment kodu tworzy pustą `for` pętli. Niektóre fragmenty kodu są Otocz wstawki kodu, które umożliwia wybór wierszy kodu, a następnie wybierz fragment kodu, który zawiera wybranych wierszy kodu. Na przykład, gdy należy wybrać wiersze kodu i aktywować `for` fragment kodu tworzy `for` pętli z tych wierszy kodu wewnątrz bloku pętli. Wstawki kodu można ustawić program pisania kodu, szybsze, łatwiejsze i bardziej niezawodny.  

 Wstawianie wstawek kodu w lokalizacji kursora lub wstawić fragment kodu Otocz wokół aktualnie zaznaczonego kodu. Wstawianie wstawek kodu jest wywoływany przez **wstawianie fragmentu kodu** lub **z funkcji Otocz przez** polecenia w **IntelliSense** menu lub przy użyciu klawiszy skrótu CTRL + K a następnie X lub CTRL + K, a następnie S odpowiednio.  

 Wstawianie wstawek kodu wyświetla nazwę wstawki kodu dla wszystkich wstawki kodu dostępne. Wstawianie wstawek kodu zawiera również — okno dialogowe wejściowych wpisuje nazwę fragmentu kodu lub część nazwy fragment kodu. Wstawianie wstawek kodu prezentuje najlepiej pasuje do nazwy fragment kodu. Naciśnięcie klawisza TAB w dowolnym momencie odrzucić Wstawianie wstawek kodu i wstawianie fragmentu kodu aktualnie zaznaczony kod. Wstawianie wstawek kodu zostanie odrzucić wpisując ESC lub kliknięcie przycisku myszy w edytorze kodu bez wstawiania wstawek kodu.  

## <a name="default-code-snippets"></a>Domyślne wstawki kodu  
 Domyślnie poniższe fragmenty kodu są uwzględniane w Visual Studio.  

|Nazwa (lub skrót)|Opis|Prawidłowe lokalizacje, aby wstawić fragment kodu|  
|--------------------------|-----------------|---------------------------------------|  
|#if|Tworzy [#if](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-if) dyrektywy i [#endif](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endif) dyrektywy.|W dowolnym miejscu.|  
|#region|Tworzy [#region](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-region) dyrektywy i [#endregion](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endregion) dyrektywy.|W dowolnym miejscu.|  
|~|Tworzy destruktor dla elementu zawierającego klasy.|Wewnątrz klasy.|  
|— atrybut|Tworzy oświadczenie dla klasy, która jest pochodną <xref:System.Attribute>.|W przestrzeni nazw (w tym globalnej przestrzeni nazw), klasy lub struktury.|  
|checked|Tworzy [zaznaczone](/dotnet/csharp/language-reference/keywords/checked) bloku.|Wewnątrz metody, indeksatora, Metoda dostępu do właściwości lub metody dostępu zdarzenia.|  
|class|Tworzy deklaracji klasy.|W przestrzeni nazw (w tym globalnej przestrzeni nazw), klasy lub struktury.|  
|ctor|Tworzy konstruktora dla klasy zawierającego.|Wewnątrz klasy.|  
|efektywna|Tworzy wywołanie <xref:System.Console.WriteLine%2A>.|Wewnątrz metody, indeksatora, Metoda dostępu do właściwości lub metody dostępu zdarzenia.|  
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
|mbox|Tworzy wywołanie <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName>. Może być konieczne dodanie odwołania do System.Windows.Forms.dll.|Wewnątrz metody, indeksatora, Metoda dostępu do właściwości lub metody dostępu zdarzenia.|  
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

## <a name="see-also"></a>Zobacz też  
 [Funkcje wstawek kodu](../ide/code-snippet-functions.md)   
 [Wstawki kodu](../ide/code-snippets.md)   
 [Parametry szablonu](../ide/template-parameters.md)   
 [Porady: Użyj Otocz wstawki kodu](../ide/how-to-use-surround-with-code-snippets.md)   
