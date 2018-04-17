---
title: 'Porady: dostosowywanie diagramów klasy (Projektant klas) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- class diagrams, customizing
- shapes, removing type from class diagrams
- type shapes, removing from class diagrams
- class diagrams, removing type shapes
ms.assetid: e9030aea-c77d-4cc1-b8f6-b6ca469b692d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5a2f58626008ba50f436f7836fe13ca92fcce155
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-customize-class-diagrams-class-designer"></a>Porady: dostosowywanie diagramów klasy (Projektant klas)
Można zmienić sposób wyświetlania informacji na diagramach klas. Można dostosować cały diagram lub poszczególne typy na powierzchni projektowej.  
  
Na przykład, można dostosować poziom powiększenia całego diagramu klasy, zmienić grupowanie i sortowanie poszczególnych składowych typu, ukrywać lub pokazywać relacje i przenieść pojedyncze typy lub zestawy typów w dowolne miejsce na diagramie.  
  
> [!NOTE]
>  Dostosowywanie sposobu wyświetlania kształtów na diagramie nie zmienia podstawowego kodu dla typów reprezentowanych na diagramie.  
  
Sekcje, które zawierają składowe typu, na przykład sekcja Właściwości w klasie, są nazywane przedziałami. Można ukryć lub pokazać poszczególne przedziały i elementy członkowskie typu.  
  
**W tym temacie**  
  
