---
title: "Porady: Korzystanie ze znaczników wizualizatora współbieżności SDK | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19a45032-f8a7-4137-890e-2ceeec938b8d
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 794a853db12f106e8f7002d93bca798d45bb582c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-concurrency-visualizer-markers-sdk"></a>Porady: korzystanie ze znaczników wizualizatora współbieżności SDK
W tym temacie przedstawiono sposób użycia zestawu wizualizatora współbieżności SDK do tworzenia zakresów i zapisać flagi, wiadomości i alerty.  
  
### <a name="to-use-c"></a>Aby użyć C++  
  
1.  Dodawanie obsługi SDK wizualizatora współbieżności dla aplikacji. Aby uzyskać więcej informacji, zobacz [SDK wizualizatora współbieżności](../profiling/concurrency-visualizer-sdk.md).  
  
2.  Dodaj `include` instrukcji i `using` instrukcji dla zestawu SDK.  
  
    ```C++  
  
    #include <cvmarkersobj.h>  
    using namespace Concurrency::diagnostic;  
  
    ```  
  
3.  Dodaj kod, aby utworzyć trzy zakresy w domyślnej serii znacznika i zapisywanie flagi, komunikat oraz alertu, do każdego zakresu. Metody można zapisać flagi, wiadomości i alerty są elementami członkowskimi [marker_series](../profiling/marker-series-class.md) klasy. Konstruktor [span](../profiling/span-class.md) wymaga klasy `marker_series` obiektu, dzięki czemu każdy zakres jest skojarzony z serii określonego znacznika. A `span` kończy się po jej usunięciu.  
  
    ```C++  
  
    marker_series series;  
    span *flagSpan = new span(series, 1, _T("flag span"));  
    series.write_flag(_T("Here is the flag."));  
    delete flagSpan;  
  
    span *messageSpan = new span(series, 2, _T("message span"));  
    series.write_flag(_T("Here is the message."));  
    delete messageSpan;  
  
    span *alertSpan = new span(series, 3, _T("alert span"));  
    series.write_flag(_T("Here is the alert."));  
    delete alertSpan;  
  
    ```  
  
4.  Na pasku menu wybierz **Analizuj**, **Concurrency Visualizer**, **rozpoczynać się od bieżącego projektu** Aby uruchomić aplikację i wyświetlić wizualizatora współbieżności. Na poniższej ilustracji przedstawiono trzy znaczniki i trzy zakresy w wizualizatora współbieżności.  
  
     ![CONCURRENCY Visualizer z 3 znaczniki i alertami](../profiling/media/cvmarkersnative.png "CvMarkersNative")  
  
5.  Dodaj kod, aby utworzyć dodatkowe, niestandardowe znacznika serii przez wywołanie konstruktora dla `marker_series` pobierającej nazwy ciągu serii znacznika.  
  
    ```C++  
  
    marker_series flagSeries(_T("flag series"));  
    span *flagSeriesSpan = new span(flagSeries, 1, _T("flag span"));  
    flagSeries.write_flag(1, _T("flag"));  
    // Sleep to even out the display in the Concurrency Visualizer.  
    Sleep(50);  
    delete flagSeriesSpan;  
  
    marker_series messageSeries(_T("message series"));  
    span *messageSeriesSpan = new span(messageSeries, 1, _T("message span"));  
    messageSeries.write_message(1, _T("message"));  
    // Sleep to even out the display in the Concurrency Visualizer.  
    Sleep(50);  
    delete messageSeriesSpan;  
  
    ```  
  
6.  Uruchom bieżącego projektu, aby wyświetlić wizualizatora współbieżności. Znacznik dwóch serii pojawiają się w ich własnych pasm w widoku wątków. Na poniższej ilustracji przedstawiono dwa nowe zakresy.  
  
     ![CONCURRENCY Visualizer z 3 serii znacznika niestandardowego](../profiling/media/cvmarkerseriesnative.png "CvMarkerSeriesNative")  
  
### <a name="to-use-visual-basic-or-c"></a>Aby użyć programu Visual Basic lub C# #
  
1.  Dodawanie obsługi SDK wizualizatora współbieżności dla aplikacji. Aby uzyskać więcej informacji, zobacz [SDK wizualizatora współbieżności](../profiling/concurrency-visualizer-sdk.md).  
  
2.  Dodaj `using` lub `Imports` instrukcji dla zestawu SDK.  
  
    ```VB  
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation  
  
    ```  
  
    ```CSharp  
    using Microsoft.ConcurrencyVisualizer.Instrumentation;  
    ```  
  
