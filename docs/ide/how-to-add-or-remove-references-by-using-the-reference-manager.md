---
title: "Porady: Dodawanie lub usuwanie odwołań za pomocą Menedżera odwołań | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 06/21/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.ReferenceManager
helpviewer_keywords:
- Visual C# projects, references
- references [Visual Studio], adding
- assemblies [Visual Studio], references
- Visual Basic projects, references
- project references, adding
- referencing components, adding references
- project references, removing
- referencing assemblies
- referencing components, removing references
- references [Visual Studio], removing
- referencing components, assemblies not listed
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1a4e225f8a68923963549ba70b7900b0692ddad3
ms.sourcegitcommit: f36eb7f989efbdbed0d0a087afea8ffe27d8ca15
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2017
---
# <a name="how-to-add-or-remove-references-by-using-the-reference-manager"></a>Porady: Dodawanie lub usuwanie odwołań za pomocą Menedżera odwołań

Można użyć **Menedżera odwołań** okno dialogowe dodawania i zarządzania nimi odwołuje się do składników tego użytkownika firmy Microsoft, lub opracowany innej firmy. Jeśli projektujesz aplikacji uniwersalnej systemu Windows projektu automatycznie odwołuje się do wszystkich bibliotek DLL poprawny zestaw SDK systemu Windows. Jeśli tworzysz aplikację .NET projektu automatycznie odwołuje się do pliku mscorlib.dll. Niektóre interfejsów API architektury .NET są widoczne w składnikach, które należy dodać ręcznie. Odwołania do składników COM lub niestandardowe składniki muszą je dodać ręcznie.

## <a name="reference-manager-dialog-box"></a>Okno dialogowe menedżera odwołań

**Menedżera odwołań** różne kategorie wyświetlane okno dialogowe z lewej strony, w zależności od typu projektu:

