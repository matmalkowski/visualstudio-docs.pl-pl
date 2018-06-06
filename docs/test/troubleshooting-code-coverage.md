---
title: Pokrycie kodu — wyszukiwanie w programie Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: troubleshooting
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 1169d4e482f097ca923cc017964724e5886658d1
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34751569"
---
# <a name="troubleshoot-code-coverage"></a>Rozwiązywanie problemów z pokryciem kodu

Narzędzie analizy pokrycia kodu w programie Visual Studio zbiera dane dotyczące zestawów natywnych i zarządzanych (pliki .dll i .exe). Jednak w niektórych przypadkach w oknie Wyniki pokrycia kodu jest wyświetlany błąd typu „Wygenerowano puste wyniki: …”. Istnieje kilka przyczyn, dlaczego otrzymasz pusty wyników. W tym artykule opisano, jak rozwiązać te problemy.

## <a name="what-you-should-see"></a>Co powinno zostać wyświetlone

Jeśli wybierzesz **Analizuj pokrycie kodu** polecenia w Test menu a kompilacji i testy wykonane pomyślnie, należy wyświetlić listę wyników w oknie pokrycia kodu. Aby wyświetlić szczegółowe informacje, należy rozwinąć elementy.

![Wyniki pokrycia kodu z kolorowanie](../test/media/codecoverage1.png)

Aby uzyskać więcej informacji, zobacz [przy użyciu pokrycia kodu do określenia, jaka część kodu jest poddawana testom](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="possible-reasons-for-seeing-no-results-or-old-results"></a>Możliwe przyczyny braku wyników lub wyświetlania starych wyników

### <a name="do-you-have-the-right-edition-of-visual-studio"></a>Czy masz odpowiednią wersję programu Visual Studio?
 Potrzebujesz programu Visual Studio Enterprise.

### <a name="no-tests-were-executed"></a>Nie zostały wykonane żadne testy

Analiza&mdash;Twojego w oknie danych wyjściowych. W **Pokaż dane wyjściowe z** listy rozwijanej wybierz pozycję **testy**. Sprawdź, czy są zarejestrowane jakieś błędy lub ostrzeżenia.

Wyjaśnienie&mdash;analizy pokrycia kodu jest wykonywane, gdy testy są uruchomione. Zawiera ona tylko te zestawy, które są ładowane do pamięci podczas wykonywania testów. Jeśli żadne testy są wykonywane, nie ma nic pokrycia kodu do raportu.

Rozdzielczość&mdash;w Eksploratorze testów, wybierz **Uruchom wszystkie** można zweryfikować, że testy uruchamiane pomyślnie. Usuń wszelkie błędy przed użyciem **Analizuj pokrycie kodu**.

### <a name="youre-looking-at-a-previous-result"></a>Patrzy poprzedni wynik

Zmodyfikować i ponownie uruchomić testy, poprzedni wynik pokrycia kodu może nadal być niewidoczna, kolorowania z tym starego uruchamiania kodu w tym.

1.  Uruchom analizę pokrycia kodu.

2.  Upewnij się, czy wybrano zestaw najbardziej aktualnych wyników w oknie wyników Pokrycia kodu.

### <a name="pdb-symbol-files-are-unavailable"></a>Pliki .pdb (symbol) są niedostępne

Analiza&mdash;Otwórz folder docelowy kompilacji (zazwyczaj bin\debug) i sprawdź, czy dla każdego zestawu jest plik PDB w tym samym katalogu co plik .dll lub .exe.

Wyjaśnienie&mdash;aparat pokrycia kodu wymaga, aby każdy zestaw miało jego .pdb skojarzonych plików dostępny podczas uruchomienia testu. Jeśli plik nie .pdb dla danego zestawu nie istnieje, nie są analizowane zestawu.

Plik .pdb musi zostać wygenerowany z tej samej kompilacji co pliki .dll i .exe.

Rozdzielczość&mdash;upewnij się, że ustawienia kompilacji wygenerować plik PDB. Jeśli .pdb, pliki nie zostaną zaktualizowane, gdy projekt jest budowany, następnie otwórz właściwości projektu, zaznacz **kompilacji** wybierz pozycję **zaawansowane**i sprawdzić **informacje o debugowaniu**.

Jeśli pliki .pdb i .dll lub .exe znajdują się w różnych miejscach, należy skopiować plik .pdb do tego samego katalogu. Można również skonfigurować silnik pokrycia kodu, aby wyszukiwał pliki .pdb w innej lokalizacji. Aby uzyskać więcej informacji, zobacz [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md).

### <a name="using-an-instrumented-or-optimized-binary"></a>Korzystanie ze zinstrumentowanego lub zoptymalizowanego pliku binarnego

Analiza&mdash;stwierdzić, czy plik binarny został poddany dowolnej formy optymalizacji zaawansowanych, takich jak profilowana Optymalizacja, albo został zinstrumentowany przez profilowania narzędzia, takiego jak vsinstr.exe lub vsperfmon.exe.

Wyjaśnienie&mdash;Jeśli została już zinstrumentowane zestawu lub zoptymalizowane przez inne narzędzie do profilowania, zestaw został pominięty analizy pokrycia kodu. Nie można wykonać analizy pokrycia kodu takich zestawów.

Rozdzielczość&mdash;Wyłącz optymalizacji i użycie nowej kompilacji.

### <a name="code-is-not-managed-net-or-native-c-code"></a>Kod nie jest zarządzany (.NET) lub nie jest kodem natywnym (C++)

Analiza&mdash;upewnij się, że używasz niektóre testy na zarządzane lub kod w języku C++.

Wyjaśnienie&mdash;analizy pokrycia kodu w programie Visual Studio jest dostępna tylko dla zarządzanego i natywnego kodu (C++). Jeśli pracujesz z narzędziami innych firm, niektórych lub wszystkich kodu może wykonać na innej platformie.

Rozdzielczość&mdash;niedostępny.

### <a name="assembly-has-been-installed-by-ngen"></a>Zestaw został zainstalowany przez NGen

Analiza&mdash;Sprawdź, czy zestaw nie są ładowane z pamięci podręcznej obrazów natywnych.

Wyjaśnienie&mdash;ze względu na wydajność, nie są analizowane zestawy obrazu macierzystego. Aby uzyskać więcej informacji, zobacz [Ngen.exe (Generator obrazu natywnego)](/dotnet/framework/tools/ngen-exe-native-image-generator).

Rozdzielczość&mdash;MSIL wersji zestawu. Nie przetwarzaj go z elementem NGen.

### <a name="custom-runsettings-file-with-bad-syntax"></a>Niestandardowy plik .runsettings o złej składni

Analiza&mdash;Jeśli używasz niestandardowego *runsettings* pliku, być może zawiera błąd składniowy. Pokrycie kodu nie jest uruchamiane, a albo okna pokrycia kodu nie zostanie otwarte po zakończeniu uruchomienia testu lub pokazuje starych wyników.

Wyjaśnienie&mdash;testy jednostkowe można uruchomić przy użyciu pliku runsettings niestandardowe, aby skonfigurować opcje pokrycia kodu. Opcje te umożliwiają uwzględnianie lub wykluczanie plików. Aby uzyskać więcej informacji, zobacz [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md).

Rozdzielczość&mdash;istnieją dwa możliwe typy błędów:

-   **Błąd XML**

     Otwórz plik .runsettings w edytorze XML programu Visual Studio. Poszukaj oznak błędów.

-   **Błąd wyrażeń regularnych**

     Każdy ciąg znaków w pliku jest wyrażeniem regularnym. Przejrzyj każdy z nich w poszukiwaniu błędów, a w szczególności zwróć uwagę na:

    -   Niedopasowane nawiasy (...) lub nawiasów niezmienionym znaczeniu \\(...) \\). Jeśli chcesz dopasować nawiasy w ciągu wyszukiwania, musisz dodać przed nimi znak ucieczki. Na przykład, aby dopasować Użyj funkcji: `.*MyFunction\(double\)`

    -   Gwiazdka lub plus na początku wyrażenia. W celu dopasowania do dowolnego ciągu znaków, należy używać pojedynczego znaku kropki, następuje znak gwiazdki: `.*`

