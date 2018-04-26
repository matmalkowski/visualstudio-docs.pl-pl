---
title: Dodaj odwołania do Menedżera odwołań
ms.date: 04/11/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ReferenceManager
helpviewer_keywords:
- C# projects, references
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 33b9b29cef4ad215e76af57e66c73eb2e8a134db
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-add-or-remove-references-by-using-the-reference-manager"></a>Porady: Dodawanie lub usuwanie odwołań za pomocą Menedżera odwołań

Można użyć **Menedżera odwołań** okno dialogowe dodawania i zarządzania nimi odwołuje się do składników tego użytkownika firmy Microsoft, lub opracowany innej firmy. Jeśli projektujesz aplikacji uniwersalnej systemu Windows projektu automatycznie odwołuje się do wszystkich bibliotek DLL poprawny zestaw SDK systemu Windows. Jeśli tworzysz aplikację .NET projektu automatycznie odwołuje się do *mscorlib.dll*. Niektóre interfejsów API architektury .NET są widoczne w składnikach, które należy dodać ręcznie. Odwołania do składników COM lub niestandardowe składniki muszą je dodać ręcznie.

## <a name="reference-manager-dialog-box"></a>Okno dialogowe menedżera odwołań

**Menedżera odwołań** różne kategorie wyświetlane okno dialogowe z lewej strony, w zależności od typu projektu:

- **Zestawy**, z **Framework** i **rozszerzenia** podgrup.

- **COM**, zawiera listę wszystkich składników modelu COM, które są dostępne dla przywołującego.

- **Rozwiązanie**, z **projekty** podgrup.

- **Windows**, z **Core** i **rozszerzenia** podgrup. Za pomocą można eksplorowania odwołań w SDK systemu Windows lub rozszerzenia SDK **przeglądarki obiektów**.

- **Przeglądaj**, z **ostatnie** podgrup.

## <a name="add-and-remove-a-reference"></a>Dodawanie i usuwanie odwołań

### <a name="to-add-a-reference"></a>Aby dodać odwołanie

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** lub **zależności** węzeł i wybierz polecenie **Dodaj odwołanie**. Możesz również kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Dodaj** > **odwołania**.

   **Menedżera odwołań** otwiera i list odwołań dostępne przez grupę.

2. Określ odwołania do dodania, a następnie wybierz **OK**.

## <a name="assemblies-tab"></a>Karta Zestawy

**Zestawy** karcie wyświetlane są wszystkie zestawy .NET Framework, które są dostępne dla przywołującego. **Zestawy** kartę nie listy żadnych zestawów z globalnej pamięci podręcznej zestawów (GAC), ponieważ zestawy w pamięci GAC są częścią środowiska czasu wykonywania. Jeśli wdrażania lub kopiowania aplikacji, która zawiera odwołanie do zestawu, który jest zarejestrowany w pamięci GAC, zestaw nie będą wdrożone lub kopiowane z aplikacją, niezależnie od tego **Kopiuj lokalnie** ustawienie. Aby uzyskać więcej informacji, zobacz [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md).

Jeśli ręcznie Dodaj odwołanie do żadnej z przestrzeni nazw EnvDTE (<xref:EnvDTE>, <xref:EnvDTE80>, <xref:EnvDTE90>, <xref:EnvDTE90a>, lub <xref:EnvDTE100>) ustaw **Osadź typy międzyoperacyjne** właściwości odwołania do **False** w **właściwości** okna. Ustawienie tej właściwości na **True** można Przyczyna kompilacji problemy z powodu niektórych właściwości EnvDTE, które nie mogą być osadzone.

Wszystkie projekty pulpitu zawierają niejawne odwołanie do **mscorlib**. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projekty zawierają niejawne odwołanie do <xref:Microsoft.VisualBasic>. Wszystkie projekty zawierają niejawne odwołanie do **System.Core**nawet wtedy, gdy zostanie ono usunięte z listy odwołania.

