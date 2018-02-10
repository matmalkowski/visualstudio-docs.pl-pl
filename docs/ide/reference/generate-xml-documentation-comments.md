---
title: Wstaw komentarze dokumentacji XML w Visual Studio | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: a98373280aa789e3c2381c5afc7d6c60c53dd171
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="how-to-insert-xml-comments-for-documentation-generation"></a>Porady: wstawianie komentarze XML dla generowania dokumentacji

Visual Studio może pomóc dokumentu kodu elementów, takich jak klasy i metody, przez automatyczne generowanie standardowe struktury komentarzy dokumentacji XML. W czasie kompilacji można wygenerować plik XML, który zawiera komentarze dokumentacji. Plik XML generowane przez kompilator mogą być dystrybuowane wraz z zestawu .NET, dzięki czemu program Visual Studio i innych IDEs może używać IntelliSense do wyświetlania szybkie informacji dotyczących typów i członków. Ponadto można uruchomić plik XML za pomocą takich narzędzi jak [DocFX](https://dotnet.github.io/docfx/) i [Sandcastle](https://www.microsoft.com/download/details.aspx?id=10526) można wygenerować odwołania API witryn sieci Web.

> [!NOTE]
> **Wstaw komentarz** polecenia, które automatycznie wstawia komentarze dokumentacji XML jest dostępna w [C#](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments) i [Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation). Jednak można wstawiać ręcznie [komentarze dokumentacji XML w języku C++](/cpp/ide/xml-documentation-visual-cpp) pliki i nadal generować pliki dokumentacji XML w czasie kompilacji.

## <a name="to-insert-xml-comments-for-a-code-element"></a>Aby wstawić komentarze XML dla elementu kodu

1. Umieść kursor nad elementem chcesz dokumentu, na przykład metoda tekstu.

1. Wykonaj jedną z następujących czynności:

   - Typ `///` w języku C# lub `'''` w języku Visual Basic

   - Z **Edytuj** menu, wybierz **IntelliSense** > **Wstaw komentarz**

   - Kliknij prawym przyciskiem myszy lub kontekstu menu lub po prostu nad elementu kodu, wybierz **fragment** > **Wstaw komentarz**

   Szablon XML jest generowany bezpośrednio powyżej elementu kodu. Na przykład podczas dodawania komentarzy metody, generuje  **\<podsumowania\>**  elementu  **\<param\>**  elementu dla każdego parametru i  **\<zwraca\>**  elementu do dokumentu wartości zwracanej.

   ![Szablon komentarza XML - C#](media/doc-preview-cs.png)

   ![Szablon komentarza XML - Visual Basic](media/doc-preview-vb.png)

1. Wprowadź opis dla każdego elementu XML do dokumentów w pełni elementu kodu.

   ![Komentarz ukończone](media/doc-result-cs.png)

> [!NOTE]
> Brak [opcji](../../ide/reference/options-text-editor-csharp-advanced.md) do przełączania komentarze dokumentacji XML po wpisaniu `///` w języku C# lub `'''` języka Visual Basic. Na pasku menu wybierz **narzędzia** > **opcje** otworzyć **opcje** okno dialogowe. Następnie przejdź do **Edytor tekstu** > **C#** lub **podstawowe** > **zaawansowane**. W **pomocy edytora** sekcji, poszukaj **Generuj komentarze dokumentacji XML** opcji.

## <a name="see-also"></a>Zobacz także

[Komentarze dokumentacji XML (C# przewodnik programowania w języku)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)  
[Dokumentowanie kodu za pomocą komentarze XML (Przewodnik C#)](/dotnet/csharp/codedoc)  
[Porady: tworzenie dokumentacji XML (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)  
[C++ — komentarze](/cpp/cpp/comments-cpp)  
[Plik dokumentacji XML (C++)](/cpp/ide/xml-documentation-visual-cpp)  
[Generowanie kodu](../code-generation-in-visual-studio.md)
