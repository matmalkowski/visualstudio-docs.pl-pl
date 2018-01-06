---
title: "Pisanie kodu w rozwiązaniach pakietu Office | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VST.Project.RefactoringCancelled
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], writing code
- managed code [Office development in Visual Studio]
- Office development in Visual Studio, programming languages supported
- Office applications [Office development in Visual Studio], automating
- Office applications [Office development in Visual Studio], writing code
- writing code for Office solutions
- programming [Office development in Visual Studio], model
- Automation [Office development in Visual Studio], managed code
- application development [Office development in Visual Studio], programming model
- Office solutions [Office development in Visual Studio], writing code
- automating Office applications
- application development [Office development in Visual Studio], writing code
- application development [Office development in Visual Studio], automating
- Office projects [Office development in Visual Studio], changing namespaces
- solutions [Office development in Visual Studio], programming model
- programming [Office development in Visual Studio]
- namespaces [Office developmentin Visual Studio], changing in Office solutions
- projects [Office development in Visual Studio], writing code
- Office applications [Office development in Visual Studio], programming model
- managed code extensions [Office development in Visual Studio], writing code
ms.assetid: 2d4d8fd0-e881-4829-976f-0d1a9221dec0
caps.latest.revision: "37"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 5d6a400f5c1ee523e2bb3fd95be215af0e5ba371
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="writing-code-in-office-solutions"></a>Pisanie kodu dla rozwiązań pakietu Office
  Brak niektórych aspektów pisanie kodu w projektach pakietu Office, które różnią się od innych typów projektów programu Visual Studio. Wiele z tych różnic dotyczące sposobu modele obiektów pakietu Office są widoczne dla kodu zarządzanego. Inne różnice są związane z projektu projektów pakietu Office.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="managed-code-and-office-programming"></a>Programowanie Office i kodu zarządzanego  
 Technologia klucza, która umożliwia tworzenie zintegrowane rozwiązanie Microsoft Office jest automatyzacji, która jest częścią technologii składnika modelu COM (Object). Automatyzacja umożliwia tworzenie i sterowanie obiektów oprogramowania udostępniane przez dowolną aplikację, biblioteki DLL, za pomocą kodu lub formantem ActiveX systemu obsługuje odpowiednich interfejsów programistycznych.  
  
