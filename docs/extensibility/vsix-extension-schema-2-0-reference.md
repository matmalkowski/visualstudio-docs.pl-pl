---
title: Odwołanie do schematu 2.0 rozszerzenia VSIX | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- vsix
- extension schema
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7459b4292220e6bb1e5a00b912efe7eb99cce825
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="vsix-extension-schema-20-reference"></a>Odwołanie do schematu 2.0 rozszerzenia VSIX
Plik manifestu VSIX wdrożenia opis zawartości pakietu VSIX. Format pliku jest regulowane przez schemat. W wersji 2.0 tego schematu obsługuje dodawanie niestandardowych typów i atrybutów.  Schemat manifestu jest otwarty. Moduł ładujący manifestu ignoruje elementów XML oraz atrybuty, które go nie zrozumieć.  
  
> [!IMPORTANT]
>  Visual Studio 2015 może ładować pliki VSIX w formatach programu Visual Studio 2010, Visual Studio 2012 lub Visual Studio 2013.  
  
## <a name="package-manifest-schema"></a>Schematu manifestu pakietu  
 Element główny pliku manifestu XML jest `<PackageManifest>`, atrybutem pojedynczego `Version`, czyli wersję formatu manifestu. W przypadku istotnych zmian na format, format wersji zostanie zmieniony. W tym temacie opisano format manifestu w wersji 2.0, które jest określone w manifeście przez ustawienie `Version` atrybut na wartość wersji = "2.0".  
  
### <a name="packagemanifest-element"></a>PackageManifest Element  
 W ramach `<PackageManifest>` elementu głównego można użyć następujących elementów:  
  
-   `<Metadata>` -Metadanych i reklam informacji na temat samego pakietu. Tylko jeden `Metadata` element jest dozwolony w manifeście.  
  
-   `<Installation>` -Ta sekcja definiuje sposób, który można zainstalować ten pakiet rozszerzenia, jednostki SKU aplikacji, które można zainstalować w tym. Tylko jeden `Installation` element jest dozwolony w manifeście. Manifest musi mieć `Installation` elementu lub tego pakietu nie można zainstalować w dowolnej jednostki SKU.  
  
-   `<Dependencies>` -Opcjonalną listę zależności dla tego pakietu są zdefiniowane w tym miejscu.  
  
-   `<Assets>` -Ta sekcja zawiera wszystkie zasoby zawarte w tym pakiecie. Bez tej sekcji tego pakietu nie powierzchni żadnej zawartości.  
  
-   `<AnyElement>*` -Schematu manifestu jest wystarczająco elastyczny, aby umożliwić inne elementy. Wszystkie elementy podrzędne nie rozpoznał manifestu modułu ładującego są widoczne w interfejsie API Menedżera rozszerzenia jako dodatkowe obiekty XmlElement. Za pomocą tych elementów podrzędnych, rozszerzenia VSIX, można zdefiniować dodatkowe dane w pliku manifestu, dostępnej w czasie wykonywania kodu uruchomionego w programie Visual Studio. Zobacz <xref:Microsoft.VisualStudio.ExtensionManager.IExtension.AdditionalElements%2A> i <xref:Microsoft.VisualStudio.ExtensionManager.IExtension.LocalizedAdditionalElements%2A>.  
  
### <a name="metadata-element"></a>Element metadanych  
 Ta sekcja ma metadane dotyczące pakietu, jego tożsamość i reklam informacji. `<Metadata>` zawiera następujące elementy:  
  
-   `<Identity>` — Definiuje informacje identyfikacyjne tego pakietu i zawiera następujące atrybuty:  
  
    -   `Id` -Tego atrybutu musi być unikatowy identyfikator dla pakietu, wybierany przez jego autora. Powinny być kwalifikowane nazwy typów CLR są należących do przestrzeni nazw tak samo: Company.Product.Feature.Name. `Id` Atrybut jest ograniczona do 100 znaków.  
  
    -   `Version` -Definiuje wersję tego pakietu i jego zawartość. Ten atrybut zgodne z formatem przechowywania wersji zestawu CLR: główna.pomocnicza.kompilacja.poprawka (1.2.40308.00). Pakiet o wyższym numerze wersji jest uznawany za aktualizacji do pakietu i można zainstalować na istniejące zainstalowanej wersji.  
  
    -   `Language` -Tego atrybutu jest to domyślny język dla pakietu i odpowiada danych tekstowych w tym manifeście. Ten atrybut następuje Konwencji kod ustawień regionalnych CLR dla zestawów zasobu, na przykład: en-us, en, fr-fr. Można określić `neutral` Aby zadeklarować rozszerzenia niezależny od języka, który będzie uruchamiany w dowolnej wersji programu Visual Studio. Wartość domyślna to `neutral`.  
  
    -   `Publisher` — Ten atrybut identyfikuje wydawcę tego pakietu, firma lub nazwy użytkownika. `Publisher` Atrybut jest ograniczona do 100 znaków.  
  
