---
title: Strony właściwości | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1b08e210a57388d77859600c02c0e6a30a404884
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="property-pages"></a>Strony właściwości
Użytkownicy mogą wyświetlać i zmieniać właściwości zależne od konfiguracji i - niezależne projektu za pomocą stron właściwości. A **strony właściwości** przycisk jest aktywny w **właściwości** oknie lub na pasku narzędzi Eksplorator rozwiązań dla obiektów, które dostarczają widoku strony właściwości zaznaczonego obiektu. Strony właściwości są tworzone przez środowisko i są dostępne dla projektów i rozwiązań. Jednak może również być udostępniane dla elementów projektu, które należy użyć właściwości zależne od konfiguracji. Ta funkcja może być używany, gdy pliki w projekcie wymagają ustawienia przełącznika kompilatora różnych kompilować się właściwie.  
  
## <a name="using-property-pages"></a>Używanie stron właściwości  
 Strony właściwości jest już wyświetlany zmieni się zaznaczenie (na przykład z rozwiązania z projektem), informacje wyświetlane na stronach zmiany, aby wyświetlić właściwości dla nowego zaznaczenia. Jeśli nie ma żadnych właściwości w obiekcie, które obsługują strony właściwości, strona właściwości jest pusta.  
  
 Jeśli zaznaczono wiele obiektów, zostanie wyświetlona strona właściwości przecięcie właściwości dla wszystkich wybranych elementów. Jeśli wybrany element nie zawiera właściwości zależne od konfiguracji i **strony właściwości** zostanie kliknięty przycisk na pasku narzędzi Eksplorator rozwiązań, nastąpi zmiana fokusu do okna właściwości. Aby uzyskać więcej informacji dotyczących okna właściwości i zaznaczenia, zobacz [rozszerzanie właściwości](../../extensibility/internals/extending-properties.md).  
  
 Jeśli właściwości są wyświetlane dla wielu obiektów i zmień wartość na stronie właściwości, wszystkie wartości dla obiektów są ustawione na nową wartość nawet jeśli były one pierwotnie różnych i strona była pusta wyświetlania właściwości pojedynczego obiektu.  
  
 Istnieją dwa typy ogólne **stron ProjectProperty** okien dialogowych dostępne w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. W pierwszym, dla projektów języka Visual Basic na przykład strony właściwości są wyświetlane przy użyciu formatu pola, jak pokazano na poniższym zrzucie ekranu. W ciągu sekundy pokazano później w tej sekcji właściwości hostów strony siatki właściwości podobnie jak w oknie właściwości.  
  
 ![Strony właściwości języka Visual Basic](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages")  
Okno dialogowe strony właściwości projektu z pola struktury formatu i drzewa  
  
 Struktura drzewa w oknie dialogowym strony właściwości nie jest utworzony przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>. Środowisko, na podstawie poziomu nazwy przekazywane do niej przez <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> interfejsy, tworzy go.  
  
 Brak dostępnych tylko dwie kategorie najwyższego poziomu w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] strony właściwości:  
  
-   Wspólne właściwości, które powoduje wyświetlenie informacji niezależny od konfiguracji dla wybranego obiektu lub obiektów. W związku z tym gdy wybierany jest jeden z podkategorii wspólnych właściwości, w górnej części okna dialogowego Opcje konfiguracji, platformy i programu Configuration Manager nie są dostępne.  
  
