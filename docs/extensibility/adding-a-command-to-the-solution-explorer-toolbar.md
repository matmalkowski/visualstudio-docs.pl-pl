---
title: Dodawanie polecenia na pasku narzędzi Eksplorator rozwiązań | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f6f732900ff3e73decb1dc01d5c131e26ba50669
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107390"
---
# <a name="adding-a-command-to-the-solution-explorer-toolbar"></a>Dodawanie polecenia na pasku narzędzi Eksplorator rozwiązań
W tym przewodniku pokazano, jak przycisk, aby dodać **Eksploratora rozwiązań** paska narzędzi.  
  
 Dowolnego polecenia na pasku narzędzi lub menu jest nazywany przycisku w programie Visual Studio. Po kliknięciu przycisku wykonywany jest kod obsługi polecenia. Zazwyczaj polecenia powiązane są zgrupowane w celu jedną grupę. Menu i pasków narzędzi działają jak kontenery grup. Priorytet określa kolejność wyświetlania poszczególnych poleceń w grupie w menu lub na pasku narzędzi. Aby zapobiec przycisk będzie wyświetlany na pasku narzędzi lub menu kontrolując jej widoczność. Polecenie, które ma na liście `<VisibilityConstraints>` sekcji pliku vsct pojawia się tylko w kontekście skojarzone. Widoczność nie może być stosowany do grup.  
  
 Aby uzyskać więcej informacji na temat menu, paska narzędzi poleceń i vsct plików, zobacz [polecenia, menu i pasków narzędzi](../extensibility/internals/commands-menus-and-toolbars.md).  
  
