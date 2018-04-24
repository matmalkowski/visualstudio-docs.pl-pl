---
title: Architektura wizualizatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 6aad395f-7170-4d9e-b2b8-a5faf453380e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b20572409ac49451f58584be20fbabfdab39a3ba
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="visualizer-architecture"></a>Architektura wizualizatora
Architektura wizualizatora debuger ma dwie części:  
  
-   *Debugera po stronie* jest uruchamiany w ramach debuger programu Visual Studio. Kod po stronie debugera tworzy i wyświetla interfejsu użytkownika dla użytkownika wizualizatora.  
  
-   *Po stronie debugowanego obiektu* jest uruchamiany w ramach procesu jest debugowania programu Visual Studio ( *debugowanego obiektu*).  
  
 Wizualizatora jest składnik debugera, który umożliwia debugera wyświetlić (*wizualizacji*) zawartości w formie łatwy do rozpoznania, zrozumiały dla obiektu danych. Niektóre wizualizatorów obsługuje również edycji obiektu danych. Tworząc niestandardowe wizualizatory można rozszerzyć debuger mógł obsłużyć własne niestandardowe typy danych.  
  
 Obiekt danych ma zostać zwizualizowany znajduje się w ramach procesu debugowania ( *debugowanego obiektu* proces). Interfejs użytkownika, który spowoduje wyświetlenie danych jest tworzone w ramach procesu debugera programu Visual Studio:  
  
|Proces debugera|Obiekt debugowany proces|  
|----------------------|----------------------|  
|Debuger interfejsu użytkownika (etykietek danych, okno czujki QuickWatch)|Obiekt danych ma zostać zwizualizowany|  
  
 W celu wizualizacji danych obiekt w interfejsie debugera, należy kodu do komunikacji między dwoma procesami. W rezultacie architektura wizualizatora składa się z dwóch części: *debugera po stronie* kodu i *po stronie debugowanego obiektu* kodu.  
  
 Kod po stronie debugera tworzy własnego interfejsu użytkownika, które mogą być wywoływane z interfejsu debugera, takie jak etykietki danych, okno czujki lub QuickWatch. Wizualizator interfejsu jest tworzona przy użyciu <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> klasy i <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> interfejsu. Jak Wizualizator interfejsów API, DialogDebuggerVisualizer i IDialogVisualizerService znajdują się w <xref:Microsoft.VisualStudio.DebuggerVisualizers> przestrzeni nazw.  
  
|Po stronie debugera|Po stronie debugowanego obiektu|  
|-------------------|-------------------|  
|Klasa DialogDebuggerVisualizer<br /><br /> Interfejs IDialogVisualizerService|Obiekt danych|  
  
 Interfejs użytkownika pobiera dane, które ma zostać zwizualizowany od dostawcy obiektu, który istnieje po stronie debugera:  
  
|Po stronie debugera|Po stronie debugowanego obiektu|  
|-------------------|-------------------|  
|Klasa DialogDebuggerVisualizer<br /><br /> Interfejs IDialogVisualizerService|Obiekt danych|  
|Obiekt dostawcy (implementuje <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>)||  
  
 Brak odpowiedniego obiektu po stronie debugowanego obiektu o nazwie źródło obiektu:  
  
|Po stronie debugera|Po stronie debugowanego obiektu|  
|-------------------|-------------------|  
|Klasa DialogDebuggerVisualizer<br /><br /> Interfejs IDialogVisualizerService|Obiekt danych|  
|Obiekt dostawcy (implementuje <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>)|Obiekt źródłowy (pochodną <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>)|  
  
 Dostawca obiektu udostępnia dane obiektu, który ma zostać zwizualizowany do wizualizatora interfejsu użytkownika. Obiekt dostawcy pobiera dane obiektu od źródła obiektu. Obiekt dostawcy i źródła obiektu Podaj interfejsów API do przekazywania danych obiektu między stronie debugera i po stronie obiektu debugowanego.  
  
 Każdy wizualizatora musi pobrać obiekt danych, który ma zostać zwizualizowany. W poniższej tabeli przedstawiono odpowiednie interfejsów API, że w tym celu użyć obiektu dostawcy i źródła obiektu:  
  
|Obiekt dostawcy|Obiekt źródłowy|  
|---------------------|-------------------|  
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A><br /><br /> —lub—<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A>|  
  
 Powiadomienia dostawcy obiektów można użyć jednej <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A> lub <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A>. Albo interfejsu API powoduje wywołanie <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A> obiektu źródłowego. Wywołanie <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A?displayProperty=fullName> wypełnia <xref:System.IO.Stream?displayProperty=fullName>, reprezentuje serializacji formularza jest wizualizowanego obiektu.  
  
 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName> deserializuje dane formularza obiektu, który można następnie wyświetlić w utworzeniu za pomocą interfejsu użytkownika do <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> wypełnia dane jako nieprzetworzone `Stream`, które należy wykonać deserializacji samodzielnie. <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName> działa przez wywołanie metody <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> uzyskać zserializowana `Stream`, a następnie podczas deserializacji danych. Użyj <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> gdy obiekt nie jest możliwy do serializacji przez .NET i wymaga niestandardowej serializacji. W takim przypadku należy również zmienić <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.Serialize%2A?displayProperty=fullName> metody.  
  
 Jeśli tworzysz wizualizatora tylko do odczytu, komunikacja jednokierunkowa z <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A> lub <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A> jest wystarczająca. Jeśli tworzysz wizualizatora, który obsługuje edycję obiektów danych, należy to robić więcej. Musi być możliwe do odesłania obiekt danych od dostawcy obiektu do obiektu źródłowego również. W poniższej tabeli przedstawiono dostawcy obiektów i interfejsów API źródłowy obiekt używany w tym celu:  
  
|Obiekt dostawcy|Obiekt źródłowy|  
|---------------------|-------------------|  
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A><br /><br /> —lub—<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A>|  
  
 Zwróć uwagę, ponownie, że istnieją dwa interfejsy API, których można użyć dostawcy obiektów. Zawsze wysłaniu danych z dostawcy obiektu do obiektu źródła jako `Stream`, ale <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A> wymaga, aby serializacji obiektu do `Stream` samodzielnie.  
  
 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A> pobiera obiekt, który podasz, serializuje go do `Stream`, następnie wywołuje <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A> do wysyłania `Stream` do <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A>.  
  
 Przy użyciu jednej z metod Zamień tworzy nowy obiekt danych w debugowanym obiekcie, który zastępuje wizualizowanego obiektu. Jeśli chcesz zmienić zawartość oryginalnego obiektu bez zastąpienia, użyj jednej z metod transferu pokazano w poniższej tabeli. Te interfejsy API transferu danych w obu kierunkach w tym samym czasie bez zastępowania obiektu, który jest wizualizowanego:  
  
|Obiekt dostawcy|Obiekt źródłowy|  
|---------------------|-------------------|  
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferData%2A><br /><br /> —lub—<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.TransferData%2A>|  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: pisanie wizualizatora](../debugger/how-to-write-a-visualizer.md)   
 [Wskazówki: Pisanie wizualizatora w C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)   
 [Wskazówki: Pisanie wizualizatora w Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)   
 [Wskazówki: Pisanie wizualizatora w Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)   
 [Zagadnienia dotyczące zabezpieczeń internetowych](../debugger/visualizer-security-considerations.md)