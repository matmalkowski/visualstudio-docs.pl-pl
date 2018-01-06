---
title: "Identyfikatory poleceń programu Visual Studio i identyfikatory GUID | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 44ae5ff7e9095d6c88d753342da30983b30b7364
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>Identyfikatory GUID i identyfikatory poleceń programu Visual Studio
Identyfikator GUID i identyfikator wartości polecenia uwzględnione w programie Visual Studio zintegrowane środowisko programistyczne (IDE) są definiowane w vsct pliki, które są instalowane jako część programu Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [IDE-Defined polecenia, menu oraz grup](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
 Aby uzyskać więcej informacji na temat pracy z obiektami IDE, które są zdefiniowane w plikach vsct, zobacz [rozszerzanie menu i poleceń](../../extensibility/extending-menus-and-commands.md).  
  
## <a name="finding-a-command-definition"></a>Znajdowanie definicji poleceń  
 Ponieważ Visual Studio określa więcej niż jednego tysiąca poleceń, jest niemożliwe do tutaj je wszystkie. Zamiast tego wykonaj następujące kroki, aby zlokalizować definicji polecenia.  
  
#### <a name="to-locate-a-command-definition"></a>Aby zlokalizować definicji poleceń  
  
1.  W programie Visual Studio Otwórz następujące pliki *ścieżki instalacji programu Visual Studio SDK*folderu \VisualStudioIntegration\Common\Inc\: SharedCmdDef.vsct, ShellCmdDef.vsct, VsDbgCmdUsed.vsct, Venusmenu.vsct.  
  
     Większość poleceń Visual Studio są definiowane w SharedCmdDef.vsct i ShellCmdDef.vsct. VsDbgCmdUsed.vsct definiuje poleceń, które odnoszą się do debugera, a Venusmenu.vsct definiuje poleceń, które są specyficzne dla aplikacji sieci Web.  
  
2.  Jeśli polecenie jest element menu, weź pod uwagę dokładny tekst elementu menu. Jeśli polecenie jest przycisku paska narzędzi, weź pod uwagę tekst etykietki narzędzia wyświetlany po wstrzymaniu na nim.  
  
3.  Naciśnij klawisze CTRL + F, aby otworzyć **znaleźć** okno dialogowe.  
  
4.  W **Znajdź** wpisz tekst zanotowaną w kroku 2.  
  
5.  Sprawdź, czy **wszystkie otwarte dokumenty** jest wyświetlany w **Szukaj w** pole.  
  
6.  Kliknij przycisk **Znajdź następny** przycisku do momentu wybrania tekst w `<Strings>` sekcji [Button Element](../../extensibility/button-element.md).  
  
     `<Button>` Elementu wyświetlanego w poleceniu jest definicji polecenia.  
  
 Po odnalezieniu definicji poleceń kopię polecenia można umieścić w innym menu lub pasek narzędzi przez utworzenie [elementu CommandPlacement](../../extensibility/commandplacement-element.md) ma taką samą `guid` i `id` wartości jako polecenie. Aby uzyskać więcej informacji, zobacz [tworzenie wielokrotnego użytku grup przycisków](../../extensibility/creating-reusable-groups-of-buttons.md).  
  
### <a name="special-cases"></a>Specjalne przypadki  
 W następujących przypadkach tekst menu lub tekst etykietki narzędzia mogą nie pasować nowości w definicji polecenia.  
  
-   Elementy menu, które obejmują podkreślony znak, takie jak **drukowania** na **pliku** menu, w którym jest podkreślona P.  
  
     Znaki, które są poprzedzone znakiem "&" w nazwach elementów menu są wyświetlane jako podkreślony. Jednak vsct pliki są zapisywane w pliku XML, który używa znaku "&", aby wskazać znaków specjalnych i wymaga się, że należy określić znak, który ma być wyświetlany jako&amp;". W związku z tym w pliku vsct **P**polecenie Drukowanie jest wyświetlany jako "&amp;drukowania".  
  
-   Polecenia, które mają dynamiczne tekstu, takich jak **zapisać** *nazwę pliku bieżącego*i dynamicznie generowane dla elementów menu, takich jak elementy **ostatnio używanych plików** listy.  
  
     Nie istnieje niezawodny sposób wyszukiwania na dynamiczny tekst. Zamiast tego należy znaleźć grupy hostującego odpowiedniego polecenia przez konsultacji [identyfikatory GUID oraz identyfikatory programu Visual Studio menu](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) lub [identyfikatory GUID oraz identyfikatory programu Visual Studio paski narzędzi](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)i wyszukiwania identyfikator w tej grupie. Jeśli definicji polecenia nie ma grupy jako jego [elementu nadrzędnego](../../extensibility/parent-element.md), wyszukaj SharedCmdPlace.vsct i ShellCmdPlace.vsct (lub VsDbgCmdPlace.vsct poleceń debugera) `<CommandPlacement>` element, który ustawia element nadrzędny polecenie. AndVsDbgCmdPlace.vsct SharedCmdPlace.vsct, ShellCmdPlace.vsct, znajdują się w *ścieżki instalacji programu Visual Studio SDK*\VisualStudioIntegration\Common\Inc\ folderu.  
  
## <a name="see-also"></a>Zobacz też  
 [MenuCommands Vs. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)   
 [Tabela polecenia programu Visual Studio (. Pliki Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Odwołanie do schematu XML VSCT](../../extensibility/vsct-xml-schema-reference.md)