---
title: "Porady: poruszanie się w programie Visual Studio IDE | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- environments [Visual Studio], navigation
- documents [Visual Studio], navigating
- IDE, navigation
- navigation [Visual Studio]
- files [Visual Studio], navigating between
- windows [Visual Studio], navigating
- Window.NextDocumentWindowNav
- IDE navigator
ms.assetid: 6c36b6eb-c93f-496b-af08-4199f7afd8bd
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 175a22ecb56f8c41d76512309df2b0443a7481b6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-move-around-in-the-visual-studio-ide"></a>Porady: poruszanie się w środowisku IDE programu Visual Studio
Zintegrowane środowisko programistyczne (IDE) została zaprojektowana do pozwalają na przenoszenie z okna i do pliku w różny sposób, w zależności od wymagań preferencji lub projekt. Można przechodzić między otwarte pliki w edytorze lub przechodzić kolejno przez wszystkie aktywne narzędzia windows w środowisku IDE. Możesz również przełączyć bezpośrednio do dowolnego Otwórz plik w edytorze, niezależnie od tego, w kolejności, w której został ostatnio używane. Te funkcje może pomóc zwiększyć produktywność podczas pracy w środowisku IDE.  
  
> [!NOTE]
> Dostępne opcje w oknach dialogowych i nazwy i lokalizacje poleceń menu, które zostanie wyświetlone, może się różnić od opisany w tym artykule, w zależności od wersji lub aktywne ustawienia. Ten artykuł dotyczy z **ogólne** ustawienia pamiętać. Aby zmienić ustawienia, na przykład aby **ogólne** lub **Visual C++** ustawienia, wybierz **narzędzia**, **Import i eksport ustawień**, a następnie Wybierz **zresetować wszystkie ustawienia**.

