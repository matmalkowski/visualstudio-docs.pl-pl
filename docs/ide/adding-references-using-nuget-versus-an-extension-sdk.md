---
title: Różnice pomiędzy dodawaniem odwołań za pomocą NuGet a Extension SDK | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4d4bfd9be5fdcf4544f9bc5c28482cb579af5033
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="adding-references-using-nuget-versus-an-extension-sdk"></a>Różnice pomiędzy dodawaniem odwołań za pomocą NuGet a extension SDK

Możesz podać pakiet do użycia w projektach Visual Studio przy użyciu albo rozszerzenie NuGet dla programu Visual Studio, albo zestaw software development kit (SDK). Przez opisujące podobieństwa i różnice między dwa mechanizmy, w tym temacie mogą pomóc Wybierz najlepszy dla zadania.

- NuGet to system zarządzania pakietami open source, ułatwiająca włączenie biblioteki projektu rozwiązania. Aby uzyskać więcej informacji, zobacz [dokumentacji NuGet](/nuget).

- Zestaw SDK jest kolekcja plików, które Visual Studio traktuje jako element jedno odwołanie. **Menedżera odwołań** okno dialogowe wyświetla wszystkie zestawy SDK, które mają zastosowanie do projektu, która jest otwarta podczas wyświetlania tego okna dialogowego. Po dodaniu zestawu SDK do projektu, możesz uzyskać dostęp do wszystkich zawartość tego zestawu SDK za pomocą funkcji IntelliSense, **przybornika**, projektantów **przeglądarki obiektów**, MSBuild, wdrażania, debugowanie i pakowania. Aby uzyskać więcej informacji na temat zestawów SDK, zobacz [tworzenie zestaw Software Development Kit](../extensibility/creating-a-software-development-kit.md).

## <a name="which-mechanism-should-i-use"></a>Jakie działania należy użyć?

Poniższa tabela ułatwia porównanie funkcji odwołaniem do zestawu SDK z odwołaniem do funkcji programu NuGet.

