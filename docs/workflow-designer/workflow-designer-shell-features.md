---
title: Funkcje powłoki Projektanta przepływu pracy
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- WFDShellFeatures.UI
ms.assetid: 14bfe312-9592-408e-92ce-e98585ad16e7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5d881a6c6e14983fd8537d8e78066ef9479b9633
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757212"
---
# <a name="workflow-designer-shell-features"></a>Funkcje powłoki Projektanta przepływu pracy

Projektant przepływów pracy składa się z trzech głównych obszarów interfejsu użytkownika: powierzchnię projektanta, pasek stron nadrzędnych powyżej i powłoki poniżej. Na pasku stron nadrzędnych, znajduje się w górnej części ekranu, służy do wyświetlania na liście elementów nadrzędnych bieżącego działania głównego. Aby uzyskać więcej informacji, zobacz [porady: użycie nadrzędnych](../workflow-designer/how-to-use-breadcrumb-navigation.md). Powierzchni projektanta, znajduje się w środku ekranu służy do tworzenia przepływów pracy. Powłoki, znajduje się w dolnej części ekranu, zawiera szereg przyciski umożliwiające zarządzanie bieżącym widokiem.

## <a name="shell-features"></a>Funkcje powłoki
 Powłoka zawiera przyciski po prawej stronie paska można powiększyć lub pomniejszyć przepływu pracy, zawartości do przepływu pracy do rozmiaru ekranu, a Pokaż lub Ukryj mapę omówienie. Można również powiększania i poza przepływu pracy za pomocą skrótów klawiaturowych CTRL ++ i CTRL +-.

## <a name="overview-map"></a>Przeglądów
 Mapą przeglądową wyświetla małą wersję działanie całego bieżącego głównego nawigacją, w tym wszystkich jego elementów podrzędnych i wszystkie ich rozwinięte elementy podrzędne. Ma okienka ekranu, prostokąt z pomarańczowy obramowania, co powoduje część działania aktualnie wyświetlany w edytorze. Przeciąganie prostokątem mapą przeglądową Przewija projektanta przepływów pracy i zmiany widoku edytora.

> [!NOTE]
> Interfejs użytkownika projektanta przepływów pracy jest zwirtualizowanych. Projektanci działań są renderowane tylko wtedy, gdy jest to wymagane. Jeśli nigdy nie został wystawiony na powierzchni projektowej część przepływu pracy, część pojawia się jako białe na mapie omówienie. Przewijanie wokół mapą przeglądową całkowicie rysuje przepływ pracy.

## <a name="copying-or-saving-workflows-as-images"></a>Kopiowanie lub zapisywanie przepływów pracy jako obrazów
 Przepływy pracy można skopiować format mapy bitowej lub zapisane w formacie mapy bitowej lub wektora. Kopiowanie lub zapisywania obraz umożliwia eksportowanie widoku całego działania w bieżącym głównym stron nadrzędnych, w tym wszystkich jego elementów podrzędnych i wszystkich ich rozwinięte elementów podrzędnych do innego programu.

 Aby skopiować jako obraz, kliknij prawym przyciskiem myszy w Projektancie i wybierz **Kopiuj jako obraz**. Aby zapisać jako obraz, kliknij prawym przyciskiem myszy w Projektancie i wybierz **Zapisz jako obraz**. Przepływy pracy mogą być zapisane w formacie JPG, GIF, PNG lub XPS. Wybrano format **Zapisz jako** okno dialogowe w **Zapisz jako typ:** listy rozwijanej listy w dolnej części okna.

## <a name="fonts-and-colors"></a>Czcionki i kolory

Czcionki używane w Projektancie przepływów pracy w programie Visual Studio są kontrolowane przez czcionkę środowiska. Kolory wyświetlane w Projektancie przepływów pracy zmienić, jeśli używasz schemat kolorów Duży kontrast dla motywu systemu operacyjnego. Po wprowadzeniu zmian w ustawieniach czcionek i kolorów, aby zmiany zostały wprowadzone w Projektancie przepływów pracy, należy ponownie uruchomić program Visual Studio.