### <a name="custom-runsettings-file-with-incorrect-exclusions"></a>Niestandardowy plik .runsettings z niepoprawnymi wykluczeniami

Analiza&mdash;Jeśli używasz niestandardowego *runsettings* plików, upewnij się, że zawiera on używanego zestawu.

Wyjaśnienie&mdash;testy jednostkowe można uruchomić przy użyciu pliku runsettings niestandardowe, aby skonfigurować opcje pokrycia kodu. Opcje te umożliwiają uwzględnianie lub wykluczanie plików. Aby uzyskać więcej informacji, zobacz [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md).

Rozdzielczość&mdash;usunięcie wszystkich `Include` węzły przy użyciu pliku runsettings, a następnie usuń wszystkie `Exclude` węzłów. Jeśli to rozwiąże problem, umieść je z powrotem w etapach.

Upewnij się, że węzeł DataCollectors określa pokrycie kodu. Porównaj je z próbki w [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md).

## <a name="some-code-is-always-shown-as-not-covered"></a>Niektóre kody są zawsze wyświetlane jako niepokryte

### <a name="initialization-code-in-native-dlls-is-executed-before-instrumentation"></a>Kod inicjowania w natywnych bibliotekach DLL jest wykonywany przed instrumentacją

Analiza&mdash;w kodzie natywnym statycznie połączone, część funkcji inicjowania **DllMain** i kod, który wywołuje czasami jest wyświetlany nie zostały podane, nawet jeśli wykonano kod.

Wyjaśnienie&mdash;narzędzie pokrycie kodu działa wstawiając Instrumentacji do zestawu tuż przed uruchamiania aplikacji. W zestawie żadnych wcześniej załadowane kod inicjujący w **DllMain** wykonuje natychmiast po załadowaniu zestawu, a przed uruchomieniem aplikacji. Ten kod wydaje się nie być objęte. Zwykle dotyczy to statycznie załadowanych zestawów.

Rozdzielczość&mdash;None.

## <a name="see-also"></a>Zobacz także

- [Korzystanie z pokrycia kodu do określania, jaka część kodu jest poddawana testom](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)