Jeśli typ projektu nie obsługuje zestawów, karcie nie będą wyświetlane w **Menedżera odwołań** okno dialogowe.

**Zestawy** kartę składa się z dwóch kart podrzędne:

1. **Framework** Wyświetla wszystkie zestawy, które stanowią docelową platformę.

    Projekty dla aplikacji ze Sklepu Windows 8.x zawierają odwołania do wszystkich zestawów na docelowej [!INCLUDE[net_win8_profile](../ide/includes/net_win8_profile_md.md)] domyślnie po utworzeniu projektu. W projektach zarządzanych, tylko do odczytu węzeł w węźle **odwołania** folderu w **Eksploratora rozwiązań** wskazuje odwołanie do całego framework. W związku z tym **Framework** kartę nie będzie żadnego z zestawów w ramach wyliczyć i zamiast tego wyświetli następujący komunikat: "wszystkie zestawy Framework są już przywoływane. Użyj przeglądarki obiektów do eksplorowania odwołań w platformie. " W przypadku projektów pulpitu **Framework** kartę wylicza zestawów platformy docelowej, a użytkownik musi dodać odwołania wymagane przez tę aplikację.

2. **Rozszerzenia** Wyświetla wszystkie zestawy, które zewnętrznych dostawców składników i formantów ma opracowany, aby rozszerzyć docelową platformę. W zależności od celu aplikacji użytkownika, może być konieczne użycie tych zestawów.

   **Rozszerzenia** jest wypełniana wyliczania zestawy, które są rejestrowane w następujących lokalizacjach:

   komputer 32-bitowe:
   - `HKEY_CURRENT_USER\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`
   - `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`

   komputer 64-bitowe:
   - `HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`
   - `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`

   I starsze wersje [Identyfikator docelowego Framework]

   Na przykład, jeśli projekt jest przeznaczony dla programu .NET Framework 4 na komputerze 32-bitowych **rozszerzenia** wylicza zestawy, które są zarejestrowane pod *\Microsoft\.NETFramework\v4.0\AssemblyFoldersEx*, *\Microsoft\.NETFramework\v3.5\AssemblyFoldersEx*, *\Microsoft\.NETFramework\v3.0\AssemblyFoldersEx*, i  *\Microsoft\.NETFramework\v2.0\AssemblyFoldersEx*.

Niektóre składniki na liście mogą nie być wyświetlane, w zależności od wersji platformy .NET projektu. Taka sytuacja może wystąpić w następujących warunkach:

- Składnik, który korzysta z najnowszej wersji programu .NET Framework jest niezgodna z projektu, który jest przeznaczony dla starszej wersji programu .NET Framework.

    Aby dowiedzieć się, jak zmienić docelową wersję .NET Framework dla projektu, zobacz [porady: wersja docelowa platformy .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

- Składnik, który używa [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] jest niezgodny z projektu, którego celem jest [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)].

    Podczas tworzenia nowej aplikacji docelowej niektóre projekty [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)] domyślnie.

- Dodawanie odwołań do pliku, aby wyjść z innego projektu w tym samym rozwiązaniu, należy unikać, ponieważ w ten sposób może spowodować błędy kompilacji. Zamiast tego należy użyć **projekty** karcie **Dodaj odwołanie** okno dialogowe, aby utworzyć odwołania do projektu do projektu. To ułatwia programowanie zespołowe przez włączenie lepsze zarządzanie utworzone w projektach biblioteki klas. Aby uzyskać więcej informacji, zobacz [rozwiązywanie uszkodzenie odwołań](../ide/troubleshooting-broken-references.md).

> [!NOTE]
> W programie Visual Studio 2015 lub nowszego zamiast odwołanie do projektu odwołanie pliku jest tworzony, jeśli docelową wersję systemu .NET Framework jeden projekt jest w wersji 4.5 lub nowszej, a wersja docelowa innych projektów jest w wersji 2, 3, 3.5 lub 4.0.

### <a name="to-display-an-assembly-in-the-add-reference-dialog-box"></a>Do wyświetlenia w oknie dialogowym Dodaj odwołanie do zestawu

