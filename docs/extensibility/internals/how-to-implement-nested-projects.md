---
title: "Porady: wdrożeniu projektów zagnieżdżonych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 757668070daacb449a6bc7cbd88ae629fe6487a5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-nested-projects"></a>Porady: wdrożeniu zagnieżdżonych projektów
Podczas tworzenia projektu zagnieżdżonego typu jest kilka dodatkowych kroków, które muszą zostać zaimplementowane. Projekt nadrzędny przejmuje niektóre z obowiązków tego samego, które rozwiązanie ma jego projektów zagnieżdżonych (podrzędny). Projekt nadrzędny jest kontenerem projektów podobne do rozwiązania. W szczególności istnieje kilka zdarzeń, które muszą zgłoszone przez rozwiązanie i projekty nadrzędnego do kompilacji hierarchia zagnieżdżonych projektów. Te zdarzenia są opisane w następujących proces tworzenia zagnieżdżonych projektów.  
  
### <a name="to-create-nested-projects"></a>Do tworzenia projektów zagnieżdżonych  
  
1.  Zintegrowane środowisko programistyczne (IDE) ładuje informacje pliku i uruchamianie projektu projektu nadrzędnego wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> interfejsu. Projekt nadrzędny jest tworzony i dodawany do rozwiązania.  
  
    > [!NOTE]
    >  W tym momencie jest zbyt wczesny procesu dla projektu nadrzędnego do tworzenia projektu zagnieżdżonego, ponieważ można utworzyć projektu nadrzędnego, aby można było utworzyć projektów podrzędnych. Po tej sekwencji projektu nadrzędnego można stosować ustawienia do projektów podrzędnych i projekty podrzędne można uzyskać informacji z projektów nadrzędnego, w razie potrzeby. Ta sekwencja jest, jeśli jest wymagana na przez klientów, takie jak kontroli kodu źródłowego (SCC) i w Eksploratorze rozwiązań.  
  
     Projekt nadrzędny musi czekać, aż <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> metody do wywołania przez IDE przed przygotowaniem zagnieżdżonych (podrzędnej) projektu lub projektów.  
  
2.  Wywołania IDE `QueryInterface` projektu nadrzędnego dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject>. Jeśli to wywołanie zakończy się powodzeniem, wywołania IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> metody element nadrzędny, aby otworzyć wszystkie zagnieżdżone projektów dla projektu nadrzędnego.  
  
3.  Wywołania projektu nadrzędnego <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> metody o zagnieżdżone projekty mają zostać utworzone. SCC, na przykład nasłuchuje tych zdarzeń, aby dowiedzieć się, jeśli kroki w procesie tworzenia rozwiązań i projektów są wykonywane w kolejności. Jeśli zostaną wykonane kroki poza kolejnością, rozwiązanie może nie być z kontroli kodu źródłowego poprawnie zarejestrowany.  
  
4.  Wywołania projektu nadrzędnego <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> metody lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> metody dla każdego z jego projektów podrzędnych.  
  
     Możesz przekazać <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> do `AddVirtualProject` metody, aby wskazać, że wirtualne projektu (zagnieżdżonego) należy dodać do okna projektu wyłączone z kompilacji, dodane do kontroli kodu źródłowego i tak dalej. `VSADDVPFLAGS`Umożliwia sterowanie widoczność projektu zagnieżdżonego i wskazywać, jakie funkcje są z nią skojarzona.  
  
     Jeśli ponownie załadować istniejących projektu podrzędnego projektu przechowywane w pliku projektu projektu nadrzędnym, wywołania projektu nadrzędnego identyfikatora GUID `AddVirtualProjectEx`. Jedyną różnicą między `AddVirtualProject` i `AddVirtualProjectEX` jest to, że `AddVirtualProjectEX` ma parametr, aby włączyć projektu nadrzędnego określić dla każdego wystąpienia `guidProjectID` dla projektu podrzędnego włączyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> funkcji poprawnie.  
  
     Jeżeli nie jest dostępny, nie identyfikatora GUID, takie jak podczas dodawania nowego projektu zagnieżdżonego rozwiązania tworzy po jednej dla projektu w czasie, dodane do elementu nadrzędnego. Jest odpowiedzialny za projektu nadrzędnego, aby utrwalić projektu identyfikatora GUID w pliku projektu. Po usunięciu projektu zagnieżdżonego identyfikatora GUID dla tego projektu mogą być również usuwane.  
  
