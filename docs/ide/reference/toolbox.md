---
title: Okno przybornika w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: article
f1_keywords:
- vs.toolbox.general
- vs.toolbox
helpviewer_keywords:
- Toolbox [Visual Studio]
- custom controls [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 50c9cc96d501eb6d7d10ab31f48600eb65eb57a7
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/22/2018
---
# <a name="toolbox"></a>Przybornik

**Przybornika** okno wyświetla formantów, które można dodać do projektów programu Visual Studio. Aby otworzyć przybornika, wybierz **przybornika** na **widoku** menu.

![Okno przybornika](media/toolbox.png)

Możesz przeciągać i upuszczać inne formanty na powierzchnię projektanta używasz i zmień rozmiar i umieść formanty.

Przybornik pojawi się w połączeniu z projektanta widoków, takich jak Widok projektanta w pliku XAML. Pasek narzędzi wyświetla tylko formanty, które mogą być używane w bieżącym projektancie. Można wyszukiwać w przyborniku filtrowi dodatkowe elementy, które są wyświetlane.

> [!NOTE]
> Dla niektórych typów projektów przybornika nie mogą być wyświetlane wszystkie elementy.

Wersja programu .NET Framework, że elementem docelowym projektu jest również wpływa na zestaw mechanizmów kontrolnych, które są widoczne w przyborniku. Można ustawić projektu pod kątem różnych wersji programu .NET Framework ze stron właściwości projektu. Wybierz węzeł projektu w **Eksploratora rozwiązań**, a następnie na pasku menu wybierz pozycję **projektu** > **\<projektu\> właściwości**. Na **aplikacji** użyj **platformy docelowej** listy rozwijanej.

## <a name="managing-the-toolbox-window-and-its-controls"></a>Zarządzanie okno przybornika i jego formantów

Domyślnie przybornik jest zwinięty z lewej strony środowiska IDE programu Visual Studio i jest wyświetlany, gdy kursor jest przesuwany nad go. Można przypiąć przybornika (klikając **numeru Pin** ikony na jego pasku narzędzi), aby zostanie zamknięte po przeniesieniu kursora. Można również Oddokuj okno przybornika i przeciągnij go w dowolnym miejscu na ekranie. Można dock, Oddokuj i Ukryj przybornika prawym przyciskiem myszy jego narzędzi i wybierając jedną z opcji.

Można zmienić kolejność elementów na karcie przybornika lub Dodaj niestandardowe karty i elementy za pomocą następujących poleceń w menu kontekstowym:

- **Zmień nazwę elementu** — zmienia nazwę wybranego elementu.

- **Pokaż wszystkie** — pokazuje wszystkie możliwe kontrole (nie tylko te, które dotyczą biezacym projektantem).

- **Widok listy** — zawiera kontrolki pionowy listy. Jeśli nie jest zaznaczone, kontrolki są wyświetlane poziomo.

- **Wybierz elementy** -otwiera **wybierz elementy przybornika** okna dialogowego, dzięki czemu można określić elementów, które są widoczne w **przybornika**. Możesz wyświetlić lub ukryć element zaznaczając lub usuwając zaznaczenie pola wyboru.

- **Sortowanie elementów alfabetycznie** -Sortuje elementy według nazwy.

- **Resetuj narzędzi** — przywraca domyślne ustawienia przybornika i elementów.

- **Dodaj kartę** -dodaje na nowej karcie przybornika.

- **Przenieś w górę** -Przenosi wybrany element w górę.

- **Przenieś w dół** -Przenosi wybrany element w dół.

## <a name="creating-and-distributing-custom-toolbox-controls"></a>Tworzenie i rozpowszechnianie niestandardowe formanty z przybornika

Można utworzyć niestandardowe formanty z przybornika, albo z szablonem projektu, który jest oparty na uruchamianie [Windows Presentation Foundation](../../extensibility/creating-a-wpf-toolbox-control.md) lub na [formularzy systemu Windows](../../extensibility/creating-a-windows-forms-toolbox-control.md). Można następnie dystrybuować formantu niestandardowego do członków zespołu lub opublikować go w sieci web za pomocą [Instalatorze formanty przybornika](http://download.microsoft.com/download/8/3/6/836657BD-9CCB-4ED4-B9D2-FB769473B284/TCI_whitepaper.docx).

## <a name="help-on-toolbox-tabs"></a>Pomoc na temat kart z przybornika

Poniższe tematy zawierają więcej informacji na temat niektóre z dostępnych **przybornika** karty.

- [Przybornik, karta Dane](../../ide/reference/toolbox-data-tab.md)

- [Przybornik, karta Składniki](../../ide/reference/toolbox-components-tab.md)

- [Przybornik, karta HTML](../../ide/reference/toolbox-html-tab.md)
