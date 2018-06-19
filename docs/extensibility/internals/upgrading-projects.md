---
title: Uaktualnianie projektów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cb64d71a50cb59a3c981dd87695bbb685f793761
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31148249"
---
# <a name="upgrading-projects"></a>Uaktualnianie projektów
Zmiany modelu projektu z jednej wersji [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] do następnego może wymagać projektów i rozwiązań uaktualnienia, dzięki czemu mogą być uruchamiane na nowszą wersję. [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Udostępnia interfejsy, które mogą służyć do implementowania obsługi uaktualniania do własnych projektów.  
  
## <a name="upgrade-strategies"></a>Strategie uaktualniania  
 Do obsługi uaktualnienia, implementacji systemu projektu należy zdefiniować i zaimplementować strategię uaktualnienia. Umożliwiającym określenie strategii, można obsługiwać side-by-side (SxS) w kopii zapasowej i kopii zapasowej.  
  
-   SxS kopii zapasowej oznacza, że projekt kopiuje tylko te pliki, które wymagają uaktualnienia w miejscu, dodawanie sufiks nazwy odpowiedniego pliku, na przykład ".old".  
  
-   Kopii zapasowej oznacza, że projekt kopiuje wszystkie elementy projektu do lokalizacji kopii zapasowej dostarczane przez użytkownika. Następnie uaktualnienia odpowiednie pliki w oryginalnej lokalizacji projektu.  
  
## <a name="how-upgrade-works"></a>Jak uaktualnić działania  
 Gdy rozwiązanie utworzony w starszej wersji programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jest otwarty w nowszej wersji, kontroli IDE plik rozwiązania Aby ustalić, jeśli musi zostać uaktualniony. Jeśli uaktualnianie jest wymagana, **Kreatora uaktualniania** jest uruchamiane automatycznie przeprowadzenie użytkownika przez proces uaktualniania.  
  
 Rozwiązanie wymaga uaktualnienia, wysyła zapytanie każdej fabryki projektu dla jego strategii uaktualniania. Strategia określa, czy fabryka projektu obsługuje kopii zapasowej lub kopii zapasowej SxS. Informacje są wysyłane do **Kreatora uaktualniania**, które zbiera informacje wymagane do tworzenia kopii zapasowej i wyświetla użytkownikowi odpowiednie opcje.  
  
### <a name="multi-project-solutions"></a>Rozwiązania dotyczące wielu projektów  
 Jeśli rozwiązanie zawiera wiele projektów i strategii uaktualnienia są różne, np. gdy projekt C++, który obsługuje tylko SxS kopii zapasowej i projektu sieci Web, które obsługują tylko kopii zapasowej, fabryki projektu muszą uzgodnić strategii uaktualniania.  
  
 Rozwiązanie wysyła zapytanie do każdego projektu fabryki dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>. Następnie wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> Aby sprawdzić, czy pliki projektu globalnego wymagają uaktualnienia i ustalić obsługiwanych strategii uaktualnienia. **Kreatora uaktualniania** następnie jest wywoływana.  
  
 Po podaniu kreatora <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> jest wywoływane dla każdego fabrykę projektów do rzeczywistego uaktualnienia. W celu ułatwienia tworzenia kopii zapasowej, podaj metody IVsProjectUpgradeViaFactory <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> usługi do logowania się szczegóły procesu uaktualniania. Nie można buforować tej usługi.  
  
 Po zaktualizowaniu wszystkich odpowiednich plików globalnych, każdej fabryki projektu można wybrać wystąpienia projektu. Implementacja projektu musi obsługiwać <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Wywoływana jest metoda następnie uaktualnić wszystkie elementy odpowiedni projekt.  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> — Metoda nie dostarcza usługi SVsUpgradeLogger. Tę usługę można uzyskać przez wywołanie metody <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>.  
  
## <a name="best-practices"></a>Najlepsze praktyki  
 Użyj <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> usługi Sprawdź, czy można edytować pliku przed rozpoczęciem edycji i można go zapisać przed zapisaniem. Dzięki temu kopii zapasowej i uaktualniania implementacje obsługują pliki projektu pod kontrolą źródła, pliki z niewystarczające uprawnienia i tak dalej.  
  
 Użyj <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> usługi wszystkich fazach kopii zapasowej, a następnie uaktualnić do przekazywania informacji o powodzeniu lub niepowodzeniu procesu uaktualniania.  
  
 Aby uzyskać więcej informacji na temat tworzenia kopii zapasowych i uaktualnianie projektów Zobacz komentarze dla IVsProjectUpgrade w vsshell2.idl.  
  
## <a name="upgrading-custom-projects"></a> Uaktualnianie projektów niestandardowych
Jeśli zmienisz informacje utrwalone w pliku projektu między różnymi wersjami programu Visual Studio produktu, a następnie wymaganych do obsługi, uaktualnianie pliku projektu ze starego do nowej wersji. Do obsługi uaktualniania umożliwiający uczestniczyć w **Kreator konwersji Visual Studio**, wdrożenie <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfejsu. Ten interfejs zawiera jedynym mechanizmem uaktualniania kopiowania. W przypadku uaktualniania projektu odbywa się jako część rozwiązania otwiera. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> Interfejs jest implementowany przez fabrykę projektów lub musi być co najmniej częściowa z fabryki projektu.  
  
 Stary mechanizm, który używa <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interfejsu nadal jest obsługiwany, ale koncepcyjnie uaktualnia system projektu jako część otwarciu projektu. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> Interfejsu w związku z tym jest wywoływana przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] środowiska, nawet jeśli <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfejs o nazwie lub zaimplementowana. Takie podejście umożliwia użycie <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> do wykonania kopii tylko części uaktualniania projektu i delegowanie reszty zadań do wykonania w miejscu (prawdopodobnie w nowej lokalizacji) przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> interfejsu.  
  
 Dla implementacji próbki <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>, zobacz [przykłady VSSDK](http://aka.ms/vs2015sdksamples).  
  
 Następujące scenariusze wyniknąć z uaktualnienia projektu:  
  
-   Jeśli plik jest nowszy format niż projekt może obsługiwać, aplikacja musi zwracać komunikat o błędzie informujący, to. Przy założeniu, że starszej wersji produktu zawiera kod, aby sprawdzić, czy wersja.  
  
-   Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> w określono flagę <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metody uaktualniania będzie wykonywane jest uaktualnienie w miejscu przed otwarciem projektu.  
  
-   Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> w określono flagę <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metody uaktualniania jest zaimplementowany jako uaktualnienia kopiowania.  
  
-   Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> w określono flagę <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> wywołań, a następnie użytkownik odebrał monit przez środowisko do uaktualnienia pliku projektu jako uaktualnienia w miejscu po otwarciu projektu. Na przykład środowiska monituje użytkownika o uaktualnienie, gdy użytkownik otwiera starszej wersji rozwiązania.  
  
-   Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> flaga nie jest określona w <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> wywołać, a następnie musi monituje użytkownika o zaktualizować pliku projektu.  
  
     Poniżej znajduje się przykładowy uaktualnienia komunikat Monituj:  
  
     "Projekt"%1"został utworzony przy użyciu starszej wersji programu Visual Studio. Jeśli otworzysz go za pomocą tej wersji programu Visual Studio, nie można go otworzyć ze starszymi wersjami programu Visual Studio. Czy chcesz kontynuować i otworzyć ten projekt?"  
  
### <a name="to-implement-ivsprojectupgradeviafactory"></a>Aby zaimplementować IVsProjectUpgradeViaFactory  
  
1.  Implementuje metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfejsu, w szczególności <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> metody w implementacji projektu fabryki lub implementacje można wywołać za pomocą implementacji fabryki projektu.  
  
2.  Jeśli chcesz wykonać uaktualnienie w miejscu jako część rozwiązania, otwieranie, podaj flagę <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> jako `VSPUVF_FLAGS` parametru w Twojej <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementacji.  
  
3.  Jeśli chcesz wykonać uaktualnienie w miejscu jako część rozwiązania, otwieranie, podaj flagę <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> jako `VSPUVF_FLAGS` parametru w Twojej <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> implementacji.  
  
4.  Oba kroki 2 i 3, rzeczywisty plik uaktualnienia czynności przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>, można zaimplementować zgodnie z opisem w temacie "wdrażania `IVsProjectUpgade`" sekcji poniżej lub możesz delegować uaktualnienia rzeczywistego pliku do <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
5.  Użyj metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> publikowania uaktualnienia powiązane wiadomości dla użytkownika przy użyciu Kreatora migracji usługi Visual Studio.  
  
6.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> Interfejs jest używany do wykonania dowolnego rodzaju uaktualnienia pliku, który musi zostać przeprowadzona w ramach uaktualnienia projektu. Ten interfejs nie jest wywoływany z <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>, ale jest dostarczany jako mechanizm uaktualnienia plików, które są częścią system projektu, ale system projektu może nie być bezpośrednio uwagę. Na przykład tej sytuacji mogą wystąpić, jeśli kompilator powiązanych plików oraz właściwości nie są obsługiwane przez sam zespół deweloperów, obsługująca reszty system projektu.  
  
### <a name="ivsprojectupgrade-implementation"></a>Implementacja IVsProjectUpgrade  
 Jeśli system projektu implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> , nie mogą uczestniczyć w **Kreator konwersji Visual Studio**. Jednak nawet w przypadku implementowania <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> interfejsu, można nadal delegować uaktualnienia pliku do <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementacji.  
  
#### <a name="to-implement-ivsprojectupgrade"></a>Aby zaimplementować IVsProjectUpgrade  
  
1.  Gdy użytkownik próbuje otworzyć projekt, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> metoda jest wywoływana przez środowisko po otwarciu i przed innymi użytkownika można podjąć akcję w projekcie. Jeśli użytkownik ma już został poproszony o Uaktualnij rozwiązanie, a następnie <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> przekazano wartość flagi `grfUpgradeFlags` parametru. Jeśli użytkownik otwiera projektu bezpośrednio, takich jak przy użyciu **Dodaj istniejący projekt** polecenia, a następnie <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> flaga nie zostanie przekazany i projekt wymaga monit, aby uaktualnić.  
  
2.  W odpowiedzi na <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> wywołanie, musi ocenić projektu, czy plik projektu jest uaktualniany. Jeśli projekt nie jest konieczne uaktualnienie typu projektu do nowej wersji, a następnie po prostu może zwrócić <xref:Microsoft.VisualStudio.VSConstants.S_OK> flagi.  
  
3.  Jeśli projekt wymaga uaktualnienia typ projektu do nowej wersji, a następnie musi ustalić, czy plik projektu może być modyfikowana przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> — metoda i przekazywanie wartości <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> dla `rgfQueryEdit` parametru. Następnie projektu należy wykonać następujące czynności:  
  
    -   Jeśli `VSQueryEditResult` wartość zwracana w `pfEditCanceled` parametr jest <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>, a następnie uaktualnienia można kontynuować, ponieważ mogą być zapisywane w pliku projektu.  
  
    -   Jeśli `VSQueryEditResult` wartość zwracana w `pfEditCanceled` parametr jest <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> i `VSQueryEditResult` ma wartość <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bitu, następnie <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> musi zwracać błąd, ponieważ użytkownicy powinno rozwiązać uprawnienia wystawić samodzielnie. Projekt, następnie należy wykonać następujące czynności:  
  
         Raport o błędzie dla użytkownika, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> i zwracać <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> kodu błędu <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>.  
  
    -   Jeśli `VSQueryEditResult` wartość jest <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> i `VSQueryEditResultFlags` ma wartość <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> bitu, a następnie plik projektu powinien zostać wyewidencjonowany przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>,...).  
  
