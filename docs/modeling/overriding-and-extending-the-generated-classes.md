---
title: Zastępowanie i rozszerzanie wygenerowanych klas
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, providing overridable classes
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 77a33546d02738ae03e4da5180aa15e2b94f91ea
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="overriding-and-extending-the-generated-classes"></a>Zastępowanie i rozszerzanie wygenerowanych klas
Definicja DSL jest platformy, na którym można tworzyć zaawansowany zestaw narzędzi, które są oparte na języka specyficznego dla domeny. Wiele rozszerzeń i dostosowania może się przez zastąpienie i rozszerzenie klasy, które są generowane na podstawie definicji DSL. Te klasy zawierać nie tylko klasy domeny, które jawnie zdefiniowane w diagramie DSL definicji, ale także inne klasy, które definiują przybornika, Eksploratora, serializacji i tak dalej.

## <a name="extensibility-mechanisms"></a>Mechanizmy rozszerzalności
 Kilka mechanizmów podano pozwala rozszerzyć wygenerowanego kodu.

### <a name="overriding-methods-in-a-partial-class"></a>Zastępowanie metody w klasie częściowej
 Definicje klas częściowych zezwala na klasy określone w kilku miejscach. Dzięki temu można oddzielić wygenerowanego kodu z kodu napisanego przez siebie. W kodzie ręcznie zapisywane można zastąpić klasy dziedziczone przez wygenerowanego kodu.

 Na przykład, jeśli w definicji DSL zdefiniuj klasę domeny o nazwie `Book`, można zapisać kodu niestandardowego, który dodaje metody zastąpienia:

 `public partial class Book`

 `{`

 `protected override void OnDeleting()`

 `{`

 `MessageBox.Show("Deleting book " + this.Title);`

 `base.OnDeleting();`

 `} }`

> [!NOTE]
>  Aby zastąpić metody w klasie wygenerowany, zawsze wpisz swój kod w pliku, który jest oddzielony od wygenerowanych plików. Zazwyczaj plik znajduje się w folderze o nazwie CustomCode. Jeśli wprowadzisz zmiany w wygenerowanym kodzie, zostaną one utracone podczas ponownego generowania kodu z definicji DSL.

 Aby sprawdzić, jakie można zastąpić metody, wpisz **zastąpienia** w klasie, następuje spacja. Etykietka narzędzia IntelliSense informuje, jakie metody może zostać zastąpiona.

### <a name="double-derived-classes"></a>Klas pochodnych o podwójnej precyzji
 Większość metod wygenerowane klasy są dziedziczone z ustalony zbiór klas w przestrzeni nazw modelowania. Jednak w przypadku niektórych metod są definiowane w wygenerowanym kodzie. Zwykle oznacza to, że nie można zastąpić. w jednej klasie częściowej nie można zastąpić metody, które są zdefiniowane w innej definicji częściowej tej samej klasy.

 Niemniej jednak zastępować te metody ustawiając **generuje podwójne pochodnych** Flaga dla klasy domeny. To powoduje, że dwie klasy do wygenerowania, jest abstrakcyjna klasa podstawowa dla innych. Wszystkie metody i właściwości definicje znajdują się w klasie podstawowej i jest tylko Konstruktor w klasie pochodnej.

 Na przykład w przykładowym Library.dsl `CirculationBook` klasy domeny ma `Generates``Double Derived` ustawioną właściwość `true`. Wygenerowany kod dla tej klasy domeny zawiera dwie klasy:

-   `CirculationBookBase`, która jest abstrakcyjny i który zawiera wszystkie metody i właściwości.

-   `CirculationBook`, która jest pochodną `CirculationBookBase`. Jest pusta, z wyjątkiem jej konstruktorów.

 Aby zastąpić dowolnej metody, utworzeniu definicji częściowej klasy pochodnej, takich jak `CirculationBook`. Można zastąpić zarówno wygenerowane metody i odziedziczone framework modelowania.

 Metoda ta ze wszystkimi typami elementu, w tym elementy modelu, relacje kształtów, diagramy i łączniki. Możesz też przesłonić metody innych wygenerowane klasy. Niektóre generowane klas takich jak ToolboxHelper są zawsze pochodnych o podwójnej precyzji.

