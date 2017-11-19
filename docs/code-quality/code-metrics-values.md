---
title: "Wartości metryk kodu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code metrics
- code analysis
- measure code quality
ms.assetid: bc38831e-2083-4ea4-8527-ee41499a342f
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 234ec06d47afee3cbde7c2333742fe43ab599219
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="code-metrics-values"></a>Wartości metryk kodów
Metryki kodu to zestaw miar oprogramowania, które zapewniają deweloperom lepszy wgląd w kodzie, że są one tworzenie. Dzięki wykorzystaniu metryki kodu, deweloperzy zrozumieć typy i/lub metody powinny zostać ponownie obrobione lub bardziej dokładnie przetestowana. Zespoły deweloperów można identyfikować potencjalne zagrożenia, zrozumieć bieżący stan projektu i śledzić postęp podczas tworzenia oprogramowania.  
  
## <a name="software-measurements"></a>Pomiarów oprogramowania  
 Na poniższej liście przedstawiono wyniki metryk kodów [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oblicza:  
  
-   **Indeks łatwości utrzymania** — oblicza wartość indeksu pomiędzy 0 a 100 reprezentującą względną łatwość utrzymania kod. Wysoka wartość oznacza lepszą utrzymania. Klasyfikacje oznaczone kolorem można szybko zidentyfikować problemy z programem w kodzie. Zielony klasyfikacji wynosi 20-100 i oznacza, że kod ma dużą łatwość utrzymania. Żółty klasyfikacji wynosi 10-19 i wskazuje, że kod jest łatwy w obsłudze średnio. Czerwony klasyfikacji jest klasyfikację od 0 do 9 i wskazuje niski łatwość utrzymania.  
  
-   **Złożoność Cyklomatyczną** -mierzy strukturalnych złożoności kodu. Jest on tworzony przez obliczenie liczba ścieżek różnego kodu w procesie programu. Program, który ma przepływu sterowania złożonego będzie wymagać większej liczby testów do osiągnięcia pokrycie kodu dobrej i będzie mniej łatwy w obsłudze.  
  
    > [!NOTE]
    >  W niektórych przypadkach obliczenia złożoność cyklomatyczną metody w [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] różni się od wcześniejszych wersji. Aby uzyskać więcej informacji, zobacz "Zmiany w Visual Studio 2010 kodu złożoności sekcji obliczenia" z [Rozwiązywanie problemów z metryki kodu](../code-quality/troubleshooting-code-metrics-issues.md).  
  
-   **Głębokość dziedziczenia** — wskazuje liczbę definicje klas, zwiększających się w katalogu głównym hierarchii klas. Lepszy hierarchii trudniejsze może być zrozumienie, gdzie są zdefiniowane pola i określonej metody lub / i ponownie zdefiniowany.  
  
-   **Klasa sprzężenia** -mierzy sprzężenia klas unikatowy poprzez parametrów, zmienne lokalne, typy zwracane, wywołania metody, wystąpień ogólne lub szablonu, klas podstawowych, implementacje interfejsu, pól zdefiniowanych dla typów zewnętrznych i decoration atrybutu. Projekt dobre decyduje, czy typy i metody powinny zawiera spójności wysoki i niski sprzężenia. Sprzężenia wysoki wskazuje projekt, który jest trudne do ponownego wykorzystania i obsługa ze względu na jego wiele zależnościami na inne typy.  
  
-   **Wiersze kodu** — Określa przybliżoną liczbę wierszy w kodzie. Wartość licznika jest oparta na kod IL i dlatego nie dokładna liczba wierszy w pliku kodu źródłowego. Bardzo wysoka liczba może wskazywać, że typ lub metoda próby zbyt dużo pracy i można podzielić. Może też wskazywać, że typ lub metoda może być trudny do zachowania.  
  
## <a name="anonymous-methods"></a>Metody anonimowe  
 *Metody anonimowej* jest po prostu metodę, która nie ma nazwy. Metody anonimowe są najczęściej używane do przekazania blok kodu jako parametru delegowanego. Wyniki metryki dla metody anonimowej, która jest zadeklarowana w elemencie członkowskim, takich jak metody lub metody dostępu są skojarzone z elementem członkowskim, który deklaruje metody. Nie są one powiązane z elementem członkowskim, który wywołuje metodę.  
  
 Aby uzyskać więcej informacji dotyczących sposobu metryki kodu traktuje anonimowe metody, zobacz [metody anonimowe i analiza kodu](../code-quality/anonymous-methods-and-code-analysis.md).  
  
## <a name="generated-code"></a>Wygenerowany kod  
 Niektóre narzędzia oprogramowania i kompilatory generowania kodu, który został dodany do projektu i projektanta projektu nie widzi ani nie należy zmieniać. Przede wszystkim metryki kodu ignoruje wygenerowany kod podczas obliczania wartości metryk. Dzięki temu wartości metryk w celu odzwierciedlenia co deweloper może wyświetlić i zmienić.  
  
 Kod wygenerowany dla formularzy systemu Windows nie jest ignorowany, ponieważ jest on kod, który deweloper może wyświetlić i zmienić.  
  
## <a name="see-also"></a>Zobacz też  
 [Mierzenie złożoności i łatwości konserwacji zarządzanego kodu](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)