3.  Dodaj kod, aby utworzyć trzy zakresy na domyślną serię znacznika i zapisywanie flagi, komunikat oraz alertu, do każdego zakresu. Możesz utworzyć <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Span> obiektu przez wywołanie metody statycznych `EnterSpan` metody. Można zapisać do serii domyślnej, użyj metody statycznej zapisu <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers> klasy.  
  
    ```VB  
  
    Dim flagSpan As Span = Markers.EnterSpan("flag span")  
    Markers.WriteFlag("Here is the flag.")  
    flagSpan.Leave()  
  
    Dim messageSpan As Span = Markers.EnterSpan("message span")  
    ' Sleep for a millisecond to even out the display in the Concurrency Visualizer.  
    System.Threading.Thread.Sleep(1)  
    Markers.WriteMessage("Here is a message")  
    messageSpan.Leave()  
  
    Dim alertSpan As Span = Markers.EnterSpan("alert span")  
    ' Sleep for a millisecond to even out the display in the Concurrency Visualizer.  
    System.Threading.Thread.Sleep(1)  
    Markers.WriteAlert("Here is an alert")  
    alertSpan.Leave()  
  
    ```  
  
    ```CSharp  
  
    Span flagSpan = Markers.EnterSpan("flag span");  
    Markers.WriteFlag("Here is the flag.");  
    flagSpan.Leave();  
  
    Span messageSpan = Markers.EnterSpan("message span");  
    // Sleep for a millisecond to even out the display in the Concurrency Visualizer.  
    System.Threading.Thread.Sleep(1);  
    Markers.WriteMessage("Here is a message");  
    messageSpan.Leave();  
  
    Span alertSpan = Markers.EnterSpan("alert span");  
    // Sleep for a millisecond to even out the display in the Concurrency Visualizer.  
    System.Threading.Thread.Sleep(1);  
    Markers.WriteAlert("Here is an alert");  
    alertSpan.Leave();  
    ```  
  
4.  Na pasku menu wybierz **Analizuj**, **Concurrency Visualizer**, **rozpoczynać się od bieżącego projektu** Aby uruchomić aplikację i wyświetlić wizualizatora współbieżności. Na poniższej ilustracji przedstawiono trzy znaczniki i trzy zakresy w widoku wątków wizualizatora współbieżności.  
  
     ![CONCURRENCY Visualizer ze znacznikami i alerty](../profiling/media/cvmarkersmanaged.png "CvMarkersManaged")  
  
5.  Dodaj kod, aby utworzyć serii znacznika klienta przy użyciu statycznych <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.CreateMarkerSeries%2A> metody. <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerSeries> Klasa zawiera metody służące do tworzenia zakresów i zapisywanie flagi, wiadomości i alerty.  
  
    ```VB  
  
    Dim flagSeries As MarkerSeries = Markers.DefaultWriter.CreateMarkerSeries("flag series")  
    Dim flagSeriesSpan As Span = flagSeries.EnterSpan("flag span")  
    System.Threading.Thread.Sleep(1)  
    flagSeries.WriteFlag(1, "flag")  
    System.Threading.Thread.Sleep(1)  
    flagSeriesSpan.Leave()  
  
    Dim messageSeries As MarkerSeries = Markers.DefaultWriter.CreateMarkerSeries("message series")  
    Dim messageSeriesSpan As Span = messageSeries.EnterSpan("message span")  
    messageSeries.WriteMessage("message")  
    System.Threading.Thread.Sleep(1)  
    messageSeriesSpan.Leave()  
    ```  
  
    ```CSharp  
  
    MarkerSeries flagSeries = Markers.DefaultWriter.CreateMarkerSeries("flag series");  
    Span flagSeriesSpan = flagSeries.EnterSpan("flag span");  
    System.Threading.Thread.Sleep(1);  
    flagSeries.WriteFlag(1, "flag");  
    System.Threading.Thread.Sleep(1);  
    flagSeriesSpan.Leave();  
  
    MarkerSeries messageSeries = Markers.DefaultWriter.CreateMarkerSeries("message series");  
    Span messageSeriesSpan = messageSeries.EnterSpan("message span");  
    messageSeries.WriteMessage("message");  
    System.Threading.Thread.Sleep(1);  
    messageSeriesSpan.Leave();  
    ```  
  
6.  Uruchom bieżącego projektu, aby wyświetlić wizualizatora współbieżności. Seria trzech znacznika pojawiają się w ich własnych pasm w widoku wątków. Na poniższej ilustracji przedstawiono trzy nowe zakresy.  
  
     ![CONCURRENCY Visualizer z 3 serii znacznika niestandardowego](../profiling/media/cvmarkerseriesmanaged.png "CvMarkerSeriesManaged")  
  
## <a name="see-also"></a>Zobacz też  
 [Zestaw SDK narzędzia Concurrency Visualizer](../profiling/concurrency-visualizer-sdk.md)
