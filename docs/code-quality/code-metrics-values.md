---
title: Oblicz metrykę kodu w programie Visual Studio
ms.date: 12/12/2017
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code metrics [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 97bfe1c23e2681e90853bc55987317e3f27c7a08
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="code-metrics-values"></a>Wartości metryk kodów

Zwiększenie stopnia złożoności nowoczesne aplikacje zwiększa także trudności dokonywania kod, niezawodny i łatwy w obsłudze. Metryki kodu to zestaw miar oprogramowania, które zapewniają deweloperom lepszy wgląd w kodzie, że są one tworzenie. Dzięki wykorzystaniu metryki kodu, deweloperzy zrozumieć typy i/lub metody powinny zostać ponownie obrobione lub bardziej dokładnie przetestowana. Zespoły deweloperów można identyfikować potencjalne zagrożenia, zrozumieć bieżący stan projektu i śledzić postęp podczas tworzenia oprogramowania.

Deweloperzy mogą używać programu Visual Studio do generowania kodu danych metryki pomiaru złożoności i łatwości konserwacji ich kodu zarządzanego. Można wygenerować danych metryki kodu dla całego rozwiązania lub projektu jednego.

Informacje o sposobie generowania danych metryki kodu w programie Visual Studio, zobacz [porady: generowanie metryk kodów](../code-quality/how-to-generate-code-metrics-data.md).

## <a name="software-measurements"></a>Pomiarów oprogramowania

Poniższa lista zawiera kod wyników metryk, które oblicza Visual Studio:

- **Indeks łatwości utrzymania** — oblicza wartość indeksu pomiędzy 0 a 100 reprezentującą względną łatwość utrzymania kod. Wysoka wartość oznacza lepszą utrzymania. Klasyfikacje oznaczone kolorem można szybko zidentyfikować problemy z programem w kodzie. Zielony klasyfikacji wynosi 20-100 i oznacza, że kod ma dużą łatwość utrzymania. Żółty klasyfikacji wynosi 10-19 i wskazuje, że kod jest łatwy w obsłudze średnio. Czerwony klasyfikacji jest klasyfikację od 0 do 9 i wskazuje niski łatwość utrzymania.

- **Złożoność Cyklomatyczną** -mierzy strukturalnych złożoności kodu. Jest on tworzony przez obliczenie liczba ścieżek różnego kodu w procesie programu. Program, który ma przepływu sterowania złożonego będzie wymagać większej liczby testów do osiągnięcia pokrycie kodu dobrej i będzie mniej łatwy w obsłudze.

- **Głębokość dziedziczenia** — wskazuje liczbę definicje klas, zwiększających się w katalogu głównym hierarchii klas. Lepszy hierarchii trudniejsze może być zrozumienie, gdzie są zdefiniowane pola i określonej metody lub / i ponownie zdefiniowany.

- **Klasa sprzężenia** -mierzy sprzężenia klas unikatowy poprzez parametrów, zmienne lokalne, typy zwracane, wywołania metody, wystąpień ogólne lub szablonu, klas podstawowych, implementacje interfejsu, pól zdefiniowanych dla typów zewnętrznych i decoration atrybutu. Projekt dobre decyduje, czy typy i metody powinny zawiera spójności wysoki i niski sprzężenia. Sprzężenia wysoki wskazuje projekt, który jest trudne do ponownego wykorzystania i obsługa ze względu na jego wiele zależnościami na inne typy.

- **Wiersze kodu** — Określa przybliżoną liczbę wierszy w kodzie. Wartość licznika jest oparta na kod IL i dlatego nie dokładna liczba wierszy w pliku kodu źródłowego. Bardzo wysoka liczba może wskazywać, że typ lub metoda próby zbyt dużo pracy i można podzielić. Może też wskazywać, że typ lub metoda może być trudny do zachowania.

## <a name="anonymous-methods"></a>Metody anonimowe

*Metody anonimowej* jest po prostu metodę, która nie ma nazwy. Metody anonimowe są najczęściej używane do przekazania blok kodu jako parametru delegowanego. Wyniki metryki dla metody anonimowej, która jest zadeklarowana w elemencie członkowskim, takich jak metody lub metody dostępu są skojarzone z elementem członkowskim, który deklaruje metody. Nie są one powiązane z elementem członkowskim, który wywołuje metodę.

Aby uzyskać więcej informacji dotyczących sposobu metryki kodu traktuje anonimowe metody, zobacz [metody anonimowe i analiza kodu](../code-quality/anonymous-methods-and-code-analysis.md).

## <a name="generated-code"></a>Wygenerowany kod

Niektóre narzędzia oprogramowania i kompilatory generowania kodu, który został dodany do projektu i projektanta projektu nie widzi ani nie należy zmieniać. Przede wszystkim metryki kodu ignoruje wygenerowany kod podczas obliczania wartości metryk. Dzięki temu wartości metryk w celu odzwierciedlenia co deweloper może wyświetlić i zmienić.

Kod wygenerowany dla formularzy systemu Windows nie jest ignorowany, ponieważ jest on kod, który deweloper może wyświetlić i zmienić.

## <a name="next-steps"></a>Następne kroki

- [Porady: generowanie metryk kodów](../code-quality/how-to-generate-code-metrics-data.md)
- [Okno wyników metryk kodów](../code-quality/working-with-code-metrics-data.md)