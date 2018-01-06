---
title: Opcje, Edytor tekstu, C#, IntelliSense | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Intellisense
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Intellisense
helpviewer_keywords:
- underlines, wavy
- IntelliSense [C#], options
- IntelliSense [C#], wavy underlines
- wavy underlines
- Text Editor Options dialog box, IntelliSense
ms.assetid: 3466dedb-e5f4-424c-8dd8-e4941b2f4fc2
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: b0b69b7eafbfbb1b5c2c582fd0c734a183ea0a78
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="options-text-editor-c-intellisense"></a>Opcje, edytor tekstu, C#, IntelliSense
Użyj **IntelliSense** strony właściwości, aby zmodyfikować ustawienia, które wpływają na zachowanie IntelliSense dla języka Visual C#. Dostęp można uzyskać **IntelliSense** strony właściwości, klikając **opcje** na **narzędzia** menu, klikając **C#** w **Edytor tekstu** folder, a następnie klikając **IntelliSense.**  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  
  
 **IntelliSense** strona zawiera następujące właściwości:  
  
## <a name="completion-lists"></a>Listy uzupełniania  
 **Pokaż listę uzupełniania po wpisaniu znaku**  
 Gdy ta opcja jest zaznaczona, IntelliSense automatycznie wyświetla listę uzupełniania po rozpoczęciu wpisywania. Gdy ta opcja nie jest zaznaczona, uzupełniania IntelliSense jest nadal dostępny z **IntelliSense** menu lub nacisnąć klawisze CTRL + SPACJA.  
  
 **Umieść słowa kluczowe na listach uzupełniania**  
 Gdy ta opcja jest zaznaczona, IntelliSense dodaje słowa kluczowe języka C#, na przykład [klasy](/dotnet/csharp/language-reference/keywords/class), do listy uzupełniania.  
  
 **Umieść wstawki kodu na listach uzupełniania**  
 Gdy ta opcja jest zaznaczona, IntelliSense dodaje aliasy wstawki kodu C# do listy zakończenia. W przypadku, gdy alias fragment kodu jest taka sama jak słowem kluczowym, na przykład [klasy](/dotnet/csharp/language-reference/keywords/class), słowo kluczowe zastępuje skrótu. Aby uzyskać więcej informacji, zobacz [Visual C# — wstawki](../../ide/visual-csharp-code-snippets.md).  
  
## <a name="selection-in-completion-lists"></a>Wybór na listach uzupełniania  
 **Zatwierdzane przez wpisanie następujących znaków:**  
 Określa wszystkie znaki, które są wykonywane automatycznego uzupełniania IntelliSense dla wybranego elementu na liście uzupełniania po wpisywania ich.  
  
 **Zatwierdzone, naciskając klawisz spacji**  
 Określa, aby uwzględnić działania naciskając klawisz spacji, aby wykonać automatycznego uzupełniania IntelliSense dla wybranego elementu na liście uzupełniania.  
  
 **Dodaj nowy wiersz po naciśnięciu klawisza enter na końcu wpisaniu całego słowa**  
 Określa, że jeśli wpisz wszystkich znaków dla wpisu na liście uzupełniania, a następnie naciśnij klawisz ENTER, automatycznie tworzony jest nowy wiersz i kursor zostanie umieszczony w nowym wierszu.  
  
 Na przykład jeśli wpiszesz `else` i naciśnij klawisz ENTER w edytorze pojawi się następujące:  
  
 `else`  
  
 `|`(Lokalizacja kursora)  
  
 Jednak w przypadku wpisania tylko `el` i naciśnij klawisz ENTER w edytorze pojawi się następujące:  
  
 `else|`(Lokalizacja kursora)  
  
## <a name="intellisense-member-selection"></a>Wybór elementu członkowskiego IntelliSense  
 **Wybiera wstępne ostatnio używany element członkowski**  
 Gdy ta opcja jest zaznaczona, IntelliSense wstępnie wybiera elementy członkowskie, które ostatnio wybrane w polu listy członków wyskakującego dla obiekt automatyczne uzupełnianie nazw, podczas bieżącej sesji w zintegrowane środowisko programistyczne (IDE). Historia ostatnio używanych elementów członkowskich jest wyczyszczone między każdej sesji w IDE. Aby uzyskać więcej informacji, zobacz [IntelliSense dla ostatnio używane członków](../../ide/visual-csharp-intellisense.md#most-recently-used-members).  
  
## <a name="see-also"></a>Zobacz też  
 [Ogólne, środowisko, opcje — Okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)   
 [Komentarze dokumentacji XML](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)   
 [Korzystanie z funkcji IntelliSense](../../ide/using-intellisense.md)