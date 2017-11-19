---
title: "Pokrycie kodu — wyszukiwanie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26de91b8-45e3-4976-a20e-a3bd1942ddcb
caps.latest.revision: "11"
ms.author: douge
manager: douge
ms.openlocfilehash: c3e5410769ba10a905c8116677ae5d03d0df656e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="troubleshooting-code-coverage"></a>Pokrycie kodu — wyszukiwanie błędów
Narzędzie analizy pokrycia kodu w programie Visual Studio zbiera dane dotyczące zestawów natywnych i zarządzanych (pliki .dll i .exe). Jednak w niektórych przypadkach w oknie Wyniki pokrycia kodu jest wyświetlany błąd typu „Wygenerowano puste wyniki: …”. Może się tak zdarzyć z kilku przyczyn. Ten temat ma pomóc w rozwiązaniu tych problemów.  
  
## <a name="what-you-should-see"></a>Co powinno zostać wyświetlone  
 Jeśli wybierzesz **Analizuj pokrycie kodu** polecenia w Test menu a kompilacji i testy wykonane pomyślnie, należy wyświetlić listę wyników w oknie pokrycia kodu. Aby wyświetlić szczegółowe informacje, należy rozwinąć elementy.  
  
 ![Efektywne kolorowanie pokrycia kodu](../test/media/codecoverage1.png "CodeCoverage1")  
  
 Aby uzyskać więcej informacji, zobacz [przy użyciu pokrycia kodu do określenia, jaka część kodu jest poddawana testom](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).  
  
## <a name="possible-reasons-for-seeing-no-results-or-old-results"></a>Możliwe przyczyny braku wyników lub wyświetlania starych wyników  
  
### <a name="do-you-have-the-right-edition-of-visual-studio"></a>Czy masz odpowiednią wersję programu Visual Studio?  
 Potrzebujesz programu Visual Studio Enterprise.  
  
### <a name="no-tests-were-executed"></a>Nie zostały wykonane żadne testy  
 Analiza  
 Sprawdź w oknie danych wyjściowych. W **Pokaż dane wyjściowe z** listy rozwijanej wybierz pozycję **testy**. Sprawdź, czy są zarejestrowane jakieś błędy lub ostrzeżenia.  
  
 Wyjaśnienie  
 Analiza pokrycia kodu odbywa się podczas wykonywania testów. Zawiera ona tylko te zestawy, które są ładowane do pamięci podczas wykonywania testów. Jeśli nie są wykonywane żadne testy, narzędzie pokrycia kodu nie ma nic do zgłoszenia.  
  
 Rozwiązanie  
 W Eksploratorze testów, wybierz **Uruchom wszystkie** można zweryfikować, że testy uruchamiane pomyślnie. Usuń wszelkie błędy przed użyciem **Analizuj pokrycie kodu**.  
  
### <a name="youre-looking-at-a-previous-result"></a>Patrzy poprzedni wynik  
 Podczas modyfikowania i ponownego uruchamiania testów poprzedni wynik pokrycia kodu może być nadal widoczny, włącznie z kolorowaniem kodu z tego starego uruchamiania.  
  
1.  Uruchom analizę pokrycia kodu.  
  
2.  Upewnij się, czy wybrano zestaw najbardziej aktualnych wyników w oknie wyników Pokrycia kodu.  
  
### <a name="pdb-symbol-files-are-unavailable"></a>Pliki .pdb (symbol) są niedostępne  
 Analiza  
 Otwórz docelowy folder kompilacji (zazwyczaj bin\debug) i sprawdź, czy dla każdego zestawu istnieje plik .pdb w tym samym katalogu, co plik .dll lub .exe.  
  
 Wyjaśnienie  
 Silnik pokrycia kodu wymaga, aby każdy zestaw miał swój skojarzony plik .pdb dostępny podczas przebiegu testowego. Jeśli określony zestaw nie ma pliku .pdb, nie zostanie on przeanalizowany.  
  
 Plik .pdb musi zostać wygenerowany z tej samej kompilacji co pliki .dll i .exe.  
  
 Rozwiązanie  
 Upewnij się, że ustawienia kompilacji generują plik .pdb. Jeśli .pdb, pliki nie zostaną zaktualizowane, gdy projekt jest budowany, następnie otwórz właściwości projektu, zaznacz **kompilacji** wybierz pozycję **zaawansowane** i sprawdzić **informacje o debugowaniu**.  
  
 Jeśli pliki .pdb i .dll lub .exe znajdują się w różnych miejscach, należy skopiować plik .pdb do tego samego katalogu. Można również skonfigurować silnik pokrycia kodu, aby wyszukiwał pliki .pdb w innej lokalizacji. Aby uzyskać więcej informacji, zobacz [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md).  
  
### <a name="using-an-instrumented-or-optimized-binary"></a>Korzystanie ze zinstrumentowanego lub zoptymalizowanego pliku binarnego  
 Analiza  
 Należy określić, czy plik binarny przeszedł przez dowolną formę procesu zaawansowanej optymalizacji, takiego jak Optymalizacja sterowana profilem, lub czy został instrumentowany przez narzędzia profilowania, takie jak vsinstr.exe lub vsperfmon.exe.  
  
 Wyjaśnienie  
 Jeśli zestaw został już zinstrumentowany lub zoptymalizowany przez inne narzędzie profilowania, zestaw jest pominięty z analizy pokrycia kodu.  
  
 Nie można wykonać analizy pokrycia kodu na takich zestawach.  
  
 Rozwiązanie  
 Wyłącz optymalizację i użyj nowej kompilacji.  
  
