---
title: "Ładowanie projektu w rozwiązaniu do zarządzania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: a2be2c75704646bab50f89377d960d44f6fa14f1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="managing-project-loading-in-a-solution"></a>Zarządzanie ładowania projektu w rozwiązaniu
Rozwiązania programu Visual Studio może zawierać wiele projektów. Domyślne zachowanie programu Visual Studio jest załadowanie wszystkich projektów w rozwiązaniu w momencie otwarcia rozwiązania, a nie Zezwalaj użytkownikowi na dostęp, żaden z projektów wszystkich z nich ma zakończenie ładowania. Gdy proces ładowania projektu trwa ponad dwie minuty, jest wyświetlany pasek postępu, przedstawiający liczbę projektów i całkowitą liczbę projektów. Użytkownik może zwolnienia projektów podczas pracy w rozwiązaniu z wieloma projektami, ale ta procedura ma niektóre wady: zwolniony projekty nie są tworzone w ramach polecenie Kompiluj rozwiązanie i IntelliSense opisy typów i członków zamknięte projekty nie są wyświetlane.  
  
 Deweloperzy mogą zmniejszyć czasy ładowania rozwiązania projektu i zarządzania zachowania ładowania Menedżera tworząc ładowania rozwiązania. Rozwiązanie Menedżera obciążenia można ustawić inny projekt ładowania priorytety dotyczące określonych projektów lub typów projektów, upewnij się, że projekty zostały załadowane przed rozpoczęciem kompilacji tła opóźnić ładowania tła dopiero po zakończeniu inne zadania w tle i wykonania inne zadania zarządzania ładowania projektu.  
  
## <a name="project-loading-priorities"></a>Ładowanie priorytetów projektu  
 Visual Studio definiuje cztery priorytety ładowania inny projekt:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>(domyślnie): po otwarciu rozwiązania, projekty są ładowane asynchronicznie. Jeśli ta priorytet został ustawiony w projekcie zwolnione po rozwiązania jest już otwarty, projekt zostanie załadowany na następny punkt bezczynności.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: po otwarciu rozwiązania, projekty są ładowane w tle, umożliwiając użytkownikowi dostęp do projektów, jak są załadowane bez konieczności poczekać, aż wszystkie projekty zostały załadowane.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: projekty są ładowane podczas uzyskiwania do nich. Projekt jest dostępna, gdy użytkownik rozwija węzeł projektu w Eksploratorze rozwiązań, po otwarciu pliku należących do projektu po otwarciu rozwiązania, ponieważ jest na liście otwartych dokumentów (utrwalane w pliku opcji rozwiązania) lub gdy innego projektu który jest ładowany ma zależności w projekcie. Ten typ projektu nie jest automatycznie załadowane przed rozpoczęciem procesu kompilacji; Rozwiązanie Menedżera obciążenia jest odpowiedzialny za zapewnienie, że wszystkie niezbędne projekty zostały załadowane. Te projekty również powinny być ładowane przed rozpoczęciem Znajdź/Zamień w plikach między całego rozwiązania.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: projektów nie mają być załadowane, chyba że wyraźnie zażąda użytkownika. Jest to sytuacji, gdy projekty są jawnie wyładowany.  
  
## <a name="creating-a-solution-load-manager"></a>Tworzenie ładowania rozwiązania manager  
 Deweloperzy mogą tworzyć ładowania rozwiązania Menedżera zaimplementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> i udzielanie porad programu Visual Studio, czy Menedżera obciążenia rozwiązania jest aktywny.  
  
#### <a name="activating-a-solution-load-manager"></a>Aktywowanie Menedżera obciążenia rozwiązania  
 Visual Studio umożliwia tylko jeden Menedżera obciążenia rozwiązania w danym momencie, konieczne jest poinformowanie programu Visual Studio można aktywować obciążenia rozwiązania menedżera. Jeśli później aktywowaniu drugi Menedżera obciążenia rozwiązania Menedżera obciążenia rozwiązania zostanie odłączony.  
  
 Należy uzyskać <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> usługi i ustaw <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> właściwości:  
  
