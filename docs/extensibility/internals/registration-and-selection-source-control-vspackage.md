---
title: "Rejestracja i wybór (VSPackage kontroli źródła) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
caps.latest.revision: "34"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 118f715e71f610d4e9dc2589767f6fb54ab4e814
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="registration-and-selection-source-control-vspackage"></a>Rejestracja i wybór (VSPackage kontroli źródła)
Pakiet VSPackage musi być zarejestrowana do udostępnienia go do kontroli źródła [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Jeśli kontroli źródła więcej niż jeden pakiet VSPackage zostanie zarejestrowany, użytkownik może wybrać których pakiet VSPackage załadować w odpowiednim czasie. Zobacz [VSPackages](../../extensibility/internals/vspackages.md) więcej szczegółów na pakiety VSPackage i jak można je zarejestrować.  
  
## <a name="registering-a-source-control-package"></a>Rejestrowanie pakietu kontroli źródła  
 Pakiet kontroli źródła jest zarejestrowany, aby [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] środowiska można znaleźć go i zapytań obsługiwanych funkcji. Jest to zgodne z schemat opóźnienia ładowania, w której jest tworzone wystąpienie pakietu tylko wtedy, gdy jego funkcji lub polecenia wymagane są lub jawnie żądają.  
  
 VSPackages umieść informacje w kluczu rejestru określonej wersji, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*X.Y*, gdzie *X* jest numer wersji głównej i *Y* jest podrzędny numer wersji. Takie rozwiązanie pozwala, aby możliwa była instalacja side-by-side wielu wersji [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Interfejsu użytkownika (UI) obsługuje wybór spośród wielu zainstalowanych źródła formantu wtyczek (przez pakiet karty kontroli źródła) oraz VSPackages do kontroli źródła. Może istnieć tylko jeden wtyczka do kontroli źródła active lub pakiet VSPackage naraz. Jednak zgodnie z poniższym opisem IDE pozwala na przełączanie się między plug-in kontroli źródła i VSPackages poprzez automatyczne rozwiązanie mechanizmu opartego na zamianę pakietu. Brak niektóre wymagania przez pakiet VSPackage kontroli źródła, aby włączyć ten mechanizm wyboru.  
  
### <a name="registry-entries"></a>Wpisy rejestru  
 Pakiet kontroli źródła wymaga trzech prywatnych identyfikatorów GUID:  
  
-   Identyfikator GUID pakietu: To jest główny identyfikator GUID pakietu, który zawiera implementację kontroli źródła (nazywane ID_Package w tej sekcji).  
  
-   Kontroli źródła identyfikator GUID: To jest identyfikator GUID dla kontroli źródła pakiet VSPackage używane do rejestrowania przy szkielet kontroli źródła programu Visual Studio i jest również używane jako kontekst interfejsu użytkownika poleceń identyfikatora GUID. Identyfikator GUID usługi kontroli źródła jest zarejestrowany pod kontrolą źródła identyfikatora GUID. W tym przykładzie kontroli źródła identyfikatora GUID jest nazywany ID_SccProvider.  
  
-   Identyfikator GUID usługi kontroli źródła: to jest usługa prywatnej identyfikator GUID używany przez program Visual Studio (nazywane SID_SccPkgService w tej sekcji). Oprócz tego pakiet kontroli źródła musi definiować innych identyfikatorów GUID dla VSPackages, narzędzia windows itd.  
  
 Następujące wpisy rejestru muszą być przekazywane kontroli źródła pakiet VSPackage:  
  
|Nazwa klucza|Wpisy|  
|--------------|-------------|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\`|(ustawienie domyślne) = rg_sz: {ID_SccProvider}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\`|(ustawienie domyślne) = rg_sz:\<przyjazną nazwę pakietu ><br /><br /> Usługa = rg_sz: {SID_SccPkgService}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\`|(ustawienie domyślne) = rg_sz: #\<identyfikator zlokalizowana nazwa zasobu ><br /><br /> Pakiet = rg_sz: {ID_Package}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (Należy pamiętać, że nazwa klucza `SourceCodeControl`, jest już używany przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i nie jest dostępny jako rozwiązaniem dla \<PackageName >.)|(ustawienie domyślne) = rg_sz: {ID_Package}|  
  
## <a name="selecting-a-source-control-package"></a>Wybieranie pakietu kontroli źródła  
 Kilka na podstawie interfejsu API dodatku typu Plug-in kontroli źródła wtyczek i VSPackages można jednocześnie zarejestrować kontroli źródła. Proces wybierania wtyczka do kontroli źródła lub pakiet VSPackage upewnij się, że [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ładuje dodatku typu plug-in lub pakiet VSPackage w odpowiednim czasie i może odroczyć ładowania składników niepotrzebne, dopóki nie są one wymagane. Ponadto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] należy usunąć wszystkie interfejsu użytkownika z innych VSPackages nieaktywny, w tym elementów menu, okna dialogowe i paski narzędzi i wyświetlać interfejsu użytkownika dla active pakiet VSPackage.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ładuje kontroli źródła pakiet VSPackage, gdy jest wykonywane jeden z następujących czynności:  
  
-   Rozwiązanie jest otwarte (Jeśli rozwiązanie podlega kontroli źródła).  
  
     Po otwarciu rozwiązania lub projektu pod kontrolą źródła IDE powoduje, że pakiet VSPackage, który został wybrany do rozwiązania do załadowania kontroli źródła.  
  
-   Dowolne polecenia menu kontroli źródła pakiet VSPackage są wykonywane.  
  
 Kontroli źródła, pakiet VSPackage powinny zostać załadowane wszystkie składniki potrzebne tylko wtedy, gdy w rzeczywistości ma być używane (w przeciwnym razie nazywane opóźnionego ładowania).  
  
### <a name="automatic-solution-based-vspackage-swapping"></a>Automatyczne rozwiązanie na podstawie pakiet VSPackage wymiany  
 Można ręcznie wymienić kontroli źródła VSPackages za pośrednictwem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **opcje** okno dialogowe, w obszarze **kontroli źródła** kategorii. Automatyczne rozwiązanie pakiet wymiany oznacza, że pakiet kontroli źródła, który wyznaczono dla danego rozwiązania jest automatycznie ustawiana aktywny po otwarciu rozwiązania. Każdy pakiet kontroli źródła należy zaimplementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Przełączanie między zarówno obsługuje źródła wtyczek formantu (Implementowanie interfejsu API dodatku typu Plug-in kontroli źródła) i VSPackages kontroli źródła.  
  
 Aby przełączyć się do żadnych API dodatku typu Plug-in kontroli źródła na podstawie jest używany pakiet karty kontroli źródła wtyczek. Musi mieć ustawioną proces przełączanie do pośredniego pakiet karty kontroli źródła i określania, które wtyczka do kontroli źródła, aktywne lub nieaktywne jest niewidoczny dla użytkownika. Pakiet karty jest zawsze aktywna, gdy wtyczkę kontroli źródła jest aktywny. Przełączanie między dwiema kwotami dodatków plug-in kontroli źródła można po prostu ładowanie i zwalnianie biblioteki DLL dodatku. Jednak przełączanie do kontroli źródła pakiet VSPackage, wymaga interakcji z IDE załadować odpowiedni pakiet VSPackage.  
  
 Kontroli źródła pakiet VSPackage jest wywoływane, gdy żadne rozwiązanie jest otwarte, a klucz rejestru pakiet VSPackage znajduje się w pliku rozwiązania. Po otwarciu rozwiązania [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] znajduje wartość rejestru i ładuje kontroli źródła odpowiedni pakiet VSPackage. Wszystkie kontroli źródła VSPackages musi mieć wpisy rejestru opisany powyżej. Rozwiązania, które jest pod kontrolą źródła jest oznaczona jako skojarzona z określonego źródła formantu pakiet VSPackage. Formant musi implementować VSPackages źródła <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> Aby włączyć automatyczne oparte na rozwiązaniu pakiet VSPackage wymiany.  
  
### <a name="visual-studio-ui-for-package-selection-and-switching"></a>Visual Studio interfejsu użytkownika dla wybór pakietów i przełączania  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]udostępnia interfejs dla kontroli źródła pakiet VSPackage i wyboru wtyczek w **opcje** okno dialogowe, w obszarze **kontroli źródła** kategorii. Umożliwia użytkownikowi wybranie wtyczkę kontroli źródła active lub pakiet VSPackage. Lista rozwijalna zawiera:  
  
-   Wszystkie zainstalowane pakiety kontroli źródła  
  
-   Wszystkie zainstalowane plug-in kontroli źródła  
  
-   Opcję "Brak", która wyłącza kontroli kodu źródłowego  
  
 Widoczny jest tylko interfejs użytkownika wyboru kontroli źródła aktywne. Wybór pakiet VSPackage ukrycie interfejsu użytkownika dla poprzedniego pakiet VSPackage i przedstawia nowego interfejsu użytkownika. Aktywne pakiet VSPackage wybranego na poszczególnych użytkowników. Jeśli użytkownik ma wiele kopii [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Otwórz współbieżnie, każda z nich mogą za pomocą różnych active pakiet VSPackage. Jeśli wielu użytkowników jest zalogowany na tym samym komputerze, każdy użytkownik może mieć różne wystąpienia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Otwórz każdy z różnych active pakiet VSPackage. Gdy wiele wystąpień [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] są zamknięte przez użytkownika, kontroli źródła pakiet VSPackage, który był aktywny dla ostatniego Otwórz rozwiązanie staje się kontroli źródła domyślny pakiet VSPackage, należy ustawić aktywne po ponownym uruchomieniu komputera.  
  
 W przeciwieństwie do poprzednich wersji [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], ponowne uruchomienie IDE nie jest już jedynym sposobem, aby przełączyć się do kontroli źródła VSPackages. Wybór pakiet VSPackage odbywa się automatycznie. Przełączanie pakietów wymaga uprawnień użytkownika systemu Windows (nie Administrator lub użytkownik zaawansowany).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>   
 [Funkcje](../../extensibility/internals/source-control-vspackage-features.md)   
 [Tworzenie wtyczki kontroli źródła](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [VSPackages](../../extensibility/internals/vspackages.md)