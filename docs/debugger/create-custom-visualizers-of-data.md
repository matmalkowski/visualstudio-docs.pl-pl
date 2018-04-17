---
title: Utwórz niestandardowe Wizualizatory danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 06/19/2017
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.visualizer.troubleshoot
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dac2fd507936ffc3b305e8d1339000def3e00e2a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="create-custom-visualizers-of-data"></a>Utwórz niestandardowe Wizualizatory danych
 Wizualizatory są składnikami [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] debugera interfejsu użytkownika. A *wizualizatora* tworzy okno dialogowe lub inny interfejs do wyświetlenia w taki sposób, który jest jego typu danych zmiennej lub obiektu. Na przykład wizualizatora HTML interpretuje ciąg HTML i wyświetla wynik w postaci pojawią się w oknie przeglądarki; Wizualizator mapy bitowej interpretuje struktury mapy bitowej i wyświetla grafiki, który reprezentuje. Niektóre wizualizatorów umożliwiają modyfikowanie, a także wyświetlić dane.

 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] Debugera obejmuje sześć standardowych wizualizatorów. Są to tekst, HTML, XML i JSON wizualizatorów, które działają w ciągu obiektów; z wizualizatora drzewa WPF do wyświetlania właściwości drzewa wizualnego obiektu WPF; i wizualizatora zestawu danych, które działa dla zestawu danych i DataView, DataTable obiektów. Wizualizatory dodatkowe mogą być dostępne do pobrania firmy Microsoft Corporation w przyszłości, a nie są dostępne z stron trzecich oraz społeczności. Ponadto możesz zapisać własnego wizualizatorów i zainstalować je w [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] debugera.

 > [!NOTE]
 > Aby utworzyć niestandardowego wizualizatora dla kodu natywnego, zobacz [Wizualizator debugowania natywnego SQLite](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/SqliteVisualizer) próbki. W aplikacji platformy uniwersalnej systemu Windows i Windows 8.x niestandardowe wizualizatory nie są obsługiwane.

 W debugerze, wizualizatorów są reprezentowane przez ikonę lupy ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "ikona wizualizatora"). Po wyświetleniu ikonę lupy w **etykietek danych**, w oknie debugera, takie jak **czujki** oknie lub w **QuickWatch** okno dialogowe, możesz kliknąć Lupa do Wybierz odpowiedni typ danych odpowiedni obiekt wizualizatora.

## <a name="overview-of-custom-visualizers"></a>Omówienie wizualizatorach niestandardowych

Można napisać niestandardowego wizualizatora dla obiekt klasy zarządzanej z wyjątkiem <xref:System.Object> lub <xref:System.Array>.  
  
 Architektura wizualizatora debuger ma dwie części:  
  
-   *Debugera po stronie* jest uruchamiany w ramach debuger programu Visual Studio. Kod po stronie debugera tworzy i wyświetla interfejsu użytkownika dla użytkownika wizualizatora.  
  
-   *Po stronie debugowanego obiektu* jest uruchamiany w ramach procesu jest debugowania programu Visual Studio ( *debugowanego obiektu*).  
  
 Obiekt danych, które mają być wyświetlane (na przykład obiekt ciągu) istnieje w ramach obiektu debugowanego procesu. Tak po stronie debugowanego obiektu ma wysłać ten obiekt danych po stronie debuger, który można następnie wyświetlać je za pomocą interfejsu użytkownika, które można utworzyć.  
  
 Po stronie debugera odbiera ten obiekt danych ma zostać zwizualizowany z *dostawcy obiektów* implementującej <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> interfejsu. Po stronie debugowanego obiektu wysyła obiekt danych za pośrednictwem *źródło obiektu*, która jest pochodną <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>. Obiekt dostawcy również może wysyłać dane z powrotem do źródła obiektu, który umożliwia pisanie wizualizatora, który umożliwia edycję, a także wyświetla, danych. Obiekt dostawcy może być zastąpiona porozmawiać ewaluatora wyrażeń i, w związku z tym źródłowego obiektu  
  
 Po stronie obiekt debugowany i debuger komunikować się ze sobą za pośrednictwem <xref:System.IO.Stream>. Metody są dostarczane do serializacji obiektu danych do <xref:System.IO.Stream> i deserializacji <xref:System.IO.Stream> do obiektu danych.  
  
 Kod po stronie debugowanego obiektu jest określona za pomocą atrybutu DebuggerVisualizer (<xref:System.Diagnostics.DebuggerVisualizerAttribute>).  
  
 Aby utworzyć wizualizatora interfejsu użytkownika po stronie debugera, należy utworzyć klasę, która dziedziczy <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> i zastąpić <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> metodę w celu wyświetlenia interfejsu.  
  
 Można użyć <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> do wyświetlania formularzy systemu Windows, okien dialogowych i formantów z Twojego wizualizatora.  
  
 Obsługa dla typów ogólnych jest ograniczona. Wizualizator dla obiektu docelowego, który jest typem ogólnym tylko wtedy, gdy typ ogólny jest typem otwartym może zapisywać. To ograniczenie jest taka sama jak ograniczenie, używając `DebuggerTypeProxy` atrybutu. Aby uzyskać więcej informacji, zobacz [przy użyciu atrybutu DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md).  
  
 Niestandardowe wizualizatory może być zagadnienia dotyczące zabezpieczeń. Zobacz [zagadnienia dotyczące zabezpieczeń internetowych](../debugger/visualizer-security-considerations.md).  
  
 Procedury przedstawione poniżej, nadaj ogólny widok co należy zrobić, aby utworzyć wizualizatora. Aby uzyskać bardziej szczegółowy opis, zobacz [wskazówki: pisanie wizualizatora w C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).  
  
### <a name="to-create-the-debugger-side"></a>Aby utworzyć po stronie debugera  
  
1.  Użyj <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> metod do pobrania na stronie debugera wizualizowanego obiektu.  
  
2.  Utwórz klasę, która dziedziczy <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>.  
  
3.  Zastąpienie <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> metodę w celu wyświetlenia interfejsu. Użyj <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> metody wyświetlania formularzy systemu Windows, okien dialogowych i formantów w ramach interfejsu.  
  
4.  Zastosuj <xref:System.Diagnostics.DebuggerVisualizerAttribute>, nadanie mu wizualizatora (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>).  
  
### <a name="to-create-the-debuggee-side"></a>Aby utworzyć po stronie debugowanego obiektu  
  
1.  Zastosuj <xref:System.Diagnostics.DebuggerVisualizerAttribute>, nadanie mu wizualizatora (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>) i źródło obiektu (<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>). W przypadku pominięcia źródło obiektu, będą używane domyślne źródło obiektu  
  
2.  Jeśli chcesz, aby Twoje wizualizatora, aby można było edytować obiekty danych, również zgodnie z ich, wyświetlenie należy zastąpić `TransferData` lub `CreateReplacementObject` metody <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>.   
  
## <a name="in-this-section"></a>W tej sekcji
  
 [Wskazówki: Pisanie wizualizatora w C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  

 [Wskazówki: Pisanie wizualizatora w Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)  
  
 [Porady: Instalacja programu Visualizer](../debugger/how-to-install-a-visualizer.md)  
  
 [Porady: testowanie i debugowanie Wizualizera](../debugger/how-to-test-and-debug-a-visualizer.md)  
  
 [Wizualizator API — odwołanie](../debugger/visualizer-api-reference.md)  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)