```csharp  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;  
object objLoadMgr = this;   //the class that implements IVsSolutionManager  
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
#### <a name="implementing-ivssolutionloadmanager"></a>Implementowanie IVsSolutionLoadManager  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnBeforeOpenProject%2A> Metoda jest wywoływana w trakcie procesu otwierania rozwiązania. Aby zaimplementować tę metodę, należy użyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManagerSupport> usługi, aby ustawić priorytet obciążenia typ projektu chcesz zarządzać. Na przykład następujący kod ustawia typy projektów C# do ładowania w tle:  
  
```csharp  
Guid guidCSProjectType = new Guid("{FAE04EC0-301F-11d3-BF4B-00C04F79EFBC}");  
pSLMgrSupport.SetProjectLoadPriority(guidProjectID, (uint)_VSProjectLoadPriority.PLP_BackgroundLoad);  
```  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> Metoda jest wywoływana, gdy trwa zamykanie programu Visual Studio lub inny pakiet przejmuje rolę menedżera obciążenia aktywnego rozwiązania przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> z <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> właściwości.  
  
#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Strategie dla różnych rodzajów Menedżera obciążenia rozwiązania  
 Menedżerowie obciążenia rozwiązania można wdrożyć na różne sposoby, w zależności od typów rozwiązań, które są przeznaczone do zarządzania.  
  
 Jeśli Menedżera obciążenia rozwiązania jest przeznaczona do zarządzania rozwiązania ładowania ogólnie rzecz biorąc, można zaimplementować jako część pakiet VSPackage. Pakiet powinien być ustawiony na automatyczne ładowanie przez dodanie <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> na pakiet VSPackage o wartości <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>. Następnie można aktywować Menedżera obciążenia rozwiązania <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat pakietów autoloading, zobacz [ładowania VSPackages](../extensibility/loading-vspackages.md).  
  
 Ponieważ program Visual Studio rozpoznaje tylko ostatni obciążenia Menedżerze rozwiązania do aktywacji, menedżerów obciążenia ogólne rozwiązanie powinien zawsze wykrywa, czy przed uaktywnieniem się jest istniejącego menedżera obciążenia. Jeśli wywołanie GetProperty() w usłudze rozwiązania dla <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> zwraca `null`, jest Brak menedżera obciążenia aktywne rozwiązanie. Jeśli nie zwracać wartości null, sprawdź, czy obiekt jest taki sam jak Menedżera obciążenia rozwiązania.  
  
 Jeśli Menedżera obciążenia rozwiązania jest przeznaczona do zarządzania tylko kilka typów rozwiązania, pakiet VSPackage możliwe subskrybowanie zdarzeń ładowania rozwiązania (wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>) i użyj programu obsługi zdarzeń dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> aktywować Menedżera obciążenia rozwiązania.  
  
 Jeśli rozwiązania Menedżera obciążenia jest przeznaczona do zarządzania tylko określone rozwiązania, informacje dotyczące aktywacji można trwale jako część pliku rozwiązania. Aby to zrobić, należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> dla sekcji wstępne rozwiązania.  
  
 Menedżerowie obciążenia konkretne rozwiązanie dezaktywować w <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> program obsługi zdarzeń, aby nie są w konflikcie z innymi menedżerami ładowania rozwiązania.  
  
 Jeśli potrzebujesz Menedżera obciążenia rozwiązania tylko do utrwalenia priorytetów obciążenia projektu globalnego (na przykład właściwości na stronie Opcje), można uaktywnić Menedżera obciążenia rozwiązania w <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> program obsługi zdarzeń, utrwalić ustawienia właściwości rozwiązania następnie Dezaktywowanie Menedżera obciążenia rozwiązania.  
  
## <a name="handling-solution-load-events"></a>Obsługa zdarzeń ładowania rozwiązania  
 Aby subskrybować zdarzeń ładowania rozwiązania, należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> po aktywacji Menedżera obciążenia rozwiązania. W przypadku zastosowania <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>, mogą odpowiadać na zdarzenia, które odnoszą się do innego projektu ładowania priorytetów.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: To jest uruchamiany przed otwarciem rozwiązania. Można go zmienić projekt ładowania priorytet dla projektów w rozwiązaniu.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: To jest uruchamiany po rozwiązaniu jest całkowicie załadowany, ale przed tła ładowanie projektu rozpoczyna się ponownie. Na przykład użytkownik może uzyskać dostęp do projektu o priorytetach obciążenia jest LoadIfNeeded lub Menedżera obciążenia rozwiązania może zmienić priorytet ładowania projektu do BackgroundLoad, który zaczyna się obciążenia tła tego projektu.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: Czy istnieje Menedżera obciążenia rozwiązania to uruchamiane po załadowaniu początkowo pełni rozwiązania. Jest on również uruchamiany po powiązaniu obciążenia w tle lub żądanie załadowania zawsze, gdy rozwiązanie staje się całkowicie załadowany. W tym samym czasie <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> uaktywnieniu.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: To jest wywoływane przed załadowaniem projektu (lub projektów). Aby upewnić się, że inne procesy w tle są wykonywane przed projekty są ładowane, ustaw `pfShouldDelayLoadToNextIdle` do **true**.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: To jest wywoływane podczas partii projektów ma być załadowany. Jeśli `fIsBackgroundIdleBatch` ma wartość true, projekty mają być ładowane w tle; Jeśli `fIsBackgroundIdleBatch` ma wartość false, projekty są teraz do załadowania synchronicznie wyniku żądania użytkownika, na przykład jeśli użytkownik rozwija oczekujące projekt w Eksploratorze rozwiązań. Można zaimplementować to kosztowna pracy, które w przeciwnym razie będzie trzeba przeprowadzić <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: To jest wywoływane po załadowaniu partii projektów.  
  
## <a name="detecting-and-managing-solution-and-project-loading"></a>Wykrywanie i zarządzanie rozwiązania i ładowanie projektu  
 W celu wykrycia stan ładowania projektów i rozwiązań, wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> z następującymi wartościami:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` zwraca `true` Jeśli rozwiązanie i wszystkie jego projekty są załadowane, w przeciwnym razie `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` zwraca `true` Jeśli partii projekty są obecnie ładowane w tle, w przeciwnym razie `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` zwraca `true` Jeśli partii projektów są obecnie ładowane synchronicznie wyniku polecenia user lub inne obciążenia jawne, w przeciwnym razie `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` zwraca `true` Jeśli rozwiązanie jest obecnie są zamknięte, w przeciwnym razie `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` zwraca `true` Jeśli rozwiązanie jest obecnie otwierany, w przeciwnym razie `false`.  
  
 Można także zapewnić, że projekty i rozwiązania zostały załadowane (niezależnie od tego, jakie są priorytetów obciążenia projektu) przez wywoływanie jednej z następujących metod:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: wywołanie tej metody wymusza projektów w rozwiązaniu załadować przed metoda zwraca.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: wywołanie tej metody wymusza projektów w `guidProject` załadować przed metoda zwraca.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: wywołanie tej metody wymusza projektu w `guidProjectID` załadować przed metoda zwraca.  
  
> [!NOTE]
>  . Domyślnie załadować projektów mających żądanie i priorytety obciążenia w tle są załadowane, ale jeśli <xref:Microsoft.VisualStudio.Shell.Interop.__VSBSLFLAGS> flaga jest przekazywany do metody, wszystkie projekty zostaną załadowane z wyjątkiem te, które są oznaczone w sposób jawny załadować.