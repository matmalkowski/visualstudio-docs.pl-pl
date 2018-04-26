---
title: Opcje, edytor tekstu, C#, zaawansowane
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
helpviewer_keywords:
- XML comments
- XML documentation, generating
- outlining options [C#]
- XML documentation, creating
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: a7675d711a4a1df6af4643a459f49b6ef518e5b4
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="options-text-editor-c-advanced"></a>Opcje, edytor tekstu, C#, zaawansowane

Użyj **zaawansowane** Strona opcji, aby zmodyfikować ustawienia formatowania edytora, code refaktoryzacji i komentarze dokumentacji XML dla C#. Aby uzyskać dostęp do tej strony opcji, należy wybrać **narzędzia** > **opcje**, a następnie wybierz pozycję **Edytor tekstu** > **C#**  >  **Zaawansowane**.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="analysis"></a>Analiza

- Włącz pełną analizę rozwiązania

   Włącza analizę kodu we wszystkich plikach w rozwiązaniu, nie wystarczy otworzyć plików kodu. Aby uzyskać więcej informacji, zobacz [Pełna analiza rozwiązania](../../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

- Analiza funkcji edytora w procesie zewnętrznym (eksperymentalne)

## <a name="using-directives"></a>Przy użyciu dyrektyw

- Najpierw umieścić dyrektywy "System" podczas sortowania użyć

- Oddziel przy użyciu grup dyrektywy

- Sugeruj użycie typów w zestawach odwołania

- Sugeruj użycie typów w pakietach NuGet

## <a name="highlighting"></a>Wyróżnianie

- Wyróżnij odwołania do symbolu pod kursorem

   Gdy kursor znajduje się wewnątrz symbolu, lub kliknij symbol, są wyróżnione wszystkich wystąpień tego symbolu w pliku kodu.

- Wyróżnij pokrewne słowa kluczowe pod kursorem

## <a name="outlining"></a>Tworzenie konspektu

- Trybu zwijania przy otwieraniu plików

   Po wybraniu automatycznie przedstawiono plik kodu, który tworzy zwijanej bloków kodu. Zwiń po raz pierwszy plik jest otwarty, bloki #regions i nieaktywnych bloków kodu.

- Pokaż separatory wierszy procedury

- Pokaż obramowanie dla konstrukcji poziomu deklaracji

- Pokaż obramowanie dla poziomu konstrukcji kodu

- Pokaż obramowanie dla komentarzy i regiony preprocesora

- Zwiń #regions podczas zwijanie do definicji

## <a name="fading"></a>Zanikania

- Stopniowe limit nieużywanych deklaracji Using

- Stopniowe kodu jest nieosiągalny

## <a name="block-structure-guides"></a>Przewodniki struktury bloku

- Pokaż przewodniki dotyczące konstrukcji poziomu deklaracji

- Pokaż przewodniki dotyczące poziomu konstrukcji kodu

## <a name="editor-help"></a>Edytor pomocy

- Generuj komentarze dokumentacji XML dla / / /

   Po wybraniu Wstawia elementy XML dla komentarzy do dokumentacji XML po wpisaniu `///` wprowadzenie komentarza. Aby uzyskać więcej informacji na temat dokumentacji XML, zobacz [komentarze dokumentacji XML (C# przewodnik programowania w języku)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments).

- Wstaw \* na początku nowych wierszy podczas pisania /\* \*/ komentarzy

- Pokaż Podglad śledzenia zmian nazw

- Wprowadź podziału literałów ciągów na

- Raport nieprawidłowe symbole zastępcze w "ciąg. Format "wywołań

## <a name="extract-method"></a>Wyodrębnij metodę

- Nie umieszczaj klauzul ref lub out w strukturze niestandardowej

## <a name="implement-interface-or-abstract-class"></a>Implementowanie interfejsu lub klasy abstrakcyjnej

- Podczas wstawiania właściwości, zdarzeń i metody, umieść je z innymi elementami członkowskimi z taką samą lub na końcu

- Podczas generowania właściwości, preferowane właściwości zgłaszanie lub użyć automatycznie właściwości

## <a name="see-also"></a>Zobacz także

- [Porady: wstawianie komentarze XML dla generowania dokumentacji](../../ide/reference/generate-xml-documentation-comments.md)
- [Komentarze dokumentacji XML (C# przewodnik programowania w języku)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Dokumentowanie kodu za pomocą komentarze XML (Przewodnik C#)](/dotnet/csharp/codedoc)
- [Ustawianie opcji edytora specyficznych dla języka](../../ide/reference/setting-language-specific-editor-options.md)
- [C# IntelliSense](../../ide/visual-csharp-intellisense.md)