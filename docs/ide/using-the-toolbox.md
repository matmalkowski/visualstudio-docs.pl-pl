---
title: Korzystanie z przybornika | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.chooseitems
- vs.toolboxpages.activexcontrols
- VS.CHOOSEITEMS.windowsuixamlcomponents
- VS.chooseitems.silverlightcomponents
- VC.EDITORS.RIBBON
- vs.customizetoolbox
- VS.chooseitems.System.Workflow_Components
- vs.chooseitems.frameworkcomponents
- VS.ToolboxPages..NET_Framework_Components
- VS.chooseitems.Microsoft.VisualStudio.Toolbox.VsToolboxPage
- vs.chooseitems.comcomponents
- vs.toolboxpages.NGWS_components
helpviewer_keywords:
- toolbox, adding items
- Visual Studio, toolbox
- toolbox, tabs
- toolbox
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c41a77a1fdb36ab8610ebc648cacb1568b330de8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-toolbox"></a>Korzystanie z Przybornika

Przybornika umożliwia Dodaj formanty i inne elementy do projektu. Możesz przeciągać i upuszczać inne formanty na powierzchnię projektanta używasz i zmień rozmiar i umieść formanty.

Przybornik pojawi się w połączeniu z projektanta widoków, takich jak Widok projektanta w pliku XAML. Pasek narzędzi wyświetla tylko formanty, które mogą być używane w bieżącym projektancie.

Wersja programu .NET Framework, że elementem docelowym projektu jest również wpływa na zestaw mechanizmów kontrolnych, które są widoczne w przyborniku. Można ustawić projektu pod kątem różnych wersji programu .NET Framework, wybierając węzeł projektu w **Eksploratora rozwiązań**, a następnie przechodząc do **platformy docelowej-właściwości/aplikacji**.

## <a name="managing-the-toolbox-and-its-controls"></a>Zarządzanie przybornika i jego formantów

Domyślnie przybornika jest zwinięty z lewej strony środowiska IDE programu Visual Studio i jest wyświetlany, gdy kursor jest przesuwany nad go. Można przypiąć przybornika (klikając **numeru Pin** ikonę na pasku narzędzi przybornika), dzięki czemu pozostanie otwarte po przeniesieniu kursora. Można również Oddokuj okno przybornika i przeciągnij go w dowolnym miejscu na ekranie. Można dock, Oddokuj i Ukryj przybornika prawym przyciskiem myszy na pasku narzędzi z przybornika i wybierając jedną z opcji.

Można zmienić kolejność elementów na karcie przybornika lub Dodaj niestandardowe karty i elementy za pomocą następujących poleceń w menu kontekstowym:

-   **Zmień nazwę elementu** — zmienia nazwę wybranego elementu.  
  
-   **Pokaż wszystkie** — pokazuje wszystkie możliwe kontrole (nie tylko te, które dotyczą biezacym projektantem).  
  
-   **Widok listy** — zawiera kontrolki pionowy listy. Jeśli nie jest zaznaczone, kontrolki są wyświetlane poziomo.  
  
-   **Wybierz elementy** -otwiera **wybierz elementy przybornika** okna dialogowego, dzięki czemu można określić elementów, które są widoczne w **przybornika**. Możesz wyświetlić lub ukryć element zaznaczając lub usuwając zaznaczenie pola wyboru.  
  
-   **Sortowanie elementów alfabetycznie** -Sortuje elementy według nazwy.  
  
-   **Resetuj narzędzi** — przywraca domyślne ustawienia przybornika i elementów.  
  
-   **Dodaj kartę** -dodaje na nowej karcie przybornika.  
  
-   **Przenieś w górę** -Przenosi wybrany element w górę.  
  
-   **Przenieś w dół** -Przenosi wybrany element w dół.  

## <a name="creating-and-distributing-custom-toolbox-controls"></a>Tworzenie i dystrybucja kontrolek niestandardowych przybornika

Można utworzyć formantu niestandardowego przybornika w języku Visual Basic lub Visual C# i można uruchomić z szablonem projektu, który jest oparty na [Windows Presentation Foundation](../extensibility/creating-a-wpf-toolbox-control.md) lub [formularzy systemu Windows](../extensibility/creating-a-windows-forms-toolbox-control.md). Możesz przekazać formantu członków zespołu lub opublikować go w sieci web za pomocą [Instalatorze formanty przybornika](http://download.microsoft.com/download/8/3/6/836657BD-9CCB-4ED4-B9D2-FB769473B284/TCI_whitepaper.docx).

## <a name="see-also"></a>Zobacz także

[Pisanie kodu w edytorze](../ide/writing-code-in-the-code-and-text-editor.md)