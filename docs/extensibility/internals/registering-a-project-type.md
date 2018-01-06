---
title: Rejestrowanie typ projektu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], new project registry entries
- registry, new project types
- registration, new project types
ms.assetid: dfc0e231-6b4e-447d-9d64-0e66dea3394a
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f60cf3fc8b4db7d33523e4583ab3da4f4596b1af
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="registering-a-project-type"></a>Rejestrowanie typ projektu
Podczas tworzenia nowego typu projektu, należy utworzyć wpisy rejestru, które umożliwiają [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rozpoznaje i pracy z danego typu projektu. Wpisy rejestru są zazwyczaj tworzone przy użyciu pliku skryptu (.rgs) z rejestru.  
  
 W poniższym przykładzie instrukcji z rejestru Podaj domyślnych ścieżek i danych w przypadku, gdy ma to zastosowanie, a następnie tabelę, która zawiera wpisy z rejestru skryptu dla każdej instrukcji. Tabele zawierają wpisy skryptu i dodatkowe informacje na temat oświadczeń.  
  
> [!NOTE]
>  Następujące informacje rejestru jest przeznaczonych do przykład typu i celów wpisów w skryptach rejestru, który będzie można zapisywania zarejestrować danego typu projektu. Rzeczywiste wpisy i ich zastosowań mogą się różnić w zależności od specyficznych wymagań danego typu projektu. Należy Przejrzyj przykłady można znaleźć, który jest bardzo podobny typ projektu, które tworzysz, a następnie przejrzyj skrypt rejestru dla tego przykładu.  
  
 Poniższe przykłady pochodzą z HKEY_CLASSES_ROOT.  
  
## <a name="example"></a>Przykład  
  
```  
\.figp  
   @="FigPrjFile"  
   "Content Type"="text/plain"  
\.figp\ShellNew  
   "NullFile"=""  
\FigPrjFile  
   @="Figure Project File"  
\DefaultIcon  
   @="<Visual Studio SDK installation path>\\9.0VSIntegration\\SomeFolder\\FigPkgs\\FigPrj\\Debug\\FigPrj.dll,-206"  
\shell\open  
   @="&Open in Visual Studio"  
\shell\open\command  
   @="devenv.exe \"%1\""  
```  
  
|Nazwa|Typ|Dane|Opis|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`FigPrjFile`|Nazwa i opis plików typu projektu, które mają .figp rozszerzenia.|  
|`Content Type`|REG_SZ|`Text/plain`|Typ zawartości dla plików projektu.|  
|`NullFile`|REG_SZ|`Null`||  
|`@`|REG_SZ|`%MODULE%,-206`|Ikona domyślna używana dla projektu tego typu. Instrukcja % modułu % zostanie ukończona w rejestrze w domyślnej lokalizacji projektu typu DLL.|  
|`@`|REG_SZ|`&Open in Visual Studio`|Domyślna aplikacja, w którym zostanie otwarty ten typ projektu.|  
|`@`|REG_SZ|`devenv.exe "%1"`|Polecenie domyślne, które będą uruchamiane po otwarciu projektu tego typu.|  
  
 Poniższe przykłady z HKEY_LOCAL_MACHINE i znajdują się w rejestrze w kluczu [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\99.0Exp\Packages].  
  
## <a name="example"></a>Przykład  
  
```  
\{ACEF4EB2-57CF-11D2-96F4-000000000000} (The CLSID for the VSPackage)  
   @="FigPrj Project Package"  
   "InprocServer32"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\                      Debug\\FigPrj.dll"  
   "CompanyName"="Microsoft"  
   "ProductName"="Figure Project Sample"  
   "ProductVersion"="9.0"  
   "MinEdition"="professional"  
   "ID"=dword:00000001  
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\SatelliteDLL  
   "DllName"="FigPrjUI.dll"  
   "Path"="9.0<Visual Studio SDK installation path>\\VSIntegration\\Archive\\FigPkgs\\FigPrj\\Debug\\"  
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\Automation  
   "FigProjects"=""  
\{ACEF4EB2-57CF-11D2-96F4-000000000000}\AutomationEvents  
   "FigProjectsEvents"="Returns the FigProjectsEvents Object"  
   "FigProjectItemsEvents"="Returns the FigProjectItemsEvents Object"  
```  
  
|Nazwa|Typ|Dane|Opis|  
|----------|----------|----------|-----------------|  
|`@`(Ustawienie domyślne)|REG_SZ|`FigPrj Project VSPackage`|Nazwa Lokalizowalny to zarejestrowanej pakiet VSPackage (typ projektu).|  
|`InprocServer32`|REG_SZ|`%MODULE%`|Ścieżka do projektu typu DLL. IDE ładuje tę bibliotekę DLL i przekazuje CLSID pakiet VSPackage do `DllGetClassObject` uzyskanie <xref:Microsoft.VisualStudio.OLE.Interop.IClassFactory> do skonstruowania <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> obiektu.|  
|`CompanyName`|REG_SZ|`Microsoft`|Nazwa firmy, która opracowała typu projektu.|  
|`ProductName`|REG_SZ|`Figure Project Sample`|Nazwa typu projektu.|  
|`ProductVersion`|REG_SZ|`9.0`|Zwolnij numer wersji tego typu projektu.|  
|`MinEdition`|REG_SZ|`professional`|Edycja pakiet VSPackage, jest zarejestrowany.|  
|`ID`|REG_DWORD|`%IDS_PACKAGE_LOAD_KEY%`|Pakiet załadować kluczy dla projektu pakiet VSPackage. Klucz sprawdzania poprawności po załadowaniu projektu po uruchomieniu środowiska.|  
|`DllName`|REG_SZ|`%RESOURCE_DLL%`|Nazwa pliku satelitarnej biblioteki DLL zawierającej zlokalizowane zasoby dla typu projektu.|  
|`Path`|REG_SZ|`%RESOURCE_PATH%`|Ścieżka satelitarnej biblioteki DLL.|  
|`FigProjectsEvents`|REG_SZ|Zobacz instrukcji dla wartości.|Określa ciąg tekstowy zwrócony dla tego zdarzenia automatyzacji.|  
|`FigProjectItemsEvents`|REG_SZ|Zobacz instrukcji dla wartości.|Określa ciąg tekstowy zwrócony dla tego zdarzenia automatyzacji.|  
  
 Poniższe przykłady znajdują się w rejestrze w kluczu [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].  
  
## <a name="example"></a>Przykład  
  
```  
\{C061DB26-5833-11D2-96F5-000000000000} (The CLSID for projects of this type)  
   @="FigPrj Project"  
   "DisplayName"="#2"  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "ProjectTemplatesDir"="C:\\Program Files\\VSIP 9.0\\EnvSDK\\FigPkgs\\                           FigPrj\\FigPrjProjects"  
   "ItemTemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                           FigPrjProjectItems"  
   "DisplayProjectFileExtensions"="#3"  
   "PossibleProjectExtensions"="figp"  
   "DefaultProjectExtension"=".figp"  
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\1       (Folder 1 contains settings for Open Files filters.)  
   @="#4"  
   "CommonOpenFilesFilter"=dword:00000000  
   "CommonFindFilesFilter"=dword:00000000  
   "NotAddExistingItemFilter"=dword:00000000  
   "FindInFilesFilter"=dword:00000000  
   "NotOpenFileFilter"=dword:00000000  
   "SortPriority"=dword:000003e8  
\{C061DB26-5833-11D2-96F5-000000000000}\Filters\2  
      (Folder 2 contains settings for Find in Files filters.)  
   @="#5"  
   "CommonOpenFilesFilter"=dword:00000000  
   "CommonFindFilesFilter"=dword:00000000  
   "NotAddExistingItemFilter"=dword:00000001  
   "FindInFilesFilter"=dword:00000001  
   "NotOpenFileFilter"=dword:00000000  
   "SortPriority"=dword:000003e8  
\{C061DB26-5833-11D2-96F5-000000000000}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (Second GUID indicates the registered project type for the Add Items templates.)  
   @="#6"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"  
   "SortPriority"=dword:00000064  
```  
  
|Nazwa|Typ|Dane|Opis|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`FigPrj Project`|Domyślna nazwa projektów tego typu.|  
|`DisplayName`|REG_SZ|`#%IDS_PROJECT_TYPE%`|Identyfikator zasobu nazwy mają zostać pobrane z satelitarnej biblioteki DLL zarejestrowany pod pakietów.|  
|`Package`|REG_SZ|`%CLSID_Package%`|Identyfikator klasy pakiet VSPackage zarejestrowany pod pakietów.|  
|`ProjectTemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Domyślna ścieżka plików szablonów projektu. Są to pliki, wyświetlane przez szablon nowego projektu.|  
|`ItemTemplatesDir`|REG_SZ|`%TEMPLATE_PATH% \FigPrjProjectItems`|Domyślna ścieżka plików szablonu elementu projektu. Są to pliki, wyświetlane przez szablon Dodaj nowy element.|  
|`DisplayProjectFileExtensions`|REG_SZ|`#%IDS_DISPLAY_PROJ_FILE_EXT%`|Włącza IDE zaimplementować **Otwórz** okno dialogowe.|  
|`PossibleProjectExtensions`|REG_SZ|`figp`|Używany przez IDE w celu określenia, czy projekt otwierany jest obsługiwany przez ten typ projektu (fabrykę projektów). Format dla więcej niż jednego wpisu znajduje się lista rozdzielanych średnikami. Na przykład "vdproj; vdp".|  
|`DefaultProjectExtension`|REG_SZ|`.figp`|Używane przez IDE jako domyślne rozszerzenie nazwy pliku dla operacji Zapisz jako.|  
|`Filter Settings`|REG_DWORD|Różne, zobacz instrukcje i komentarze w poniższej tabeli.|Te ustawienia są używane do definiowania różnych filtrów do wyświetlania plików w oknach dialogowych interfejsu użytkownika.|  
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Identyfikator zasobu dla szablonów Dodaj element.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Ścieżka projektu elementy wyświetlane w oknie dialogowym **Dodaj nowy element** szablonu.|  
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Określa porządek sortowania, w węźle drzewa plików wyświetlanych w **Dodaj nowy element** okno dialogowe.|  
  
 W poniższej tabeli przedstawiono opcje filtry dostępne w poprzednich segment kodu.  
  
|Opcja filtra|Opis|  
|-------------------|-----------------|  
|`CommonFindFilesFilter`|Wskazuje, że filtr jest jednym z typowych filtrów w **Znajdź w plikach** okno dialogowe. Filtry wspólne są wyświetlane na liście filtrów przed filtrami nieoznaczona jako wspólne.|  
|`CommonOpenFilesFilter`|Wskazuje, że filtr jest jednym z typowych filtrów w **Otwórz plik** okno dialogowe. Filtry wspólne są wyświetlane na liście filtrów przed filtrami nieoznaczona jako wspólne.|  
|`FindInFilesFilter`|Wskazuje, że filtr będzie jeden z filtrów w **Znajdź w plikach** okna dialogowego polu i zostaną wyświetlone po wspólnej filtrów.|  
|`NotOpenFileFilter`|Wskazuje, że filtr nie można użyć w **Otwórz plik** okno dialogowe.|  
|`NotAddExistingItemFilter`|Wskazuje, czy filtr nie będzie używany w dodawania **istniejący element** okno dialogowe.|  
  
 Domyślnie, jeśli filtr nie ma jedną lub więcej te flagi zestawu, filtr jest używane w **Dodaj istniejący element** okno dialogowe i **Otwórz plik** okno dialogowe po typowe filtry są widoczne. Filtr nie jest używany w **Znajdź w plikach** okno dialogowe.  
  
 Poniższe przykłady znajdują się w rejestrze w kluczu [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].  
  
## <a name="example"></a>Przykład  
  
```  
{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4} (The CLSID for Enterprise Projects)  
\{FE3BBBB6-72D5-11d2-9ACE-00C04F79A2A4}\AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000}\1 (CLSID for projects of this type)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|Nazwa|Typ|Dane|Opis|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`#%IDS_NEWPROJ_ TEMPLATES_ENTRY%`|Identyfikator zasobu dla szablonów nowy projekt.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Domyślna ścieżka dla projektów typu projektu w zarejestrowany.|  
|`SortPriority`|REG_DWORD|`41 (x29)`|Ustawia sortowania kolejności projektów wyświetlane w oknie dialogowym Kreatora nowych projektów.|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|wartość 0 wskazuje, że projekty tego typu są wyświetlane tylko w oknie dialogowym Nowy projekt.|  
  
 Poniższe przykłady znajdują się w rejestrze w kluczu [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Projects].  
  
## <a name="example"></a>Przykład  
  
```  
\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3} (CLSID for Miscellaneous Files projects)  
   @="Miscellaneous Files Project"  
\AddItemTemplates\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1  
                                 (CLSID for Figures Project projects)  
   @="#6"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\                    FigPrjProjectItems"  
   "SortPriority"=dword:00000064  
```  
  
|Nazwa|Typ|Dane|Opis|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|Brak|Wartość domyślna, który wskazuje, że następujące wpisy dla pozycji projektów różne pliki.|  
|`@`|REG_SZ|`#%IDS_ADDITEM_TEMPLATES_ENTRY%`|Wartość Identyfikatora zasobu pliki szablonów Dodaj nowe elementy.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjectItems`|Domyślna ścieżka elementów, które będą wyświetlane w **Dodaj nowy element** okno dialogowe.|  
|`SortPriority`|REG_DWORD|`100 (vcprx64)`|Określa porządek sortowania dla wyświetlana w węźle drzewa **Dodaj nowy element** okno dialogowe.|  
  
 Poniższy przykład znajduje się w rejestrze w kluczu [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\Menus].  
  
## <a name="example"></a>Przykład  
  
```  
"{ACEF4EB2-57CF-11D2-96F4-000000000000}"=",1000,1"  
```  
  
 Pozycja menu wskazuje IDE zasobów do pobierania informacji menu. W przypadku tych danych została scalona menu bazy danych, ten sam klucz zostanie dodany w sekcji MenusMerged rejestru. Pakiet VSPackage niczego w sekcji MenusMerged nie należy modyfikować bezpośrednio. W polu danych w poniższej tabeli istnieją trzy przecinkami — oddzielone pola. Pierwsze pole określa pełną ścieżkę pliku zasobu menu:  
  
-   W przypadku pominięcia pierwsze pole menu zasobów są ładowane z satelitarnej biblioteki DLL identyfikowany przez identyfikator GUID pakietu VSPackage.  
  
 Drugie pole identyfikuje menu identyfikator zasobu typu CTMENU:  
  
-   Jeśli jest określony identyfikator zasobu i ścieżka pliku jest dostarczana przez pierwszy parametr, zasobów menu są ładowane z pełną ścieżką do pliku.  
  
-   Jeżeli identyfikator zasobu, ale nie jest ścieżka do pliku, zasobów menu są ładowane z satelitarnej biblioteki DLL.  
  
-   Jeśli podano pełną ścieżkę pliku i pominięcia identyfikator zasobu, załadowania pliku oczekuje pliku CTO.  
  
 Ostatnie pole określa numer wersji dla zasobu CTMENU. Menu można scalać ponownie, zmieniając numer wersji.  
  
|Nazwa|Typ|Dane|Opis|  
|----------|----------|----------|-----------------|  
|% CLSID_Package %|REG_SZ|`,1000,1`|Zasób, który można pobrać informacji o menu.|  
  
 Poniższe przykłady znajdują się w rejestrze w kluczu [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\NewProjectTemplates].  
  
```  
\TemplateDirs\{ACEF4EB2-57CF-11D2-96F4-000000000000}\1                (CLSID for Figures Project projects)  
   @="#7"  
   "TemplatesDir"="<Visual Studio SDK installation path>\\VSIntegration\\Archive9.0\\FigPkgs\\FigPrj\\FigPrjProjects"  
   "SortPriority"=dword:00000029  
   "NewProjectDialogOnly"=dword:00000000  
```  
  
|Nazwa|Typ|Dane|Opis|  
|----------|----------|----------|-----------------|  
|`@`|REG_SZ|`#%IDS_NEWPROJ_TEMPLATES_ENTRY%`|Wartość Identyfikatora zasobu dla szablonów rysunki nowy projekt.|  
|`TemplatesDir`|REG_SZ|`%TEMPLATE_PATH%\FigPrjProjects`|Domyślna ścieżka katalogu nowych projektów. Elementy w tym katalogu będą wyświetlane w **Kreatora nowego projektu** okno dialogowe.|  
|`SortPriority`|REG_DWORD|`41 (x29)`|Określa kolejność wyświetlania projektów w węźle drzewa **nowy projekt** okno dialogowe.|  
|`NewProjectDialogOnly`|REG_DWORD|`0`|0 wskazuje, że projekty tego typu są wyświetlane tylko w **nowy projekt** okno dialogowe.|  
  
 Poniższy przykład znajduje się w rejestrze w kluczu [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0Exp\InstalledProducts].  
  
```  
\FiguresProductSample  
   "Package"="{ACEF4EB2-57CF-11D2-96F4-000000000000}"  
   "UseInterface"=dword:00000001  
```  
  
|Nazwa|Typ|Dane|Opis|  
|----------|----------|----------|-----------------|  
|`Package`|REG_SZ|`%CLSID_Package%`|Identyfikator klasy zarejestrowanych pakiet VSPackage.|  
|`UseInterface`|REG_DWORD|`1`|wartość 1 oznacza, że interfejs użytkownika będzie służyć do interakcji z tego projektu. 0 wskazuje, że nie interfejs użytkownika.|  
  
 Pliki the.vsz, określające nowe typy projektu często zawierają wpis RELATIVE_PATH. Ta ścieżka jest określana względem ścieżki określonej w pozycji \ProductDir typu projektu w następującym kluczu Instalatora:  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup  
  
 Na przykład szablony projektów Enterprise Frameworks Dodaj następujące wpisy rejestru:  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\7.0Exp\Setup\EF\ProductDir = C:\Program Files\Microsoft Visual Studio\EnterpriseFrameworks\  
  
 Oznacza to, że Jeśli dołączysz PROJECT_TYPE = EF wpis w pliku .vsz, znalezione środowiska użytkownika .vsz pliki w katalogu ProductDir określony wcześniej.  
  
## <a name="see-also"></a>Zobacz też  
 [Lista kontrolna: Tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Elementy modelu projektu](../../extensibility/internals/elements-of-a-project-model.md)   
 [Tworzenie wystąpień projektów przy użyciu fabryk projektów](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)