- Przenieś lub skopiuj ten plik zestawu do jednego z następujących lokalizacji:

    - Bieżący katalog projektu. (Te zestawy można znaleźć przy użyciu **Przeglądaj** kartę.)

    - Innych katalogów projektu w tym samym rozwiązaniu. (Te zestawy można znaleźć przy użyciu **projekty** kartę.)

    \- lub -

- Ustaw klucz rejestru, który określa lokalizację zestawów do wyświetlenia:

   W przypadku 32-bitowym systemie operacyjnym należy dodać jedną z następujących kluczy rejestru.

   - `[HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

   - `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

   Dla 64-bitowym systemie operacyjnym należy dodać jedną z następujących kluczy rejestru w gałęzi rejestru w 32-bitowych.

   - `[HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

   - `[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

   *\<VersionMinimum\>*  jest najniższa wersja .NET Framework, która ma zastosowanie. Jeśli *\<VersionMinimum\>* jest w wersji 3.0, foldery określone w *AssemblyFoldersEx* Zastosuj do projektów przeznaczonych dla platformy .NET Framework 3.0 i nowszych.

   *\<AssemblyLocation\>*  jest to katalog zestawy, które mają być wyświetlane w **Dodaj odwołanie** okno dialogowe, na przykład *C:\MyAssemblies*.

   Tworzenie klucza rejestru w kluczu `HKEY_LOCAL_MACHINE` węzeł zezwala wszystkim użytkownikom wyświetlić zestawy w określonej lokalizacji w **Dodaj odwołanie** okno dialogowe. Tworzenie klucza rejestru w kluczu `HKEY_CURRENT_USER` węzeł ma wpływ tylko ustawienia dla bieżącego użytkownika.

   Otwórz **Dodaj odwołanie** ponownie okno dialogowe. Zestawy powinny pojawiać się na **.NET** kartę. Jeśli nie, upewnij się, że zestawy znajdują się w określonym *AssemblyLocation* katalogu, uruchom ponownie program Visual Studio i spróbuj ponownie.

## <a name="projects-tab"></a>Karta projekty

**Projekty** w karcie wyświetlane są wszystkie zgodne projekty w bieżącym rozwiązaniu **rozwiązania** karty podrzędnej.

Projekt może się odwoływać do innego projektu, który jest przeznaczony dla innej wersji platformy .NET Framework. Na przykład można utworzyć projektu którego element docelowy [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] , ale który odwołuje się do zestawu, który jest został skompilowany dla platformy .NET Framework 2. Jednak nie może odwoływać się projekt .NET Framework 2 [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] projektu. Aby uzyskać więcej informacji, zobacz [omówienie wielowersyjności](../ide/visual-studio-multi-targeting-overview.md).

Projekt, którego celem jest [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] jest niezgodny z projektu, którego celem jest [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)].

Odwołanie do pliku jest tworzony zamiast odwołania projektu, jeśli jeden projekt przeznaczony dla platformy .NET Framework 4 i inny projekt jest przeznaczony dla starszej wersji.

Projekt, którego celem jest [!INCLUDE[net_win8_profile](../ide/includes/net_win8_profile_md.md)] nie można dodać odwołania projektu do projektu przeznaczonego dla programu .NET Framework i na odwrót.

## <a name="windows-tab"></a>Karta Windows

**Windows** karta zawiera listę wszystkich zestawów SDK, które są specyficzne dla platformy, na które systemy operacyjne Windows uruchom.

Można wygenerować plik WinMD w Visual Studio na dwa sposoby:

