---
title: Wymagania modelu użytkownika
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- requirements
- stories
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: a8f79e80b5b4e4e14772548ad92e8886150749b7
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34749060"
---
# <a name="model-user-requirements"></a>Wymagania modelu użytkownika

Visual Studio ułatwia zrozumienie, omówiono w nim i komunikować się potrzeb użytkowników za pomocą rysowania diagramy o ich działaniach i części systemu odgrywa w pomagając im ich celach. Wymagania modelu jest zestaw tych diagramów, z których każdy koncentruje się na różnych aspektów potrzeb użytkowników. Aby demonstracyjne wideo, zobacz: [modelowanie biznesowe domeny](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-3-Modeling-the-Business-Domain/).

 Aby sprawdzić, które wersje programu Visual Studio obsługi każdego typu modelu, zobacz [obsługę wersji architektura i modelowanie narzędzia](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Wymagania modelu pomoże Ci:

-   Skoncentruj się na zachowanie zewnętrznego systemu, niezależnie od jej wewnętrzny projekt.

-   Opis użytkowników i zainteresowanych musi ze znacznie mniej niejednoznaczności, niż jest to możliwe w języku naturalnym.

-   Zdefiniuj spójne słownik terminów, które mogą być używane przez użytkowników, deweloperów i testerów.

-   Zmniejsz luki i niespójności w wymaganiach.

-   Zmniejsz ilość pracy potrzebnych do reagowania na zmiany wymagań.

-   Planowanie kolejności opracowanych funkcji.

-   Użyj modeli jako podstawa dla testów systemowych, co clear relację między testy i wymagania. Po zmianie wymagań, ta relacja pomaga poprawnie zaktualizować testy. Dzięki temu się, że system spełnia nowe wymagania.

 W przypadku umożliwia dyskusji fokus użytkowników lub ich i ponownie go na początku każdej iteracji, modelu wymagania zapewnia największe korzyści. Nie masz oczekiwania na zakończenie jego szczegółowo pisania kodu. Częściowo działającą aplikację, nawet jeśli znacznie uproszczony, zwykle stanowi podstawę najbardziej zachęca dyskusji wymagania użytkownikom. Model jest efektywny sposób podsumowywania wyniki tych dyskusji. Aby uzyskać więcej informacji, zobacz [używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md).

> [!NOTE]
> W tych tematach "system" oznacza systemu lub aplikacji, które tworzysz. Może być duży zbiór wiele składników sprzętu i oprogramowania; lub pojedynczej aplikacji; lub składnik oprogramowania w systemie większy. W każdym przypadku modelu wymagania opisano zachowanie nie jest widoczny spoza systemu, czy za pośrednictwem interfejsu użytkownika lub interfejsu API.

## <a name="common-tasks"></a>Wspólne zadania

Można utworzyć kilka widoków różne wymagania dotyczące użytkowników.  Każdy widok zawiera określonego typu informacji.  Podczas tworzenia tych widoków, najlepiej przenoszenie często z jednego do drugiego. Można uruchomić z dowolnego widoku.

|Diagramu lub dokumentu|Znaczenie w modelu wymagania|Sekcja|
|-------------------------|-----------------------------------------------|-------------|
|Diagram koncepcyjny — klasa|Słownik typów, które służą do opisywania wymagania; typy widoczne w interfejsie systemu.||
|Dodatkowe dokumenty lub elementy pracy|Kryteria wydajności, zabezpieczeń, użytecznością i niezawodności.|[Opisujące jakości wymagania dotyczące usługi](#QoSRequirements)|
|Dodatkowe dokumenty lub elementy pracy|Ograniczenia i reguły nie odnoszą się do określonego przypadek użycia|[Wyświetlanie reguły biznesowe](#BusinessRules)|

 Zwróć uwagę, że większość typów diagram mogą być używane do innych celów. Omówienie typów diagramu, zobacz [tworzenia modeli dla aplikacji](../modeling/create-models-for-your-app.md).

##  <a name="BusinessRules"></a> Wyświetlanie reguły biznesowe

Reguła biznesowa jest wymaganie, który nie jest skojarzony z konkretnego przypadku użycia i powinien być uwzględniony w całym systemie.

 Wiele reguły biznesowe są ograniczenia na relacje między koncepcyjnej klasy. Można napisać te *statycznych ** reguły biznesowe* jako komentarze skojarzone z odpowiednich klas na diagram koncepcyjny klasy. Na przykład:

 ![Reguła w komentarzu dołączonym do klasy Order.](../modeling/media/uml_reqmcd2.png)

 *Reguły biznesowe dynamiczne* Ogranicz dozwolone sekwencja zdarzeń. Na przykład użyć diagramu sekwencji lub działania, aby pokazać, że użytkownik musi zalogować się przed wykonaniem innych operacji w tym systemie.

 Jednak wiele reguł dynamicznej można efektywniej i objęty zgłaszane przez zamianę statyczne reguły. Na przykład można dodać atrybut logiczny rejestrowane w klasie w modelu koncepcyjnym klasy. Czy dodatek rejestrowane jako warunku końcowego dziennika w przypadku użycia, a następnie dodaj go jako warunek wstępny większości innych przypadków użycia. To rozwiązanie umożliwia Unikaj definiowania wszystkie możliwe kombinacje sekwencja zdarzeń. Jest również bardziej elastyczne, gdy konieczne jest dodanie nowych przypadków użycia w modelu.

 Zwróć uwagę, czy wybór w tym miejscu jest o jak zdefiniować wymagania i jest niezależna od sposobu implementacji wymagania w kodzie programu.

 Więcej informacji można znaleźć w następujących tematach:

|Aby dowiedzieć się więcej o|Odczyt|
|--------------------|----------|
|Jak wdrażać kod, który działa zgodnie z regułami biznesowymi|[Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)|

##  <a name="QoSRequirements"></a> Opisujące jakości wymagania dotyczące usługi

Istnieje kilka kategorii wymagania jakości usługi. Obejmują one następujące czynności:

-   Wydajność

-   Zabezpieczenia

-   Użyteczność

-   Niezawodność

-   Niezawodność

Niektóre z tych wymagań można uwzględnić w opisach przypadków użycia określonego. Inne wymagania nie są specyficzne dla przypadki użycia i najbardziej efektywne są zapisywane w osobnym dokumencie. Możesz, jest przydatne do przestrzegania słownictwa zdefiniowane za pomocą modelu wymagania. W poniższym przykładzie należy zauważyć, że głównym słowa używane wymaganie są tytuły uczestników, przypadków użycia i klasy w powyższej ilustracji:

Jeśli restauracji usuwa element Menu, gdy klient jest porządkowanie zawierają najważniejsze nowości, dowolny element kolejność, która odwołuje się do tego elementu Menu będzie wyświetlany w czerwony.

Zobacz [modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md) więcej informacji na temat tworzenia kodu zgodną jakości wymagania dotyczące usługi.

## <a name="see-also"></a>Zobacz także

- [Używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md)
- [Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)
