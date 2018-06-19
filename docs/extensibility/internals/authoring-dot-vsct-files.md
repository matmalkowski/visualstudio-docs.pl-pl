---
title: Tworzenie. Pliki Vsct | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 65fc62d5685ca7c81b3ebb7f524db3cdbebe72c7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134776"
---
# <a name="authoring-vsct-files"></a>Tworzenie. Pliki Vsct
Ten dokument przedstawia sposób tworzenia pliku vsct, aby dodać elementy menu, paski narzędzi i inne elementy interfejsu użytkownika do programu Visual Studio zintegrowane środowisko programistyczne (IDE). Po dodaniu elementów interfejsu użytkownika do pakietu Visual Studio (pakiet VSPackage), który nie ma jeszcze pliku vsct, wykonaj następujące kroki.  
  
 Dla nowych projektów zaleca się, ponieważ generuje on pliku vsct, który w zależności od ustawień, jest już wymagane elementy tego polecenia menu okna narzędzia i edytora niestandardowego w przypadku użycia szablonu pakietu Visual Studio. Można modyfikować tego pliku vsct, aby spełnić te wymagania VSPackage. Aby uzyskać więcej informacji na temat sposobu modyfikowania pliku vsct, zobacz przykłady w [rozszerzanie menu i poleceń](../../extensibility/extending-menus-and-commands.md).  
  
## <a name="authoring-the-file"></a>Tworzenie pliku  
 Tworzenie pliku vsct w tych fazach: Utwórz strukturę dla plików i zasobów, deklarować elementów interfejsu użytkownika, umieść elementy interfejsu użytkownika w środowisku IDE i Dodaj wszelkie specjalne zachowania.  
  
### <a name="file-structure"></a>Struktura pliku  
 Podstawowa struktura pliku vsct jest [CommandTable](../../extensibility/commandtable-element.md) elementu głównego, który zawiera [polecenia](../../extensibility/commands-element.md) elementu i [symbole](../../extensibility/symbols-element.md) elementu.  
  
##### <a name="to-create-the-file-structure"></a>Aby utworzyć struktury plików  
  
1.  Dodawanie pliku vsct do projektu, wykonując kroki opisane w [porady: tworzenie. Pliku Vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md).  
  
2.  Dodawanie wymaganych obszarów nazw do `CommandTable` element, jak pokazano w poniższym przykładzie.  
  
    ```xml  
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"   
        xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
    ```  
  
3.  W `CommandTable` elementu, Dodaj `Commands` element do obsługi wszystkich niestandardowych menu, paski narzędzi, polecenia grup i poleceń. Tak, aby załadować niestandardowe elementy interfejsu użytkownika, `Commands` element musi mieć jego `Package` atrybutów należy ustawić nazwę pakietu.  
  
     Po `Commands` elementu, Dodaj `Symbols` element, aby zdefiniować identyfikatory GUID dla pakietu i nazwy i identyfikatory poleceń dla elementów interfejsu użytkownika.  
  
### <a name="including-visual-studio-resources"></a>W tym zasobów programu Visual Studio  
 Użyj [Extern](../../extensibility/extern-element.md) element dostęp do plików, które definiują polecenia programu Visual Studio i menu, które są wymagane, aby umieścić elementów interfejsu użytkownika w środowisku IDE. Jeśli używasz poleceń zdefiniowanych poza pakietu, należy użyć [UsedCommands](../../extensibility/usedcommands-element.md) elementu, aby poinformować Visual Studio.  
  
##### <a name="to-include-visual-studio-resources"></a>Aby uwzględnić zasoby programu Visual Studio  
  
1.  W górnej części `CommandTable` elementu, dodaj je `Extern` elementu dla każdego pliku zewnętrznego, odwołania i ustawienie `href` atrybutu nazwy pliku. Możesz odwoływać się do następujących plików nagłówka dostęp do zasobów programu Visual Studio:  
  
    -   Stdidcmd.h, definiuje identyfikatory wszystkich poleceń uwidocznionych przez program Visual Studio.  
  
    -   Vsshlids.h, zawiera identyfikatory poleceń dla menu programu Visual Studio.  
  