- **Projekty zarządzanych aplikacji ze Sklepu Windows 8.x**: projektami aplikacji dla systemu Windows 8.x magazynu można wyjściowe pliki binarne WinMD przez ustawienie **właściwości projektu** > **typ danych wyjściowych = plik WinMD**. Nazwa pliku WinMD musi być nadzbiorem przestrzeni nazw wszystkich przestrzeni nazw, które w nim istnieją. Na przykład, jeśli projekt składa się z przestrzeni nazw `A.B` i `A.B.C`, są możliwe nazwy dla jego outputted WinMD *A.winmd* i *A.B.winmd*. Jeśli użytkownik wprowadzi **właściwości projektu** > **nazwy zestawu** lub **właściwości projektu** > **Namespace**wartość, która jest rozłączna z zestawu przestrzeni nazw w projekcie lub brak nie jest nadzbiorem obszaru nazw w projekcie, generowania ostrzeżeń kompilacji: "" A.winmd"nie jest prawidłową winmd nazwę pliku dla tego zestawu." Wszystkie typy w pliku metadanych systemu Windows musi istnieć w podrzędnej przestrzeni nazw nazwy pliku. Typy, które nie istnieje w przestrzeni nazw sub nazwy pliku nie będzie można znajdować się w czasie wykonywania. W tym zestawie najmniejszą wspólnej przestrzeni nazw jest `CSWSClassLibrary1`. Pulpit Visual Basic lub C# projektu można korzystać tylko metadanych Winmd, generowanych przez korzystanie z systemu Windows 8 zestawów SDK, które są określane jako firmy metadanych Winmd, i nie można wygenerować metadanych Winmd.

- **Projekty natywnych aplikacji systemu Windows 8.x magazynu**: natywny plik WinMD, który składa się z tylko metadane. Jego realizacja istnieje w oddzielnym pliku DLL. Co może spowodować natywne pliki binarne, wybierając szablon projektu składnika środowiska wykonawczego systemu Windows w **nowy projekt** okno dialogowe lub uruchamiając od pustego projektu i modyfikowanie właściwości projektu, aby wygenerować plik WinMD. Jeżeli projekt zawiera rozłączne przestrzenie nazw, błąd kompilacji poinformuje użytkownika, że należy połączyć ich przestrzenie nazw lub uruchomić narzędzie MSMerge.

**Windows** kartę składa się z dwóch podgrup.

### <a name="core-subgroup"></a>Podgrupy Core

**Core** podgrupa zawiera listę wszystkich metadanych winmd (w przypadku elementów środowiska wykonawczego systemu Windows) w zestawie SDK dla docelowej wersji systemu Windows.

Projekty aplikacji systemu Windows 8.x magazynu zawierają odwołania do wszystkich metadanych winmd w zestawie SDK systemu Windows 8, domyślnie na tworzenie projektu. W projektach zarządzanych, tylko do odczytu węzeł w węźle **odwołania** folderu w **Eksploratora rozwiązań** wskazuje odwołanie do całego systemu Windows 8 SDK. W związku z tym **Core** podgrupy w **Menedżera odwołań** nie wyliczyć żadnego z zestawów z zestawu SDK systemu Windows 8 i zamiast tego zostanie wyświetlony komunikat: "Windows SDK istnieje już odwołanie. Użyj przeglądarki obiektów do eksplorowania odwołań w SDK systemu Windows."

W projektach pulpitu **Core** podgrupy nie jest wyświetlane domyślnie. Środowisko wykonawcze systemu Windows można dodać przez otwarcie menu skrótów węzła projektu wybieranie **Zwolnij projekt**, dodając następujący fragment kodu i ponownie otworzyć projekt (na węzeł projektu, wybierz **Załaduj ponownie projekt**). Podczas wywołania **Menedżera odwołań** okno dialogowe **Core** pojawi się podgrupę.

```xml
<PropertyGroup>
  <TargetPlatformVersion>8.0</TargetPlatformVersion>
</PropertyGroup>
```

