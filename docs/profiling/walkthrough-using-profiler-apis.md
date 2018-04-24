---
title: 'Wskazówki: Korzystanie z interfejsów API profilera | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
ms.assetid: c2ae0b3e-a0ca-4967-b4df-e319008f520e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9bebc312858e16688598ba289e4c53d93010122b
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="walkthrough-using-profiler-apis"></a>Wskazówki: korzystanie z interfejsów API profilera
Instruktaż nawiązywał prezentują sposób użycia aplikacji C# [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] API narzędzi profilowania. Aby ograniczyć ilość danych zbieranych podczas profilowania Instrumentacji użyjesz profilera interfejsów API.  
  
 Kroki opisane w tym przewodniku są zazwyczaj stosowane do aplikacji C/C++. Dla każdego języka będzie trzeba odpowiednio skonfigurować środowisko kompilacji.  
  
 Zazwyczaj powoduje rozpoczęcie analizowanie wydajności aplikacji za pomocą przykładowej profilowania. Jeśli przykładowe profilowania nie zapewnia informacje, które określa wąskiego gardła, profilowanie Instrumentacji zapewniają większy poziom szczegółowości. Profilowanie Instrumentacji jest bardzo przydatna do badania interakcji wątku.  
  
 Jednak większy poziom szczegółowości oznacza, że dane są zbierane. Może się okazać, że profilowanie Instrumentacji tworzy pliki dużej ilości danych. Ponadto Instrumentacji jest bardziej prawdopodobne, że wpływ na wydajność aplikacji. Aby uzyskać więcej informacji, zobacz [wartościami danych Instrumentacji opis](../profiling/understanding-instrumentation-data-values.md) i [wartościami danych próbkowania opis](../profiling/understanding-sampling-data-values.md)  
  
 Profilera Visual Studio umożliwia ograniczenie zbierania danych. Ten przewodnik zawiera przykładowy sposób ograniczyć zbieranie danych przy użyciu interfejsów API profilera. Profilera Visual Studio udostępnia interfejs API kontrolowanie zbierania danych z aplikacji.  
  
 Dla kodu natywnego profilera Visual Studio interfejsy API są VSPerf.dll. Plik nagłówka, VSPerf.h i biblioteki importu, VSPerf.lib, znajdują się w katalogu narzędzi Narzędzia 9\Team programu Microsoft Visual Studio.  
  
 Dla kodu zarządzanego profilera interfejsy API są Microsoft.VisualStudio.Profiler.dll. Ta biblioteka DLL znajduje się w katalogu narzędzi Narzędzia 9\Team programu Microsoft Visual Studio. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.Profiler>.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym przewodniku przyjęto założenie, że wybór środowisko projektowe jest skonfigurowany do obsługi debugowania i pobierania próbek. Przegląd wymagań wstępnych można znaleźć w następujących tematach:  
  
 [Porady: Wybieranie metod kolekcji](../profiling/how-to-choose-collection-methods.md)  
  
 [Porady: odwołania informacji o symbolach systemu Windows](../profiling/how-to-reference-windows-symbol-information.md)  
  
 Domyślnie podczas uruchamiania profilera profiler zbiera dane na poziomie globalnym. Następujący kod na początku program włącza globalne profilowania wyłączone.  
  
```  
DataCollection.StopProfile(  
ProfileLevel.Global,  
DataCollection.CurrentId);  
```  
  
 Można wyłączyć zbieranie danych w wierszu polecenia bez użyciu wywołania interfejsu API. W następujących krokach założono, środowiska kompilacji wiersza polecenia jest skonfigurowany do uruchamiania z narzędzi do profilowania i jako narzędzia do programowania. W tym ustawienia wymagane dla VSInstr i narzędzia VSPerfCmd. Zobacz narzędzi profilowania z wiersza polecenia.  
  
## <a name="limiting-data-collection-using-profiler-apis"></a>Ograniczanie kolekcji danych przy użyciu interfejsów API profilera  
  
#### <a name="to-create-the-code-to-profile"></a>Aby utworzyć kod do profilu  
  
1.  Utwórz nowy projekt C# w programie Visual Studio lub korzystanie z kompilacji wiersza polecenia, w zależności od swoich preferencji.  
  
    > [!NOTE]
    >  Biblioteka Microsoft.VisualStudio.Profiler.dll, znajduje się w katalogu narzędzia narzędzia 9\Team programu Microsoft Visual Studio musi odwoływać się kompilację.  
  