2.  Jeśli pakiet wymaga żadnych poleceń, które są zdefiniowane przez program Visual Studio lub przez inne pakiety, Dodaj `UsedCommands` elementu po `Commands` elementu. Wypełnij ten element z [UsedCommand](../../extensibility/usedcommand-element.md) elementu dla każdego polecenia, który jest wywołania nie jest częścią pakietu. Ustaw `guid` i `id` atrybuty `UsedCommand` elementy z wartościami identyfikator GUID i identyfikator polecenia do wywołania. Aby uzyskać więcej informacji o sposobach znajdowania polecenia identyfikatorów GUID i identyfikatory programu Visual Studio, zobacz [identyfikatory GUID oraz identyfikatory programu Visual Studio — polecenia](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md). Aby wywołać polecenia od innych pakietów, użyj identyfikator GUID i identyfikator polecenia zgodnie z definicją w pliku vsct dla tych pakietów.  
  
### <a name="declaring-ui-elements"></a>Zadeklarowanie elementów interfejsu użytkownika  
 Deklarowanie nowe elementy interfejsu użytkownika w `Symbols` sekcji pliku vsct.  
  
##### <a name="to-declare-ui-elements"></a>Aby zadeklarować elementy interfejsu użytkownika  
  
1.  W `Symbols` elementu, Dodaj trzy [GuidSymbol](../../extensibility/guidsymbol-element.md) elementów. Każdy `GuidSymbol` element ma `name` atrybutu i `value` atrybutu. Ustaw `name` atrybutu, aby odzwierciedlały celem elementu. `value` Atrybut przyjmuje postać identyfikatora GUID. (Do generowania identyfikatora GUID, na **narzędzia** menu, kliknij przycisk **utworzyć identyfikatora GUID**, a następnie wybierz **Format rejestru**.)  
  
     Pierwszy `GuidSymbol` — element reprezentuje pakiet i zazwyczaj nie ma elementów podrzędnych. Drugi `GuidSymbol` element reprezentuje polecenie Ustaw i będzie zawierać wszystkie symbole, które definiują menu, grup i poleceń. Trzeci `GuidSymbol` — element reprezentuje sklepu obrazu i zawiera symbole dla wszystkich ikony poleceń. Jeśli nie masz żadnych poleceń, które ikony, można pominąć trzeci `GuidSymbol` elementu.  
  
2.  W `GuidSymbol` elementu, który reprezentuje zestaw poleceń, Dodaj jeden lub kilka [IDSymbol](../../extensibility/idsymbol-element.md) elementów. Każdy z nich reprezentują menu, paska narzędzi, grupy lub polecenia, które dodajesz do interfejsu użytkownika.  
  
     Dla każdego `IDSymbol` , ustaw `name` atrybutu nazwa będzie używana do odwoływania się do odpowiedniego menu, grupy lub polecenia, a następnie ustaw `value` elementu w postaci szesnastkowej reprezentujące identyfikatora polecenia. Nie dwa `IDSymbol` elementów, które mają ten sam nadrzędny element może mieć taką samą wartość.  
  
3.  Jeśli dowolne elementy interfejsu użytkownika wymaga ikony, Dodaj `IDSymbol` elementu dla każdego ikonę, aby `GuidSymbol` elementu, który reprezentuje obraz sklepu.  
  
### <a name="putting-ui-elements-in-the-ide"></a>Umieszczanie elementy interfejsu użytkownika w środowisku IDE  
 [Menu](../../extensibility/menus-element.md) elementu [grup](../../extensibility/groups-element.md) elementu i [przyciski](../../extensibility/buttons-element.md) element zawiera definicje dla wszystkich menu, grup i poleceń, które są zdefiniowane w pakiecie. Umieść te menu, grup i poleceń w IDE przy użyciu [nadrzędnej](../../extensibility/parent-element.md) element, który jest częścią definicji elementu interfejsu użytkownika lub za pomocą [CommandPlacement](../../extensibility/commandplacement-element.md) element, który jest zdefiniowany w innym miejscu.  
  
 Każdy `Menu`, `Group`, i `Button` element ma `guid` atrybutu i `id` atrybutu. Zawsze wartość `guid` atrybutu do dopasowania nazwy `GuidSymbol` elementu, który reprezentuje polecenie ustawić i `id` atrybutu nazwy `IDSymbol` elementu, który reprezentuje z menu, grupę lub polecenie `Symbols`sekcji.  
  
##### <a name="to-define-ui-elements"></a>Aby zdefiniować elementy interfejsu użytkownika  
  
