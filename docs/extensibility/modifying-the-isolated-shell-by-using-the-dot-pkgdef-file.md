---
redirect_url: shell/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file
title: "Modyfikowanie przy użyciu programu Isolated Shell. Pliku Pkgdef | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode, .pkgdef file
ms.assetid: 69e8f78e-bcf1-46cb-8866-7de37d134997
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: addeeaa294a81acce6558feb5257fee1344532f8
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/22/2018
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgdef-file"></a>Modyfikowanie przy użyciu programu Isolated Shell. Pliku Pkgdef
Plik .pkgdef obsługuje ustawienia używane do dostosowywania aplikacji isolated shell. Określa wartości, które są tworzone, gdy aplikacja jest zainstalowana na komputerze i że odwołuje się powłoki programu Visual Studio podczas uruchamiania aplikacji. Ustawienia są zorganizowane w pliku oparte na kluczach rejestru odpowiednich.  
  
> [!WARNING]
>  Należy pamiętać, że .pkgdef pliki, które nie są zadeklarowane w pliku .vsixmanifest pakiet VSPackage nie są skanowane po uruchomieniu programu Visual Studio.  
  
 Plik .pkgdef zawiera sekcje, które są identyfikowanych za pomocą klucza albo `[$RootKey$]` lub `[$RootKey$\` *podklucz*`]`, gdzie $RootKey$ jest klucz główny dla aplikacji.  
  
 Każda sekcja zawiera pary nazwa/wartość, które mają następujący format: `"` *ValueName*`"=`*wartość*.  
  
 Wartości są ciąg, który jest ujęta w cudzysłowy lub 32-bitową liczbę całkowitą, która jest reprezentowany jako wartość typu dword. Wartości mają następujące ograniczenia:  
  
-   Wszystkie wartości dword są w formacie szesnastkowym, na przykład `dword:00000001`.  
  
     Dla wartości logicznych 1 oznacza wartość PRAWDA, a 0 reprezentuje wartość false.  
  
-   Wszystkie ciągi GUID są w formacie rejestru, na przykład `"{00000000-0000-0000-0000-000000000000}"`.  
  
-   Wszystkie identyfikatory zasobu Lokalizowalny mieć postać "@*resourceID*" lub "#*resourceID*", gdzie *resourceID* jest identyfikator zasobu w pakiecie aplikacji interfejsu użytkownika na przykład `"@102"`. Pakiet interfejsu użytkownika aplikacji jest pakiet, który odwołuje się do ustawienia AppLocalizationPackage.  
  
 Na przykład  
  
```  
"HideSolutionConcept"=dword:00000001  
"DefaultDebugEngine"="{00000000-0000-0000-0000-000000000000}"  
```  
  
 Komentarze można dodawać do pliku .pkgdef. Komentarz jednowierszowy zawiera dwa ukośniki jako pierwsze dwa znaki.  
  
 Aby uzyskać listę ciągów podstawienia, zobacz [podstawienia ciągi używane w. Pkgdef i. Pliki Pkgundef](../extensibility/substitution-strings-used-in-dot-pkgdef-and-dot-pkgundef-files.md).  
  
 W poniższych sekcjach opisano wartości rejestru, które wpływają na zachowanie powłoki programu Visual Studio w trybie izolowanym. Można również definiować wartości dodatkowe rejestru dla aplikacji, w tym pliku.  
  
> [!NOTE]
>  Jeśli to ustawienie nie zostanie podany w pliku .pkgdef, nie odpowiadającego mu wpisu jest przeprowadzane w rejestrze.  
  
## <a name="settings"></a>Ustawienia  
 W poniższej tabeli opisano wartości zdefiniowane w obszarze [$RootKey$].  
  
|Nazwa|Typ|Wartość|  
|----------|----------|-----------|  
|AddinsAllowed|DWORD|Wartość true, jeśli można załadować dodatków; w przeciwnym razie wartość false.<br /><br /> Wartość domyślna to true.|  
|AllowsDroppedFilesOnMainWindow|DWORD|Wartość true, jeśli okno główne może akceptować porzucone pliki; w przeciwnym razie wartość false. Pliki, usunąć w oknie głównym są otwierane przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> metody. To jest równoznaczne z otwarciem dokumentu za pomocą **Otwórz** na **pliku** menu w aplikacji.<br /><br /> Wartość domyślna to true.|  
|AppIcon|string|Pełna ścieżka ikonę programu. Ta ikona jest wyświetlana na pasku tytułu z lewej strony nazwy aplikacji.<br /><br /> Wartością domyślną jest "$RootFolder$\\*Nazwa rozwiązania*.ico", gdzie *Nazwa rozwiązania* to nazwa pliku rozwiązania aplikacji.|  
|AppLocalizationPackage|string|Identyfikator GUID pakiet VSPackage, który zawiera zestawu satelickiego interfejsu użytkownika dla aplikacji. Ten pakiet VSPackage obejmuje skompilowanej wersji pliku vsct i może zawierać inne zlokalizowanych ciągów. Zestawy funkcji i grupami polecenie menu można można włączać lub wyłączać, zmieniając ustawienia w pliku vsct projektu interfejsu użytkownika.<br /><br /> Wartość domyślna to "{*vsUiPackageGuid*}", gdzie *vsUiPackageGuid* jest identyfikatorem GUID przypisany do interfejsu użytkownika pakietu aplikacji.|  
|AppName|string|Nazwa aplikacji. Nazwa jest wyświetlana na pasku tytułu okna aplikacji.<br /><br /> Wartość domyślna to nazwa pliku rozwiązania aplikacji.|  
|CommandLineLogo|string|Tekst transparentu, gdy aplikacja jest uruchamiana w oknie konsoli. To ustawienie dotyczy tylko te aplikacje, które obsługują operacje kompilacji wiersza polecenia.<br /><br /> Wartość domyślna to "*NazwaFirmy ** Nazwa rozwiązania* w wersji 1.0.", gdzie *NazwaFirmy* to nazwa firmy podane podczas instalacji systemu Windows i *Nazwa rozwiązania*to nazwa pliku rozwiązania aplikacji.|  
|DefaultDebugEngine|string|Identyfikator GUID domyślnych debugowania aparatu do użycia na potrzeby aplikacji.<br /><br /> Uwaga: Określono pusty identyfikator GUID (same zera) wskazuje, że aplikacja nie określa domyślny aparat debugowania. Dzięki temu debugera wybrać aparat debugowania do użycia.<br /><br /> Wartość domyślna to "{00000000-0000-0000-0000-000000000000}".|  
|DefaultHomePage|string|Domyślny adres URL strony głównej wewnętrzny okna przeglądarki sieci Web.<br /><br /> Jeśli **strony głównej** opcja jest dostępna w aplikacji, a następnie to ustawienie dotyczy również domyślnego stanu opcji. Aby uzyskać więcej informacji, zobacz [przeglądarki sieci Web, środowisko, opcje — Okno dialogowe](../ide/reference/web-browser-environment-options-dialog-box.md).<br /><br /> Wartość domyślna to adres URL firmy podane podczas instalacji systemu Windows.|  
|DefaultProjectsLocation|string|Pełna ścieżka domyślny folder projektów. Na przykład<br /><br /> `"DefaultProjectsLocation"="$MyDocuments$\MyVSShellStub\Projects"`<br /><br /> Jeśli **lokalizacji projektów programu Visual Studio** opcja jest dostępna w aplikacji, a następnie to ustawienie dotyczy również domyślnego stanu opcji. <br /><br /> Wartością domyślną jest "$MyDocuments$\\*Nazwa rozwiązania*", gdzie *Nazwa rozwiązania* to nazwa pliku rozwiązania aplikacji.|  
|DefaultSearchPage|string|Domyślny adres URL strony wyszukiwania dla wewnętrznego okna przeglądarki sieci Web.<br /><br /> Jeśli **stronę wyszukiwania** opcja jest dostępna w aplikacji, a następnie to ustawienie dotyczy również domyślnego stanu opcji. Aby uzyskać więcej informacji, zobacz [przeglądarki sieci Web, środowisko, opcje — Okno dialogowe](../ide/reference/web-browser-environment-options-dialog-box.md).<br /><br /> Wartość domyślna to "http://search.live.com".|  
|DefaultUserFilesFolderRoot|string|Nazwa folderu użytkownika, względem bieżącego użytkownika danego folderu Moje dokumenty.<br /><br /> Wartość domyślna to nazwa pliku rozwiązania aplikacji.|  
|DisableOutputWindow|DWORD|Wskazuje, czy jako wyłączony z programu isolated shell powinny traktować w oknie danych wyjściowych.<br /><br /> Jeśli ta wartość jest równa true, Visual Studio nie wyświetla danych wyjściowych Menedżera kompilacji rozwiązania w **dane wyjściowe** okno i ukrywa **okna Pokaż dane wyjściowe kiedy rozpoczyna się kompilacja** pole wyboru w  **Projekty i rozwiązania** kategorii w **opcje** okno dialogowe.<br /><br /> Wartość domyślna to false.|  
|HideMiscellaneousFilesByDefault|DWORD|Wartość PRAWDA, aby Ukryj **różne pliki** folderu domyślnie w **Eksploratora rozwiązań**; w przeciwnym razie wartość false.<br /><br /> Jeśli **Pokaż różne pliki w Eksploratorze rozwiązań** opcja jest dostępna w aplikacji, a następnie to ustawienie dotyczy również domyślnego stanu opcji. Aby uzyskać więcej informacji, zobacz [dokumenty, środowisko, opcje — Okno dialogowe](../ide/reference/documents-environment-options-dialog-box.md).<br /><br /> Wartość domyślna to false.|  
|HideSolutionConcept|DWORD|Wartość true, aby tworzyć projekty wszystkie projekty jako autonomiczny i Ukryj rozwiązanie i rozwiązania dotyczące poleceń dla autonomicznych projektów domyślnie; w przeciwnym razie wartość false.<br /><br /> Jeśli **zawsze pokazuj rozwiązania** opcja jest dostępna w aplikacji, a następnie to ustawienie dotyczy również domyślnego stanu opcji.<br /><br /> Wartość domyślna to false.|  
|NewProjDlgInstalledTemplatesHdr|string|Nazwa nagłówka szablony programu Visual Studio utworzenie w **szablony** na liście **nowy projekt** okno dialogowe. Jest to ciąg lub identyfikator zlokalizowania zasobów, które są ładowane z interfejsu użytkownika pakietu aplikacji.<br /><br /> Wartość domyślna to "*Nazwa rozwiązania* zainstalowane szablony", gdzie *Nazwa rozwiązania* to nazwa pliku rozwiązania aplikacji.|  
|NewProjDlgSlnTreeNodeTitle|string|Nazwa **rozwiązań programu Visual Studio** w węźle **typy projektów** drzewa w **nowy projekt** okno dialogowe. Jest to ciąg lub identyfikator zlokalizowania zasobów, które są ładowane z interfejsu użytkownika pakietu aplikacji.<br /><br /> Wartość domyślna to "*Nazwa rozwiązania* zainstalowane szablony", gdzie *Nazwa rozwiązania* to nazwa pliku rozwiązania aplikacji.|  
|SolutionFileCreatorIdentifier|string|Identyfikator aplikacji, która pojawia się w drugim wierszu plików rozwiązania, które są generowane przez aplikację. Ten wiersz wskazuje aplikacji, która utworzyła plik. Konwencja ta wartość obejmuje nazwę aplikacji oraz numer wersji aplikacji. Na przykład<br /><br /> `"SolutionFileCreatorIdentifier"="MyVSShellStub Solution File, Format Version 10.00"`<br /><br /> Program VSLauncher.exe, który jest domyślnym programem do otwierania pliku rozwiązanie Visual Studio, używa tego drugiego wiersza w celu określenia wersji programu Visual Studio, w którym można otworzyć pliku rozwiązania. Aplikacja wymaga własnego uruchamiania obsługi jego rozwiązanie skojarzonych plików. Uruchom okno można użyć również wiersz w pliku rozwiązania ustalenie, w jakiej wersji aplikacji w celu otwarcia rozwiązania.<br /><br /> Uwaga: Program Visual Studio VSLauncher.exe nie obsługuje pliki SLN, które zostały utworzone przez aplikację programu isolated shell.<br /><br /> Wartość domyślna to "*Nazwa rozwiązania* plik rozwiązania, wersja formatu 10,00", gdzie *Nazwa rozwiązania* to nazwa pliku rozwiązania aplikacji.|  
|SolutionFileExt|string|Rozszerzenie nazwy pliku rozwiązania dla aplikacji. Zaleca się, że wybierz rozszerzenie unikatową nazwę pliku (not.sln).<br /><br /> Wartość domyślna to "*Nazwa rozwiązania*_sln", gdzie *Nazwa rozwiązania* to nazwa pliku rozwiązania aplikacji.|  
|SplashScreenBitmap|string|Pełna ścieżka pliku mapy bitowej dla ekranu powitalnego aplikacji.<br /><br /> Wartość domyślna to "$RootFolder$\Splash.bmp".|  
|ThisVersionDTECLSID|string|Identyfikator klasy (CLSID) obiekt automatyzacji dla aplikacji.<br /><br /> Obiekt automatyzacji aplikacji jest obiektem najwyższego poziomu dla aplikacji w Visual Studio shell automatyzacji modelu i implementuje <xref:EnvDTE._DTE?displayProperty=fullName> interfejsu.<br /><br /> Jeśli obiekt automatyzacji aplikacji jest poprawnie zarejestrowany w kluczu rejestru HKEY_CLASSES_ROOT\CLSID, a następnie można użyć [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance) funkcji można bezpośrednio utworzyć wystąpienia aplikacji.<br /><br /> Visual Studio shell używa tego identyfikatora CLSID zarejestrować obiektu automatyzacji aplikacji w tabeli z obiektu (zaprojektowana) przy użyciu flagi ACTIVEOBJECT_WEAK. Dzięki temu można używać [GetActiveObject](http://msdn.microsoft.com/en-us/a276e30c-6a7f-4cde-9639-21a9f5170b62)funkcji, aby pobrać wskaźnika uruchomione wystąpienie aplikacji. Ponadto w przypadku definiowania ProgID dla obiekt automatyzacji aplikacji, następnie powłoki programu Visual Studio również rejestruje każdego wystąpienia aplikacji w zaprojektowana przy użyciu krótkiej nazwy elementu w postaci *progID*:*processID* , gdzie *progID* jest ProgID obiektu automatyzacji aplikacji i *processID* jest identyfikatorem procesu dla danego wystąpienia aplikacji. Jeśli na przykład utworzyć krótkiej nazwy w następujący sposób:<br /><br /> `CreateItemMoniker(L"!",`  *instanceString* `, &instanceMoniker)`<br /><br /> gdzie `instanceString` jest *progID*:*processID* ciągu. następnie można użyć `instanceMoniker` za pomocą funkcji ROT GetObject można pobrać wystąpienia.<br /><br /> Jeśli ustawienie ThisVersionDTECLSID zostanie pominięty, następnie aplikacja nie jest uwidaczniana, za pomocą modelu obiektów składników (COM). W takim przypadku nie można utworzyć wystąpienia aplikacji przez wywołanie metody [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance) funkcji i nie można zarejestrować w zaprojektowana.<br /><br /> Każda wersja programu pakiet VSPackage musi mieć inny identyfikator CLSID.<br /><br /> Wartość domyślna to identyfikator GUID generowany dla obiekt automatyzacji aplikacji Visual Studio.|  
|ThisVersionSolutionCLSID|string|Identyfikator CLSID obiektu rozwiązanie dla aplikacji.<br /><br /> Obiekt automatyzacji rozwiązanie zawiera informacje o bieżącej otwartego rozwiązania w przypadku aplikacji i implementuje <xref:EnvDTE._Solution?displayProperty=fullName> interfejsu.<br /><br /> Jeśli obiekt automatyzacji rozwiązania jest poprawnie zarejestrowany w kluczu rejestru HKEY_CLASSES_ROOT\CLSID, a następnie można użyć [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance) funkcja bezpośrednio utworzyć obiektu rozwiązanie dla aplikacji.<br /><br /> Visual Studio shell używa tego identyfikatora CLSID zarejestrować obiektu automatyzacji rozwiązania w zaprojektowana przy użyciu flagi ACTIVEOBJECT_WEAK.<br /><br /> Jeśli to ustawienie zostanie pominięty, to klasa rozwiązania nie jest zarejestrowana z składnika modelu COM (Object) i obiekt rozwiązania nie można utworzyć przez wywołanie metody [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance) funkcji i nie można zarejestrować w ZAPROJEKTOWANA.<br /><br /> Wartość domyślna to identyfikator GUID generowany dla obiekt rozwiązania aplikacji programu Visual Studio.|  
|UserFilesSubFolderName|string|Nazwa podfolderu w folderze Moje dokumenty użytkownika, w którym aplikacja tworzy użytkownika pliki i podfoldery.<br /><br /> Wartość domyślna to nazwa pliku rozwiązania aplikacji.|  
|UserOptsFileExt|string|Rozszerzenie dla rozwiązania pliki opcji użytkownika dla aplikacji.<br /><br /> Wartość domyślna to nazwa pliku rozwiązania aplikacji.|  
  
## <a name="binding-path-settings"></a>Ścieżka ustawienia powiązania  
 [$RootKey$ \BindingPaths\\{00000000-0000-0000-0000-000000000000}] klucz zawiera listę katalogów, które powłoki sprawdza, czy zestawy. Te katalogi są dodawane do listy katalogów, które powłoki sondy dla zestawy prywatne dla aplikacji.  
  
 Domyślnie nie wpisy ścieżkę wiązania są dodawane do pliku .pkgdef. Jednak poniższe podkatalogi katalogu instalacyjnego programu Visual Studio są automatycznie dodawane do listy aplikacji ścieżkę wiązania w rejestrze.  
  
-   Common7\IDE\  
  
-   Common7\IDE\\\PrivateAssemblies  
  
-   Common7\IDE\\\PublicAssemblies  
  
 Aby dodać katalog do ścieżki powiązanie, Dodaj wpis w postaci "*directoryName*"="", gdzie *directoryName* jest ścieżką bezwzględną. Na przykład  
  
```  
[$RootKey$\BindingPaths\{00000000-0000-0000-0000-000000000000}]  
"$RootFolder$\directory1"=""  
"%CommonProgramFiles%\directory2"=""  
```  
  
## <a name="profile-settings"></a>Ustawienia profilu  
 W poniższej tabeli opisano wartości, które są definiowane dla każdego pakietu skojarzony w obszarze [$RootKey$ \Profile].  
  
|Nazwa|Typ|Wartość|  
|----------|----------|-----------|  
|AutoSaveFile|string|Katalog, w którym aplikacja przechowuje pliki automatycznego zapisywania.<br /><br /> Wartość domyślna to "$RootFolder$\Profiles\CurrentSettings.vssettings".|  
  
## <a name="package-satellite-dll-settings"></a>Pakiet satelitarnej biblioteki DLL ustawienia  
 W poniższej tabeli przedstawiono wartości, które są zdefiniowane w obszarze [$RootKey$ \Packages\\{*vsPackageGuid*} \SatelliteDll] dla satelitarnej biblioteki DLL każdego pakietu skojarzony, gdzie *vsPackageGuid* jest identyfikatorem GUID skojarzonego pakietu.  
  
|Nazwa|Typ|Wartość|  
|----------|----------|-----------|  
|DllName|string|Nazwa pliku biblioteki dll.<br /><br /> Wartość domyślna to "*Nazwa rozwiązania*ui.dll", gdzie *Nazwa rozwiązania* to nazwa pliku rozwiązania aplikacji.|  
|Ścieżka|string|Katalog, który zawiera satelitarnej biblioteki DLL.<br /><br /> Wartość domyślna to "$PackageFolder$".|  
  
## <a name="package-menu-item-settings"></a>Ustawienia elementu Menu pakietu  
 Klucz rejestru [$RootKey$ \Menus] Określa pliki zasobów interfejsu użytkownika dla aplikacji.  
  
 Wartości pozycji menu mieć postać "{*vsUiPackageGuid*}"=" *resourceId*, *Numerwersji*", gdzie *vsUiPackageGuid* jest identyfikatorem GUID pakiet interfejsu użytkownika aplikacji, *resourceId* jest identyfikator zasobu zasób CTMENU, który zawiera elementy interfejsu użytkownika i *Numerwersji* jest numer wersji wirtualnych dla CTMENU zasób. Aby uzyskać więcej informacji, zobacz [rejestrowanie Interop zestawu programy obsługi poleceń](../extensibility/internals/registering-interop-assembly-command-handlers.md).  
  
 Domyślnie wpis element menu jest tworzony w pliku .pkgdef interfejsu użytkownika pakietu aplikacji.  
  
 Dla każdego pakietu, który zawiera elementy menu i rozproszonym jako część aplikacji należy dodać wpis elementu menu dla pakietu.  
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowywanie programu Isolated Shell](../extensibility/customizing-the-isolated-shell.md)   
 [. Pliki Pkgundef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file.md)