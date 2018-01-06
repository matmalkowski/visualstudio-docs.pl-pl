---
title: "Polecenia, menu i pasków narzędzi | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- commands [Visual Studio]
- toolbars [Visual Studio], commands
ms.assetid: 07b4ed90-dbbd-40df-b6c9-8395fd6f2ab6
caps.latest.revision: "60"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fa1513bcd61ac63fb9d2a59f69a8b2ce22cf5114
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="commands-menus-and-toolbars"></a>Polecenia, menu i pasków narzędzi
Menu i pasków narzędzi są przez użytkowników dostępu do polecenia w pakiecie VSPackage. Polecenia są funkcje, których wykonywanie zadań, takich jak drukowanie dokumentu, odświeżenie widoku lub utworzenie nowego pliku. Menu i pasków narzędzi są graficznego wygodnie prezentować poleceniach użytkownikom. Zazwyczaj pokrewnych poleceń są zgrupowane razem z menu lub pasek narzędzi.  
  
-   Menu zwykle są wyświetlane jako ciągi jednowyrazowym klastrowane w wierszu w górnej części zintegrowane środowisko programistyczne (IDE) lub okna narzędzia. Menu również mogą być wyświetlane jako wynik zdarzenia, kliknij prawym przyciskiem myszy i są określane jako menu skrótów, w tym kontekście. Po kliknięciu menu Rozwiń do wyświetlenia co najmniej jedno polecenie. Polecenia, po kliknięciu, można wykonywać zadania lub uruchom podmenu, które zawierają dodatkowe polecenia. Niektóre nazwy menu dobrze znanego to plik, Edytuj widok i okna. Aby uzyskać więcej informacji, zobacz [rozszerzanie menu i poleceń](../../extensibility/extending-menus-and-commands.md).  
  
-   Paski narzędzi są zwykle wierszy przycisków i innych kontrolek, takich jak pola kombi, pola listy, pola tekstowe i kontrolerów menu. Wszystkie formanty paska narzędzi są skojarzone z poleceń. Po kliknięciu przycisku paska narzędzi jego skojarzone polecenie jest aktywowane. Przyciski paska narzędzi zwykle mają ikony, które sugeruje podstawowych poleceń, takich jak drukarki dla polecenia drukowania. W formancie listy rozwijanej każdego elementu na liście jest skojarzona z inną polecenia. Kontroler menu jest hybrydowego, w którym jednej stronie formantu jest przycisku paska narzędzi i drugiej stronie jest strzałkę w dół, który wyświetla dodatkowe polecenia po kliknięciu. Aby uzyskać więcej informacji, zobacz [dodawania kontrolera Menu do paska narzędzi](../../extensibility/adding-a-menu-controller-to-a-toolbar.md).  
  
-   Podczas tworzenia polecenia należy także utworzyć program obsługi zdarzeń dla niego. Program obsługi zdarzeń określa, kiedy polecenie jest widoczny czy włączone, można zmodyfikować jego tekstu i zapewnia, że polecenie odpowiednio reaguje ("tras") po uaktywnieniu. W większości przypadków środowiska IDE programu obsługi poleceń przy użyciu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu. Polecenia w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] trasy hierarchicznie, począwszy od kontekstu polecenia najbardziej wewnętrznego, na podstawie zaznaczenia lokalne i nastąpi przejście najbardziej zewnętrznego kontekst, w oparciu o wybór globalne. Polecenia dodane do menu głównego są natychmiast dostępne dla skryptów. Aby uzyskać więcej informacji, zobacz [MenuCommands Vs. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md) i [wybór obiektów kontekstu](../../extensibility/internals/selection-context-objects.md).  
  
 Aby zdefiniować nowe menu i pasków narzędzi, musi opisywać je w pliku tabeli poleceń w usłudze Visual Studio (vsct). Szablon pakietu Visual Studio tworzy ten plik, oraz elementy niezbędne do obsługi niezależnie od polecenia, paski narzędzi i edytory wybranego szablonu. Alternatywnie można napisać własny plik vsct za pomocą schematu xml opisane tutaj: [odwołanie do schematu XML VSCT](../../extensibility/vsct-xml-schema-reference.md).  
  
 Aby uzyskać więcej informacji na temat pracy z plikami vsct, zobacz [tabeli poleceń w usłudze Visual Studio (. Pliki Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Tematy w tej sekcji opisano, jak działają polecenia, menu i pasków narzędzi w VSPackages.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Szczegółowy opis specyfikacji formatu tabeli polecenia.  
  
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)  
 Zawiera opis składni opartych na języku XML i kompilatora dla polecenia tabel.  
  
 [Domyślne położenie poleceń, grup i pasków narzędzi](../../extensibility/internals/default-command-group-and-toolbar-placement.md)  
 W tym artykule opisano wstępnie zdefiniowanych poleceń, grupy menu i pasków narzędzi.  
  
 [Polecenia, menu i grupy definiowane w środowisku IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)  
 Określa wstępnie zdefiniowanych menu, poleceń i dostępny do użytku przez grupy polecenia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 [Projektowanie poleceń](../../extensibility/internals/command-design.md)  
 Wyjaśniono, jak zaprojektować poleceń.  
  
 [Optymalizacja poleceń menu i paska narzędzi](../../extensibility/internals/optimizing-menu-and-toolbar-commands.md)  
 Zawiera wskazówki dotyczące poleceń.  
  
 [Udostępnianie poleceń](../../extensibility/internals/making-commands-available.md)  
 Wyjaśniono, jak udostępnić polecenia dla programu Visual Studio.  
  
 [Polecenia i menu, w których używane są zestawy międzyoperacyjne](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)  
 Opisuje sposób nadawania poleceń, które używają zestawów międzyoperacyjnych.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Routing poleceń w pakietach VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)  
 W tym artykule wyjaśniono, routing poleceń w VSPackages.