1.  Jeśli definiujesz nowe menu, podmenu, menu skrótów i paski narzędzi, Dodaj `Menus` elementu `Commands` elementu. Następnie dla każdego menu ma zostać utworzony, Dodaj [Menu](../../extensibility/menu-element.md) elementu `Menus` elementu.  
  
     Ustaw `guid` i `id` atrybuty `Menu` elementu, a następnie ustawić `type` do typu menu ma atrybut. Można również ustawić `priority` atrybutu ustanowienie względne położenie menu w grupie nadrzędnej.  
  
    > [!NOTE]
    >  `priority` Atrybutu nie obejmuje pasków narzędzi i menu kontekstowego.  
  
2.  Wszystkie polecenia w środowisku IDE programu Visual Studio musi być obsługiwana przez polecenie grup, które są bezpośrednimi elementami podrzędnymi menu i pasków narzędzi. Jeśli dodajesz nowe menu i pasków narzędzi do środowiska IDE programu zawierają one nowe grupy polecenia. Możesz też dodać grupy polecenia do istniejącego menu i pasków narzędzi, dzięki czemu będzie można grupować poleceń.  
  
     Po dodaniu nowych grup polecenia, należy najpierw utworzyć `Groups` elementu, a następnie dodaj do niej [grupy](../../extensibility/group-element.md) elementu dla każdej grupy polecenia.  
  
     Ustaw `guid` i `id` atrybuty każdego `Group` elementu, a następnie ustawić `priority` atrybutu ustanowienie względne położenie grupy menu nadrzędnego. Aby uzyskać więcej informacji, zobacz [tworzenie wielokrotnego użytku grup przycisków](../../extensibility/creating-reusable-groups-of-buttons.md).  
  
3.  Jeśli dodajesz nowe polecenia do środowiska IDE, Dodaj `Buttons` elementu `Commands` elementu. Następnie dla każdego polecenia Dodaj [przycisk](../../extensibility/button-element.md) elementu `Buttons` elementu.  
  
    1.  Ustaw `guid` i `id` atrybuty każdego `Button` elementu, a następnie ustawić `type` do rodzaj przycisku, który ma atrybut. Można również ustawić `priority` atrybutu ustanowienie względne położenie polecenia w grupie nadrzędnej.  
  
        > [!NOTE]
        >  Użyj `type="button"` przycisków na paskach narzędzi i poleceń menu standardowego.  
  
    2.  W `Button` elementu, Dodaj [ciągów](../../extensibility/strings-element.md) element, który zawiera [ButtonText](../../extensibility/buttontext-element.md) elementu i [CommandName](../../extensibility/commandname-element.md) elementu. `ButtonText` Element udostępnia etykietę tekstową dla elementu menu lub etykietkę narzędzia dla przycisku paska narzędzi. `CommandName` Element zawiera nazwę polecenia można również użyć w poleceniu.  
  
    3.  Jeśli polecenie zostanie ikony, Utwórz [ikona](../../extensibility/icon-element.md) element `Button` element i ustaw jej `guid` i `id` atrybuty do `Bitmap` element ikony.  
  
        > [!NOTE]
        >  Przyciski paska narzędzi musi mieć ikon.  
  
     Aby uzyskać więcej informacji, zobacz [MenuCommands Vs. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md).  
  
4.  Jeśli dowolne poleceniach wymagają ikony, Dodaj [mapy bitowe](../../extensibility/bitmaps-element.md) elementu `Commands` elementu. Następnie dla każdego ikony, Dodaj [mapy bitowej](../../extensibility/bitmap-element.md) elementu `Bitmaps` elementu. Jest to, gdzie należy określić lokalizację zasobu mapy bitowej. Aby uzyskać więcej informacji, zobacz [dodawanie ikon do poleceń Menu](../../extensibility/adding-icons-to-menu-commands.md).  
  
 Użytkownik może polegać na strukturze element nadrzędny poprawnie umieścić większości menu, grup i poleceń. Dla polecenia bardzo dużych zestawów lub po menu, grupy lub polecenia musi występować w wielu miejscach, zalecamy, aby określić położenie polecenia.  
  
##### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>Polegać na element nadrzędny, aby umieścić elementy interfejsu użytkownika w środowisku IDE  
  