Upewnij się wybrać **Windows** pole wyboru na tym podgrupy. Wówczas można używać elementów środowiska wykonawczego Windows. Jednak również należy dodać <xref:System.Runtime>, w której środowiska uruchomieniowego systemu Windows definiuje niektóre standardowe klasy i interfejsy, takich jak <xref:System.Collections.IEnumerable>, używane w całej biblioteki środowiska uruchomieniowego systemu Windows. Aby uzyskać informacje o sposobie dodawania <xref:System.Runtime>, zobacz [zarządzanych aplikacji klasycznych i środowiska wykonawczego systemu Windows](http://msdn.microsoft.com/library/windows/apps/jj856306.aspx#consuming_standard_windows_runtime_types).

### <a name="extensions-subgroup"></a>Podgrupy rozszerzeń

**Rozszerzenia** wymieniono użytkownika zestawów SDK rozszerzających docelowej platformy systemu Windows. Ta karta jest wyświetlana dla systemu Windows 8.x magazynu aplikacji tylko dla projektów. Projekty pulpitu nie zostanie wyświetlona na tej karcie, ponieważ mogą one wykorzystywać tylko firmy *winmd* plików.

Zestaw SDK jest zbiorem plików, który program Visual Studio traktuje jako samodzielny składnik. W **rozszerzenia** karcie zestawów SDK, które są stosowane do projektu, z których **Menedżera odwołań** wywołano okno dialogowe są wyświetlane jako pojedynczej wpisów. Dodane do projektu, cała zawartość zestawu SDK jest używane przez program Visual Studio taki sposób, że użytkownik nie musisz podejmować dalsze działania wykorzystać zawartość zestawu SDK w funkcji IntelliSense, przybornika, projektantów przeglądarki obiektów, kompilowanie, wdrażanie, debugowanie i pakowania. Aby uzyskać informacje o wyświetlaniu zestawu SDK w **rozszerzenia** karcie, zobacz [tworzenie zestaw Software Development Kit](../extensibility/creating-a-software-development-kit.md).

> [!NOTE]
> Jeśli projekt zawiera odwołania do zestawu SDK, który jest zależny od innego zestawu SDK, Visual Studio nie korzysta z drugiego zestawu SDK, chyba że użytkownik ręcznie dodaje odwołanie do drugiego zestawu SDK. Gdy użytkownik wybierze SDK na **rozszerzenia** karcie **Menedżera odwołań** okno dialogowe ułatwia użytkownikom identyfikację zależności zestawu SDK przez wyświetlanie nie tylko nazwę i wersję zestawu SDK, ale także nazwę dowolnego zestawu SDK zależności w okienku szczegółów. Jeśli użytkownik nie należy zauważyć, zależności i dodaje tylko, że zestaw SDK, program MSBuild monitują użytkownika można dodać zależności.

Jeśli typ projektu nie obsługuje rozszerzeń, nie ma karty **Menedżera odwołań** okno dialogowe.

## <a name="com-tab"></a>Karta COM

**COM** karta zawiera listę wszystkich składników modelu COM, które są dostępne dla przywołującego. Jeśli chcesz dodać odwołanie do zarejestrowanej DLL modelu COM, zawierającej manifest wewnętrzny, najpierw wyrejestruj bibliotekę DLL. W przeciwnym razie program Visual Studio dodaje odwołanie do zestawu jako formant ActiveX, a nie jako natywnej biblioteki DLL.

Jeśli typ projektu nie obsługuje modelu COM, nie ma karty **Menedżera odwołań** okno dialogowe.

## <a name="browse-button"></a>Przycisk Przeglądaj

Można użyć **Przeglądaj** przycisk, aby przeglądać składnika w systemie plików.

Projekt może się odwoływać do składnika, który jest przeznaczony dla innej wersji platformy .NET Framework. Na przykład można tworzenia aplikacji którego element docelowy .NET Framework 4.7, który odwołuje się składnik, który jest przeznaczony dla platformy .NET Framework 4. Aby uzyskać więcej informacji, zobacz [omówienie wielowersyjności](../ide/visual-studio-multi-targeting-overview.md).

Nie należy dodawać odwołań do pliku do danych wyjściowych innego projektu w tym samym rozwiązaniu, ponieważ takie rozwiązanie może spowodować błędy kompilacji. Zamiast tego należy użyć **rozwiązania** karcie **Menedżera odwołań** okno dialogowe, aby utworzyć odwołania do projektu do projektu. To ułatwia programowanie zespołowe przez włączenie lepsze zarządzanie bibliotek klas, które możesz utworzyć w projektach. Aby uzyskać więcej informacji, zobacz [rozwiązywanie uszkodzenie odwołań](../ide/troubleshooting-broken-references.md).

Nie można przejść do zestawu SDK i dodaj go do projektu. Można przeglądać tylko w pliku (na przykład zestawu lub *winmd*) i dodaj go do projektu.

Podczas wykonywania odwołanie pliku do WinMD, oczekiwano układ jest  *<FileName>winmd*,  *<FileName>.dll*, i  *<FileName>PRI* są pliki wszystkie umieszczone obok siebie. Jeśli odwołujesz się do WinMD w następujących scenariuszach, niepełny zestaw plików zostanie skopiowany do katalogu wyjściowego projektu i, w związku z tym, wystąpią błędy kompilacji i czasu wykonywania.

- **Składnik macierzysty**: natywnego projektu spowoduje utworzenie jednego WinMD dla każdego zestawu rozłącznych obszarów nazw i jeden DLL, która składa się z implementacji. Pliki WinMD będą miały odmienne nazwy. Podczas odwoływania się do tego pliku składnik macierzysty, MSBuild nie rozpoznaje, czy dissimilarly nazwanego metadanych Winmd wprowadzić jeden składnik. W rezultacie tylko o identycznej nazwie  *<FileName>.dll* i  *<FileName>winmd* zostaną skopiowane, a wystąpią błędy podczas wykonywania. Aby obejść ten problem, Utwórz rozszerzenia SDK. Aby uzyskać więcej informacji, zobacz [utworzyć zestaw Software Development Kit](../extensibility/creating-a-software-development-kit.md).

- **Korzystanie z formantów**: co najmniej kontrolki XAML składa się z  *<FileName>winmd*,  *<FileName>.dll*,  *<FileName>PRI*,  *<XamlName>.xaml*i  *<ImageName>.jpg*. Podczas tworzenia projektu, pliki zasobów, które są skojarzone z odwołaniem pliku nie będzie otrzymywał skopiowany do katalogu wyjściowego projektu i tylko  *<FileName>winmd*,  *<FileName>.dll*i  *<FileName>PRI* zostaną skopiowane. Błąd kompilacji jest rejestrowane w celu poinformowania użytkownika o który zasoby  *<XamlName>.xaml* i  *<ImageName>.jpg* brakuje. Aby kompilacja się powiodła, trzeba ręcznie skopiować te pliki zasobów do katalogu wyjściowego projektu dla kompilacji i debugowania/czasu wykonywania. Aby obejść ten problem, Utwórz extension SDK wykonując kroki opisane w [utworzyć zestaw Software Development Kit](../extensibility/creating-a-software-development-kit.md) lub edytować plik projektu do dodania następującej właściwości:

    ```xml
    <PropertyGroup>
       <GenerateLibraryOutput>True</GenerateLibraryOutput>
    </PropertyGroup>
    ```

    > [!NOTE]
    > Jeśli dodasz właściwość, kompilacja może być wolniejsza.

## <a name="recent"></a>Ostatnie

**Zestawy**, **COM**, **Windows**, i **Przeglądaj** każdego Obsługa **ostatnie** kartę, która wylicza listę składniki, które zostały ostatnio dodane do projektów.

## <a name="search"></a>Wyszukaj

Pasek wyszukiwania w **Menedżera odwołań** okno dialogowe działa przez kartę, który jest aktywny. Na przykład, jeśli użytkownik wpisze "System" na pasku wyszukiwania podczas **rozwiązania** kartę fokus, wyszukiwanie nie zwróciła żadnych wyników, chyba że rozwiązania składa się z nazwy projektu, który zawiera "System".

## <a name="see-also"></a>Zobacz także

- [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md)