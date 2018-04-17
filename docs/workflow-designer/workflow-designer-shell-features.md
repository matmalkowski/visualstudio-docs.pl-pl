---
title: Funkcji powłoki projektanta przepływów pracy | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- WFDShellFeatures.UI
ms.assetid: 14bfe312-9592-408e-92ce-e98585ad16e7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ecf7d88b6436ba117b85c2ea6cc423520f9fd873
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="workflow-designer-shell-features"></a>Funkcji powłoki projektanta przepływów pracy

Projektant przepływu pracy systemu Windows składa się z trzech głównych obszarów interfejsu użytkownika: powierzchnię projektanta, pasek stron nadrzędnych powyżej i powłoki poniżej. Na pasku stron nadrzędnych, znajduje się w górnej części ekranu, służy do wyświetlania na liście elementów nadrzędnych bieżącego działania głównego. Aby uzyskać więcej informacji, zobacz [porady: użycie nadrzędnych](../workflow-designer/how-to-use-breadcrumb-navigation.md). Powierzchni projektanta, znajduje się w środku ekranu służy do tworzenia przepływów pracy. Powłoki, znajduje się w dolnej części ekranu, zawiera szereg przyciski umożliwiające zarządzanie bieżącym widokiem.

## <a name="shell-features"></a>Funkcje powłoki
 Powłoka zawiera przyciski po prawej stronie paska można powiększyć lub pomniejszyć przepływu pracy, zawartości do przepływu pracy do rozmiaru ekranu, a Pokaż lub Ukryj mapę omówienie. Można również powiększania i poza przepływu pracy za pomocą skrótów klawiaturowych CTRL ++ i CTRL +-.

## <a name="overview-map"></a>Przeglądów
 Mapą przeglądową wyświetla małą wersję działanie całego bieżącego głównego nawigacją, w tym wszystkich jego elementów podrzędnych i wszystkie ich rozwinięte elementy podrzędne. Ma okienka ekranu, prostokąt z pomarańczowy obramowania, co powoduje część działania aktualnie wyświetlany w edytorze. Przeciąganie prostokątem mapą przeglądową Przewija projektanta przepływów pracy i zmiany widoku edytora.

> [!NOTE]
> [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] Zostaje zwirtualizowany interfejsu użytkownika. Projektanci działań są renderowane tylko wtedy, gdy jest to wymagane. Jeśli nigdy nie został wystawiony na powierzchni projektowej część przepływu pracy, część pojawia się jako białe na mapie omówienie. Przewijanie wokół mapą przeglądową całkowicie rysuje przepływ pracy.

## <a name="copying-or-saving-workflows-as-images"></a>Kopiowanie lub zapisywanie przepływów pracy jako obrazów
 Przepływy pracy można skopiować format mapy bitowej lub zapisane w formacie mapy bitowej lub wektora. Kopiowanie lub zapisywania obraz umożliwia eksportowanie widoku całego działania w bieżącym głównym stron nadrzędnych, w tym wszystkich jego elementów podrzędnych i wszystkich ich rozwinięte elementów podrzędnych do innego programu.

 Aby skopiować jako obraz, kliknij prawym przyciskiem myszy w Projektancie i wybierz **Kopiuj jako obraz**. Aby zapisać jako obraz, kliknij prawym przyciskiem myszy w Projektancie i wybierz **Zapisz jako obraz**. Przepływy pracy mogą być zapisane w formacie JPG, GIF, PNG lub XPS. Wybrano format **Zapisz jako** okno dialogowe w **Zapisz jako typ:** listy rozwijanej listy w dolnej części okna.

## <a name="fonts-and-colors"></a>Czcionki i kolory

Czcionki używane w [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] wewnątrz [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] są kontrolowane przez czcionkę środowiska. Kolory wyświetlane w [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] zmienić, jeśli używasz schemat kolorów Duży kontrast dla motywu systemu operacyjnego. Należy ponownie uruchomić [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] po wprowadzeniu zmian w ustawieniach czcionek i kolorów, aby zmiany zostały wprowadzone [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].