## <a name="keyboard-shortcuts"></a>Skróty klawiaturowe  
Prawie wszystkie polecenia menu w programie Visual Studio ma skrótów klawiaturowych. Można też utworzyć własne niestandardowe skrótów. Aby uzyskać więcej informacji, zobacz [zidentyfikowanie i dostosowywanie skrótów klawiaturowych](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  
  
## <a name="navigating-among-files-in-the-editor"></a>Nawigacja pomiędzy pliki w edytorze  
Można użyć kilku metod można przenieść za pomocą otwarty w edytorze plików. Można przenosić między plikami na podstawie kolejności, w której możesz uzyskiwać do nich dostęp, użyj Nawigator IDE, aby szybko znaleźć wszystkie aktualnie otwarty plik lub pliki ulubionych numeru pin do karty również, aby zawsze były widoczne.  
  
Przejdź wstecz i przejdź do przodu cyklicznie otwarte pliki w edytorze, na podstawie kolejności korzystał, podobnie kopii i nie przesyłaj dalej w historii przeglądania w programie Internet Explorer.  
  
#### <a name="to-move-through-open-files-in-order-of-use"></a>Aby przenieść za pomocą otwarte pliki w kolejności użycia  
  
-   Aby aktywować otwarte dokumenty w kolejności ostatnio odwoływały, naciśnij klawisz **Ctrl**+**-**.  
  
-   Aby aktywować otwarte dokumenty w odwrotnej kolejności, naciśnij klawisz **Ctrl**+**Shift**+**-**.  
  
    > [!NOTE]
    > **Przejdź wstecz** i **przejdź do przodu** również znajduje się na **widoku** menu.  
  
Można również przełączyć się do określonego pliku otwarty w edytorze, niezależnie od tego, kiedy ostatniego dostępu do pliku, przy użyciu **Nawigator IDE**, **pliki Active** listy w edytorze lub **systemuWindows** okno dialogowe.  
  
**Nawigator IDE** działa podobnie jak przełącznik aplikacji systemu Windows. Nie jest dostępne w menu i jest możliwy tylko za pomocą klawiszy skrótów. Można użyć jednej z dwóch poleceń dostępu do **Nawigator IDE** (pokazana poniżej), aby przechodzić kolejno przez pliki, w zależności od kolejności, w którym mają przechodzić.  
  
![Nawigator IDE programu Visual Studio](../ide/media/vs2015_ide_navigator.png "VS2015_IDE_Navigator")  
  
`Window.PreviousDocumentWindowNav`Umożliwia przeniesienie do ostatniego dostępu do pliku i `Window.NextDocumentWindowNav` umożliwia przeniesienie w odwrotnej kolejności. Ogólne ustawienia środowiska deweloperskiego przypisuje **Shift**+**Alt**+**F7** do `Window.PreviousDocumentWindowNav` i **Alt** + **F7** do `Window.NextDocumentWindowNav`.
  
> [!NOTE]
> Jeśli korzystasz z kombinacji ustawień nie ma już kombinację klawiszy skrótu przypisane do tego polecenia, można przypisać przy użyciu własnego polecenia niestandardowych **klawiatury** strony **opcje** okna dialogowego pole. Aby uzyskać więcej informacji, zobacz [zidentyfikowanie i dostosowywanie skrótów klawiaturowych](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  
  
#### <a name="to-switch-to-specific-files-in-the-editor"></a>Aby przełączyć się do określonych plików w edytorze  
  
-   Naciśnij klawisz **Ctrl**+**kartę** do wyświetlenia **Nawigator IDE**. Naciśnij i przytrzymaj klawisz CTRL i naciskaj klawisz TAB aż do wybrania pliku, który chcesz przełączyć się do.  
  
    > [!TIP]
    >  Do odwracania kolejności, w którym można przejść przez **pliki Active** liście, naciśnij i przytrzymaj **Ctrl**+**Shift** kluczy i naciśnij klawisz **kartę**.  
  
    \-lub -  
  
-   W prawym górnym rogu edytora wybierz **pliki Active** przycisk, a następnie wybierz plik z listy, aby przełączyć się do.  
  
    \-lub -  
  
-   Na pasku menu wybierz **okna**, **Windows**.  
  
-   Na liście, wybierz plik, który chcesz wyświetlić, a następnie wybierz pozycję **Aktywuj**.  
  
## <a name="navigating-among-tool-windows-in-the-ide"></a>Nawigacja pomiędzy narzędzia systemu Windows w środowisku IDE  
**Nawigator IDE** również umożliwia przechodzenie między okna narzędzi, masz otwarty w IDE. Można użyć jednej z dwóch poleceń dostępu do **Nawigator IDE** aby przechodzić kolejno przez narzędzie systemu windows, w zależności od kolejności, w której chcesz przechodzenie między. `Window.PreviousToolWindowNav`Umożliwia przeniesienie do ostatniego dostępu do pliku i `Window.NextToolWindowNav` umożliwia przeniesienie w odwrotnej kolejności. Ogólne ustawienia środowiska deweloperskiego przypisuje **Shift**+**Alt**+**F7** do `Window.PreviousDocumentWindowNav` i **Alt** + **F7** do `Window.NextDocumentWindowNav`.
  
> [!NOTE]
> Jeśli korzystasz z kombinacji ustawień nie ma już kombinację klawiszy skrótu przypisane do tego polecenia, można przypisać przy użyciu własnego polecenia niestandardowych **klawiatury** strony **opcje** okna dialogowego pole. Aby uzyskać więcej informacji, zobacz [zidentyfikowanie i dostosowywanie skrótów klawiaturowych](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  
  
#### <a name="to-switch-to-a-specific-tool-window-in-the-ide"></a>Aby przełączyć się do okna narzędzia określonych w środowisku IDE  
  
-   Naciśnij klawisz **Alt**+**F7** do wyświetlenia **Nawigator IDE**. Naciśnij i przytrzymaj **Alt** i naciśnij **F7** aż do momentu, gdy wybierz chcesz przełączyć się do okna.  
  
    > [!TIP]
    > Aby odwrócić kolejność, w którym można przejść przez **aktywnego okna narzędzi** , przytrzymaj klawisze ALT + SHIFT, a następnie naciśnij klawisz F7.  
  
## <a name="see-also"></a>Zobacz także
[Dostosowywanie układów okien](../ide/customizing-window-layouts-in-visual-studio.md)   
[Domyślne skróty klawiaturowe](../ide/default-keyboard-shortcuts-in-visual-studio.md)