1.  Typowy element nadrzędny, można utworzyć `Parent` elementu w każdym `Menu`, `Group`, i `Command` element, który jest zdefiniowany w pakiecie.  
  
     Element docelowy `Parent` jest element menu lub grupy, która będzie zawierać menu, grupy lub polecenie.  
  
    1.  Ustaw `guid` atrybutu nazwy `GuidSymbol` element, który definiuje zestaw poleceń. Jeśli element docelowy nie jest częścią pakietu, należy użyć identyfikatora guid dla tego zestawu poleceń, zgodnie z definicją w odpowiedniego pliku vsct.  
  
    2.  Ustaw `id` atrybutu do dopasowania `id` atrybut menu docelowej lub grupy. Dla listy menu i grupy, które są dostępne w programie Visual Studio, zobacz [identyfikatory GUID oraz identyfikatory programu Visual Studio menu](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) lub [identyfikatory GUID oraz identyfikatory programu Visual Studio paski narzędzi](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md).  
  
 Jeśli masz dużą liczbę elementów interfejsu użytkownika można umieścić w IDE lub mają elementy, które powinny być wyświetlane w wielu miejscach, zdefiniuj ich rozmieszczanie w [CommandPlacements](../../extensibility/commandplacements-element.md) element, jak pokazano w poniższych krokach.  
  
##### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>Na potrzeby umieszczania polecenie Umieść elementy interfejsu użytkownika w środowisku IDE  
  
1.  Po `Commands` elementu, Dodaj `CommandPlacements` elementu.  
  
2.  W `CommandPlacements` elementu, Dodaj `CommandPlacement` elementu dla każdego menu, grupy lub polecenia do umieszczenia.  
  
     Każdy `CommandPlacement` element lub `Parent` element umieszcza jeden menu, grupy lub polecenia w jednym miejscu IDE. Element interfejsu użytkownika może mieć tylko jednego zdarzenia nadrzędnego, ale może mieć wielu rozmieszczanie polecenia. Można umieścić elementu interfejsu użytkownika w wielu lokalizacjach, należy dodać `CommandPlacement` elementu dla każdej lokalizacji.  
  
3.  Ustaw `guid` i `id` atrybuty każdego `CommandPlacement` elementu do hostingu menu lub grupy, podobnie jak w przypadku `Parent` elementu. Można również ustawić `priority` atrybutu ustanowienie względne położenie elementu interfejsu użytkownika.  
  
 Można mieszać umieszczania przez element nadrzędny i położenie polecenia. Dla polecenia bardzo dużych zestawów, zalecamy użycie tylko polecenia umieszczania.  
  
### <a name="adding-specialized-behaviors"></a>Dodawanie zachowań specjalne  
 Można użyć [CommandFlag](../../extensibility/command-flag-element.md) elementy, aby zmodyfikować zachowanie menu i poleceń, na przykład, aby zmienić ich wyglądu i widoczności. Można także wpływać po poleceniu jest widoczna przy użyciu [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md), lub dodać skróty klawiaturowe przy użyciu [powiązania klawiszy](../../extensibility/keybindings-element.md). Niektóre rodzaje menu i poleceń już mieć specjalizowany zachowania wbudowane.  
  
##### <a name="to-add-specialized-behaviors"></a>Aby dodać specjalne zachowania  
  
1.  Aby element interfejsu użytkownika było widoczne tylko w niektórych kontekstach interfejsu użytkownika, na przykład po załadowaniu rozwiązania, użyj ograniczenia widoczności.  
  
    1.  Po `Commands` elementu, Dodaj `VisibilityConstraints` elementu.  
  
    2.  Dla każdego elementu interfejsu użytkownika ograniczyć, Dodaj [VisibilityItem](../../extensibility/visibilityitem-element.md) elementu.  
  
    3.  Dla każdego `VisibilityItem` , ustaw `guid` i `id` atrybuty do menu, grupy lub polecenia, a następnie ustawić `context` atrybutu kontekstu interfejsu użytkownika, należy zgodnie z definicją w <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> klasy. Aby uzyskać więcej informacji, zobacz [VisibilityItem elementu](../../extensibility/visibilityitem-element.md).  
  
2.  Aby ustawić widoczność lub dostępność elementu interfejsu użytkownika w kodzie, należy użyć co najmniej jeden z następujących flag polecenia:  
  
    -   DefaultDisabled  
  
    -   DefaultInvisible  
  
    -   DynamicItemStart  
  
    -   DynamicVisibility  
  
    -   NoShowOnMenuController  
  
    -   NotInTBList  
  
     Aby uzyskać więcej informacji, zobacz [Element Command flagi](../../extensibility/command-flag-element.md).  
  
