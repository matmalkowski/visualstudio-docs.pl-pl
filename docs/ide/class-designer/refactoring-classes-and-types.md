---
title: Zmień nazwę i przenieść klas i typów w Projektancie klas
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ClassDesigner.OverrideMembersDialog
helpviewer_keywords:
- members, overriding
- overriding members
- classes [Visual Studio], refactoring
- type members, overriding
- refactoring, types
- types [Visual Studio], refactoring
- Class Designer [Visual Studio], refactoring classes
- refactoring, classes
ms.assetid: dcf07bb4-fa3b-4224-9dec-566fd924a8ce
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ee534ca3c8b2a1cef441005586bc58601fb15ed7
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
ms.locfileid: "33957436"
---
# <a name="refactor-classes-and-types-in-class-designer"></a>Refaktoryzuj klas i typów w Projektancie klas

Gdy zrefaktoryzuj kod, można ułatwić zrozumienie, obsługa i bardziej wydajne, zmieniając jej wewnętrznej struktury i sposobu jego obiektów zaprojektowany nie jego zachowanie zewnętrznych. Korzystanie z projektanta klas i okno Szczegóły klasy do Zmniejsz ilość pracy, które musisz wykonać oraz ryzyko wprowadzenia usterki, gdy Refaktoryzuj kodu C#, VB lub C++ w projekcie programu Visual Studio.

> [!NOTE]
> Pliki projektu może być tylko do odczytu, ponieważ projekt jest pod kontrolą kodu źródłowego i nie został wyewidencjonowany, jest przywoływanego projektu lub jego pliki są oznaczone jako tylko do odczytu na dysku. Podczas pracy w projekcie w jeden z tych stanów zostaną wyświetlone różne sposoby, aby zapisać swoją pracę, w zależności od stanu projektu. Dotyczy to refaktoryzacji kodu, a także kod w inny sposób, na przykład bezpośrednio edytując ją zmienić.

## <a name="common-tasks"></a>Wspólne zadania

|Zadanie|Zawartość pomocnicza|
|----------|------------------------|
|**Refaktoryzacja klas:** refaktoryzacji operacji można użyć do podział klas na klasy częściowe lub Implementowanie abstrakcyjnych klas podstawowych.|-   [Porady: podział klas na klasy częściowe](how-to-split-a-class-into-partial-classes.md)|
|**Praca z interfejsów:** Projektant klas można zaimplementować interfejsu na diagramie klas, łącząc go z klasy, która udostępnia kod dla metody interfejsu.|-   [Porady: Implementowanie interfejsu](how-to-implement-an-interface.md)|
|**Refaktoryzacja typy, elementy członkowskie typu i parametry:** za pomocą projektanta klas, można zmienić nazwy typów, zastępują elementy członkowskie typu lub przenoszeniu ich z jednego typu. Można również utworzyć typy dopuszczające wartości zerowe.|-   [Zmiana nazwy, typy i elementy członkowskie typu](#rename-types-and-type-members)<br />-   [Przenieś elementy członkowskie typu z jednego typu na inny](#move-type-members-from-one-type-to-another)<br />-   [Porady: Tworzenie typu Zerowalnego](how-to-create-a-nullable-type.md)|

## <a name="rename-types-and-type-members"></a>Zmiana nazwy, typy i elementy członkowskie typu

W Projektancie klas, można zmienić nazwę typu lub elementu członkowskiego typu na diagramie klas, lub w **właściwości** okna. W **szczegółów klasy** okna, można zmienić nazwę członka, lecz nie jest typem. Zmiana nazwy typu lub elementu członkowskiego typu propaguje do wszystkich systemu windows i gdzie pojawił się starą nazwę lokalizacji kodu.

### <a name="rename-in-the-class-designer"></a>Zmień nazwę w Projektancie klas

1. Na diagramie klas wybierz typ lub element członkowski, a następnie wybierz nazwę.

     Nazwa elementu członkowskiego będzie można edytować.

2. Wpisz nową nazwę typu lub elementu członkowskiego typu

### <a name="rename-in-the-class-details-window"></a>Zmień nazwę okno Szczegóły klasy

1. Aby wyświetlić **szczegółów klasy** okna, kliknij prawym przyciskiem myszy typ lub element członkowski typu i wybierz **szczegółów klasy**.

     **Szczegółów klasy** zostanie wyświetlone okno.

2. W **nazwa** kolumny, Zmień nazwę elementu członkowskiego typu

3. Aby przenieść fokus od komórki, naciśnij klawisz **Enter** klucza, lub kliknij przycisk od komórki.

    > [!NOTE]
    > W **szczegółów klasy** okna, można zmienić nazwę członka, lecz nie jest typem.

### <a name="rename-in-the-properties-window"></a>Zmień nazwę w oknie właściwości

1. Na diagramie klas, lub **szczegółów klasy** okna, kliknij prawym przyciskiem myszy typ lub element członkowski, a następnie wybierz **właściwości**.

     **Właściwości** okno zostanie wyświetlony i właściwości dla typu lub elementu członkowskiego typu.

2. W **nazwa** właściwości, Zmień nazwę typu lub elementu członkowskiego typu.

     Nowa nazwa propaguje do wszystkich lokalizacji kodu w bieżącym projekcie gdzie pojawił się starą nazwę i systemu windows.

## <a name="move-type-members-from-one-type-to-another"></a>Przenieś elementy członkowskie typu z jednego typu na inny

Przy użyciu **Projektant klas**, członka typu z jednego typu można przenieść do innego typu. Oba typy muszą być widoczne w bieżącym diagramu klas.

1. Typu, który jest widoczny na powierzchni projektu, kliknij prawym przyciskiem myszy składnik, który chcesz przenieść do innego typu, a następnie wybierz **Wytnij**.

2. Kliknij prawym przyciskiem myszy typ docelowy i wybierz **Wklej**.

     Właściwość zostanie usunięta ze źródłowego typu i pojawia się w typie docelowym.

## <a name="see-also"></a>Zobacz także

- [Wyświetlanie typów i relacji](viewing-types-and-relationships.md)
- [Projektowanie klas i typów](designing-classes-and-types.md)