-   `<DisplayName>` — Ten element określa nazwa pakietu przyjazną dla użytkownika, która jest wyświetlana w Interfejsie użytkownika Menedżera rozszerzenia. `DisplayName` Zawartości jest ograniczona do 50 znaków.  
  
-   `<Description>` — To opcjonalny element jest krótki opis pakietu oraz jego zawartość jest wyświetlana w interfejsie użytkownika Menedżera rozszerzenia. `Description` Zawartości mogą zawierać dowolny tekst, który ma, ale ma ograniczone do 1000 znaków.  
  
-   `<MoreInfo>` — To opcjonalny element jest adres URL do trybu online strony, która zawiera pełen opis tego pakietu. Protokół muszą być określone jako http.  
  
-   `<License>` — To opcjonalny element jest ścieżką względną do pliku licencji (txt, .rtf) zawartych w pakiecie.  
  
-   `<ReleaseNotes>` — To opcjonalny element jest względna ścieżka do pliku informacje o wersji zawartych w pakiecie (txt, .rtf) w przeciwnym razie adres URL do witryny sieci Web, który wyświetla informacje o wersji.  
  
-   `<Icon>` — To opcjonalny element jest ścieżką względną do pliku obrazu (png, bmp, jpeg, ico) zawartych w pakiecie. Obraz ikony powinny być 32 x 32 piksele (lub zostanie zmniejszony do tego rozmiaru) i jest wyświetlany w elemencie listview interfejsu użytkownika. Jeśli nie `Icon` element jest określony, domyślnie korzysta z interfejsu użytkownika.  
  
-   `<PreviewImage>` — To opcjonalny element jest ścieżką względną do pliku obrazu (png, bmp, jpeg) zawartych w pakiecie. Obraz podglądu powinien być 200 x 200 pikseli i wyświetlane w szczegółach interfejsu użytkownika. Jeśli nie `PreviewImage` element jest określony, domyślnie korzysta z interfejsu użytkownika.  
  
-   `<Tags>` — To opcjonalny element zawiera dodatkowy tekst rozdzielone średnikami tagi, które są używane do wskazówki dotyczące wyszukiwania. `Tags` Element jest ograniczona do 100 znaków.  
  
-   `<GettingStartedGuide>` — To opcjonalny element jest ścieżką względną do pliku HTML lub adres URL do witryny sieci Web, który zawiera informacje o sposobie używania rozszerzenia lub zawartości w ramach tego pakietu. Ten przewodnik jest uruchamiane w ramach instalacji.  
  
-   `<AnyElement>*` -Schematu manifestu jest wystarczająco elastyczny, aby umożliwić inne elementy. Wszystkie elementy podrzędne, które nie są rozpoznawane przez moduł ładujący manifestu są widoczne w postaci listy obiektów XmlElement. Za pomocą tych elementów podrzędnych, rozszerzenia VSIX można zdefiniować dodatkowe dane w pliku manifestu i wyliczenia w czasie wykonywania.  
  
### <a name="installation-element"></a>Element instalacji  
 Ta sekcja definiuje sposób instalowania tego pakietu i jednostki SKU aplikacji, które można zainstalować w. Ta sekcja zawiera następujące atrybuty:  
  
-   `Experimental` — Wartość tego atrybutu na wartość true, jeśli masz rozszerzenia, które jest obecnie zainstalowany dla wszystkich użytkowników, ale tworzysz zaktualizowanej wersji na tym samym komputerze. Na przykład jeśli zainstalowano MyExtension 1.0 dla wszystkich użytkowników, ale chcesz debugować MyExtension 2.0 na tym samym komputerze, ustaw eksperymentalne = "true". Ten atrybut jest dostępne w programie Visual Studio 2015 Update 1 lub nowszy.  
  
-   `Scope` -Tego atrybutu może zająć wartość "Global" lub "ProductExtension":  
  
    -   "Globalne" Określa, że instalacja jest poza zakresem określonym jednostki SKU. Na przykład ta wartość jest używana podczas instalowania zestawu SDK rozszerzenia.  
  
    -   "ProductExtension" Określa, że tradycyjnych rozszerzenia VSIX (w wersji 1.0) ograniczone do poszczególnych SKU Visual Studio jest zainstalowany. Jest to wartość domyślna.  
  
