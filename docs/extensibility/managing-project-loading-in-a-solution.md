---
title: Ładowanie projektu w rozwiązaniu do zarządzania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d0e479a96252710d1f7e6285ffaaa2baf383c061
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31146222"
---
# <a name="managing-project-loading-in-a-solution"></a>Zarządzanie ładowania projektu w rozwiązaniu
Rozwiązania programu Visual Studio może zawierać wiele projektów. Domyślne zachowanie programu Visual Studio jest załadowanie wszystkich projektów w rozwiązaniu w momencie otwarcia rozwiązania, a nie Zezwalaj użytkownikowi na dostęp, żaden z projektów wszystkich z nich ma zakończenie ładowania. Gdy proces ładowania projektu trwa ponad dwie minuty, jest wyświetlany pasek postępu, przedstawiający liczbę projektów i całkowitą liczbę projektów. Użytkownik może zwolnienia projektów podczas pracy w rozwiązaniu z wieloma projektami, ale ta procedura ma niektóre wady: zwolniony projekty nie są tworzone w ramach polecenie Kompiluj rozwiązanie i IntelliSense opisy typów i członków zamknięte projekty nie są wyświetlane.  
  
 Deweloperzy mogą zmniejszyć czasy ładowania rozwiązania projektu i zarządzania zachowania ładowania Menedżera tworząc ładowania rozwiązania. Rozwiązanie Menedżera obciążenia można upewnij się, że projekty zostały załadowane przed rozpoczęciem kompilacji tła, opóźnić ładowania tła dopiero po zakończeniu inne zadania w tle i wykonywać inne zadania zarządzania ładowania projektu.  
  
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
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> Metoda jest wywoływana, gdy trwa zamykanie programu Visual Studio lub inny pakiet przejmuje rolę menedżera obciążenia aktywnego rozwiązania przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> z <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> właściwości.  
  
#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>Strategie dla różnych rodzajów Menedżera obciążenia rozwiązania  
 Menedżerowie obciążenia rozwiązania można wdrożyć na różne sposoby, w zależności od typów rozwiązań, które są przeznaczone do zarządzania.  
  
 Jeśli Menedżera obciążenia rozwiązania jest przeznaczona do zarządzania rozwiązania ładowania ogólnie rzecz biorąc, można zaimplementować jako część pakiet VSPackage. Pakiet powinien być ustawiony na automatyczne ładowanie przez dodanie <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> na pakiet VSPackage o wartości <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>. Następnie można aktywować Menedżera obciążenia rozwiązania <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat pakietów autoloading, zobacz [ładowania VSPackages](../extensibility/loading-vspackages.md).  
  
 Ponieważ program Visual Studio rozpoznaje tylko ostatni obciążenia Menedżerze rozwiązania do aktywacji, menedżerów obciążenia ogólne rozwiązanie powinien zawsze wykrywa, czy przed uaktywnieniem się jest istniejącego menedżera obciążenia. Jeśli wywołanie GetProperty() w usłudze rozwiązania dla <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> zwraca `null`, jest Brak menedżera obciążenia aktywne rozwiązanie. Jeśli nie zwracać wartości null, sprawdź, czy obiekt jest taki sam jak Menedżera obciążenia rozwiązania.  
  
 Jeśli Menedżera obciążenia rozwiązania jest przeznaczona do zarządzania tylko kilka typów rozwiązania, pakiet VSPackage możliwe subskrybowanie zdarzeń ładowania rozwiązania (wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>) i użyj programu obsługi zdarzeń dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> aktywować Menedżera obciążenia rozwiązania.  
  
 Jeśli rozwiązania Menedżera obciążenia jest przeznaczona do zarządzania tylko określone rozwiązania, informacje dotyczące aktywacji mógł być trwały jako część pliku rozwiązania przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> dla sekcji wstępne rozwiązania.  
  
 Menedżerowie obciążenia konkretne rozwiązanie dezaktywować w <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> program obsługi zdarzeń, aby nie są w konflikcie z innymi menedżerami ładowania rozwiązania.  
  
 Jeśli potrzebujesz Menedżera obciążenia rozwiązania tylko do utrwalenia właściwości obciążenia projektu globalnego (na przykład właściwości na stronie Opcje), można uaktywnić Menedżera obciążenia rozwiązania w <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> program obsługi zdarzeń, utrwalić ustawienia właściwości rozwiązania następnie Dezaktywowanie Menedżera obciążenia rozwiązania.  
  
## <a name="handling-solution-load-events"></a>Obsługa zdarzeń ładowania rozwiązania  
 Aby subskrybować zdarzeń ładowania rozwiązania, należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> po aktywacji Menedżera obciążenia rozwiązania. W przypadku zastosowania <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>, mogą odpowiadać na zdarzenia, które odnoszą się do innego projektu ładowania właściwości.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: To zdarzenie jest wywoływane przed otwarciem rozwiązania.
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: To zdarzenie jest wywoływane po rozwiązaniu jest całkowicie załadowany, ale przed tła ładowanie projektu rozpoczyna się ponownie.
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: To zdarzenie jest wywoływane po załadowaniu początkowo pełni rozwiązania, czy istnieje Menedżera obciążenia rozwiązania. Jest on również uruchamiany po powiązaniu obciążenia w tle lub żądanie załadowania zawsze, gdy rozwiązanie staje się całkowicie załadowany. W tym samym czasie <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> uaktywnieniu.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: To zdarzenie jest wywoływane przed załadowaniem projektu (lub projektów). Aby upewnić się, że inne procesy w tle są wykonywane przed projekty są ładowane, ustaw `pfShouldDelayLoadToNextIdle` do **true**.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: To zdarzenie jest wywoływane podczas partii projektów ma być załadowany. Jeśli `fIsBackgroundIdleBatch` ma wartość true, projekty mają być ładowane w tle; Jeśli `fIsBackgroundIdleBatch` ma wartość false, projekty są teraz do załadowania synchronicznie wyniku żądania użytkownika, na przykład jeśli użytkownik rozwija oczekujące projekt w Eksploratorze rozwiązań. To zdarzenie kosztowne pracy, które w przeciwnym razie będzie trzeba przeprowadzić może obsłużyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: To zdarzenie jest wywoływane po załadowaniu partii projektów.  
  
## <a name="detecting-and-managing-solution-and-project-loading"></a>Wykrywanie i zarządzanie rozwiązania i ładowanie projektu  
 W celu wykrycia stan ładowania projektów i rozwiązań, wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> z następującymi wartościami:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` zwraca `true` Jeśli rozwiązanie i wszystkie jego projekty są załadowane, w przeciwnym razie `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` zwraca `true` Jeśli partii projektów są obecnie ładowane w tle, w przeciwnym razie `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` zwraca `true` Jeśli partii projektów aktualnie Trwa ładowanie synchronicznie wyniku polecenia user lub inne obciążenia jawne, w przeciwnym razie `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` zwraca `true` Jeśli rozwiązanie jest obecnie są zamknięte, w przeciwnym razie `false`.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` zwraca `true` Jeśli rozwiązanie jest obecnie otwierany, w przeciwnym razie `false`.  
  
 Można również upewnić, że projekty i rozwiązania są ładowane przez wywoływanie jednej z następujących metod:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: wywołanie tej metody wymusza projektów w rozwiązaniu załadować przed metoda zwraca.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: wywołanie tej metody wymusza projektów w `guidProject` załadować przed metoda zwraca.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: wywołanie tej metody wymusza projektu w `guidProjectID` załadować przed metoda zwraca.  
