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
ms.assetid: 85976ad9-4c9a-4e7b-896e-66ec6f955199
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6c295efd0cb6fcf46ed9d76f080a951d9ae79080
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="code-snippets"></a>Wstawki kodu
Wstawki kodu są małe bloki kodu wielokrotnego użytku, które można wstawiać w pliku kodu za pomocą polecenia menu kontekstowego lub kombinację klawiszy dostępu. Zwykle zawierają bloki kodu powszechnie używane, takich jak try-finally lub if-else bloków, ale może służyć do wstawienia całej klasy lub metody.  
  
## <a name="expansion-snippets-and-surround-with-snippets"></a>Wstawki rozszerzenia i wstawki z funkcji Otocz przez  
 W programie Visual Studio istnieją dwa rodzaje fragment kodu: wstawki rozszerzenia, które są dodawane w określonym kursora, a może zastąpić skrót fragment i Otocz wstawki (C# i tylko C++), które zostaną dodane wokół zaznaczonego bloku kodu.  
  
 Przykład fragment wstawiania: w języku C# tryf skrótu służy do wstawiania blok try-finally:  
  
```  
try  
{  
  
}  
finally  
{  
  
}  
  
```  
  
 Ta Wstawka kodu można wstawiać, klikając **wstawić fragment** w menu kontekstowe okna Kod, następnie **Visual C#**, wpisz `tryf`, a następnie kartę, lub można wpisać `tryf` i naciśnij klawisz TAB + TAB.  
  
 Przykład fragment Otocz: w języku C++ skrót `if` może służyć jako fragment wstawiania lub fragment Otocz. W przypadku wybrania wiersz kodu (na przykład `return FALSE;`), a następnie kliknij przycisk **z funkcji Otocz przez**, następnie **Jeśli**, fragment jest rozwinięta wokół wiersza:  
  
```  
if (true)  
{  
    return FALSE;  
}  
  
```  
  
## <a name="snippet-replacement-parameters"></a>Parametry zamiany fragment kodu  
 Wstawki kodu programu może zawierać parametry zamiany, które symboli zastępczych, które należy zastąpić do dopasowania dokładne pisania kodu. W poprzednim przykładzie `true` jest to parametr zastąpienia, należy zastąpić z odpowiedniego warunku. Wprowadzone zastąpienia jest powtarzany dla każdego wystąpienia tego samego parametru zastępczy we fragmencie.  
  
 Na przykład w języku Visual Basic istnieje fragment kodu, która wstawia właściwości. Kliknij przycisk **wstawić fragment** w menu kontekstowym okna Kod, następnie **wzorce kodu**, następnie **zdarzenia właściwości, procedur,**, następnie zdefiniuj właściwość. Dodaje się następujący kod:  
  
```  
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
 Można wyświetlić wszystkie fragmenty kodu, które są aktualnie zainstalowane, a także ich lokalizacji na dysku, klikając **Menedżerze fragmentów kodu/narzędzia**. Fragmenty kodu są wyświetlane przez język.  
  
 Można dodawać i usuwać katalogi fragment kodu z **Dodaj** i **Usuń** przycisków w **Menedżerze fragmentów kodu** okna dialogowego. Aby dodać poszczególne fragmenty kodu, użyj **importu** przycisku.  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Tworzenie wstawek kodu](../ide/walkthrough-creating-a-code-snippet.md)   
 [Porady: rozprowadzanie wstawek kodu](../ide/how-to-distribute-code-snippets.md)   
 [Najlepsze rozwiązania dotyczące korzystania z wstawek kodu](../ide/best-practices-for-using-code-snippets.md)   
 [Rozwiązywanie problemów z wstawki kodu programu](../ide/troubleshooting-snippets.md)   
 [Wstawki kodu Visual C#](../ide/visual-csharp-code-snippets.md)   
 [Wstawki kodu języka Visual C++](../ide/visual-cpp-code-snippets.md)   
 [Odwołanie do schematu wstawki kodu](../ide/code-snippets-schema-reference.md)