- [Zestawy](#assemblies), z podgrupy Framework i rozszerzenia.

- [COM](#com), zawiera listę wszystkich składników modelu COM, które są dostępne dla przywołującego.

- [Rozwiązanie](#solution), z podgrupy projektów.

- [Windows](#windows), z podgrupy rdzeni i rozszerzenia. Za pomocą można eksplorowania odwołań w SDK systemu Windows lub rozszerzenia SDK **przeglądarki obiektów**.

- [Przeglądaj](#browse), z ostatnich podgrup.

## <a name="adding-and-removing-a-reference"></a>Dodawanie i usuwanie odwołań

### <a name="to-add-a-reference"></a>Aby dodać odwołanie

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł odniesienia i wybierz **Dodaj odwołanie**.

2. Określ odwołania do dodania, a następnie wybierz pozycję **OK** przycisku.

   **Menedżera odwołań** otwiera i list odwołań dostępne przez grupę.

## <a name="a-idassemblies-assemblies-tab"></a><a id="assemblies" />Karta zestawów

**Zestawy** karcie wyświetlane są wszystkie zestawy .NET Framework, które są dostępne dla przywołującego. **Zestawy** kartę nie listy żadnych zestawów z globalnej pamięci podręcznej zestawów (GAC), ponieważ zestawy w pamięci GAC są częścią środowiska czasu wykonywania. Jeśli wdrażania lub kopiowania aplikacji, która zawiera odwołanie do zestawu, który jest zarejestrowany w pamięci GAC, zestaw nie będą wdrożone lub skopiowane z aplikacją, bez względu na ustawienie kopii lokalnej. Aby uzyskać więcej informacji, zobacz [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md).

Jeśli ręcznie Dodaj odwołanie do dowolnego zestawu (EnvDTE EnvDTE80, EnvDTE90, EnvDTE90a albo EnvDTE100), obszary nazw EnvDTE **Osadź typy międzyoperacyjne** właściwości odwołania do **False** w Okno właściwości. Ustawienie tej właściwości na **True** można Przyczyna kompilacji problemy z powodu niektórych właściwości EnvDTE, które nie mogą być osadzone.

Wszystkie projekty pulpitu zawierają niejawne odwołanie do mscorlib. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]projekty zawierają niejawne odwołanie do właśnie Microsoft.VisualBasic. Wszystkie projekty zawiera niejawne odwołanie do właśnie System.Core, nawet jeśli zostanie ono usunięte z listy odwołania.

Jeśli typ projektu nie obsługuje zestawów, karcie nie będą wyświetlane w **Menedżera odwołań** okno dialogowe.

Karta Zestawy zawiera dwie karty podrzędne:

1. **Framework** Wyświetla wszystkie zestawy, które stanowią docelową platformę.

    Projekty dla [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikacje zawierają odwołania do wszystkich zestawów na docelowej [!INCLUDE[net_win8_profile](../ide/includes/net_win8_profile_md.md)] domyślnie po utworzeniu projektu. W projektach zarządzanych, tylko do odczytu węzła w folderze odwołań w **Eksploratora rozwiązań** wskazuje odwołanie do całego Framework. W związku z tym karcie Framework nie wyliczyć żadnego z zestawów w ramach i zamiast tego wyświetli następujący komunikat: "wszystkie zestawy Framework są już przywoływane. Użyj przeglądarki obiektów do eksplorowania odwołań w platformie. " Dla projektów pulpitu karcie Framework wylicza zestawów platformy docelowej, a użytkownika należy dodać odwołania wymagane przez tę aplikację.

2. **Rozszerzenia** Wyświetla wszystkie zestawy, które zewnętrznych dostawców składników i formantów ma opracowany, aby rozszerzyć docelową platformę. W zależności od celu aplikacji użytkownika, może być konieczne użycie tych zestawów.

    - Rozszerzenia jest wypełniane przez wyliczanie zestawów, które są zarejestrowane w następujących lokalizacjach:

        ```
        32-bit machine:
        HKEY_CURRENT_USER\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]  
        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]  
        64-bit machine:
        HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]  
        HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]  
        And older versions of the [Target Framework Identifier]  
        ```

        Na przykład, jeśli projekt jest przeznaczony dla programu .NET Framework 4 na komputerze 32-bitowy, rozszerzenia wylicza zestawy, które są zarejestrowane pod \Microsoft\\. NETFramework\v4.0\AssemblyFoldersEx\\, \Microsoft\\. NETFramework\v3.5\AssemblyFoldersEx\\, \Microsoft\\. NETFramework\v3.0\AssemblyFoldersEx\\i \Microsoft\\. NETFramework\v2.0\AssemblyFoldersEx\\.

Niektóre składniki na liście mogą nie być wyświetlane, w zależności od [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] wersji projektu. Taka sytuacja może wystąpić w następujących warunkach:

- Składnik, który korzysta z najnowszej wersji programu .NET Framework jest niezgodna z projektu, który jest przeznaczony dla starszej wersji programu .NET Framework.

    Aby dowiedzieć się, jak zmienić docelową wersję .NET Framework dla projektu, zobacz [porady: wersja docelowa platformy .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

- Składnik, który używa [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] jest niezgodny z projektu, którego celem jest [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)].

    Podczas tworzenia nowej aplikacji docelowej niektóre projekty [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)] domyślnie.

- Dodawanie odwołań do pliku, aby wyjść z innego projektu w tym samym rozwiązaniu, należy unikać, ponieważ w ten sposób może spowodować błędy kompilacji. Zamiast tego należy użyć **projekty** karcie **Dodaj odwołanie** okno dialogowe, aby utworzyć odwołania do projektu do projektu. To ułatwia programowanie zespołowe przez włączenie lepsze zarządzanie utworzone w projektach biblioteki klas. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z odwołaniami uszkodzony](../ide/troubleshooting-broken-references.md).

> [!NOTE]
> W programie Visual Studio 2015 lub nowszego zamiast odwołanie do projektu odwołanie pliku jest tworzony, jeśli docelową wersję systemu .NET Framework jeden projekt jest w wersji 4.5 lub nowszej, a wersja docelowa innych projektów jest w wersji 2, 3, 3.5 lub 4.0.

### <a name="to-display-an-assembly-in-the-add-reference-dialog-box"></a>Do wyświetlenia w oknie dialogowym Dodaj odwołanie do zestawu

- Przenieś lub skopiuj ten plik zestawu do jednego z następujących lokalizacji:

    - Bieżący katalog projektu. (Te zestawy można znaleźć przy użyciu **Przeglądaj** kartę.)

    - Innych katalogów projektu w tym samym rozwiązaniu. (Te zestawy można znaleźć przy użyciu **projekty** kartę.)

    \-lub -

- Ustaw klucz rejestru, który określa lokalizację zestawów do wyświetlenia:

    W przypadku 32-bitowym systemie operacyjnym należy dodać jedną z następujących kluczy rejestru.

    - [HKEY_CURRENT_USER\SOFTWARE\Microsoft\\. NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@= "*AssemblyLocation*"

    - [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@= "*AssemblyLocation*"

    Dla 64-bitowym systemie operacyjnym należy dodać jedną z następujących kluczy rejestru w gałęzi rejestru w 32-bitowych.

    - [HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@= "*AssemblyLocation*"

    - [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@= "*AssemblyLocation*"

    *VersionMinimum* jest najniższa wersja .NET Framework, która ma zastosowanie. Jeśli *VersionMinimum* jest w wersji 3.0, foldery określone w AssemblyFoldersEx dotyczą projektów przeznaczonych .NET Framework 3.0 i nowszych.

    *AssemblyLocation* jest to katalog zestawy, które mają być wyświetlane w **Dodaj odwołanie** okno dialogowe, na przykład C:\MyAssemblies\\.

    Tworzenie klucza rejestru w węźle HKEY_LOCAL_MACHINE zezwala wszystkim użytkownikom na zobacz zestawy w określonej lokalizacji w **Dodaj odwołanie** okno dialogowe. Tworzenie klucza rejestru w węźle HKEY_CURRENT_USER ma wpływ tylko ustawienia dla bieżącego użytkownika.

    Otwórz **Dodaj odwołanie** ponownie okno dialogowe. Zestawy powinny pojawiać się na **.NET** kartę. Jeśli nie, upewnij się, że zestawy znajdują się w określonym *AssemblyLocation* katalogu, uruchom ponownie program Visual Studio i spróbuj ponownie.

## <a name="a-idcom-com-tab"></a><a id="com" />Karta COM

Na karcie COM znajduje się lista wszystkich składników COM, które są dostępne dla odwołań. Jeśli chcesz dodać odwołanie do zarejestrowanej DLL modelu COM, zawierającej manifest wewnętrzny, najpierw wyrejestruj bibliotekę DLL. W przeciwnym razie Visual Studio dodaje odwołanie do zestawu jako formant ActiveX, a nie jako natywną DLL.

Jeśli typ projektu nie obsługuje modelu COM, nie pojawi się na karcie **Menedżera odwołań** okno dialogowe.

## <a name="a-idsolution-solution-tab"></a><a id="solution" />Karta rozwiązania

Na karcie Rozwiązanie znajduje się lista wszystkich zgodnych projektów w obrębie bieżącego rozwiązania, na karcie podrzędnej Projekty.

Projekt może się odwoływać do innego projektu, który jest przeznaczony dla innej wersji platformy .NET Framework. Na przykład można utworzyć projektu którego element docelowy [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] , ale który odwołuje się do zestawu, który jest został skompilowany dla platformy .NET Framework 2. Jednak nie może odwoływać się projekt .NET Framework 2 [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] projektu. Aby uzyskać więcej informacji, zobacz [przeznaczonych dla określonej wersji programu .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).

Projekt, którego celem jest [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] jest niezgodny z projektu, którego celem jest [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)].

Odwołanie do pliku jest tworzony zamiast odwołania projektu, jeśli jeden projekt przeznaczony dla platformy .NET Framework 4 i inny projekt jest przeznaczony dla starszej wersji.

Projekt, którego celem jest [!INCLUDE[net_win8_profile](../ide/includes/net_win8_profile_md.md)] nie można dodać odwołania projektu do projektu przeznaczonego dla programu .NET Framework i na odwrót.

## <a name="a-idwindows-windows-tab"></a><a id="windows" />Karta Windows

Na karcie Windows są wymienione wszystkie zestawy SDK specyficzne dla platform, na których jest uruchamiany system operacyjny Windows.

Można wygenerować plik WinMD w Visual Studio na dwa sposoby:

- **[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]Aplikacja zarządzana projekty**: [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] projekty aplikacji można wyjściowe pliki binarne WinMD przez ustawienie właściwości projektu &#124; Dane wyjściowe typu = plik WinMD. Nazwa pliku WinMD musi być nadzbiorem przestrzeni nazw wszystkich przestrzeni nazw, które w nim istnieją. Na przykład, jeżeli projekt składa się z przestrzeni nazw A.B i A.B.C, możliwe nazwy dla wygenerowanego WinMD to A.winmd i A.B.winmd. Jeśli użytkownik wprowadzi właściwości projektu &#124; Nazwa zestawu lub właściwości projektu &#124; Wartość Namespace, która jest odłączony od zestaw przestrzeni nazw w projekcie lub brak nie jest nadzbiorem obszaru nazw w projekcie, generowania ostrzeżeń kompilacji: "A.winmd" nie jest prawidłową winmd nazwę pliku dla tego zestawu. Wszystkie typy w pliku metadanych systemu Windows musi istnieć w podrzędnej przestrzeni nazw nazwy pliku. Typy, które nie istnieje w przestrzeni nazw sub nazwy pliku nie będzie można znajdować się w czasie wykonywania. W tym zestawie najmniejszą wspólną przestrzenią nazw jest „CSWSClassLibrary1”. Pulpitu projekt Visual Basic lub Visual C# może używać tylko metadanych Winmd, które zostały wygenerowane za pomocą [!INCLUDE[win8](../debugger/includes/win8_md.md)] zestawów SDK, które są określane jako metadanych Winmd firmy i nie można wygenerować metadanych Winmd.

- **[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]projektów natywnych aplikacji**: natywny plik WinMD, który składa się z tylko metadane. Jego realizacja istnieje w oddzielnym pliku DLL. Co może spowodować natywne pliki binarne, wybierając szablon projektu składnika środowiska wykonawczego systemu Windows w **nowy projekt** okno dialogowe lub uruchamiając od pustego projektu i modyfikowanie właściwości projektu, aby wygenerować plik WinMD. Jeżeli projekt zawiera rozłączne przestrzenie nazw, błąd kompilacji poinformuje użytkownika, że należy połączyć ich przestrzenie nazw lub uruchomić narzędzie MSMerge.

Karta Windows składa się z dwóch podgrup.

### <a name="core-subgroup"></a>Podgrupy Core

Podgrupa podstawowa zawiera listę wszystkich WinMD (dla elementów wykonawczych Windows) w zestawie SDK dla docelowej wersji systemu Windows.

[!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]Projekty aplikacji zawierają odwołania do wszystkich metadanych winmd w [!INCLUDE[win8](../debugger/includes/win8_md.md)] zestaw SDK domyślnie po utworzeniu projektu. W projektach zarządzanych, tylko do odczytu węzła w folderze odwołań w **Eksploratora rozwiązań** wskazuje odwołanie do całej [!INCLUDE[win8](../debugger/includes/win8_md.md)] zestawu SDK. W związku z tym podgrupy Core Menedżera odwołań nie będzie żadnego z zestawów z wyliczenia [!INCLUDE[win8](../debugger/includes/win8_md.md)] zestawu SDK i zamiast tego zostanie wyświetlony komunikat: "Windows SDK istnieje już odwołanie. Użyj przeglądarki obiektów do eksplorowania odwołań w SDK systemu Windows."

W projektach pulpitu podgrupy Core nie jest wyświetlany domyślnie. Środowisko wykonawcze systemu Windows można dodać przez otwarcie menu skrótów węzła projektu wybieranie **Zwolnij projekt**, dodając następujący fragment kodu i ponownie otworzyć projekt (na węzeł projektu, wybierz **Załaduj ponownie projekt**). Gdy wywołanie **Menedżera odwołań** , podgrupy Core okno dialogowe.

```xml
<PropertyGroup>
  <TargetPlatformVersion>8.0</TargetPlatformVersion>
</PropertyGroup>
```

Upewnij się wybrać **Windows** pole wyboru na tym podgrupy. Wówczas można używać elementów środowiska wykonawczego Windows. Jednak warto również dodać System.Runtime, w którym środowisko wykonawcze Windows definiuje kilka standardowych klas i interfejsów, takich jak IEnumerable, które są używane we wszystkich bibliotekach uruchomieniowych Windows. Aby uzyskać informacje o sposobie dodawania System.Runtime, zobacz [zarządzanych aplikacji klasycznych i środowiska wykonawczego systemu Windows](http://msdn.microsoft.com/library/windows/apps/jj856306.aspx#consuming_standard_windows_runtime_types).

### <a name="extensions-subgroup"></a>Podgrupy rozszerzeń

Rozszerzenia wyświetla pakiety SDK użytkownika, które rozszerzają docelową platformę Windows. Ta karta jest wyświetlana dla [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikacji tylko projekty. Projekty pulpitu nie zostanie wyświetlona na tej karcie, ponieważ mogą one wykorzystywać tylko pliki cookie winmd.

Zestaw SDK jest zbiorem plików, który program Visual Studio traktuje jako samodzielny składnik. Na karcie rozszerzenia zestawów SDK, które są stosowane do projektu, z których **Menedżera odwołań** wywołano okno dialogowe są wyświetlane jako pojedynczej wpisów. Dodane do projektu, cała zawartość zestawu SDK jest używane przez program Visual Studio taki sposób, że użytkownik nie musisz podejmować dalsze działania wykorzystać zawartość zestawu SDK w funkcji IntelliSense, przybornika, projektantów przeglądarki obiektów, kompilowanie, wdrażanie, debugowanie i pakowania. Aby uzyskać informacje o wyświetlaniu zestawu SDK na karcie rozszerzenia, zobacz [tworzenie zestaw Software Development Kit](../extensibility/creating-a-software-development-kit.md).

> [!NOTE]
> Jeśli projekt zawiera odwołania do zestawu SDK, który jest zależny od innego zestawu SDK, Visual Studio nie korzysta z drugiego zestawu SDK, chyba że użytkownik ręcznie dodaje odwołanie do drugiego zestawu SDK. Gdy użytkownik wybierze SDK na **rozszerzenia** karcie **Menedżera odwołań** okno dialogowe ułatwia użytkownikom identyfikację zależności zestawu SDK przez wyświetlanie nie tylko nazwę i wersję zestawu SDK, ale także nazwę dowolnego zestawu SDK zależności w okienku szczegółów. Jeśli użytkownik nie należy zauważyć, zależności i dodaje tylko, że zestaw SDK, program MSBuild monitują użytkownika można dodać zależności.

Jeśli typ projektu nie obsługuje **rozszerzenia**, nie jest wyświetlane w karcie **Menedżera odwołań** okno dialogowe.

## <a name="a-idbrowse-browse-button"></a><a id="browse" />Przycisk Przeglądaj

Można użyć **Przeglądaj** przycisk, aby przeglądać składnika w systemie plików.

Projekt może się odwoływać do składnika, który jest przeznaczony dla innej wersji platformy .NET Framework. Na przykład, można utworzyć aplikację, która jest przeznaczona dla .NET Framework 4 Client Profile, który odwołuje się do składnika przeznaczonego dla .NET Framework 2. Aby uzyskać więcej informacji, zobacz [przeznaczonych dla określonej wersji programu .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).

Nie należy dodawać odwołań do pliku do danych wyjściowych innego projektu w tym samym rozwiązaniu, ponieważ takie rozwiązanie może spowodować błędy kompilacji. Zamiast tego należy użyć **rozwiązania** karcie **Menedżera odwołań** okno dialogowe, aby utworzyć odwołania do projektu do projektu. To ułatwia programowanie zespołowe przez włączenie lepsze zarządzanie bibliotek klas, które możesz utworzyć w projektach. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z odwołaniami uszkodzony](../ide/troubleshooting-broken-references.md).

Nie można przejść do zestawu SDK i dodaj go do projektu. Można przeglądać tylko w poszukiwaniu pliku (na przykład zestawu lub .winmd) i dodać go do projektu.

Podczas wykonywania odwołanie pliku do WinMD, oczekiwano układ jest *FileName*winmd, *FileName*dll, i *FileName*pliki PRI zostaną umieszczone obok siebie. Jeśli odwołujesz się do WinMD w następujących scenariuszach, niepełny zestaw plików zostanie skopiowany do katalogu wyjściowego projektu i, w związku z tym, wystąpią błędy kompilacji i czasu wykonywania.

- **Składnik macierzysty**: natywnego projektu spowoduje utworzenie jednego WinMD dla każdego zestawu rozłącznych obszarów nazw i jeden DLL, która składa się z implementacji. Pliki WinMD będą miały odmienne nazwy. Podczas odwoływania się do tego pliku składnik macierzysty, MSBuild nie rozpoznaje, czy dissimilarly nazwanego metadanych Winmd wprowadzić jeden składnik. W rezultacie tylko o identycznej nazwie *FileName*dll i *FileName*winmd zostaną skopiowane, a wystąpią błędy podczas wykonywania. Aby obejść ten problem, należy utworzyć SDK rozszerzenia. Aby uzyskać więcej informacji, zobacz [tworzenie zestaw Software Development Kit](../extensibility/creating-a-software-development-kit.md).

- **Korzystanie z formantów**: co najmniej kontrolki XAML składa się z *FileName*winmd, *FileName*dll, *FileName*PRI, *xamlname —* .xaml i *Nazwa_obrazu*jpg. Podczas tworzenia projektu, pliki zasobów, które są skojarzone z odwołaniem pliku nie będzie otrzymywał skopiowany do katalogu wyjściowego projektu i tylko *FileName*winmd, *FileName*dll i *FileName*PRI zostaną skopiowane. Błąd kompilacji jest rejestrowane w celu poinformowania użytkownika o który zasoby *xamlname —*.xaml i *Nazwa_obrazu*brakuje jpg. Aby kompilacja się powiodła, trzeba ręcznie skopiować te pliki zasobów do katalogu wyjściowego projektu dla kompilacji i debugowania/czasu wykonywania. Aby obejść ten problem, Utwórz zestawu SDK rozszerzenia wykonując kroki opisane w [tworzenie zestaw Software Development Kit](../extensibility/creating-a-software-development-kit.md) lub edytować plik projektu do dodania następującej właściwości:

    ```xml
    <PropertyGroup>
       <GenerateLibraryOutput>True</GenerateLibraryOutput>
    </PropertyGroup>
    ```

    > [!NOTE]
    > Jeśli dodasz właściwość, kompilacja może być wolniejsza.

## <a name="recent"></a>Ostatnie

Każda z kart Zestawy, COM, Windows i Przeglądaj obsługuje kartę Najnowsze, która wylicza listę składników ostatnio dodanych do projektów.

## <a name="search"></a>Wyszukaj

Pasek wyszukiwania w **Menedżera odwołań** okno dialogowe działa przez kartę, który jest aktywny. Na przykład, jeśli użytkownik wpisze "System" na pasku wyszukiwania podczas **rozwiązania** kartę fokus, wyszukiwanie nie zwróciła żadnych wyników, chyba że rozwiązania składa się z nazwy projektu, który zawiera "System".

## <a name="see-also"></a>Zobacz także

[Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md)