4.  Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> wywołania w pliku projektu powoduje, że plik do wyewidencjonowania najnowszą wersję można pobrać, a następnie zwalnianie i ponownie załadować projektu. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> Metoda jest wywoływana ponownie po utworzeniu wystąpienia innego projektu. W tym drugie wywołanie pliku projektu mogą być zapisywane na dysku; Zaleca się, że projekt zapisać kopię pliku projektu w poprzednim formacie z. STARE rozszerzenie, zmiany jego niezbędne uaktualnienia i Zapisz plik projektu do nowego formatu. Ponownie, jeśli dowolną część proces uaktualniania zakończy się niepowodzeniem, metoda musi wskazywać błąd zwracając <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>. Powoduje to, że projekt, aby zostać zwolniony w Eksploratorze rozwiązań.  
  
     Ważne jest, aby zrozumieć, Zakończ proces, który występuje w środowisku, w przypadku, w którym można wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> — metoda (wartość ReportOnly określenia) zwraca <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> i <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> flagi.  
  
5.  Użytkownik próbuje otworzyć pliku projektu.  
  
6.  Wywołania środowiska użytkownika <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementacji.  
  
7.  Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> zwraca `true`, a następnie wywołania środowiska użytkownika <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> implementacji.  
  
8.  Wywołania środowiska użytkownika <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> implementacji do otwierania pliku i zainicjowania obiektu projektu, na przykład Project1.  
  