-   [Powiększanie i diagramu klas](how-to-customize-class-diagrams.md#ZoomInOut)  
  
-   [Dostosowywanie grupowanie i sortowanie elementy członkowskie typu](how-to-customize-class-diagrams.md#CustomizeGroupingSorting)  
  
-   [Ukryj przedziałów w typie](how-to-customize-class-diagrams.md#HideCompartments)  
  
-   [Ukryj poszczególne elementy na typ](how-to-customize-class-diagrams.md#HideMembers)  
  
-   [Pokaż ukryte przedziałów i elementów członkowskich w typie](how-to-customize-class-diagrams.md#DisplayHiddenCompartmentsAndMemberrs)  
  
-   [Ukryj relacji](how-to-customize-class-diagrams.md#HideAssociationAndInheritance)  
  
-   [Pokaż ukryte relacji](how-to-customize-class-diagrams.md#DisplayAssociationAndInheritance)  
  
-   [Usunąć kształt z diagramu klas](how-to-customize-class-diagrams.md#RemoveCodeAndShape)  
  
-   [Usuwanie kształtu typu i jego kod źródłowy](how-to-customize-class-diagrams.md#DeleteTypeShapeAndCode)  
  
##  <a name="ZoomInOut"></a> Powiększanie i diagramu klas  
  
1.  Otwórz i wybierz plik diagramu klasy w Projektancie klas.  
  
2.  Kliknij na pasku narzędzi projektanta klas **Powiększ** lub **Pomniejsz** przycisk, aby zmienić poziom powiększenia powierzchni projektanta.  
  
     lub  
  
     Określ konkretną wartość stopnia powiększenia. Można użyć **powiększenie** listy rozwijanej lub wpisz prawidłową powiększenia (prawidłowy zakres to od 10% i 400%).  
  
    > [!NOTE]
    >  Zmiana powiększenia nie wpływa na skalę wydruku diagramu klasy.  
  
##  <a name="CustomizeGroupingSorting"></a> Dostosowywanie grupowanie i sortowanie elementy członkowskie typu  
  
1.  Otwórz i wybierz plik diagramu klasy w Projektancie klas.  
  
2.  Kliknij prawym przyciskiem myszy pusty obszar na powierzchni projektu, a następnie wskaż **członków grupy**.  
  
3.  Wybierz jedną z dostępnych opcji:  
  
    1.  **Grupuj według rodzaju** oddziela elementy członkowskie typu poszczególnych na listę pogrupowanych właściwości, metody, zdarzeń i pól. Pojedyncze grupy zależą od definicji jednostki: na przykład, klasa nie wyświetli żadnej grupy zdarzeń, jeśli nie istnieją jeszcze żadne zdarzenia zdefiniowane dla tej klasy.  
  
    2.  **Grupuj według dostępu** modyfikatorów dostępu oddziela elementy członkowskie typu poszczególnych na listę pogrupowanych według elementu członkowskiego. Na przykład, publiczne i prywatne.  
  
    3.  **Sortuj alfabetycznie** Wyświetla elementy wchodzące w skład jednostki jako jedną listę porządku alfabetycznym. Lista jest sortowana w kolejności rosnącej.  
  
##  <a name="HideCompartments"></a> Ukryj przedziałów w typie  
  
1.  Otwórz i wybierz plik diagramu klasy w Projektancie klas.  
  
2.  Kliknij prawym przyciskiem myszy kategorii Członkowskich w typie, który chcesz dostosować (na przykład wybierz **metody** węzła w klasie.  
  
3.  Kliknij przycisk **Ukryj przedział**.  
  
     Wybrany przedział znika z kontenera typu.  
  
##  <a name="HideMembers"></a> Ukryj poszczególne elementy na typ  
  
1.  Otwórz i wybierz plik diagramu klasy w Projektancie klas.  
  
2.  Kliknij prawym przyciskiem myszy element członkowski w typie, który chcesz ukryć.  
  
3.  Kliknij przycisk **Ukryj**.  
  
     Wybrany element członkowski znika z kontenera typu.  
  
##  <a name="DisplayHiddenCompartmentsAndMemberrs"></a> Pokaż ukryte przedziałów i elementów członkowskich w typie  
  
1.  Otwórz i wybierz plik diagramu klasy w Projektancie klas.  
  
2.  Kliknij prawym przyciskiem myszy nazwę typu z ukrytym przedziałem.  
  
3.  Kliknij przycisk **Pokaż wszystkie elementy członkowskie**.  
  
     Wszystkie ukryte przedziały i elementy członkowskie pojawiają się w kontenerze typu.  
  
##  <a name="HideAssociationAndInheritance"></a> Ukryj relacji  
  
1.  Otwórz i wybierz plik diagramu klasy w Projektancie klas.  
  
2.  Kliknij prawym przyciskiem myszy linię skojarzenia lub dziedziczenia, którą chcesz ukryć.  
  
3.  Kliknij przycisk **Ukryj** linie asocjacji, a następnie kliknij przycisk **Ukryj linii dziedziczenia** linii dziedziczenia.  
  
4.  Kliknij przycisk **Pokaż wszystkie elementy członkowskie**.  
  
     Wszystkie ukryte przedziały i elementy członkowskie pojawiają się w kontenerze typu.  
  
##  <a name="DisplayAssociationAndInheritance"></a> Pokaż ukryte relacji  
  
1.  Otwórz i wybierz plik diagramu klasy w Projektancie klas.  
  
2.  Kliknij prawym przyciskiem myszy typ z ukrytym skojarzeniem lub dziedziczeniem.  
  
 Kliknij przycisk **Pokaż wszystkie elementy członkowskie** linie asocjacji, a następnie kliknij przycisk **Pokaż klasa podstawowa** lub **Pokaż klas pochodnych** linii dziedziczenia.  
  
##  <a name="RemoveCodeAndShape"></a> Usunąć kształt z diagramu klas  
Możesz usunąć kształt typu z diagramu klasy bez wpływu na podstawowy kod typu. Usuwanie kształtów typu z diagramu klasy dotyczy tylko tego diagramu: podstawowy kod, który określa typ, i inne diagramy, które wyświetlają typ, nie są modyfikowane.  
  
1.  Na diagramie klasy zaznacz kształt typu, który chcesz usunąć z diagramu.  
  
2.  Na **Edytuj** menu, wybierz **usunąć z diagramu**.  
  
     Kształt typu i wszystkie linie skojarzeń lub dziedziczenia połączone z kształtem nie są już wyświetlane na diagramie.  
  
##  <a name="DeleteTypeShapeAndCode"></a> Usuwanie kształtu typu i jego kod źródłowy  
  
1.  Kliknij prawym przyciskiem myszy kształt na powierzchni projektowej.  
  
2.  Wybierz **usunąć kod** z menu kontekstowego.  
  
     Kształt zostanie usunięty z diagramu, a jego podstawowy kod zostanie usunięty z projektu.  
  
## <a name="see-also"></a>Zobacz także
[Praca z diagramami klas](working-with-class-diagrams.md)   
[Porady: zmiana pomiędzy notacją członka i skojarzeniem notacji](how-to-change-between-member-notation-and-association-notation.md)   
[Porady: wyświetlanie istniejących typów](how-to-view-existing-types.md)   
[Wyświetlanie typów i relacji](viewing-types-and-relationships.md)