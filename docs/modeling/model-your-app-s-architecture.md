---
title: Model aplikacji&#39;architektura s
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UML, modeling architecture
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 2f7da241dc6090339bd5d9d9e6f731041a27fe84
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="model-your-app39s-architecture"></a>Model aplikacji&#39;architektura s
Aby pomóc w zapewnieniu, że z oprogramowania systemu lub aplikacji spełnia użytkowników musi, możesz utworzyć modeli w programie Visual Studio jako część opisie ogólną strukturę i zachowania systemu oprogramowania lub aplikacji. Przy użyciu modeli, można również opisać wzorców, które są używane w projekcie. Te modele pomagają zrozumieć istniejącej architektury, omówiono w nim zmiany i wyraźnie komunikacji zamiaru.

 Aby dowiedzieć się, które wersje programu Visual Studio obsługują tę funkcję, zobacz [obsługę wersji architektura i modelowanie narzędzia](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Celem modelu jest zmniejszenie niejednoznaczności, które występują w języku naturalnym opisy, a także aby pomóc Ciebie i Twoich współpracowników do wizualizacji projektu i omówimy alternatywnych projektów. Model powinien być używany razem z innymi dokumentów lub dyskusji. Samodzielnie model nie reprezentuje pełną specyfikację architektury.

> [!NOTE]
>  W tym temacie "system" oznacza, że oprogramowanie, które tworzysz. Może być duży zbiór wiele składników oprogramowania i sprzętu, lub pojedynczej aplikacji lub część aplikacji.

 Architektura systemu można podzielić na dwa obszary:

-   [Ogólnymi procedurami projektowania](#Structure). Opisuje główne składniki i sposób ich interakcji ze sobą w celu spełnienia poszczególnych wymagań. Jeśli system jest duży, każdego składnika może mieć własny projekt wysokiego poziomu, który pokazuje, jak składa się z mniejszych składników.

-   [Wzorce projektowe](#Patterns) i konwencje używane w projektach składników. Wzorzec w tym artykule opisano sposób postępowania w osiąganiu celu programowania. Przy użyciu tego samego wzorce w projekcie, zespół może zmniejszyć koszt wprowadzanie zmian i tworzenia nowego oprogramowania.

##  <a name="Structure"></a> Projekt wysokiego poziomu
 Ogólny projekt zawiera opis głównych składników systemu i sposób ich interakcji ze sobą w celu osiągnięcia celów projektu. Działania na poniższej liście są zaangażowane w tworzenie projektu wysokiego poziomu, ale niekoniecznie w określonej kolejności.

 Aby zaktualizować istniejący kod może zacząć głównych składników opisano w nim. Upewnij się, zrozumieć wszelkie zmiany wymagań użytkownika, a następnie dodaje lub modyfikuje interakcje między składnikami. Jeśli tworzysz nowy system Rozpocznij zrozumienie najważniejszych funkcji potrzeb użytkowników. Następnie eksplorować sekwencji interakcji dla przypadków użycia głównego i następnie skonsolidować sekwencji do projektowania składnika.

 W każdym przypadku jest przydatne w celu utworzenia innego działania równoległe i Opracuj kodu i testy na wczesnym etapie. Unikać prób przed rozpoczęciem innego, wykonaj jedną z tych aspektów. Zazwyczaj zarówno wymagania i zrozumieć najlepszy sposób, aby zaprojektować system ulegnie zmianie podczas pisania i testowania kodu. W związku z tym należy rozpocząć, opis i kodowania najważniejszych funkcji, wymagań i projektowania. Wprowadź szczegóły w późniejszym iteracji projektu.

-   [Zapoznanie się z wymaganiami](#Requirements). Punkt początkowy dowolnego projektu jest przejrzysty potrzeb użytkowników.

-   [Wzorce architektury](#BigDecisions). Opcje wprowadzone informacje podstawowe technologie i architektury elementów systemu.

-   Model danych składników i interfejsów. Diagramy klas opisujących informacje przekazywane między składnikami i przechowywane wewnątrz składników może wykonywać Rysowanie.

##  <a name="Requirements"></a> Zapoznanie się z wymaganiami
 Ogólny projekt kompletna aplikacja jest najbardziej efektywne opracowany wraz z wymagań modelu lub innych opis potrzeb użytkowników. Aby uzyskać więcej informacji o modelach wymagania, zobacz [modelu wymagania użytkownika](../modeling/model-user-requirements.md).

 W przypadku systemu, które tworzysz składnika w systemie większy, część lub wszystkie wymagania użytkownika dotyczące może zostać zawarte w interfejsów programistycznych.

 Wymagania modelu zawiera te elementy istotnych informacji:

-   Należy podać interfejsów. Udostępnionym interfejsem zawiera listę usług lub operacje, które system lub składnik podać swoim użytkownikom człowieka użytkowników lub innych składników oprogramowania.

-   Wymaganych interfejsów. Wymagany interfejs Wyświetla listę usług lub operacje, których można użyć systemu lub składnik. W niektórych przypadkach można zaprojektować tych usług w ramach własnego systemu. W innych przypadkach zwłaszcza, jeśli projektujesz składnik, który można łączyć z innymi składnikami w wielu konfiguracjach wymaganego interfejsu zostaną ustawione przez zewnętrznego zagadnienia.

-   Jakość usługi wymagania. Wydajność, zabezpieczeń, niezawodności i innych celów i ograniczenia, które muszą spełniać systemu.

 Wymagania modelu są zapisywane z punktu widzenia użytkowników w systemie, osób lub innych składników oprogramowania. Nie wiedzą niczego wewnętrzne działanie systemu. Z kolei w modelu architektury jest do opisu wewnętrzne działanie i pokazać, jak spełniają użytkowników wymaga.

 Oddzieleniu wymagania i modele architektury jest przydatne, ponieważ jego ułatwia omówiono wymagania z użytkownikami. Pomaga również Refaktoryzuj projektu i alternatywne architektury wziąć pod uwagę podczas aktualizowania wymagania bez zmian.

 Szczegółów, które należy umieścić w wymagania lub model architektury zależy od skali projektu i rozmiaru i dystrybucji zespołu. Mały zespół projektu krótki może go nie więcej niż powstawać diagramu klas rozwiązań biznesowych oraz niektóre wzorców projektowych; dużego projektu rozproszone na więcej niż jeden region potrzebny znacznie więcej szczegółów.

##  <a name="BigDecisions"></a> Wzorce architektury
 Wczesnym etapie programowania należy wybrać najważniejszych technologii i elementy, od których zależy projektu. Obszary, w których należy te opcje są następujące:

-   Podstawowa Wybór technologii, takich jak wybór między bazę danych i system plików i wybór między sieciowych aplikacji klienta sieci Web i tak dalej.

-   Opcje platform, takich jak wybór między Windows Workflow Foundation lub ADO.NET Entity Framework.

-   Opcje — metoda integracji, na przykład między usługi service bus enterprise lub kanał point-to-point.

 Te opcje są często określane przez jakości wymagań, takie jak skalowalność i elastyczność i można wykonać, zanim szczegółowe wymagania są znane. W systemie duży konfiguracji sprzętu i oprogramowania są zdecydowanie powiązanych.

 Wybrane wpływa na sposób używania i interpretować architektury modelu. Na przykład w systemie, który korzysta z bazy danych, skojarzenia na diagramie klas może reprezentować relacji lub klucze obce w bazie danych w systemie, która jest oparta na plikach XML, skojarzenia może wskazują odsyłacze korzystających z języka XPath. W rozproszonym systemie komunikatów na diagramie sekwencji może reprezentować wiadomości umieszczonego; w aplikacji niezależne reprezentują wywołania funkcji.

##  <a name="Patterns"></a> Wzorce projektowe
 Wzorzec projektowy jest konspekt sposobu projektowania określonej proporcji oprogramowania, szczególnie taki, który występuje w innej części systemu. Przez przyjęcie podejścia uniform w projekcie, można zmniejszyć koszt projektu, zapewnienia spójności interfejsu użytkownika i zmniejszenie kosztów zrozumienie i zmiana kodu.

 Niektóre wzorce projektowe ogólne, takie jak obserwatora są dobrze znanych i powszechnie stosowane. Istnieją ponadto wzorców, które mają zastosowanie tylko do projektu. Na przykład w sieci Web systemu sprzedaży, będzie kilka operacji w kodzie gdzie zmian w kolejności klienta. W celu zapewnienia był wyświetlany na każdym etapie stanu zlecenia, wszystkie czynności musi występować po konkretnego protokołu aktualizacji bazy danych.

 Część pracy architektura oprogramowania ma na celu określenie, jakie wzorce powinny być stosowane przez projekt. Jest to zazwyczaj bieżących zadań, ponieważ nowe wzorce i ulepszenia istniejących wzorców zostaną odnalezione w miarę postępów projektu. Warto zorganizować planu rozwoju wykonywania każdego z Twoich wzorców głównych projektu na wczesnym etapie.

 Większość wzorców projektowych może zostać częściowo zawarte w kodzie struktury. Część wzorca można zmniejszyć żądania deweloperom stosowanie poszczególnych klas lub składniki, takie jak warstwa dostępu do bazy danych, które zapewnia, że poprawnie obsługi bazy danych.

 Wzorzec projektowy jest opisana w dokumencie i zwykle obejmuje następujące elementy:

-   Nazwa.

-   Opis elementu kontekstu, o których ona dotyczy. Kryteria, jakie należy się upewnić, deweloperów, należy rozważyć stosowanie tego wzorca?

-   Krótki opis to rozwiąże problem.

-   Model główne elementy i ich relacji. Może to być klasy lub składników i interfejsów o skojarzenia i zależności między nimi. Elementy zazwyczaj można podzielić na dwie kategorie:

-   Konwencje nazewnictwa.

-   Opis sposobu wzorzec rozwiązuje problem.

-   Opis zmian, które deweloperzy mogą być w stanie przyjąć.

## <a name="see-also"></a>Zobacz też

- [Tworzenie wizualizacji kodu](../modeling/visualize-code.md)
- [Wymagania modelu użytkownika](../modeling/model-user-requirements.md)
- [Opracowywanie testów na podstawie modelu](../modeling/develop-tests-from-a-model.md)
- [Używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md)