-   `AllUsers` -Ta opcjonalny atrybut określa, czy ten pakiet zostanie zainstalowany dla wszystkich użytkowników. Domyślnie ten atrybut ma wartość false, określa, czy pakiet jest dla każdego użytkownika. (Jeśli ta wartość jest ustawiona na wartość true, instalowania użytkownika musi podniesienia uprawnień do poziomu uprawnień administracyjnych do zainstalowania wynikowego pliku VSIX.  
  
-   `InstalledByMsi` -Ta opcjonalny atrybut określa, czy ten pakiet jest zainstalowane przez Instalatora MSI. Pakiety zainstalowane przez Instalatora MSI nie zostaną zainstalowane i zarządzane przez MSI (programy i funkcje), a nie przez Visual Studio Menedżera rozszerzeń.  Domyślnie ten atrybut ma wartość false, który określa, że pakiet nie jest instalowany przez Instalatora MSI.  
  
-   `SystemComponent` -Ta opcjonalny atrybut określa, czy ten pakiet należy traktować jako składnik systemu. Składniki systemowe nie pokazuj w Interfejsie użytkownika Menedżera rozszerzenia i nie można zaktualizować. Domyślnie ten atrybut ma wartość false, który określa, że pakiet nie jest składnikiem systemu.  
  
-   `AnyAttribute*` - `Installation` Element akceptuje otwarty zestaw atrybutów, które mają być widoczne w czasie wykonywania w formie słownika pary nazwa wartość.  
  
-   `<InstallationTarget>` — Ten element określa lokalizację, w której Instalator VSIX instaluje pakiet. Jeśli wartość `Scope` atrybutu jest "ProductExtension" pakietu musi wskazywać SKU, na którym jest zainstalowana pliku manifestu w ramach jego zawartość do anonsowania jego dostępność na rozszerzenia. `<InstallationTarget>` Element ma następujące atrybuty, kiedy `Scope` atrybut ma jawnych lub wartość domyślną "ProductExtension":  
  
    -   `Id` — Ten atrybut identyfikuje pakiet.  Atrybut jest zgodna z Konwencją przestrzeni nazw: Company.Product.Feature.Name. `Id` Atrybut może zawierać tylko znaki alfanumeryczne i nie może przekraczać 100 znaków. Oczekiwano wartości:  
  
        -   Microsoft.VisualStudio.IntegratedShell  
  
        -   Microsoft.VisualStudio.Pro  
  
        -   Microsoft.VisualStudio.Premium  
  
        -   Microsoft.VisualStudio.Ultimate  
  
        -   Microsoft.VisualStudio.VWDExpress  
  
        -   Microsoft.VisualStudio.VPDExpress  
  
        -   Microsoft.VisualStudio.VSWinExpress  
  
        -   Microsoft.VisualStudio.VSLS  
  
        -   My.Shell.App  
  
    -   `Version` — Ten atrybut określa zakres wersji z minimalną i maksymalną obsługiwane wersje to jednostki SKU. Pakiet można szczegółowo wersji jednostki SKU, które obsługuje. Wersja zakres jest [10.0 11.0], gdzie  
  
        -   [-minimalna wersja włącznie.  
  
        -   ]-maksymalna wersja włącznie.  
  
        -   (-minimalna wersja wyłącznego.  
  
        -   ) — maksymalna wersja wyłącznego.  
  
        -   Jednej wersji # - określonej wersji.  
  
        > [!IMPORTANT]
        >  Wersja 2.0 schematu VSIX została wprowadzona w programie Visual Studio 2012. Aby użyć tego schematu musi mieć programu Visual Studio 2012 lub później zainstalowane na tym komputerze i używać VSIXInstaller.exe będącej częścią tego produktu. Możesz zastosować wcześniejszych wersji programu Visual Studio za pomocą programu Visual Studio 2012 lub nowszym VSIXInstaller, ale tylko przy użyciu nowszej wersji Instalatora.  
  
    -   `AnyAttribute*` - `<InstallationTarget>` Element umożliwia otwarty zestaw atrybutów, które będą udostępniane w czasie wykonywania w formie słownika pary nazwa wartość.  
  
### <a name="dependencies-element"></a>Element zależności  
 Ten element zawiera listę zależności, które deklaruje tego pakietu. Jeśli wszystkie zależności są określone, tych pakietów (identyfikowana na podstawie ich `Id`) musi być zainstalowane przed.  
  
-   `<Dependency>` Element — ten element podrzędny ma następujące atrybuty:  
  
    -   `Id` -Tego atrybutu musi być unikatowy identyfikator pakietu zależnego. Ta wartość tożsamości musi odpowiadać `<Metadata><Identity>Id` atrybut pakietu, który jest zależny od tego pakietu. `Id` Atrybut jest zgodna z Konwencją przestrzeni nazw: Company.Product.Feature.Name. Atrybut może zawierać tylko znaki alfanumeryczne i nie może przekraczać 100 znaków.  
  
    -   `Version` — Ten atrybut określa zakres wersji z minimalną i maksymalną obsługiwane wersje to jednostki SKU. Pakiet można szczegółowo wersji jednostki SKU, które obsługuje. Wersja zakres jest [12,0, 13,0], gdzie:  
  
        -   [-minimalna wersja włącznie.  
  
        -   ]-maksymalna wersja włącznie.  
  
        -   (-minimalna wersja wyłącznego.  
  
        -   ) — maksymalna wersja wyłącznego.  
  
        -   Jednej wersji # - określonej wersji.  
  
    -   `DisplayName` — Ten atrybut to nazwa wyświetlana zależnego pakietu, który jest używany w elementów interfejsu użytkownika, takich jak okien dialogowych i komunikaty o błędach. Ten atrybut jest opcjonalne, chyba że zależny pakiet jest instalowany przez Instalatora MSI.  
  
    -   `Location` — Ten opcjonalny atrybut określa ścieżkę względną w tym pliku VSIX do zagnieżdżonych pakietu VSIX albo adres URL do lokalizacji pobierania dla zależności. Ten atrybut służy pomóc użytkownikowi zlokalizuj pakiet wymagań wstępnych.  
  
    -   `AnyAttribute*` - `Dependency` Element akceptuje otwarty zestaw atrybutów, które mają być widoczne w czasie wykonywania w formie słownika pary nazwa wartość.  
  
### <a name="assets-element"></a>Element zasobów  
 Ten element zawiera listę `<Asset>` znaczniki dla każdego rozszerzenia lub zawartości elementu udostępniane przez ten pakiet.  
  
-   `<Asset>` — Ten element zawiera następujące atrybuty i elementy:  
  
    -   `Type` — Jest to typ rozszerzenia lub reprezentowanego przez ten element zawartości. Każdy `<Asset>` element musi mieć pojedynczy `Type`, ale wiele `<Asset>` elementy mogą mieć takie same `Type`. Ten atrybut powinny być reprezentowane jako nazwę FQDN, zgodnie z konwencjami przestrzeni nazw. Znane typy to:  
  
        1.  Microsoft.VisualStudio.VsPackage  
  
        2.  Microsoft.VisualStudio.MefComponent  
  
        3.  Microsoft.VisualStudio.ToolboxControl  
  
        4.  Microsoft.VisualStudio.Samples  
  
        5.  Microsoft.VisualStudio.ProjectTemplate  
  
        6.  Microsoft.VisualStudio.ItemTemplate  
  
        7.  Microsoft.VisualStudio.Assembly  
  
         Tworzenie własnych typów i nadaj im unikatowe nazwy. W czasie wykonywania w programie Visual Studio kodu można wyliczyć i dostęp do tych typów niestandardowych za pomocą interfejsu API Menedżera rozszerzenia.  
  
    -   Ścieżka - ścieżkę względną do pliku lub folderu w pakiecie, który zawiera element zawartości.  
  
    -   `AnyAttribute*` -Otwarty zestaw atrybutów, które będą udostępniane w czasie wykonywania w formie słownika pary nazwa wartość.  
  
         `<AnyElement>*` -Wszelkie uporządkowana zawartość jest dozwolone między `<Asset>` rozpoczęcia i zakończenia znacznika. Wszystkie elementy są widoczne w postaci listy obiektów XmlElement. Rozszerzenia VSIX można zdefiniować strukturalnych metadanych określonego typu w pliku manifestu i wyliczenia w czasie wykonywania.  
  
### <a name="sample-manifest"></a>Manifest próbki  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">  
  <Metadata>  
    <Identity Id="0000000-0000-0000-0000-000000000000" Version="1.0" Language="en-US" Publisher="Company" />  
    <DisplayName>Test Package</DisplayName>  
    <Description>Information about my package</Description>  
    <MoreInfo>http://www.fabrikam.com/Extension1/</MoreInfo>  
    <License>eula.rtf</License>  
    <ReleaseNotes>notes.txt</ReleaseNotes>  
    <Icon>Images\icon.png</Icon>  
    <PreviewImage>Images\preview.png</PreviewImage>  
  </Metadata>  
  <Installation InstalledByMsi="false" AllUsers="false" SystemComponent="false" Scope="ProductExtension">  
    <InstallationTarget Id="Microsoft.VisualStudio.Pro" Version="[11.0, 12.0]" />  
  </Installation>  
  <Dependencies>  
    <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="[4.5,)" />  
    <Dependency Id="Microsoft.VisualStudio.MPF.12.0" DisplayName="Visual Studio MPF 12.0" d:Source="Installed" Version="[12.0]" />  
  </Dependencies>  
  <Assets>  
    <Asset Type="Microsoft.VisualStudio.VsPackage" d:Source="Project" d:ProjectName="%CurrentProject%" Path="|%CurrentProject%;PkgdefProjectOutputGroup|" />  
  </Assets>  
</PackageManifest>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dostarczanie rozszerzeń programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md)