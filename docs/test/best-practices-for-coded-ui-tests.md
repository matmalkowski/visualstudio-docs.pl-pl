---
title: Najlepsze praktyki dotyczące kodowanych testów interfejsu użytkownika w programie Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, best practices
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2a5da37b8b86f7529ffb4a870bc74787487ec5c0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31967031"
---
# <a name="best-practices-for-coded-ui-tests"></a>Najlepsze praktyki dotyczące kodowanych testów interfejsu użytkownika

W tym temacie opisano niektóre zalecenia dotyczące opracowywania kodowane testy interfejsu użytkownika.

## <a name="best-practices"></a>Najlepsze praktyki

Poniższe wskazówki umożliwiają utworzenie elastyczne kodowanego testu interfejsu użytkownika.

-   Użyj **konstruktora kodowanego testu interfejsu użytkownika** zawsze, gdy jest to możliwe.

-   Nie należy modyfikować `UIMap.designer.cs` pliku bezpośrednio. Jeśli zmodyfikujesz plik zmiany w pliku zostaną zastąpione.

-   Tworzenie testu za pomocą sekwencji zarejestrowane metody. Aby uzyskać więcej informacji o sposobie rejestrowania metody, zobacz [tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md).

-   Każda metoda zarejestrowane powinna działać na jednej stronie, formularzach i oknach dialogowych. Utworzenie nowej metody testu dla każdej nowej strony, formularzach i oknach dialogowych.

-   Podczas tworzenia metody należy użyć nazwy metody znaczący zamiast domyślnej nazwy. Nazwę opisową pomaga w identyfikacji przeznaczenia metody.

-   Jeśli to możliwe, należy ograniczyć każdej metody zarejestrowane do mniej niż 10 akcji. Takie podejście moduły ułatwia zastąpić metodę, w przypadku zmiany interfejsu użytkownika.

-   Tworzenie przy użyciu każdego potwierdzenia **konstruktora kodowanego testu interfejsu użytkownika**, która automatycznie dodaje metody potwierdzenia do `UIMap.Designer.cs` pliku.

-   Zmiany interfejsu użytkownika (UI), ponowne nagrać metody testowe lub metody potwierdzenia, czy ponowne nagrać poszczególnych sekcjach istniejące metody testowej.

-   Utwórz oddzielne <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> pliku dla każdego modułu w testowanej aplikacji. Aby uzyskać więcej informacji, zobacz [testowanie dużej aplikacji przy użyciu wielu map UI](../test/testing-a-large-application-with-multiple-ui-maps.md).

-   W testowanej aplikacji, użyj łatwy do rozpoznania nazwy podczas tworzenia formantów interfejsu użytkownika. Przy użyciu łatwy do rozpoznania nazwy zapewnia większą jasności i użyteczność do nazwy wygenerowanej automatycznie formantów.

-   Jeśli tworzysz potwierdzenia przez kodowanie przy użyciu interfejsu API, tworzenie metody, dla każdego potwierdzenia w części <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> klasy, która znajduje się w `UIMap.cs` pliku. Aby wykonać to potwierdzenie, tę metodę należy wywoływać z Twojej metody testowej.

-   Jeśli są bezpośrednio kodowania, przy użyciu interfejsu API, użyj właściwości i metod w klasach wygenerowanych w `UIMap.Designer.cs` pliku w kodzie, jak można wykonywać następujące czynności. Te klasy spowoduje swoją pracę, łatwiejsze i bardziej niezawodne i mogą pomóc w bardziej wydajnej pracy.

Kodowane testy interfejsu użytkownika automatycznie dostosowania do dużej liczby zmian w interfejsie użytkownika. Jeśli na przykład element interfejsu użytkownika zmieniła położenie i kolor, w większości przypadków kodowanego testu interfejsu użytkownika będą nadal znaleźć poprawny element.

Podczas uruchomienia testu kontrolek interfejsu użytkownika znajduje się w ramach testowania przy użyciu zestawu właściwości wyszukiwania. Właściwości wyszukiwania są stosowane do każdej klasy formantu w definicjach utworzone przez **konstruktora kodowanego testu interfejsu użytkownika** w `UIMap.Designer.cs` pliku. Właściwości wyszukiwania zawiera pary nazwa wartość nazw właściwości i wartości właściwości, które mogą służyć do identyfikowania formantu, takich jak <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.FriendlyName%2A>, <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.Name%2A>, i <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.ControlType%2A> właściwości formantu. Jeśli właściwości wyszukiwania nie uległy zmianie, kodowanego testu interfejsu użytkownika pomyślnie odnaleźć formantu w interfejsie użytkownika. Zmiana właściwości wyszukiwania kodowane testy interfejsu użytkownika ma algorytm dopasowania inteligentne, który stosuje Algorytm heurystyczny można znaleźć kontrolki i systemu windows w interfejsie użytkownika. Po zmianie interfejsu użytkownika, można zmodyfikować właściwości wyszukiwania poprzednio zdefiniowane elementy, aby upewnić się, że zostały znalezione.

## <a name="if-your-user-interface-changes"></a>W przypadku zmiany interfejsu użytkownika

Interfejsy użytkownika często zmieniają się podczas tworzenia. Poniżej przedstawiono kilka sposobów w celu ograniczenia wpływu tych zmian:

-   Znajdź zarejestrowane metodę, która odwołuje się do tego formantu, a następnie użyć **konstruktora kodowanego testu interfejsu użytkownika** do ponownego rejestrowania akcji dla tej metody. Można użyć tej samej nazwie w metodzie zastąpić istniejące działania.

-   Jeśli w kontrolce potwierdzenia, że nie jest już prawidłowy:

    -   Usuń metodę, która zawiera potwierdzenia.

    -   Usuń wywołanie tej metody z metody testowej.

    -   Dodaj potwierdzenie nowego przeciągając przycisk krzyżyk na formantu interfejsu użytkownika, otwórz mapy interfejsu użytkownika i Dodaj nowe potwierdzenia.

Aby uzyskać więcej informacji o sposobie rejestrowania kodowanych testów interfejsu użytkownika, zobacz [Użyj interfejsu użytkownika do testów Your kodu automatyzacji](../test/use-ui-automation-to-test-your-code.md).

## <a name="if-a-background-process-needs-to-complete-before-the-test-can-continue"></a>Jeśli proces w tle musi móc testu kontynuować

Może być konieczne poczekaj na zakończenie procesu, zanim będzie można kontynuować z następnej akcji interfejsu użytkownika. Można użyć w tym celu <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyLevel%2A> oczekiwania na uruchomienie testu będzie nadal występował, jak w poniższym przykładzie:

```csharp
// Set the playback to wait for all threads to finish
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.AllThreads;

// Press the submit button
this.UIMap.ClickSubmit();

// Reset the playback to wait only for the UI thread to finish
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.UIThreadOnly;
```

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>
- <xref:Microsoft.VisualStudio.TestTools.UITesting>
- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
- [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md)
- [Testowanie dużej aplikacji przy użyciu wielu map UI](../test/testing-a-large-application-with-multiple-ui-maps.md)
- [Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i rejestrowania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)