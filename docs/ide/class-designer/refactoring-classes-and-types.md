---
title: "Refaktoryzacja klas i typów (Projektant klas) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 3bdf6237fdbfb6e15df0d58835c260252cd8efdb
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2018
---
# <a name="refactoring-classes-and-types-class-designer"></a>Refaktoryzacja klas i typów (Projektant klas)

Gdy zrefaktoryzuj kod, można ułatwić zrozumienie, obsługa i bardziej wydajne, zmieniając jej wewnętrznej struktury i sposobu jego obiektów zaprojektowany nie jego zachowanie zewnętrznych. Korzystanie z projektanta klas i okno Szczegóły klasy do Zmniejsz ilość pracy, które musisz wykonać oraz ryzyko wprowadzenia usterki, gdy Refaktoryzuj kodu C#, VB lub C++ w projekcie programu Visual Studio.

> [!NOTE]
> Pliki projektu może być tylko do odczytu, ponieważ projekt jest pod kontrolą kodu źródłowego i nie został wyewidencjonowany, jest przywoływanego projektu lub jego pliki są oznaczone jako tylko do odczytu na dysku. Podczas pracy w projekcie w jeden z tych stanów zostaną wyświetlone różne sposoby, aby zapisać swoją pracę, w zależności od stanu projektu. Dotyczy to refaktoryzacji kodu, a także kod w inny sposób, na przykład bezpośrednio edytując ją zmienić.

## <a name="common-tasks"></a>Typowe zadania  
  
|Zadanie|Zawartość pomocnicza|  
|----------|------------------------|  
|**Refaktoryzacja klas:** refaktoryzacji operacji można użyć do podział klas na klasy częściowe lub Implementowanie abstrakcyjnych klas podstawowych.|-   [Porady: podział klas na klasy częściowe](how-to-split-a-class-into-partial-classes.md)|  
|**Praca z interfejsów:** Projektant klas można zaimplementować interfejsu na diagramie klas, łącząc go z klasy, która udostępnia kod dla metody interfejsu.|-   [Porady: Implementowanie interfejsu](how-to-implement-an-interface.md)|  
|**Refaktoryzacja typy, elementy członkowskie typu i parametry:** za pomocą projektanta klas, można zmienić nazwy typów, zastępują elementy członkowskie typu lub przenoszeniu ich z jednego typu. Można również utworzyć typy dopuszczające wartości zerowe.|-   [Zmiana nazwy, typy i elementy członkowskie typu](refactoring-classes-and-types.md#RenamingTypesAndMembers)<br />-   [Przenoszenie elementów członkowskich typu z jednego typu na inny](refactoring-classes-and-types.md#MovingTypeMembers)<br />-   [Porady: Tworzenie typu Zerowalnego](how-to-create-a-nullable-type.md)|  
  
###  <a name="RenamingTypesAndMembers"></a>Zmiana nazwy, typy i elementy członkowskie typu  
W Projektancie klas można zmienić nazwy typu lub elementu członkowskiego typu na diagramie klas, lub w oknie właściwości. W oknie szczegółów klasy można zmienić nazwę członka, lecz nie jest typem. Zmiana nazwy typu lub elementu członkowskiego typu propaguje do wszystkich systemu windows i gdzie pojawił się starą nazwę lokalizacji kodu.  
  
##### <a name="to-rename-a-name-in-the-class-designer"></a>Aby zmienić nazwę w Projektancie klas  
  
1.  Na diagramie klas wybierz typ lub element członkowski, a następnie kliknij nazwę.  
  
     Nazwa elementu członkowskiego będzie można edytować.  
  
2.  Wpisz nową nazwę typu lub elementu członkowskiego typu  
  
##### <a name="to-rename-a-name-in-the-class-details-window"></a>Aby zmienić nazwę w okno Szczegóły klasy  
  
1.  Aby wyświetlić okno Szczegóły klasy, kliknij prawym przyciskiem myszy typ lub element członkowski typu, a następnie kliknij przycisk **szczegółów klasy**.  
  
     Zostanie wyświetlone okno Szczegóły klasy.  
  
2.  W **nazwa** kolumny, Zmień nazwę elementu członkowskiego typu  
  
3.  Aby przenieść fokus od komórki, naciśnij klawisz **ENTER** klucza, lub kliknij przycisk od komórki.  
  
    > [!NOTE]
    >  W oknie szczegółów klasy można zmienić nazwę członka, lecz nie jest typem.  
  
##### <a name="to-rename-a-name-in-the-properties-window"></a>Aby zmienić nazwę w oknie właściwości  
  
1.  Na diagramie klas lub okno Szczegóły klasy, kliknij prawym przyciskiem myszy typ lub element członkowski, a następnie kliknij przycisk **właściwości**.  
  
     Okno właściwości pojawia się i wyświetla właściwości dla typu lub elementu członkowskiego typu.  
  
2.  W **nazwa** właściwości, Zmień nazwę typu lub elementu członkowskiego typu.  
  
     Nowa nazwa propaguje do wszystkich lokalizacji kodu w bieżącym projekcie gdzie pojawił się starą nazwę i systemu windows.  
  
###  <a name="MovingTypeMembers"></a>Przenoszenie elementów członkowskich typu z jednego typu na inny  
Przy użyciu **Projektant klas**, można przenieść członka typu z jednego typu do innego typu, jeśli są widoczne w bieżącym diagramu klas.  
  
##### <a name="to-move-a-type-member-from-one-type-to-another"></a>Aby przenieść jeden typ członka typu  
  
1.  Typu, który jest widoczny na powierzchni projektu, kliknij prawym przyciskiem myszy składnik, który chcesz przenieść do innego typu, a następnie kliknij przycisk **Wytnij**.  
  
2.  Kliknij prawym przyciskiem myszy typ docelowy, a następnie kliknij przycisk **Wklej**.  
  
     Właściwość zostanie usunięta ze źródłowego typu i pojawia się w typie docelowym.  
  
## <a name="see-also"></a>Zobacz także
[Wyświetlanie typów i relacji](viewing-types-and-relationships.md)  
[Projektowanie klas i typów](designing-classes-and-types.md)