-   Właściwości konfiguracji, który zawiera informacje zależne od konfiguracji odnoszące się do parametrów debugowanie, optymalizacji i kompilacji dla rozwiązania lub projektu.  
  
 Nie można utworzyć dodatkowe kategorie najwyższego poziomu, ale nie można wyświetlić jednego lub drugiego w implementacji `IVsPropertyPage`. Jeśli na przykład nie masz żadnych właściwości niezależny od konfiguracji, aby wyświetlić dla obiekt, możesz nie wyświetlić kategorii Wspólne właściwości. Wyświetl typowe właściwości, jeśli `ISpecifyPropertyPages` zaimplementowano z obiektu przeglądania elementu i właściwości konfiguracji podczas implementowania `ISpecifyPropertyPages` w obiekcie konfiguracji (obiekt implementujący `IVsCfg`, `IVsProjectCfg`i pokrewne interfejsy).  
  
 Każda kategoria wyświetlane w obszarze kategorią najwyższego poziomu reprezentuje strony oddzielne właściwości. Kategorii i podkategorii wpisy dostępne w oknie dialogowym są określane przez implementacji `ISpecifyPropertyPages` i `IVsPropertyPage`.  
  
 `IDispatch` obiekty dla elementów w kontenerze zaznaczenia, których właściwości, który będzie wyświetlany na wdrożenie stron właściwości `ISpecifyPropertyPages` wyliczyć listy identyfikatorów klas. Identyfikatory klas są przekazywane jako zmienne `ISpecifyPropertyPages` i służą do utworzenia wystąpienia strony właściwości. Lista identyfikatorów klas również jest przekazywana do `IVsPropertyPage` umożliwiające utworzenie struktury drzewa po lewej stronie okna dialogowego. Strony właściwości, a następnie Przekaż informacje z powrotem do `IDispatch` obiekt, który implementuje `ISpecifyPropertyPages` i wypełnia informacji dla każdej strony.  
  
 Właściwości obiektu przeglądania są pobierane przy użyciu `IDispatch` dla każdego obiektu w kontenerze zaznaczenia.  
  
 Implementowanie `Help::DisplayTopicFromF1Keyword` w pakiecie VSPackage udostępnia funkcje dla przycisku pomocy.  
  
 Aby uzyskać więcej informacji, zobacz `IDispatch` i `ISpecifyPropertyPages`w bibliotece MSDN.  
  
 Drugi typ strony właściwości wyświetlane w hostach przykłady formularza siatki właściwości, jak pokazano na poniższym zrzucie ekranu.  
  
 ![Strony właściwości VC](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages")  
Właściwości strony — okno dialogowe Właściwości siatki  
  
 Interfejsy `IVSMDPropertyBrowser` i `IVSMDPropertyGrid` (deklaracja w vsmanaged.h) są używane do tworzenia i wypełniania siatki właściwości, w ramach lub oknie dialogowym.  
  
 Architektura projektów zmienił się znacznie z poprzednich wersji programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. W szczególności pojęcie projektu jest aktywna została zmieniona. W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], brak nie koncepcja aktywnego projektu. W poprzednich środowisk deweloperskich aktywnego projektu jest domyślnie projekt, który jest tworzenie i wdrażanie polecenia niezależnie od tego, w tym kontekście. Teraz rozwiązania formanty i rozstrzyga o kolejności przetwarzania którego tworzenia i wdrażania polecenia Zastosuj w poszczególnych projektach.  
  
 Jaka była wcześniej aktywnego projektu jest teraz przechwycić w jednym z trzech sposobów:  
  
-   Projekt startowy  
  
     Można określić projektu lub projektów ze strony właściwości rozwiązania, który zostanie uruchomiony, gdy użytkownik naciśnie klawisz F5 lub wybiera Uruchom z menu Kompiluj. Działa to w sposób podobny do starego aktywnego projektu w tym sensie, że jego nazwa jest wyświetlana w Eksploratorze rozwiązań pogrubioną czcionką.  
  
     Projekt startowy można pobrać jako właściwości w modelu automatyzacji przez wywołanie metody `DTE.Solution.SolutionBuild.StartupProjects`. W pakiet VSPackage, należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> metody. `IVsSolutionBuildManager` jest dostępna jako usługa przez `QueryService` na SID_SVsSolutionBuildManager. Aby uzyskać więcej informacji, zobacz [obiekt konfiguracji projektu](../../extensibility/internals/project-configuration-object.md) i [konfiguracji rozwiązania](../../extensibility/internals/solution-configuration.md).  
  
-   Konfiguracja aktywnego rozwiązania kompilacji  
  
     [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aktywne rozwiązanie konfiguracji dostępne w modelu automatyzacji zaimplementowanie `DTE.Solution.SolutionBuild.ActiveConfiguration`. Konfiguracja rozwiązania jest kolekcja, która zawiera jedną konfigurację projektu dla każdego projektu w rozwiązaniu (każdy projekt może mieć wielu konfiguracji na wielu platformach o różnych nazwach). Aby uzyskać więcej informacji dotyczących strony właściwości rozwiązania, zobacz [konfiguracji rozwiązania](../../extensibility/internals/solution-configuration.md).  
  
-   Obecnie wybranego projektu  
  
     Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> metoda pobierania hierarchii projektu i elementu projektu lub wybrane elementy. Z DTE, należy użyć `SelectedItems.SelectedItem.Project` i `SelectedItems.SelectedItem.ProjectItem` metody. Brak przykładowy kod tych pozycji w rdzeniu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dokumentów.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>   
 [Opcje konfiguracji zarządzania](../../extensibility/internals/managing-configuration-options.md)   
 [Obiekt konfiguracji projektu](../../extensibility/internals/project-configuration-object.md)   
 [Konfiguracja rozwiązania](../../extensibility/internals/solution-configuration.md)