|Funkcja|Obsługa w zestawie SDK|Uwagi dotyczące zestawu SDK|Obsługa NuGet|Informacje o NuGet|
|-------------|-----------------|---------------|-------------------|-----------------|
|Mechanizm odwołuje się do jednego obiektu, a następnie wszystkie pliki i funkcje są dostępne.|T|Dodaj zestaw SDK usługi za pomocą **Menedżera odwołań** okno dialogowe i wszystkich plików i funkcje są dostępne podczas tworzenia przepływu pracy.|T||
|MSBuild automatycznie wykorzystuje zestawy i metadanych systemu Windows (*winmd*) plików.|T|Odwołania do zestawu SDK są automatycznie przekazywane do kompilatora.|T||
|MSBuild automatycznie wykorzystuje pliki .h lub lib.|T|*SDKName.props* pliku programu Visual Studio zawiera informacje dotyczące konfigurowania katalogu Visual C++ i tak dalej, automatyczne *.h* lub *.lib* pliku zużycia.|N||
|Automatycznie wykorzystuje MSBuild *js* lub *.css* plików.|T|W **Eksploratora rozwiązań**, można rozwinąć węzła odwołanie JavaScript SDK w celu wyświetlania poszczególnych *js* lub *.css* pliki, a następnie wygenerować `<source include/>` tagi przeciągając te pliki do ich plików źródłowych. Zestaw SDK obsługuje F5 i automatyczne pakiet Instalatora.|T||
|MSBuild automatycznie dodaje do formantu w **przybornika**.|T|**Przybornika** można korzystać z zestawów SDK i Pokaż formanty w kartach, które określisz.|N||
|Mechanizm obsługuje Instalator programu Visual Studio (VSIX) rozszerzeń.|T|VSIX ma specjalne manifestu i logiki do tworzenia pakietów SDK|T|Inny program instalacyjny można ją osadzić pliku VSIX.|
|**Przeglądarki obiektów** wylicza odwołań.|T|**Przeglądarki obiektów** pobiera listę odwołań w SDK i wylicza je automatycznie.|N||
|Pliki i łącza automatycznie zostaną dodane do **Menedżera odwołań** okno dialogowe (łącza pomocy i itp. automatycznie wypełnić)|T|**Menedżera odwołań** okno dialogowe automatycznie wylicza zestawów SDK, a także łącza pomocy i listę zależności zestawu SDK.|N|NuGet zawiera własną **Zarządzaj pakietami NuGet** okno dialogowe.|
|Mechanizm obsługuje wielu architektur.|T|Zestawy SDK można wysłać wiele konfiguracji. MSBuild zużywa odpowiednie pliki dla każdej konfiguracji projektu.|N||
|Mechanizm obsługuje wiele konfiguracji.|T|Zestawy SDK można wysłać wiele konfiguracji. W zależności od architektury projektu MSBuild zużywa odpowiednie pliki dla każdej architektury projektu.|N||
|Mechanizm można określić "nie do kopiowania."|T|W zależności od tego, czy pliki są usuwane *\redist* lub *\designtime* folderu, można kontrolować plików do skopiowania do pakietu odbierającą aplikację.|N|Należy zadeklarować plików do skopiowania w manifeście pakietu.|
|Zawartość jest wyświetlana w zlokalizowanych plików.|T|Zlokalizowane dokumentów XML w zestawy SDK automatycznie uwzględniono lepsze środowisko czasu projektowania.|N||
|MSBuild obsługuje jednocześnie zużywa wiele wersji zestawu SDK.|T|Zestaw SDK obsługuje jednocześnie zużywa wiele wersji.|N|To nie odwołuje się do. W czasie, nie może mieć więcej niż jedną wersję plików NuGet w projekcie.|
|Mechanizm obsługuje określenie odpowiednich docelowych platform, wersji programu Visual Studio i typów projektów.|T|**Menedżera odwołań** okno dialogowe i **przybornika** Pokaż tylko zestawy SDK, które są stosowane do projektu, dzięki czemu użytkownicy mogą łatwiej wybrać odpowiednie zestawów SDK.|T (częściowe)|PIVOT jest platformy docelowej. Nie ma żadnych filtrowanie w interfejsie użytkownika. Podczas instalacji może zwrócić błąd.|
|Mechanizm obsługuje określania informacji o rejestracji dla natywnych metadanych Winmd.|T|Można określić korelacji między plik winmd i w pliku dll *SDKManifest.xml*.|N||
|Mechanizm obsługuje określania zależności w innych zestawów SDK.|T|Zestaw SDK tylko powiadamia użytkownika; Użytkownik nadal należy ich zainstalować i odwoływać je ręcznie.|T|NuGet pobiera je automatycznie. użytkownik nie jest powiadamiany.|
|Mechanizm integruje się z [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] pojęcia, takie jak manifest aplikacji i identyfikator Framework.|T|Zestaw SDK musi przejść pomyślnie pojęcia, które są specyficzne dla [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)] tak, aby opakowania i F5 działają poprawnie zestawów SDK, które są dostępne w[!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)].|N||
|Mechanizm integruje się z aplikacją debugowania potoku dla [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikacji.|T|Zestaw SDK musi przejść pomyślnie [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]-określonych tak, aby opakowania i F5 działają poprawnie zestawów SDK jest dostępny w [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)].|T|Zawartość NuGet staje się częścią projektu. Niezbędne jest nie szczególną uwagę F5.|
|Mechanizm integruje się z manifestów aplikacji.|T|Zestaw SDK musi przejść pomyślnie [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)]-określonych tak, aby opakowania i F5 działają poprawnie zestawów SDK jest dostępny w [!INCLUDE[win8_appstore_short](../ide/includes/win8_appstore_short_md.md)].|T|Zawartość NuGet staje się częścią projektu. Niezbędne jest nie szczególną uwagę F5.|
|Mechanizm wdraża pliki bez odwołań (na przykład wdrożyć struktury testowej, na których można uruchamiać testy z [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikacji).|T|Jeśli zgubisz pliki *\redist* folderów, pliki są automatycznie wdrażane.|T||
|Mechanizm automatycznie dodaje zestaw SDK platformy w programie Visual Studio IDE.|T|Jeśli zgubisz [!INCLUDE[win8](../debugger/includes/win8_md.md)] zestawu SDK lub Windows Phone SDK w określonym miejscu z układem określonego zestawu SDK automatycznie jest zintegrowany z wszystkimi funkcjami programu Visual Studio.|N||
|Mechanizm obsługuje maszyny czystą developer. (Oznacza to, że instalacja nie jest wymagana, i działa proste pobierania z kontroli kodu źródłowego.)|N|Ponieważ odwołanie SDK, musisz sprawdzić rozwiązania i zestawu SDK oddzielnie. Można sprawdzić w zestawie SDK z dwóch lokalizacji rejestru z systemem innym niż domyślny, z których MSBuild iteruje zestawów SDK (Aby uzyskać więcej informacji, zobacz [tworzenie zestaw Software Development Kit](../extensibility/creating-a-software-development-kit.md)). Alternatywnie Jeśli lokalizacja niestandardowa składa się z zestawów SDK, można określić następujący kod w pliku projektu:<br /><br /> `<PropertyGroup>    <SDKReferenceDirectoryRoot>C:\MySDKs</SDKReferenceDirectoryRoot>   </PropertyGroup>`<br /><br /> Następnie zaznacz zestawy SDK do tej lokalizacji.|T|Można wyewidencjonować rozwiązania, a program Visual Studio natychmiast rozpoznaje i działa na plikach.|
|Możesz także dołączyć do dużych społeczności istniejącego pakietu autorów.|Brak|Nowości społeczności.|T||
|Możesz także dołączyć do dużych społeczności istniejących konsumentów pakietu.|Brak|Nowości społeczności.|T||
|Możesz także dołączyć do ekosystem partnerów (galerie niestandardowe, repozytoria i tak dalej).|Brak|Dostępne repozytoria obejmują Visual Studio Marketplace, Microsoft Download Center, a [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)].|T||
|Mechanizm integruje się z serwerami kompilacji ciągłej integracji dla tworzenia pakietu i zużycia.|T|Zestaw SDK musi przejść pomyślnie lokalizacji zaewidencjonowania (właściwość SDKReferenceDirectoryRoot) w wierszu polecenia dla programu MSBuild.|T||
|Mechanizm obsługuje obie wersje pakietu stabilny i wersji wstępnej.|T|Zestaw SDK obsługuje dodawanie odwołań do wielu wersji.|T||
|Mechanizm obsługuje automatyczne aktualizowanie dla zainstalowanych pakietów.|T|Jeśli zostały wydane jako VSIX lub część aktualizacje automatyczne programu Visual Studio, zestaw SDK zawiera automatycznych powiadomień.|T||
|Mechanizm zawiera autonomiczny *.exe* plik do tworzenia i używania pakietów.|T|Zestaw SDK zawiera *MSBuild.exe*.|T||
|Pakietów można sprawdzić w kontroli wersji.|T|Nie można zaewidencjonować niczego poza węzeł dokumentów, co oznacza, że rozszerzenia SDK nie może być zaznaczona w. Rozmiar rozszerzenia SDK może być duży.|T||
|Tworzenie i stosowanie pakietów, można użyć interfejsu programu PowerShell.|T (zużycie), N (Tworzenie)|Nie narzędzi do tworzenia zestawu SDK. Użycie jest wykonywanie programu MSBuild w wierszu polecenia.|T||
|Pakiet symboli służy do obsługi debugowania.|T|Jeśli zgubisz *.pdb* pliki w zestawie SDK, pliki uzyskać pobrana automatycznie.|T||
|Mechanizm obsługuje auto aktualizacji Menedżera pakietów.|Brak|Zestaw SDK pobiera zaktualizowany przy użyciu programu MSBuild.|T||
|Mechanizm obsługuje lekkie format manifestu.|T|*SDKManifest.xml* obsługuje wiele atrybutów, ale zazwyczaj konieczne jest mały podzbiór.|T||
|Mechanizm jest dostępna dla wszystkich wersji programu Visual Studio.|T|Zestaw SDK obsługuje wszystkie wersje programu Visual Studio.|T|NuGet obsługuje wszystkie wersje programu Visual Studio.|
|Mechanizm jest dostępna dla wszystkich typów projektów.|N|Zestaw SDK obsługuje [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikacji w programie [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)].|N|Możesz przejrzeć listę dozwolonych projektów.|

## <a name="see-also"></a>Zobacz także

[Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md)