---
title: Fragmenty kodu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ExpansionManagerImport
- vs.codesnippetmanager
helpviewer_keywords:
- surround with
- code snippets
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 2d41a5a3995c9c93f17f090e5befc10a0bd544c3
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37117215"
---
# <a name="code-snippets"></a>Fragmenty kodu

Wstawki kodu są małe bloki kodu wielokrotnego użytku, które można wstawiać w pliku kodu za pomocą polecenia menu kontekstowego lub kombinację klawiszy dostępu. Zwykle zawierają bloki kodu często używane, takich jak `try-finally` lub `if-else` bloków, ale może służyć do wstawienia całej klasy lub metody.

Wstawki kodu są dostępne dla wielu języków, w tym C#, C++, Visual Basic, XML i T-SQL, kilka. Aby wyświetlić wszystkie dostępne zainstalowanych fragmenty kodu dla języka, otwórz **Menedżerze fragmentów kodu** z **narzędzia** menu programu Visual Studio i wybierz język z menu rozwijane u góry.

![Okno dialogowe Menedżer wstawek kodu](media/code-snippets-manager.png)

Wstawki kodu jest możliwy w następujący sposób ogólne:

- Na pasku menu wybierz **Edytuj** > **IntelliSense** > **wstawić fragment kodu**

- Z menu kliknij prawym przyciskiem myszy lub kontekstu w edytorze kodu, wybierz **fragment** > **wstawić fragment kodu**

- Z klawiatury, naciśnij klawisz **Ctrl**+**K**+**X**

## <a name="expansion-snippets-and-surround-with-snippets"></a>Wstawki rozszerzenia i wstawki z funkcji Otocz przez

W programie Visual Studio istnieją dwa rodzaje fragment kodu: wstawki rozszerzenia, które są dodawane w określonym kursora, a może zastąpić skrót fragment i Otocz wstawki (C# i tylko C++), które zostaną dodane wokół zaznaczonego bloku kodu.

Przykład fragment rozwinięcia: w języku C# tryf skrótu służy do wstawiania blok try-finally:

```csharp
try
{

}
finally
{

}
```

Ta Wstawka kodu można wstawiać, klikając **wstawić fragment** w menu kontekstowe okna Kod, następnie **Visual C#**, wpisz `tryf`, a następnie naciśnij klawisz **kartę**. Alternatywnie możesz wpisać `tryf` i naciśnij klawisz **kartę** dwa razy.

Przykład fragment Otocz: w języku C++ skrót `if` może służyć jako fragment wstawiania lub fragment Otocz. W przypadku wybrania wiersz kodu (na przykład `return FALSE;`), a następnie wybierz pozycję **z funkcji Otocz przez** > **Jeśli**, fragment jest rozwinięta wokół wiersza:

```cpp
if (true)
{
    return FALSE;
}
```

## <a name="snippet-replacement-parameters"></a>Parametry zamiany fragment kodu

Wstawki kodu programu może zawierać parametry zamiany, które symboli zastępczych, które należy zastąpić do dopasowania dokładne pisania kodu. W poprzednim przykładzie `true` jest to parametr zastąpienia, należy zastąpić z odpowiedniego warunku. Wprowadzone zastąpienia jest powtarzany dla każdego wystąpienia tego samego parametru zastępczy we fragmencie.

Na przykład w języku Visual Basic istnieje fragment kodu, która wstawia właściwości. Aby wstawić fragment kodu, wybierz **fragment** > **wstawić fragment** z menu kliknij prawym przyciskiem myszy lub kontekstu w pliku kodu języka Visual Basic. Następnie wybierz pozycję **wzorce kodu** > **zdarzenia właściwości, procedur,** > **definiuje właściwości**.

![Menu fragment kodu dla Definiuj właściwości](media/code-snippets-vb-property.png)

Dodaje się następujący kod:

```vb
Private newPropertyValue As String
Public Property NewProperty() As String
    Get
        Return newPropertyValue
    End Get
    Set(ByVal value As String)
        newPropertyValue = value
    End Set
End Property
```

Jeśli zmienisz `newPropertyValue` do `m_property`, następnie każde wystąpienie `newPropertyValue` zostanie zmieniona. Jeśli zmienisz `String` do `Int` w deklaracji właściwości następnie wartość metody set jest również zmienić `Int`.

## <a name="see-also"></a>Zobacz także

- [Wskazówki: Tworzenie wstawek kodu](../ide/walkthrough-creating-a-code-snippet.md)
- [Porady: rozprowadzanie wstawek kodu](../ide/how-to-distribute-code-snippets.md)
- [Najlepsze rozwiązania dotyczące korzystania z wstawek kodu](../ide/best-practices-for-using-code-snippets.md)
- [Rozwiązywanie problemów z wstawki kodu programu](../ide/troubleshooting-snippets.md)
- [Wstawki kodu C#](../ide/visual-csharp-code-snippets.md)
- [Wstawki kodu programu Visual C++ kod](../ide/visual-cpp-code-snippets.md)
- [Fragmenty kodu — informacje o schemacie](../ide/code-snippets-schema-reference.md)