5.  Wywołania IDE `M:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren` metody dla każdego projektu podrzędnego projektu nadrzędnego.  
  
     Projekt nadrzędny musi implementować `IVsParentProject` Aby zagnieździć projektów. Ale nadrzędnego projektu nigdy nie wywołuje `QueryInterface` dla `IVsParentProject` nawet wtedy, gdy posiada projektów nadrzędnego podrzędne. Rozwiązanie obsługuje wywołanie `IVsParentProject` i, jeśli jest stosowana, wywołuje metodę `OpenChildren` do tworzenia projektów zagnieżdżonych. `AddVirtualProjectEX`zawsze jest wywoływana z `OpenChildren`. Nigdy nie powinna być wywoływana przez projektu nadrzędnego, aby zachować hierarchię zdarzeń tworzenia w kolejności.  
  
6.  Wywołania IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> metody projektu podrzędnego.  
  
7.  Wywołania projektu nadrzędnego <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> metody do powiadamiania słuchaczy utworzono projektów podrzędnych dla obiektu nadrzędnego.  
  
8.  Wywołania IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> metody dla projektu nadrzędnego po otwarciu wszystkich projektów podrzędnych.  
  
     Jeśli go jeszcze nie istnieje, projektu nadrzędnego tworzy identyfikator GUID dla każdego projektu zagnieżdżonego przez wywołanie metody `CoCreateGuid`.  
  
    > [!NOTE]
    >  `CoCreateGuid`Interfejs API modelu COM jest wywoływane, gdy jest identyfikator GUID ma zostać utworzony. Aby uzyskać więcej informacji, zobacz `CoCreateGuid` i identyfikatory GUID w bibliotece MSDN.  
  
     Projekt nadrzędny przechowuje ten identyfikator GUID w pliku projektu mają zostać pobrane przy następnym otwarciu w IDE. Zobacz krok 4, aby uzyskać więcej informacji dotyczących telefonicznej z `AddVirtualProjectEX` można pobrać `guidProjectID` dla projektu podrzędnego.  
  
9. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> Następnie wywoływana jest metoda identyfikator elementu nadrzędnego Konwencja delegowanie w celu projektu zagnieżdżonego. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> Pobiera właściwości węzła, który zagnieżdżony projektu, który chcesz delegować w wywołanego w nadrzędnej.  
  
     Ponieważ projekty nadrzędne i podrzędne są tworzone programowo, można ustawić właściwości dla projektów zagnieżdżonych w tym momencie.  
  
    > [!NOTE]
    >  Nie tylko czy są wyświetlane informacje o kontekście z projektu zagnieżdżonego, ale możesz również poprosić, jeśli projekt nadrzędny ma dowolnego kontekstu dla tego elementu sprawdzając <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>. W ten sposób można dodać dodatkowe atrybuty dynamiczna Pomoc i opcje menu określonych dla poszczególnych projektów zagnieżdżonych.  
  
10. Hierarchia zaprojektowano pod kątem wyświetlania w Eksploratorze rozwiązań w wyniku wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> metody.  
  
     Przekaż hierarchii do środowiska za pośrednictwem `GetNestedHierarchy` do tworzenia hierarchii do wyświetlenia w Eksploratorze rozwiązań. W ten sposób rozwiązania wie, że projekt istnieje i mogą być zarządzane dla tworzenia przez Menedżera kompilacji lub umożliwiają pliki w projekcie, które należy umieścić pod kontrolą kodu źródłowego.  
  
11. Po utworzeniu wszystkich zagnieżdżonych projektach Project1 kontroli jest przekazywane z powrotem do rozwiązania, a proces jest powtarzany w przypadku projekcie 2.  
  
     Ten sam proces tworzenia projektów zagnieżdżony występuje dla projektu podrzędnego, który ma element podrzędny. W takim przypadku BuildProject1, który jest elementem podrzędnym Project1, gdyby projektów podrzędnych one zostałyby utworzone po BuildProject1 i przed projekcie 2. Proces jest rekursywny i hierarchia składa się z góry w dół.  
  
     Gdy projektu zagnieżdżonego jest zamknięty, ponieważ użytkownik zamknął rozwiązania lub konkretnym projektu, inne metody na `IVsParentProject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A>, nosi nazwę. Projekt nadrzędny opakowuje wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> metody z <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> metody o do rozwiązania zdarzeń są zamykane zagnieżdżonych projektów.  
  
 Poniższe tematy dotyczy kilka pojęć wziąć pod uwagę podczas implementowania zagnieżdżonych projektów:  
  
 [Zagadnienia dotyczące zwalniania i ponownego ładowania zagnieżdżonych projektów](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)  
  
 [Obsługa kreatora dla zagnieżdżonych projektów](../../extensibility/internals/wizard-support-for-nested-projects.md)  
  
 [Implementowanie obsługi poleceń dla zagnieżdżonych projektów](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)  
  
 [Filtrowanie okna dialogowego Dodawanie elementu dla projektów zagnieżdżonych](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie elementów do Dodaj nowy element okien dialogowych](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Rejestrowanie szablony projektów i elementów](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Lista kontrolna: Tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Parametry kontekstu](../../extensibility/internals/context-parameters.md)   
 [Kreator (plik Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)