3.  Aby zmienić sposób element pojawi się lub zmienić jego wygląd dynamicznie, należy użyć co najmniej jeden z następujących flag polecenia:  
  
    -   AlwaysCreate  
  
    -   CommandWellOnly  
  
    -   DefaultDocked  
  
    -   DontCache  
  
    -   DynamicItemStart  
  
    -   FixMenuController  
  
    -   IconAndText  
  
    -   PICT  
  
    -   StretchHorizontally  
  
    -   TextMenuUseButton  
  
    -   TextChanges  
  
    -   TextOnly  
  
     Aby uzyskać więcej informacji, zobacz [Element Command flagi](../../extensibility/command-flag-element.md).  
  
4.  Aby zmienić zachowaniem elementu po odebraniu polecenia, należy użyć co najmniej jeden z następujących flag polecenia:  
  
    -   AllowParams  
  
    -   CaseSensitive  
  
    -   CommandWellOnly  
  
    -   KlawiszeFiltru  
  
    -   NoAutoComplete  
  
    -   NoButtonCustomize  
  
    -   NoKeyCustomize  
  
    -   NoToolbarClose  
  
    -   PostExec  
  
    -   RouteToDocs  
  
    -   TextIsAnchorCommand  
  
     Aby uzyskać więcej informacji, zobacz [Element Command flagi](../../extensibility/command-flag-element.md).  
  
5.  Aby dołączyć skrót klawiaturowy zależne od menu menu lub elementu menu, Dodaj znak handlowe "i" ("&") w `ButtonText` elementu menu lub elementu menu. Znaku handlowego "i" następującego skrót klawiaturowy active po otwarciu menu nadrzędnego.  
  
6.  Aby dołączyć skrót klawiaturowy niezależny od menu do polecenia, użyj [powiązania klawiszy](../../extensibility/keybindings-element.md). Aby uzyskać więcej informacji, zobacz [KeyBinding elementu](../../extensibility/keybinding-element.md).  
  
7.  Aby zlokalizować tekst menu, użyj `LocCanonicalName` elementu. Aby uzyskać więcej informacji, zobacz [Element ciągów](../../extensibility/strings-element.md).  
  
 Niektóre typy menu i przycisk to specjalne zachowania. W poniższej tabeli opisano niektóre specjalne menu i typy przycisku. Dla innych typów, zobacz `types` atrybutu opisów w [Menu Element](../../extensibility/menu-element.md), [Button Element](../../extensibility/button-element.md), i [kombi Element](../../extensibility/combo-element.md).  
  
 Pola kombi  
 Pola kombi jest listy rozwijanej, która może być używany na pasku narzędzi. Aby dodać pola kombi do interfejsu użytkownika, należy utworzyć [kombinacje](../../extensibility/combos-element.md) element `Commands` elementu. Następnie dodaj do `Combos` element `Combo` elementu dla każdego pola kombi do dodania. `Combo` elementy mają te same atrybuty i elementy podrzędne jako `Button` elementy, a także `DefaultWidth` i `idCommandList` atrybutów. `DefaultWidth` Atrybut Ustawia szerokość w pikselach i `idCommandList` atrybutu punktów Identyfikatora polecenia, który jest używany do wypełnienia pola kombi. Aby uzyskać więcej informacji, zobacz `Combo` dokumentację elementu.  
  
 MenuController  
 Kontroler menu jest przycisk strzałka obok niej. Klikając strzałkę Otwiera listę. Aby dodać kontroler menu do interfejsu użytkownika, należy utworzyć `Menu` element i ustaw jej `type` atrybutu **MenuController** lub **MenuControllerLatched**w oparciu o żądane zachowanie. Aby wypełnić kontrolera menu, ustaw go jako element nadrzędny `Group` elementu. Kontroler menu spowoduje wyświetlenie wszystkich obiektów podrzędnych tej grupy na liście rozwijanej.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie menu i poleceń](../../extensibility/extending-menus-and-commands.md)   
 [Tabela polecenia programu Visual Studio (. Pliki Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Odwołanie do schematu XML VSCT](../../extensibility/vsct-xml-schema-reference.md)