### <a name="code-is-not-managed-net-or-native-c-code"></a>Kod nie jest zarządzany (.NET) lub nie jest kodem natywnym (C++)  
 Analiza  
 Sprawdź, czy niektóre testy są uruchomione na kodzie zarządzanym lub kodzie C++.  
  
 Wyjaśnienie  
 Analiza pokrycia kodu w programie Visual Studio jest dostępna tylko dla zarządzanego i natywnego kodu (C++). Jeżeli pracujesz na narzędziach innych firm, część kodu lub cały kod może być wykonywany na innej platformie.  
  
 Rozwiązanie  
 Brak dostępnych.  
  
### <a name="assembly-has-been-installed-by-ngen"></a>Zestaw został zainstalowany przez NGen  
 Analiza  
 Upewnij się, że zestaw nie jest ładowany z pamięci podręcznej obrazu natywnego.  
  
 Wyjaśnienie  
 Ze względu na wydajność zestawy obrazu natywnego nie są analizowane. Aby uzyskać więcej informacji, zobacz [Ngen.exe (Generator obrazu natywnego)](/dotnet/framework/tools/ngen-exe-native-image-generator).  
  
 Rozwiązanie  
 Należy użyć wersji MSIL zestawu. Nie przetwarzaj go z NGen.  
  
### <a name="custom-runsettings-file-with-bad-syntax"></a>Niestandardowy plik .runsettings o złej składni  
 Analiza  
 Jeśli używasz pliku niestandardowego .runsettings, może on zawierać błąd składni.  
  
 Wynikiem tego jest całkowity brak uruchomienia pokrycia kodu. Okno pokrycia kodu nie zostanie otwarte po zakończeniu przebiegu testowego lub pokaże stare wyniki.  
  
 Wyjaśnienie  
 Można uruchomić testy jednostkowe z pliku niestandardowego .runsettings, aby skonfigurować opcje pokrycia kodu. Opcje te umożliwiają uwzględnianie lub wykluczanie plików. Aby uzyskać więcej informacji, zobacz [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md).  
  
 Rozwiązanie  
 Istnieją dwa typy możliwych błędów:  
  
-   **Błąd XML**  
  
     Otwórz plik .runsettings w edytorze XML programu Visual Studio. Poszukaj oznak błędów.  
  
-   **Błąd wyrażeń regularnych**  
  
     Każdy ciąg znaków w pliku jest wyrażeniem regularnym. Przejrzyj każdy z nich w poszukiwaniu błędów, a w szczególności zwróć uwagę na:  
  
    -   Niedopasowane nawiasy (...) lub nawiasów niezmienionym znaczeniu \\(...) \\). Jeśli chcesz dopasować nawiasy w ciągu wyszukiwania, musisz dodać przed nimi znak ucieczki. Na przykład, aby dopasować Użyj funkcji:`.*MyFunction\(double\)`  
  
    -   Gwiazdka lub plus na początku wyrażenia. W celu dopasowania do dowolnego ciągu znaków, należy używać pojedynczego znaku kropki, następuje znak gwiazdki:`.*`  
  
### <a name="custom-runsettings-file-with-incorrect-exclusions"></a>Niestandardowy plik .runsettings z niepoprawnymi wykluczeniami  
 Analiza  
 Korzystając z pliku niestandardowego .runsettings, upewnij się, że zawiera on Twój zestaw.  
  
 Wyjaśnienie  
 Można uruchomić testy jednostkowe z pliku niestandardowego .runsettings, aby skonfigurować opcje pokrycia kodu. Opcje te umożliwiają uwzględnianie lub wykluczanie plików. Aby uzyskać więcej informacji, zobacz [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md).  
  
 Rozwiązanie  
 Usuń wszystkie `Include` węzły przy użyciu pliku runsettings, a następnie usuń wszystkie `Exclude` węzłów. Jeśli to rozwiąże problem, umieść je z powrotem w etapach.  
  
 Upewnij się, że węzeł DataCollectors określa pokrycie kodu. Porównaj je z próbki w [Dostosowywanie analizy pokrycia kodu](../test/customizing-code-coverage-analysis.md).  
  
## <a name="some-code-is-always-shown-as-not-covered"></a>Niektóre kody są zawsze wyświetlane jako niepokryte  
  
### <a name="initialization-code-in-native-dlls-is-executed-before-instrumentation"></a>Kod inicjowania w natywnych bibliotekach DLL jest wykonywany przed instrumentacją  
 Analiza  
 W kodzie natywnym statycznie połączone, część funkcji inicjowania **DllMain** i kod, który wywołuje czasami jest wyświetlany nie zostały podane, nawet jeśli wykonano kod.  
  
 Wyjaśnienie  
 Narzędzie pokrycia kodu działa przez wstawienie instrumentacji do zestawu tuż przed uruchomieniem aplikacji. W dowolnym zestawie załadowane przed upływem wskazanego terminu, kod inicjowania **DllMain** wykonuje natychmiast po załadowaniu zestawu, a przed uruchomieniem aplikacji. Kod ten zostanie wyświetlony jako niepokryty.  
  
 Zwykle dotyczy to statycznie załadowanych zestawów.  
  
 Rozwiązanie  
 Brak.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z pokrycia kodu do określenia, jaka część kodu jest poddawana testom](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
