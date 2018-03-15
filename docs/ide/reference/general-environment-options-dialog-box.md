---
title: "Ogólne, środowisko, opcje ― Okno dialogowe | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.Message.0x800a002e
- VS.ToolsOptionsPages.Environment.General
- VS.Environment.General
helpviewer_keywords:
- MRU lists
- windows, customizing
- MDI, environment options
- speed, environment animation
- File menu
- menus, customizing
- Windows menu customizing
- status bars, displaying
- Visual Studio Start page, setting
- IDE, startup options
- editors, autocompletion
- Options dialog box, General Environment
- General Environment Options dialog box
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 5c434b60efa054dbadcb8ef24470ed135d450e12
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="general-environment-options-dialog-box"></a>Ogólne, środowisko, opcje — Okno dialogowe

Ta strona służy do zmiany motywy kolorów, ustawienia paska stanu i skojarzenia rozszerzeń plików, wśród innych opcji, zintegrowane środowisko programistyczne (IDE). Można uzyskać dostępu do **opcje** okno dialogowe, otwierając **narzędzia** menu, wybierając **opcje**, otwierając **środowiska** folder, a następnie Wybieranie **ogólne** strony. Jeśli ta strona nie ma na liście, wybierz **Pokaż wszystkie ustawienia** pole wyboru w **opcje** okno dialogowe.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, otwórz **narzędzia** menu, a następnie wybierz pozycję **Import i eksport ustawień**. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="visual-experience"></a>Środowisko Visual

**Kolor motywu**

Wybierz **Blue**, **światła** lub **ciemny** motywu kolorów dla IDE.

Można zainstalować dodatkowe wstępnie zdefiniowanych motywów i tworzenie niestandardowych kompozycji przez pobranie i zainstalowanie **Visual Studio kolor motywu edytora** z [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor). Po zainstalowaniu tego narzędzia motywy kolorów dodatkowe są wyświetlane w polu listy Kolor motywu.

**Zastosuj wielkość liter tytułu paska menu**

Menu znajdują się w **wielkość liter w tytule** domyślnie. Usuń zaznaczenie tej opcji, aby ustawić je **wersaliki**.

**Automatycznie Dostosuj wyglądu na podstawie wydajności klienta**

Określa, czy program Visual Studio dostosowanie środowiska visual automatycznie ustawia lub jawnie ustaw dostosowania. To dopasowanie może zmienić wyświetlanie kolorów z gradienty kolorów ani może ograniczyć stosowanie animacji w menu lub okna podręcznego.

**Włączanie obsługi wzbogaconego klienta**

Włącza pełne visual środowiska Visual Studio, w tym gradienty i animacji. Usuń zaznaczenie tej opcji, gdy za pomocą połączenia pulpitu zdalnego lub starszych kart graficznych, ponieważ te funkcje może mieć pogorszenie wydajności w takich przypadkach. Ta opcja jest dostępna tylko wtedy, gdy zostanie ono wyczyszczone **automatycznie Dostosuj interfejs do klienta możliwości** opcji.

**Użyj sprzętowego przyspieszania grafiki, jeśli jest dostępne**

Używa sprzętowego przyspieszania grafiki, jeśli jest dostępna, a nie przyspieszenie oprogramowania.

## <a name="other"></a>Inne

**Elementy(ów) w menu okna** dostosowuje liczbę systemu windows, które pojawiają się na liście Windows **okna** menu. Wpisz liczbę z zakresu od 1 do 24. Domyślnie liczba wynosi 10.

**Elementy(ów) w ostatnio używane listy** dostosowuje liczbę ostatnio używanych projektów i pliki, które znajdują się w **pliku** menu. Wpisz liczbę z zakresu od 1 do 24. Domyślnie liczba wynosi 10. Jest to prosty sposób na pobranie ostatnio używanych projektów i pliki.

**Pokaż pasek stanu** Wyświetla pasek stanu. Pasek stanu znajduje się w dolnej części okna IDE i wyświetla informacje o postępie trwających operacji.

**Przycisk Zamknij dotyczy tylko aktywnego okna narzędzi** Określa, że w przypadku **Zamknij** przycisk zostanie kliknięty tylko aktywnego okna narzędzia został zamknięty i nie wszystkie z okna narzędzi w zestawie dokowanych. Domyślnie ta opcja jest zaznaczona.

**Przycisk Ukryj automatycznie dotyczy tylko aktywnego okna narzędzi** Określa, że w przypadku **automatyczne ukrywanie** przycisku, okna narzędzia, który ma fokus jest ukrywane automatycznie i nie wszystkie okna narzędzi w zestawie dokowanych. Domyślnie ta opcja nie wybrano żadnych działań.

## <a name="see-also"></a>Zobacz także

[Okno dialogowe opcji środowiska](../../ide/reference/environment-options-dialog-box.md)
[dostosowywanie układów okien](../../ide/customizing-window-layouts-in-visual-studio.md)