9. Wywołania środowiska użytkownika `IVsProjectUpgrade::UpgradeProject` implementacji, aby określić, czy plik projektu musi zostać uaktualniony.  
  
10. Należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> i przekaż wartość <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> dla `rgfQueryEdit` parametru.  
  
11. Zwraca środowiska <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> dla `VSQueryEditResult` i <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> w jest ustawiony bit `VSQueryEditResultFlags`.  
  
12. Twoje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> implementacja wywołuje `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>).  
  
 To wywołanie może spowodować nową kopię pliku projektu wyewidencjonowania i pobrać najnowszą wersję, oraz należy ponownie załadować pliku projektu. W tym momencie być jedną z następujących operacji:  
  
-   Jeśli obsługiwać własne ponowne załadowanie projektu, następnie środowisko wywołuje Twojej <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> implementacji (VSITEMID_ROOT). Po odebraniu połączenia Załaduj ponownie pierwsze wystąpienie projektu (Project1) i Kontynuuj uaktualnianie pliku projektu. Środowisko zna obsługiwać własne ponowne załadowanie projektu, jeśli `true` dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>).  
  
-   Jeśli nie obsługiwać własne ponowne załadowanie projektu, a następnie wróć `false` dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>). W takim przypadku przed <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>(QEF_ForceEdit_NoPrompting, QEF_DisallowInMemoryEdits) zwraca środowiska tworzy nowe wystąpienie innego projektu, na przykład w projekcie 2, w następujący sposób:  
  
    1.  Wywołania środowiska <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A> Twojego pierwszego obiektu projektu Project1, w związku z tym umieszczanie tego obiektu w stan nieaktywny.  
  
    2.  Wywołania środowiska użytkownika `IVsProjectFactory::CreateProject` implementację, aby utworzyć drugiego wystąpienia projektu, w projekcie 2.  
  
    3.  Wywołania środowiska użytkownika `IPersistFileFormat::Load` implementację, aby otworzyć plik i zainicjuj drugi obiekt projektu projekcie 2.  
  
    4.  Wywołania środowiska `IVsProjectUpgrade::UpgradeProject` raz drugi w celu ustalenia, czy obiekt project powinny zostać uaktualnione. Jednak to wywołanie nowy, drugie wystąpienie projektu projekcie 2. Jest to projekt, który jest otwarty w rozwiązaniu.  
  
        > [!NOTE]
        >  W przypadku pierwszego projektu, Project1, znajduje się w nieaktywnym stanie, a następnie wróć <xref:Microsoft.VisualStudio.VSConstants.S_OK> z pierwszym wywołaniu z <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> implementacji.  
  
    5.  Należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> i przekaż wartość <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> dla `rgfQueryEdit` parametru.  
  
    6.  Zwraca środowiska <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> i można kontynuować uaktualnianie, ponieważ mogą być zapisywane w pliku projektu.  
  
 Jeśli nie można uaktualnić, zwróć <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> z `IVsProjectUpgrade::UpgradeProject`. Jeśli uaktualnienie nie jest konieczne lub nie chcesz uaktualnić, Traktuj `IVsProjectUpgrade::UpgradeProject` wywołać jako pusta. Jeśli <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>, węzeł symbol zastępczy zostanie dodany do rozwiązania dla projektu.  
  
## <a name="upgrading-project-items"></a>Uaktualnianie elementów projektu
  
Jeśli dodasz lub zarządzać elementów w systemach projektu, które nie implementują, konieczne może być uczestniczą w procesie uaktualniania projektu. Crystal Reports to przykład elementu, który można dodać do projektu systemu.  
  
 Zwykle obiektów implementujących element projektu można wykorzystać już pełni wystąpień i uaktualnionych projektów, ponieważ muszą wiedzieć, jakie są odwołania do projektu i jakie będą inne właściwości projektu istnieje dokonanie wyboru uaktualnienia.  
  
### <a name="to-get-the-project-upgrade-notification"></a>Aby otrzymywać powiadomienia uaktualniania projektu  
  
1.  Ustaw <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> Flaga (zdefiniowany w vsshell80.idl) w implementacji elementu projektu. Powoduje to tego elementu projektu pakiet VSPackage można automatycznie załadować podczas [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] powłoki Określa, czy system projektu trwa uaktualnianie.  
  
2.  Zalecamy <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interfejsu za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A> metody.  
  
3.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> Interfejsu jest wywoływane po implementacji systemu projektu zakończeniu uaktualniania i tworzenia nowego projektu uaktualniony. W zależności od scenariusza <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> interfejsu jest uruchamiany po <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>, lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> metody.  
  
### <a name="to-upgrade-the-project-item-files"></a>Aby uaktualnić pliki elementu projektu  
  
1.  Proces tworzenia kopii zapasowej pliku należy starannie zarządzać w implementacji elementu projektu. W szczególności dotyczy to kopia zapasowa side-by-side, gdzie `fUpgradeFlag` parametr <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> ustawiono metodę <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS>, w którym pliki kopii zapasowej są umieszczane wzdłuż plików po stronie, które są oznaczone jako ".old". Kopie zapasowe plików starszych niż czas systemowy, gdy projekt został uaktualniony może zostać wyznaczony jako przestarzały. Ponadto one mogą zostać zastąpione, jeśli podjąć specjalne kroki, aby zapobiec takiej sytuacji.  
  
2.  W czasie Twojej elementu projektu pobiera powiadomienie z informacją o uaktualnieniu projektu **Kreator konwersji Visual Studio** jest nadal wyświetlany. W związku z tym należy użyć metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> interfejsu zapewnienie uaktualnienia wiadomości do interfejsu użytkownika kreatora.  
  
## <a name="see-also"></a>Zobacz też  
 [Projekty](../../extensibility/internals/projects.md)   
