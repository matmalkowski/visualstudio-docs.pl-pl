---
title: 'Diagramy zależności: wskazówki'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 9ce90746d89dd41c1f53d7150d83afaa2e2bad46
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31954395"
---
# <a name="dependency-diagrams-guidelines"></a>Diagramy zależności: wskazówki
Opis architektury aplikacji na wysokim poziomie, tworząc *diagramy zależności* w programie Visual Studio. Upewnij się, kod pozostaje zgodne z tym projekcie weryfikując kodu przy użyciu diagramu zależności. Walidacja warstw mogą również obejmować procesu kompilacji. Zobacz [Channel 9 wideo: projektowania i walidacji architektury przy użyciu diagramów zależności](http://go.microsoft.com/fwlink/?LinkID=252073).

 Aby dowiedzieć się, które wersje programu Visual Studio obsługują tę funkcję, zobacz [obsługę wersji architektura i modelowanie narzędzia](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="what-is-a-dependency-diagram"></a>Co to jest diagram zależności?
 Jak diagramie architektury tradycyjnych diagram zależności identyfikuje główne składniki lub jednostki organizacyjne projektu i jego zależnościami. Każdy węzeł na diagramie, nazywany *warstwy*, reprezentuje grupę logiczną przestrzeni nazw, projektów lub innych artefaktów. Może wykonywać Rysowanie zależności, które powinny istnieć w projekcie. W odróżnieniu od diagram architektury tradycyjnych można sprawdzić, zgodność z zamierzonym zależności, których określono rzeczywistych zależności w kodzie źródłowym. Dokonując weryfikacji część regularne kompilacji na [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)], można zapewnić, że kod programu w dalszym ciągu odpowiednia architektura systemu za pośrednictwem przyszłe zmiany. Zobacz [diagramy zależności: odwołanie](../modeling/layer-diagrams-reference.md).

##  <a name="Update"></a> Jak projektowanie lub aktualizowanie aplikacji przy użyciu diagramów zależności
 Poniższe kroki zawierają omówienie sposobu używania diagramów zależności w ramach procesu tworzenia. Nowsze sekcje w tym temacie opisano szczegółowo o każdym kroku. Jeśli tworzysz nowy projekt, należy pominąć kroki, które odwołują się do istniejącego kodu.

> [!NOTE]
>  Te kroki są wyświetlane w kolejności przybliżonej. Prawdopodobnie warto nakłada się na zadania, Zmień kolejność ich do potrzeb własnych sytuacji i przeanalizowanie na początku każdej iteracji w projekcie.

1.  [Utwórz diagram zależności](#Create) dla całej aplikacji lub dla warstwy znajdujące się w nim.

2.  [Zdefiniuj warstwy do reprezentowania podstawowej funkcjonalności obszarów i składników](#CreateLayers) aplikacji. Nazwy tych warstw zgodnie z ich funkcji, na przykład "Prezentacji" lub "Usługi". Jeśli masz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozwiązania, każda warstwa można skojarzyć z kolekcją *artefakty*, takich jak projekty, przestrzenie nazw, plików i tak dalej.

3.  [Odnajdywanie zależności istniejących](#Generate) między warstwami.

4.  [Edycja warstw i zależności](#EditArchitecture) pokazanie zaktualizowanego projektu, które mają kod, aby odzwierciedlić.

5.  [Projektowanie nowego obszary aplikacji](#NewAreas) przez tworzenie warstwy do reprezentowania główna bloków architektury i składników i definiowanie zależności pokazanie sposobu używania innych każdej warstwy.

6.  [Edytuj układ i wygląd diagramu](#EditLayout) ułatwiające omawia współpracownikom.

7.  [Weryfikacja kodu przed diagram zależności](#Validate) aby wyróżnić konfliktów między kodem i architektura wymagane.

8.  [Zaktualizuj kod z nowej architektury](#UpdateCode). Wielokrotnie powtarzane opracowanie i zrefaktoryzuj kod do sprawdzania poprawności przedstawia żadne konflikty.

9. [Obejmują warstwy weryfikacji w procesie kompilacji](#BuildValidation) aby upewnić się, że kod nadal stosować się do projektu.

##  <a name="Create"></a> Utwórz diagram zależności
 Diagram zależności, należy utworzyć w projekcie modelowania. Można dodać nowego diagramu zależności do istniejącego projektu modelowania, Utwórz nowy projekt modelowania diagramu zależności lub skopiuj istniejący diagram zależności w ramach tego samego projektu modelowania.

> [!IMPORTANT]
>  Nie dodawać, przeciągnij lub skopiuj istniejący diagram zależności z projektem modelowania do innego projektu modelowania lub w innej lokalizacji w rozwiązaniu. Diagram zależności, który jest skopiowany w ten sposób mają tego samego odwołania co oryginalna diagram, nawet w przypadku modyfikowania diagramu. Uniemożliwi weryfikację warstwy z działaniem i może spowodować innych problemów, takich jak brakujące elementy, lub inne błędy podczas próby otwarcia na diagramie.

 Zobacz [tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md).

##  <a name="CreateLayers"></a> Zdefiniuj warstwy do reprezentowania funkcjonalności obszarów i składników
 Warstwy reprezentują logiczne grupy *artefakty*, takich jak projekty, pliki kodu przestrzeni nazw, klasy i metody. Można utworzyć warstwy z artefaktów z projektów Visual C# i Visual Basic, lub możesz dołączyć specyfikacji lub plany do warstwy, łączenie dokumentów, takich jak pliki programu Word lub prezentacji programu PowerPoint. Każda warstwa pojawia się jako prostokąt na diagramie i pokazuje liczbę artefaktów, które są z nim połączone. Warstwa może zawierać zagnieżdżone warstwy, które opisują innych zadań.

 Generalnie, warstwy nazwy zgodnie z ich funkcji, na przykład "Prezentacji" lub "Usługi". Jeśli artefakty są ściśle współzależne, umieść je w tej samej warstwie. Jeśli artefakty mogą być aktualizowane oddzielnie lub używany w aplikacjach oddzielne, umieść je w różnych warstwach. Aby poznać wzorce Tworzenie warstw, odwiedź witrynę wzorce, praktyki i rozwiązania pod [ http://go.microsoft.com/fwlink/?LinkId=145794 ](http://go.microsoft.com/fwlink/?LinkId=145794).

> [!TIP]
>  Istnieją pewne typy artefaktów, które można połączyć z warstwy, ale nie obsługują sprawdzenia poprawności względem diagram zależności. Aby sprawdzić, czy artefakt obsługuje sprawdzanie poprawności, otwórz **Explorer warstwy** do sprawdzenia **obsługuje sprawdzanie poprawności** właściwości link artefaktu. Zobacz [odnajdywanie istniejących zależności między warstwami](#Generate).

 Podczas aktualizowania doświadczenia w pracy aplikacji, można również utworzyć mapy kodu. Te diagramy ułatwia odnajdywanie wzorców i zależności podczas eksplorowania kodu. Użyj Eksploratora rozwiązań do eksplorowania obszary nazw i klasy, które często odnoszą się również z istniejącymi warstwami. Przypisz tych artefaktów kodu do warstwy, przeciągając je z Eksploratora rozwiązań do diagramów zależności. Następnie można diagramy zależności ułatwiające zaktualizuj kod i zachowania ich spójności z projektu.

 Zobacz:

-   [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)

-   [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)

-   [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)

##  <a name="Generate"></a> Odnajdywanie istniejących zależności między warstwami
 Zależność istnieje wszędzie tam, gdzie artefakt, który jest skojarzony z jedną warstwą zawiera odwołanie do artefaktu skojarzonego z inną warstwą. Na przykład klasa w jednej warstwie deklaruje zmienną, która zawiera klasę w innej warstwie. Zależności istniejących może wykrywać przy odtwarzania je.

> [!NOTE]
>  Zależności nie mogą być odtwarzane dla niektórych rodzajów artefaktów. Na przykład nie zostaną odtworzone żadne zależności z lub do warstwy, która jest połączona z plikiem tekstowym. Aby zobaczyć, które artefakty zależnościami mogących odtwarzanie, kliknij prawym przyciskiem myszy jednego lub wielu warstw, a następnie kliknij przycisk **Wyświetl łącza**. W **Explorer warstwy**, sprawdź **weryfikacji obsługuje** kolumny. Nie można w zależności, odtworzone artefaktów, dla których ta kolumna zawiera **False**.

#### <a name="to-reverse-engineer-existing-dependencies-between-layers"></a>Odtwarzanie istniejącej zależności między warstwami

-   Wybierz warstwę jednego lub wielu warstw, kliknij prawym przyciskiem myszy wybrane warstwy, a następnie kliknij **Generowanie zależności**.

 Zazwyczaj zobaczysz niektóre zależności, które nie powinny istnieć. Możesz edytować te zależności, aby dopasować je do zamierzonego projektu.

##  <a name="EditArchitecture"></a> Edycja warstw i zależności, aby pokazać projektowi
 Do opisania zmian, które mają być system lub docelowej architektury, umożliwia edytowanie diagram zależności następujące kroki. Można także rozważyć pewne zmiany refaktoryzacji zwiększające struktury kodu przed jej rozszerzeniem. Zobacz [poprawy struktury kodu](#Improving).

|**Aby**|**Wykonaj te kroki**|
|------------|-----------------------------|
|Usuwanie zależności, które nie powinny istnieć|Kliknij zależności, a następnie naciśnij klawisz **usunąć**.|
|Zmień lub ogranicz kierunek zależności|Ustaw jego **kierunek** właściwości.|
|Tworzenie nowych zależności|Użyj **zależności** i **zależności dwukierunkowego** narzędzia.<br /><br /> Aby narysować wiele zależności, kliknij dwukrotnie narzędzie. Gdy skończysz, kliknij przycisk **wskaźnika** narzędzi lub naciśnij klawisz **ESC** klucza.|
|Określanie, że artefakty skojarzone z warstwą nie mogą zależeć od określonych przestrzeni nazw|Typ przestrzeni nazw na warstwie **zabronione zależności Namespace** właściwości. Użyj średnika (**;**) do oddzielania przestrzenie nazw.|
|Określanie, że artefakty skojarzone z warstwą nie mogą należeć do określonych przestrzeni nazw|Typ przestrzeni nazw na warstwie **zabronione przestrzenie nazw** właściwości. Użyj średnika (**;**) do oddzielania przestrzenie nazw.|
|Określanie, że artefakty skojarzone z warstwą muszą należeć do jednej z określonych przestrzeni nazw|Typ przestrzeni nazw na warstwie **wymagane obszary nazw** właściwości. Użyj średnika (**;**) do oddzielania przestrzenie nazw.|

###  <a name="Improving"></a> Poprawa struktury kodu
 Refaktoryzacji zmiany są ulepszeń, które nie wpływają na zachowanie aplikacji, ale ułatwić kod Zmień i rozszerzanie w przyszłości. Dobrze strukturalny ma projekt, który ułatwia abstrakcyjnej do diagramu zależności.

 Na przykład jeśli tworzysz warstwę dla każdej przestrzeni nazw w kodzie i następnie odtwarzanie zależności, powinien istnieć minimalny zbiór jednokierunkowe zależności między warstwami. W przypadku utworzenia bardziej szczegółowego diagramu przy użyciu klasy lub metody jako warstw, w wyniku powinny również mają te same parametry.

 Jeśli nie jest to możliwe, kod będzie trudne do zmiany w całym cyklu ich życia i będzie mniej odpowiednie do weryfikacji przy użyciu diagramów zależności.

##  <a name="NewAreas"></a> Obszary nowy projekt aplikacji
 Po rozpoczęciu tworzenia nowego projektu lub nowy obszar w nowym projekcie można narysować warstwy i zależności, aby ułatwić identyfikację głównych składników, przed rozpoczęciem tworzenia kodu.

-   **Pokaż do zidentyfikowania wzorców architektury** diagramy zależności, jeśli to możliwe. Na przykład diagramu zależności, który opisuje aplikacja może zawierać warstwy prezentacji, logika domeny i magazynu danych. Diagram zależności, który obejmuje jednej funkcji w aplikacji może być warstw, takich jak Model, widok i kontroler. Aby uzyskać więcej informacji o tych wzorców, zobacz [wzorce, praktyki i rozwiązania: aplikacja — architektura](http://go.microsoft.com/fwlink/?LinkId=145794).

-   **Tworzenie artefaktu kodu, dla każdej warstwy** takie jak przestrzeń nazw, klasy lub składnika. Ułatwia do wykonania kodu, a także połączyć artefakty kodu do warstwy. Natychmiast po utworzeniu każdego artefaktu połączyć je do odpowiedniej warstwy.

-   **Nie masz połączyć większość klas i innych artefaktów warstwy** ponieważ mieści się w ramach większych artefaktów, takich jak przestrzenie nazw, które zostały już połączone warstwy.

-   **Utwórz nowy diagram dla nowej funkcji**. Zazwyczaj będzie jeden lub więcej diagramów zależności opisujące całej aplikacji. W przypadku projektowania nowych funkcji w aplikacji, Dodaj do lub nie zmieniać istniejących diagramów. Zamiast tego utworzyć własne diagramu, który odzwierciedla nowe części kodu. Warstwy w nowym diagramie może obejmować prezentacji, logika domeny i warstwy bazy danych dla nowych funkcji.

     Podczas tworzenia aplikacji, kodu zostanie zweryfikowana zarówno przed diagram ogólny i bardziej szczegółowe diagramu funkcji.

##  <a name="EditLayout"></a> Edytowanie układu prezentacji oraz omówienie
 Aby ułatwić identyfikację warstwy i zależności lub omówić je z członków zespołu, Edycja wyglądu i układu diagramu w następujący sposób:

-   Zmień rozmiary, kształtów i pozycje warstwy.

-   Zmienianie kolorów warstwy i zależności.

    -   Wybierz co najmniej jeden warstwy lub zależności, kliknij prawym przyciskiem myszy, a następnie kliknij **właściwości**. W **właściwości** okno edycji **kolor** właściwości.

##  <a name="Validate"></a> Weryfikacja kodu względem diagramu
 Po zakończeniu edycji diagramu, użytkownik może sprawdzić jego poprawność kodu ręcznie w dowolnym momencie lub automatycznie zawsze uruchomić lokalnej kompilacji lub [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)].

 Zobacz:

-   [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md)

-   [Obejmują warstwy weryfikacji w procesie kompilacji](#BuildValidation)

##  <a name="UpdateCode"></a> Zaktualizuj kod, aby był zgodny ze nowej architektury
 Zwykle błędy pojawi się sprawdzanie poprawności kodu na diagramie zależności zaktualizowane po raz pierwszy. Błędy te mogą mieć kilka przyczyn:

-   Artefakt jest przypisany do niewłaściwej warstwy. W takim przypadku przenieś artefakt.

-   Artefakt, taki jak klasa, używa innej klasy w sposób, który powoduje konflikt z architekturą. W tym przypadku zrefaktoryzuj kod, aby usunąć zależność.

 Aby rozwiązać te błędy, aktualizuj kod, dopóki nie przestaną pojawiać się błędy podczas walidacji. Zazwyczaj jest procesem iteracyjnym. Aby uzyskać więcej informacji o tych błędach, zobacz [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md).

> [!NOTE]
>  Podczas opracowywania lub zrefaktoryzuj kod może być nowe artefakty do odesłania do diagramu zależności. Jednak może nie to konieczne, na przykład, jeśli masz warstwy, które reprezentują istniejącej przestrzeni nazw, a nowy kod dodaje więcej materiału tylko do tych przestrzeni nazw.

 Podczas procesu projektowania możesz pominąć niektóre konflikty zgłoszone podczas walidacji. Na przykład możesz pominąć błędy, które są już poprawiane lub które nie są istotne w konkretnym scenariuszu. Pomiń błąd, jest dobrą praktyką jest zalogować elementu roboczego [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)]. Aby wykonać to zadanie, zobacz [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md).

##  <a name="BuildValidation"></a> Obejmują warstwy weryfikacji w procesie kompilacji
 Aby upewnić się, że przyszłe zmiany w kodzie odpowiadają na wykresach zależności, obejmują Walidacja warstw do procesu tworzenia standardowego rozwiązania. Zawsze, gdy inni członkowie zespołu Skompiluj rozwiązanie, różnice między zależności w kodzie i wykres zależności, będzie zgłaszane jako błędy kompilacji. Aby uzyskać więcej informacji o tym warstwy weryfikacji w procesie kompilacji, zobacz [Weryfikacja kodu przy użyciu diagramów zależności](../modeling/validate-code-with-layer-diagrams.md).

## <a name="see-also"></a>Zobacz też

- [Diagramy zależności: Odwołanie](../modeling/layer-diagrams-reference.md)
- [Tworzenie diagramów zależności z kodu](../modeling/create-layer-diagrams-from-your-code.md)
