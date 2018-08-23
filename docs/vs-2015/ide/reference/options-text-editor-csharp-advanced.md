---
title: Zaawansowane opcje, Edytor tekstu, C# | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Advanced
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
helpviewer_keywords:
- XML comments
- XML documentation, generating
- outlining options [C#]
- outlining options [J#]
- XML documentation, creating
ms.assetid: 947f9d9a-b0f3-408d-9866-d82895bcee31
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 64e01a00fbb4fcbd637652a161982bd86b645f20
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42630176"
---
# <a name="options-text-editor-c-advanced"></a>Opcje, edytor tekstu, C#, zaawansowane
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [opcje, Edytor tekstu, C#, zaawansowane](https://docs.microsoft.com/visualstudio/ide/reference/options-text-editor-csharp-advanced).  
  
  
Aby zmodyfikować ustawienia formatowania edytora, refaktoryzacji kodu i komentarze dokumentacji XML dla języka Visual C#, należy użyć tego okna dialogowego. Aby otworzyć to okno dialogowe, kliknij przycisk **opcje** na **narzędzia** menu rozwiń **Edytor tekstu** folder, rozwiń węzeł **C#**, a następnie kliknij przycisk  **Zaawansowane**.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="outlining"></a>Tworzenie konspektu  
 Przejdź do trybu konspektu po otwarciu plików  
 Po wybraniu automatycznie przedstawia plik kodu, który tworzy zwijany bloków kodu. Przy pierwszym otwarciu pliku #regions bloków i bloków nieaktywnego kodu Zwiń.  
  
## <a name="editor-help"></a>Pomoc Edytora  
 Underline błędy w edytorze  
 Identyfikuje błędy kompilacji w kodzie. Gdy ta opcja jest zaznaczona, faliste podkreślenia są wyświetlane w kolorów, które mają określone znaczenie:  
  
-   Błędy analizy są oznaczone kolorem czerwonym.  
  
-   Błędy kompilacji są niebieski.  
  
-   Ostrzeżenia kompilacji są zielone.  
  
-   Nieprawidłowy [Edytuj i Kontynuuj](../../debugger/edit-and-continue.md) Edycje elementów purpurowy.  
  
 Przesuń wskaźnik nad segment podkreślony kodu, aby wyświetlić etykietkę narzędzia, za pomocą informacji o błędzie.  
  
 Pokaż błędy semantyczne na żywo  
 Identyfikuje pewne błędy kompilacji bez kompilację typu explicit, na przykład deklarowania i przy użyciu nieznanego typu lub odwołuje się do nieznanej właściwości.  
  
 Wyróżnij odwołania do symbolu pod kursorem  
 Gdy kursor znajduje się wewnątrz symbolu lub po kliknięciu symbolu, zostały wyróżnione wszystkich wystąpień symbolu w pliku kodu.  
  
## <a name="refactoring"></a>Refaktoryzacja  
 Sprawdź wyniki refaktoryzacji  
 Wyświetla **wyniki weryfikacji** okno dialogowe podczas refaktoryzacji kodu, który zawiera błędy kompilacji lub podczas refaktoryzacji spowodowałoby odwołanie kodu powiązać coś, co różni się od jej oryginalnego powiązania.  
  
 Ostrzegaj przed witrynami dla elementów członkowskich z odwołaniami do wygenerowanego przez kompilator  
 Wyświetla okno dialogowe z ostrzeżeniem, podczas refaktoryzacji elementu członkowskiego, który ma taką samą nazwę jak odwołanie wygenerowanego przez kompilator.  
  
## <a name="xml-documentation-comments"></a>Komentarze dokumentacji XML  
 Generowanie komentarzy dokumentacji XML dla / / /  
 Po wybraniu wstawia \<podsumowania > początek i koniec tagi automatycznie dla komentarzy dokumentacji XML, po wpisaniu wprowadzenie komentarz / / /. Aby uzyskać więcej informacji na temat dokumentacji XML, zobacz [komentarze dokumentacji XML](http://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199).  
  
## <a name="implement-interface"></a>Implementowanie interfejsu  
 Otocz wygenerowanego kodu za pomocą #region  
 Wstawia #region \< *nazwę interfejsu*> wokół metody, gdy jest używana implementuj interfejs implementuj interfejs jawnie lub element członkowski.  
  
## <a name="organize-usings"></a>Organizuj użycia  
 Umieść najpierw dyrektywy "System" podczas sortowania deklaracji Using  
 Po wybraniu `System` przy użyciu dyrektywy są wyświetlane przed innymi za pomocą dyrektywy. Aby uzyskać więcej informacji, zobacz [Sortuj wyrażenia Using](../../misc/sort-usings.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Komentarze dokumentacji XML](http://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199)   
 [Ustawianie opcji edytora specyficznych dla języka](../../ide/reference/setting-language-specific-editor-options.md)   
 [Funkcja IntelliSense dla języka Visual C#](../../ide/visual-csharp-intellisense.md)