### <a name="understanding-primary-interop-assemblies"></a>Opis podstawowe zestawy międzyoperacyjne  
 Aplikacje Microsoft Office ujawniać znacznie ich funkcji automatyzacji. Jednak nie można użyć kodu zarządzanego (np. Visual Basic lub C#) bezpośrednio do automatyzowania aplikacji pakietu Office. Aby zautomatyzować aplikacje pakietu Office za pomocą kodu zarządzanego, należy użyć podstawowe zestawy międzyoperacyjne pakietu Office (PIAs). Podstawowe zestawy międzyoperacyjne Włącz kodu zarządzanego do interakcji z modelu obiektu oparte na modelu COM w aplikacjach pakietu Office.  
  
 Każda aplikacja Microsoft Office ma PIA. Podczas tworzenia projektu pakietu Office w Visual Studio, odwołanie do odpowiedniego PIA jest automatycznie dodawany do projektu. Aby zautomatyzować funkcje innych aplikacjach pakietu Office z projektu, można ręcznie dodać odwołanie do odpowiedniego PIA. Aby uzyskać więcej informacji, zobacz [porady: docelowy Office aplikacji za pośrednictwem podstawowe zestawy międzyoperacyjne](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).  
  
### <a name="using-primary-interop-assemblies-at-design-time-and-run-time"></a>W czasie projektowania i w czasie wykonywania za pomocą podstawowe zestawy międzyoperacyjne  
 Musi mieć PIAs Office zainstalowanych i zarejestrowanych w globalnej pamięci podręcznej zestawów na komputerze deweloperskim do wykonywania większości zadań programowania. Aby uzyskać więcej informacji, zobacz [Konfigurowanie komputera na potrzeby programowania rozwiązań pakietu Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
 PIAs pakietu Office nie są wymagane na komputerach użytkowników końcowych do uruchamiania rozwiązań pakietu Office przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym. Aby uzyskać więcej informacji, zobacz [projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md).  
  
### <a name="using-types-in-primary-interop-assemblies"></a>Używanie typów w podstawowe zestawy międzyoperacyjne  
 Office PIAs zawierają kombinację typów, które udostępniają modelu obiektów z aplikacji pakietu Office i typów dodatkowej infrastruktury, które nie są przeznaczone do użycia bezpośrednio w kodzie. Omówienie typów w PIAs pakietu Office, zobacz [Przegląd klasy i interfejsy w podstawowe zestawy międzyoperacyjne pakietu Office](http://msdn.microsoft.com/en-us/da92dc3c-8209-44de-8095-a843659368d5).  
  
 Ponieważ typów w Office PIAs odpowiada typów modeli obiektów oparte na modelu COM, sposobu korzystania z tych typów często różni się od innych typów zarządzanych. Na przykład sposób wywołania metody, które ma następujące parametry opcjonalne w podstawowy zestaw międzyoperacyjny Office zależy od języka programowania, używaną w projekcie. Więcej informacji znajduje się w następujących tematach:  
  
-   [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md).  
  
-   [Późne wiązania w rozwiązaniach pakietu Office](../vsto/late-binding-in-office-solutions.md).  
  
## <a name="programming-model-of-office-projects"></a>Model programowania projektów pakietu Office  
 Wszystkie projekty pakietu Office zawierają co najmniej jeden wygenerowane klasy, które zapewniają punkt wejścia dla kodu. Te klasy również zapewniają dostęp do modelu obiektów w aplikacji hosta i dostęp do funkcji, takich jak okienka akcji i niestandardowych okienek zadań.  
  
### <a name="understanding-the-generated-classes"></a>Opis wygenerowanego klas  
 Wygenerowana klasa w projektach na poziomie dokumentu dla programów Excel i Word, podobny do obiektu najwyższego poziomu w modelu obiektu aplikacji. Na przykład wygenerowanego `ThisDocument` klasy w projekcie dokument programu Word zawiera tych samych elementów członkowskich jako <xref:Microsoft.Office.Interop.Word.Document> klasy w modelu obiektów programu Word. Aby uzyskać więcej informacji na temat wygenerowane klasy w projektach na poziomie dokumentu, zobacz [programowania dostosowań na poziome dokumentu](../vsto/programming-document-level-customizations.md).  
  
 Wygenerowana klasa o nazwie Podaj projektów dodatku VSTO `ThisAddIn`. Ta klasa nie przypominać klasy w modelu obiektów w aplikacji hosta. Zamiast tego należy ta klasa reprezentuje dodatku VSTO sam i zapewnia elementów członkowskich, który umożliwia dostęp do modelu obiektów w aplikacji hosta a dostęp inne funkcje, które są dostępne dla dodatków narzędzi VSTO. Aby uzyskać więcej informacji, zobacz [programowania VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
 Obejmują wszystkie wygenerowane klasy w projektach pakietu Office `Startup` i `Shutdown` procedury obsługi zdarzeń. Aby rozpocząć pisanie kodu, zwykle dodać kod do obsługi tych zdarzeń. Zainicjować dodatku VSTO programu, można dodać kod `Startup` obsługi zdarzeń. Aby wyczyścić zasoby używane przez dodatek VSTO, można dodać kod `Shutdown` obsługi zdarzeń. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).  
  
### <a name="accessing-the-generated-classes-at-run-time"></a>Uzyskiwanie dostępu do wygenerowanych klas w czasie wykonywania  
 Po załadowaniu rozwiązania do pakietu Office [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] tworzy wygenerowanych klas w projekcie. Są dostępne te obiekty kod w projekcie przy użyciu `Globals` klasy. Na przykład można użyć `Globals` klasę, aby wywoływać kod `ThisAddIn` klasy z obsługi zdarzeń z przyciskiem wstążki w dodatku VSTO.  
  
 Aby uzyskać więcej informacji, zobacz [globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
### <a name="namespace-considerations-in-office-solutions"></a>Zagadnienia dotyczące Namespace w rozwiązaniach pakietu Office  
 Nie można zmienić *domyślny obszar nazw* (lub *głównej przestrzeni nazw* w języku Visual Basic) programu Office project po utworzeniu projektu. Domyślny obszar nazw będzie zawsze zgodna z nazwą projektu, określone podczas tworzenia projektu. Jeśli zmienisz projekt, nie powoduje zmiany domyślnej przestrzeni nazw. Aby uzyskać więcej informacji o domyślnej przestrzeni nazw w projektach, zobacz [&#40; stron aplikacji, Projektant projektu K & 35; &#41; ](/visualstudio/ide/reference/application-page-project-designer-csharp) i [&#40; stron aplikacji, Projektant projektu Visual Basic &#41; ](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
### <a name="changing-the-namespace-of-host-item-classes-in-c-projects"></a>Zmiana Namespace klas elementu hosta w projektów C#  
 Host elementu klasy (na przykład `ThisAddIn`, `ThisWorkbook`, lub `ThisDocument` klasy) mają własne przestrzenie nazw w projektach Visual C# pakietu Office. Domyślnie w przestrzeni nazw dla hosta elementów w projekcie jest zgodna z nazwą projektu, określone podczas tworzenia projektu.  
  
 Aby zmienić nazw elementów hosta w projektach Visual C# pakietu Office, należy użyć **Namespace elementu hosta** właściwości. Aby uzyskać więcej informacji, zobacz [właściwości w projektach pakietu Office](../vsto/properties-in-office-projects.md).  
  
## <a name="supported-programming-languages-in-office-projects"></a>Obsługiwane języki programowania w języku w projektach pakietu Office  
 Szablony projektów pakietu Office w Visual Studio obsługują tylko Visual Basic i Visual C# języków programowania. W związku z tym te szablony projektu są dostępne tylko w ramach **Visual Basic** i **Visual C#** węzłów **nowy projekt** okno dialogowe w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Aby uzyskać więcej informacji, zobacz [porady: tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
## <a name="language-choice-and-office-programming"></a>Wybór języka i programowaniu pakietu Office  
 Microsoft Office i Visual Basic for Applications (VBA) zostały opracowane współdziałają ze sobą w celu zoptymalizowania przepływu pracy dostosowywania aplikacji. Visual Basic odziedziczył niektóre z tych zmian. Na przykład Visual Basic obsługuje następujące parametry opcjonalne, co oznacza, że może zapisywać mniejsza ilość kodu podczas wywoływania metody w przypadku niektórych metod w Microsoft Office podstawowe zestawy międzyoperacyjne niż w przypadku użycia języka Visual C#.  
  
## <a name="programming-with-visual-basic-vs-visual-c-in-office-solutions"></a>Programowania w języku Visual Basic vs. Visual C# w rozwiązaniach pakietu Office  
 Rozwiązania pakietu Office można utworzyć za pomocą języka Visual Basic lub Visual C#. Modele obiektów Microsoft Office są przeznaczone do użycia z Microsoft Visual Basic for Applications (VBA), deweloperów języka Visual Basic może pracować wygodnie z obiektami udostępnianych przez aplikacje pakietu Microsoft Office. Visual C# deweloperzy mogą używać większość tych samych funkcji jako deweloperów języka Visual Basic, ale istnieją przypadki, gdzie należy napisać dodatkowy kod w celu użycia modele obiektów pakietu Office. Istnieją pewne różnice między podstawowe funkcje programowania Office rozwoju i zarządzany kod napisany w języku Visual Basic i C#.  
  
## <a name="key-differences-between-visual-basic-and-visual-c"></a>Podstawowe różnice między Visual Basic i Visual C#  
 W poniższej tabeli przedstawiono podstawowe różnice między Visual Basic i Visual C# w programowanie Office.  
  
|Funkcja|Opis|Obsługa języka Visual Basic|Obsługa programu Visual C#|  
|-------------|-----------------|--------------------------|------------------------|  
|Parametry opcjonalne|Wiele metod Microsoft Office ma parametry, które nie są wymagane w przypadku wywołania metody. Jeśli nie przekazano żadnej wartości dla parametru, zostanie użyta domyślna wartość.|Visual Basic obsługuje następujące parametry opcjonalne.|Visual C# obsługuje następujące parametry opcjonalne w większości przypadków. Aby uzyskać więcej informacji, zobacz [następujące parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md).|  
|Przekazywanie parametrów przez odwołanie|Parametry opcjonalne w większości podstawowe zestawy międzyoperacyjne Microsoft Office może być przekazywany przez wartość. Jednak w niektórych podstawowe zestawy międzyoperacyjne parametry opcjonalne, które akceptują typy referencyjne muszą być przekazywane przez odwołanie.<br /><br /> Aby uzyskać więcej informacji na temat parametrów typu odwołanie i wartość, zobacz [przekazywanie argumentów według wartości i według odwołania &#40; Visual Basic &#41; ](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) (w języku Visual Basic) i [przekazywanie parametrów &#40; K & 35; Przewodnik programowania w języku &#41; ](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).|Żadne dodatkowe czynności niezbędne do przekazania parametrów odwołania. Kompilator Visual Basic automatycznie przekazuje parametry przez odwołanie, gdy jest to konieczne.|Kompilator Visual C# w większości przypadków jest automatycznie przekazuje parametry przez odwołanie, gdy jest to konieczne. Aby uzyskać więcej informacji, zobacz [następujące parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md).|  
|Właściwości sparametryzowane|Niektóre właściwości akceptują parametrów i działać jako funkcje tylko do odczytu.|Visual Basic obsługuje właściwości, które akceptują parametrów.|Visual C# obsługuje właściwości, które akceptują parametrów.|  
|Późne powiązania|Późne wiązanie obejmuje określenie właściwości obiektów w czasie wykonywania, zamiast zmiennych Rzutowanie na typ obiektu, w czasie projektowania.|Visual Basic wykonuje późne wiązanie podczas **Option Strict** jest wyłączona. Gdy **Option Strict** jest włączona, należy jawnie przekonwertować obiekty i Użyj typów w <xref:System.Reflection> przestrzeni nazw, aby dostęp do elementów członkowskich z późnym wiązaniem. Aby uzyskać więcej informacji, zobacz [późne wiązania w rozwiązaniach pakietu Office](../vsto/late-binding-in-office-solutions.md).|Visual C# wykonuje późne wiązanie w projektach przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Aby uzyskać więcej informacji, zobacz [późne wiązania w rozwiązaniach pakietu Office](../vsto/late-binding-in-office-solutions.md).|  
  
## <a name="key-differences-between-office-development-and-managed-code"></a>Podstawowe różnice między programowanie Office i kod zarządzany  
 W poniższej tabeli przedstawiono podstawowe różnice między programowanie Office i zarządzany kod napisany w języku Visual Basic lub Visual C#.  
  
|Funkcja|Opis|Obsługa języka Visual Basic i Visual C#|  
|-------------|-----------------|-----------------------------------------|  
|Indeksy tablicy|Dolnej granicy tablicy kolekcji aplikacji pakietu Microsoft Office rozpoczyna się od 1. Visual Basic i Visual C# Użyj tablic oparte na 0. Aby uzyskać więcej informacji, zobacz [tablice &#40; K & 35; Przewodnik programowania w języku &#41; ](/dotnet/csharp/programming-guide/arrays/index) i [tablic w języku Visual Basic](/dotnet/visual-basic/programming-guide/language-features/arrays/index).|Aby uzyskać dostęp do pierwszego elementu w kolekcji w modelu obiektów z aplikacji pakietu Microsoft Office, należy użyć indeks 1 zamiast 0.|  
  
## <a name="see-also"></a>Zobacz też  
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md)   
 [Porady: docelowa aplikacji pakietu Office za pośrednictwem podstawowe zestawy międzyoperacyjne](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Porady: tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md)   
 [Późne wiązania w rozwiązaniach pakietu Office](../vsto/late-binding-in-office-solutions.md)   
 [Programowanie zespołowe rozwiązań pakietu Office](../vsto/collaborative-development-of-office-solutions.md)  
  
  