### <a name="custom-constructors"></a>Niestandardowe konstruktorów
 Nie można zastąpić konstruktora. Nawet w przypadku klas pochodnych o podwójnej precyzji Konstruktor musi być w klasie pochodnej.

 Jeśli chcesz podać własne konstruktora, można to zrobić przez ustawienie `Has Custom Constructor` dla klasy domeny w definicji DSL. Po kliknięciu **Przekształć wszystkie szablony**, konstruktora dla klasy nie zostaną uwzględnione w wygenerowanym kodzie. Obejmuje on wywołanie konstruktora brakuje. To powoduje, że raport o błędach podczas kompilowania rozwiązania. Kliknij dwukrotnie pozycję raportu o błędach, aby wyświetlić w wygenerowanym kodzie, który objaśnia, należy podać.

 Zapisać definicji częściowej klasy w pliku, który różni się od wygenerowanych plików i podaj konstruktora.

### <a name="flagged-extension-points"></a>Oflagowane punktów rozszerzenia
 Punkt rozszerzenia oflagowane to miejsce w definicji DSL, w którym można ustawić właściwość lub pole wyboru, aby wskazać zapewni niestandardowej metody. Konstruktory niestandardowe są jednym z przykładów. To ustawienie `Kind` obliczona lub magazynu niestandardowego i ustawienie właściwości domeny **jest niestandardowa** flagi w Konstruktorze połączenia.

 W każdym przypadku gdy Ustaw flagę i ponownie wygenerować kodu, kompilacji spowoduje błąd. Kliknij dwukrotnie błąd, aby wyświetlić komentarz wyjaśniający, co należy podać.

### <a name="rules"></a>Reguły
 Menedżer transakcji można zdefiniować reguły uruchamiane przed zakończeniem transakcji, w którym wystąpiło zdarzenie wyznaczonych, np. o zmianie właściwości. Reguły są zwykle używane do obsługi synchronism między różnych elementów w magazynie. Na przykład zasady są używane do upewnij się, że diagram Wyświetla bieżący stan modelu.

 Zasady są zdefiniowane w zasadzie na klasy, dzięki czemu nie trzeba mieć kod który rejestruje reguły dla każdego obiektu. Aby uzyskać więcej informacji, zobacz [reguły propagowanie zmian w modelu](../modeling/rules-propagate-changes-within-the-model.md).

### <a name="store-events"></a>Zdarzenia magazynu
 Magazyn modelowania udostępnia mechanizm zdarzeń, który można użyć do nasłuchiwania dla określonych typów zmian w magazynie, w tym dodawanie i usuwanie elementów zmiany wartości właściwości i tak dalej. Programy obsługi zdarzeń są nazywane po zamknięciu transakcji, w którym zostały wprowadzone zmiany. Zazwyczaj te zdarzenia są używane do aktualizacji zasobów spoza sklepu.

### <a name="net-events"></a>Zdarzenia platformy .NET
 Niektóre zdarzenia kształtów mogą subskrybować. Na przykład można nasłuchiwać kliknięć myszą kształtu. Trzeba napisać kod, który subskrybuje zdarzenia dla każdego obiektu. Ten kod może być napisane w przesłonięcie InitializeInstanceResources().

 Niektóre zdarzenia są generowane na ShapeFields, które są używane do rysowania elementów decorator kształtu. Na przykład, zobacz [porady: Przechwytywanie kliknięcie kształtu lub Dekoratora](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md).

 Zdarzenia te zwykle występuje wewnątrz transakcji. Należy utworzyć transakcji, jeśli chcesz wprowadzić zmiany w magazynie.