2.  Skopiuj i wklej następujący kod do projektu:  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using Microsoft.VisualStudio.Profiler;  
  
    namespace ConsoleApplication2  
    {  
        class Program  
        {  
            public class A  
            {  
             private int _x;  
  
             public A(int x)  
             {  
              _x = x;  
             }  
  
             public int DoNotProfileThis()  
             {  
              return _x * _x;  
             }  
  
             public int OnlyProfileThis()  
             {  
              return _x + _x;  
             }  
  
             public static void Main()  
             {  
            DataCollection.StopProfile(  
            ProfileLevel.Global,  
            DataCollection.CurrentId);  
              A a;  
              a = new A(2);  
              int x;      
              Console.WriteLine("2 square is {0}", a.DoNotProfileThis());  
              DataCollection.StartProfile(  
                  ProfileLevel.Global,  
                  DataCollection.CurrentId);  
              x = a.OnlyProfileThis();  
              DataCollection.StopProfile(  
                  ProfileLevel.Global,   
                  DataCollection.CurrentId);  
              Console.WriteLine("2 doubled is {0}", x);  
             }  
            }  
  
        }  
    }  
    ```  
  
#### <a name="to-collect-and-view-data-in-the-visual-studio-ide"></a>Do zbierania i wyświetlania danych w środowisku IDE programu Visual Studio  
  
1.  Otwórz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE. Do **Analizuj** menu wskaż **profilera**, a następnie wybierz **nowej sesji wydajności.**  
  
2.  Dodaj użytkownika skompilowanym plikiem binarnym do **cele** listy w **Eksplorator wydajności** okna. Kliknij prawym przyciskiem myszy **elementy docelowe**, a następnie wybierz **dodać docelowy binarne**. Zlokalizuj plik binarny w **dodać docelowy binarne** , a następnie kliknij przycisk **Otwórz**.  
  
3.  Wybierz **Instrumentacji** z **metody** listy na **Eksplorator wydajności** paska narzędzi.  
  
4.  Kliknij przycisk **uruchamianie o profilowania**.  
  
     Profiler będzie Instrumentacja i wykonaj plik binarny i tworzy plik raportu wydajności. Plik raportu wydajności będą wyświetlane w **raporty** węzła **Eksplorator wydajności**.  
  
5.  Otwórz wynikowy plik raportu wydajności.  
  
 Domyślnie podczas uruchamiania profilera profilera będzie zbierać dane na poziomie globalnym. Następujący kod na początku program włącza globalne profilowania wyłączone.  
  
```  
DataCollection.StopProfile(  
ProfileLevel.Global,  
DataCollection.CurrentId);  
```  
  
#### <a name="to-collect-and-view-data-at-the-command-line"></a>Aby zbierać i przeglądać dane w wierszu polecenia  
  
1.  Kompiluj wersję do debugowania kodu przykładowej utworzonego w procedurze "Tworzenie kodu do profilu" we wcześniejszej części tego przewodnika.  
  
2.  Profilowanie aplikacji zarządzanej, wpisz następujące polecenie, aby ustawić zmienne środowiskowe odpowiednie:  
  
     **VsPefCLREnv /traceon**  
  
3.  Wpisz następujące polecenie:**VSInstr \<nazwa pliku > .exe**  
  
4.  Wpisz następujące polecenie:**/Output /start:trace VSPerfCmd:\<nazwa pliku > plik Vsp**  
  
5.  Wpisz następujące polecenie:**VSPerfCmd /globaloff**  
  
6.  Wykonanie programu.  
  
7.  Wpisz następujące polecenie:**VSPerfCmd/shutdown**  
  
8.  Wpisz następujące polecenie:**VSPerfReport/calltrace:\<nazwa pliku > plik Vsp**  
  
     Plik CSV jest tworzony w bieżącym katalogu z danych wydajności.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Profiler>   
 [Interfejsy API profilera Visual Studio (Native)](../profiling/visual-studio-profiler-api-reference-native.md)   
 [Wprowadzenie](../profiling/getting-started-with-performance-tools.md)   
 [Profilowanie z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)