> [!NOTE]
>  Użyj plików XML polecenia tabeli (vsct) zamiast pliki konfiguracji (.ctc) tabeli poleceń do definiowania wygląd menu i poleceń w Twojej VSPackages. Aby uzyskać więcej informacji, zobacz [tabeli poleceń w usłudze Visual Studio (. Pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, użytkownik nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest uwzględniona jako opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-an-extension-with-a-menu-command"></a>Tworzenie rozszerzenia za pomocą polecenia Menu  
 Tworzenie projektu VSIX o nazwie `SolutionToolbar`. Dodaj szablon elementu menu polecenie o nazwie **ToolbarButton**. Aby dowiedzieć się, jak to zrobić, zobacz [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="adding-a-button-to-the-solution-explorer-toolbar"></a>Dodawanie przycisku w pasku narzędzi Eksplorator rozwiązań  
 Ta część przewodnika pokazano, jak przycisk, aby dodać **Eksploratora rozwiązań** paska narzędzi. Po kliknięciu przycisku jest uruchamiany kod w metodzie wywołania zwrotnego.  
  
1.  W pliku ToolbarButtonPackage.vsct, przejdź do `<Symbols>` sekcji. `<GuidSymbol>` Węzeł zawiera grupy menu i poleceń, który został wygenerowany przez szablon pakietu. Dodaj `<IDSymbol>` elementu, aby ten węzeł, aby zadeklarować grupy, w którym będą przechowywane polecenia.  
  
    ```xml  
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>  
    ```  
  
2.  W `<Groups>` sekcji po istniejący wpis grupy, zdefiniuj nową grupę, która można zadeklarować w poprzednim kroku.  
  
    ```xml  
    <Group guid="guidToolbarButtonPackageCmdSet"  
           id="SolutionToolbarGroup" priority="0xF000">  
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>  
          </Group>  
    ```  
  
     Ustawienie nadrzędnego pary GUID:ID `guidSHLMainMenu` i `IDM_VS_TOOL_PROJWIN` umieszcza w tej grupie **Eksploratora rozwiązań** narzędzi, a ustawienie wartości o wysokim priorytecie umieszcza je od innych grup polecenia.  
  
3.  W `<Buttons>` sekcji, zmień identyfikator elementu nadrzędnego wygenerowany `<Button>` wpis w celu uwzględnienia grupy, który został zdefiniowany w poprzednim kroku. Zmodyfikowane `<Button>` element powinien wyglądać następująco:  
  
    ```xml  
    <Button guid="guidToolbarButtonPackageCmdSet" id="ToolbarButtonId" priority="0x0100" type="Button">  
        <Parent guid="guidToolbarButtonPackageCmdSet" id="SolutionToolbarGroup" />  
        <Icon guid="guidImages" id="bmpPicStrikethrough" />  
        <Strings>  
            <ButtonText>Invoke ToolbarButton</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
4.  Skompiluj projekt i Rozpocznij debugowanie. Pojawi się eksperymentalne wystąpienie.  
  
     **Eksploratora rozwiązań** na prawo od istniejących przycisków paska narzędzi powinien być wyświetlany nowy przycisk polecenia. Ikona przycisku jest przekreślenia.  
  
5.  Kliknij przycisk Nowy.  
  
     Okno dialogowe ma wiadomości **ToolbarButtonPackage wewnątrz SolutionToolbar.ToolbarButton.MenuItemCallback()** powinien być wyświetlany.  
  
## <a name="controlling-the-visibility-of-a-button"></a>Kontrolowanie widoczności przycisku  
 Ta część przewodnika pokazano, jak ustawić widoczność przycisku paska narzędzi. Ustawiając jeden lub więcej projektów w kontekście `<VisibilityConstraints>` sekcji pliku SolutionToolbar.vsct ograniczyć przycisk się pojawić tylko po projektu lub projektów są otwarte.  
  
#### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>Do wyświetlania przycisku, gdy jeden lub więcej projektów są otwarte  
  
1.  W `<Buttons>` sekcji ToolbarButtonPackage.vsct, dodać dwie flagi polecenia do istniejącego `<Button>` elementu, między `<Strings>` i `<Icons>` tagów.  
  
    ```xml  
    <CommandFlag>DefaultInvisible</CommandFlag>  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    ```  
  
     `DefaultInvisible` i `DynamicVisibility` flagi musi być ustawiona dlatego w tym wpisy `<VisibilityConstraints>` sekcji zostały wprowadzone.  
  
2.  Utwórz `<VisibilityConstraints>` sekcja, która ma dwa `<VisibilityItem>` wpisów. Umieść nową sekcję tylko po upływie `</Commands>` tagu.  
  
    ```xml  
    <VisibilityConstraints>  
        <VisibilityItem guid="guidToolbarButtonPackageCmdSet"  
              id="ToolbarButtonId"  
              context="UICONTEXT_SolutionHasSingleProject" />  
        <VisibilityItem guid="guidToolbarButtonPackageCmdSet"  
              id="ToolbarButtonId"  
              context="UICONTEXT_SolutionHasMultipleProjects" />  
    </VisibilityConstraints>  
    ```  
  
     Każdy element widoczność reprezentuje warunku, pod którym jest wyświetlany przycisk określony. Aby zastosować wiele warunków, należy utworzyć wiele pozycji dla tego samego przycisku.  
  
3.  Skompiluj projekt i Rozpocznij debugowanie. Pojawi się eksperymentalne wystąpienie.  
  
     **Eksploratora rozwiązań** paska narzędzi nie zawiera przycisk przekreślenia.  
  
4.  Otwórz dowolnego rozwiązania, które zawiera projekt.  
  
     Na pasku narzędzi z prawej strony istniejące przyciski pojawi się przycisk przekreślenia.  
  
5.  Na **pliku** menu, kliknij przycisk **Zamknij rozwiązanie**. Przycisk zniknie z paska narzędzi.  
  
 Widoczność przycisku jest kontrolowany przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] do momentu załadowania pakiet VSPackage. Po załadowaniu pakiet VSPackage widoczność przycisku jest kontrolowana przez pakiet VSPackage.  Aby uzyskać więcej informacji, zobacz [MenuCommands Vs. OleMenuCommands](../extensibility/menucommands-vs-olemenucommands.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)