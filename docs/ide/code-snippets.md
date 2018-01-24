---
title: Wstawki kodu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.ExpansionManagerImport
- vs.codesnippetmanager
helpviewer_keywords:
- code snippets, replacement parameters
- code snippets, surround with
- replacement parameters
- code snippets, expansion
- surround with
- code snippets
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e2b973b00e132973b8569bc5cad8c1f1318317cd
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2018
---
# <a name="code-snippets"></a>Wstawki kodu

Wstawki kodu są małe bloki kodu wielokrotnego użytku, które można wstawiać w pliku kodu za pomocą polecenia menu kontekstowego lub kombinację klawiszy dostępu. Zwykle zawierają bloki kodu powszechnie używane, takich jak try-finally lub if-else bloków, ale może służyć do wstawienia całej klasy lub metody.

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

Ta Wstawka kodu można wstawiać, klikając **wstawić fragment** w menu kontekstowe okna Kod, następnie **Visual C#**, wpisz `tryf`, a następnie naciśnij klawisz **kartę**, lub można wpisać `tryf` i naciśnij klawisz **kartę** dwa razy.

Przykład fragment Otocz: w języku C++ skrót `if` może służyć jako fragment wstawiania lub fragment Otocz. W przypadku wybrania wiersz kodu (na przykład `return FALSE;`), a następnie kliknij przycisk **z funkcji Otocz przez**, następnie **Jeśli**, fragment jest rozwinięta wokół wiersza:

```cpp
if (true)
{
    return FALSE;
}
```

## <a name="snippet-replacement-parameters"></a>Parametry zamiany fragment kodu

Wstawki kodu programu może zawierać parametry zamiany, które symboli zastępczych, które należy zastąpić do dopasowania dokładne pisania kodu. W poprzednim przykładzie `true` jest to parametr zastąpienia, należy zastąpić z odpowiedniego warunku. Wprowadzone zastąpienia jest powtarzany dla każdego wystąpienia tego samego parametru zastępczy we fragmencie.

Na przykład w języku Visual Basic istnieje fragment kodu, która wstawia właściwości. Kliknij przycisk **wstawić fragment** w menu kontekstowym okna Kod, następnie **wzorce kodu**, następnie **zdarzenia właściwości, procedur,**, następnie zdefiniuj właściwość. Dodaje się następujący kod:

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

## <a name="code-snippet-manager"></a>Menedżer wstawek kodu

Można wyświetlić wszystkie fragmenty kodu, które są aktualnie zainstalowane, a ich lokalizacji na dysku, wybierając **narzędzia**, **Menedżerze fragmentów kodu**. Fragmenty kodu są wyświetlane przez język.

Można dodawać i usuwać katalogi fragment kodu z **Dodaj** i **Usuń** przycisków w **Menedżerze fragmentów kodu** okna dialogowego. Aby dodać poszczególne fragmenty kodu, użyj **importu** przycisku.

## <a name="see-also"></a>Zobacz także

[Przewodnik: Tworzenie fragmentu kodu](../ide/walkthrough-creating-a-code-snippet.md)  
[Instrukcje: Dystrybucja fragmentów kodu](../ide/how-to-distribute-code-snippets.md)  
[Najlepsze rozwiązania dotyczące korzystania z fragmentów kodu](../ide/best-practices-for-using-code-snippets.md)  
[Rozwiązywanie problemów z fragmentami kodu](../ide/troubleshooting-snippets.md)  
[Fragmenty kodu Visual C#](../ide/visual-csharp-code-snippets.md)  
[Fragmenty kodu Visual C++](../ide/visual-cpp-code-snippets.md)  
[Fragmenty kodu — informacje o schemacie](../ide/code-snippets-schema-reference.md)