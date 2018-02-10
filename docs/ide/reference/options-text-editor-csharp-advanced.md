---
title: Zaawansowane opcje, Edytor tekstu, C# | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Advanced
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
helpviewer_keywords:
- XML comments
- XML documentation, generating
- outlining options [C#]
- XML documentation, creating
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 119d6660b476dd025ff8def009369a4e38d09d28
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="options-text-editor-c-advanced"></a>Opcje, edytor tekstu, C#, zaawansowane

To okno dialogowe służy do modyfikowania ustawienia formatowania edytora, refaktoryzacji kodu i komentarze dokumentacji XML dla C#. Aby uzyskać dostęp do tego okna dialogowego, kliknij przycisk **opcje** na **narzędzia** menu, rozwiń węzeł **Edytor tekstu** folder, rozwiń węzeł **C#**, a następnie kliknij przycisk  **Zaawansowane**.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="outlining"></a>Tworzenie konspektu

Trybu zwijania przy otwieraniu plików  
Po wybraniu automatycznie przedstawiono plik kodu, który tworzy zwijanej bloków kodu. Zwiń po raz pierwszy plik jest otwarty, bloki #regions i nieaktywnych bloków kodu.

## <a name="editor-help"></a>Edytor pomocy

Podkreślenie błędy w edytorze  
Identyfikuje błędy kompilacji w kodzie. Jeśli ta opcja jest zaznaczona, faliste podkreślenie pojawią się w kolorów, które mają określone znaczenie:
  
-   Błędy analizy są oznaczone kolorem czerwonym.  
  
-   Niebieski są błędy kompilacji.  
  
-   Ostrzeżenia kompilacji są zielone.  
  
-   Nieprawidłowy [Edytuj i Kontynuuj](../../debugger/edit-and-continue.md) zmiany są purpurowy.  
  
Wskaźnika na segment kodu podkreślone, aby wyświetlić etykietkę zawierającą informacje o tym błędzie.  
  
Pokaż błędy semantyczne na żywo  
Identyfikuje niektóre błędy kompilacji bez jawnego kompilacji, na przykład deklarowanie i za pomocą nieznanego typu lub odwołuje się do nieznanej właściwości.  
  
Wyróżnij odwołania do symbolu pod kursorem  
Gdy kursor znajduje się wewnątrz symbolu, lub kliknij symbol, są wyróżnione wszystkich wystąpień tego symbolu w pliku kodu.  
  
## <a name="refactoring"></a>Refaktoryzacja

Sprawdź wyniki refaktoryzacji  
Wyświetla **wyniki weryfikacji** okno dialogowe podczas refaktoryzacji kodu, który zawiera błędy kompilacji lub refaktoryzacji spowodowałoby kodu odwołania powiązać z inną z jej oryginalnej powiązania.  

Ostrzegaj w elementach członkowskich z odwołaniami do wygenerowanego przez kompilator  
Wyświetla okno dialogowe z ostrzeżeniem, podczas próby Refaktoryzuj elementu członkowskiego, który ma taką samą nazwę jak odwołanie do wygenerowanego przez kompilator.

## <a name="xml-documentation-comments"></a>Komentarze dokumentacji XML

Generuj komentarze dokumentacji XML dla / / /  
Po wybraniu Wstawia elementy XML dla komentarzy do dokumentacji XML po wpisaniu `///` wprowadzenie komentarza. Aby uzyskać więcej informacji na temat dokumentacji XML, zobacz [komentarze dokumentacji XML (C# przewodnik programowania w języku)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments).

## <a name="implement-interface"></a>Implementowanie interfejsu

Otaczające wygenerowanego kodu z #region  
Wstawia #region \< *Nazwa interfejsu*> elementu członkowskiego wokół metody, gdy używany jest implementowanie interfejsu lub zaimplementuj interfejs jawnie.

## <a name="organize-usings"></a>Organizacja deklaracji Using

Najpierw umieścić dyrektywy "System" podczas sortowania użyć  
Po wybraniu `System` przy użyciu dyrektywy występować przed innymi przy użyciu dyrektyw. Aby uzyskać więcej informacji, zobacz deklaracje Using Organizuj w [C#, IntelliSense](../../ide/visual-csharp-intellisense.md#automatic-code-generation).

## <a name="see-also"></a>Zobacz także

[Porady: wstawianie komentarze XML dla generowania dokumentacji](../../ide/reference/generate-xml-documentation-comments.md)  
[Komentarze dokumentacji XML (C# przewodnik programowania w języku)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)  
[Dokumentowanie kodu za pomocą komentarze XML (Przewodnik C#)](/dotnet/csharp/codedoc)  
[Ustawianie opcji edytora specyficznych dla języka](../../ide/reference/setting-language-specific-editor-options.md)  
[C# IntelliSense](../../ide/visual-csharp-intellisense.md)