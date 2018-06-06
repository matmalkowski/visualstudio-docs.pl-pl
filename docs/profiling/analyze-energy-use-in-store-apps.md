---
title: Analiza zużycia energii w aplikacjach platformy uniwersalnej systemu Windows | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 96d06843-b97e-45a8-8126-07478a40bfc4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 4ad28707c6f90a84d69734959f783851e3bc783c
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34692138"
---
# <a name="analyze-energy-use-in-uwp-apps"></a>Analiza zużycia energii w aplikacjach platformy uniwersalnej systemu Windows
Visual Studio **zużycie energii** profilera pomaga analizować zasilania i zużycie energii aplikacji platformy uniwersalnej systemu Windows na tablecie niskiego poboru energii urządzenia z systemem całość lub część czasu na ich własnych baterii. Działająca na urządzeniu zasilanym z baterii aplikacja, która zużywa zbyt dużo energii, może powodować niezadowolenia klienta, przez co klient może ją nawet odinstalować. Optymalizacja zużycia energii można zwiększyć wdrożenia aplikacji i korzystać przez klientów.  
  
## <a name="what-the-energy-consumption-profiler-is-how-it-works-and-what-it-measures"></a>Co to jest profiler Zużycie energii, jak działa i co mierzy  
 Profiler Zużycie energii przechwytuje działania wyświetlacza, procesora i połączeń sieciowych urządzenia podczas sesji profilowania. Następnie generuje szacunki zużycia mocy na potrzeby wykonania tych działań i całkowitej ilości energii dla sesji profilowania.  
  
> [!NOTE]
>  Profiler energii szacuje pobór mocy i zużycie energii, używając programowego modelu standardowego sprzętu referencyjnego, który jest reprezentatywny dla tabletów o niskim poziomie zasilania, na których może być uruchamiana dana aplikacja. Aby uzyskać najlepsze szacunki, zaleca się zbieranie danych profilu na tablecie o niskim poziomie zasilania.  
>   
>  Chociaż model zapewnia dobre oszacowania dla różnych urządzeń o niskim poziomie zasilania, rzeczywiste wartości dotyczące profilowanego urządzenia mogą być inne. Należy użyć wartości, aby wykryć działania wyświetlacza, procesora i sieci, które są kosztowne względem innych działań wykorzystujących zasoby, i mogą nadawać się do optymalizacji.  
  
 Profiler zużycia energii używa tych definicji *zasilania* i *energii*:  
  
-   *Power* środki szybkość, z jaką wymusić służy do wykonywania pracy, który odbywa się w danym okresie czasu. W nauce elektrycznego standardowe jednostki zasilania jest *zasilacz*, która została zdefiniowana jako szybkości, w którym praca jest wykonywana, gdy jeden ampere — bieżący przepływów za pośrednictwem elektrycznego potencjalnych różnica volt jeden. W **zużycia energii** wykresu, jednostki są wyświetlane jako miliwatach **mW** , które są/1000 jeden z watt.  
  
     Należy zauważyć, że moc jest stosunkiem, więc ma kierunek (praca w danym czasie może wzrosnąć lub zmaleć) i szybkość (ilość, o jaką praca rośnie lub maleje).  
  
-   *Energii* środków wynosił łączną ilość zasilania, pojemności lub możliwości, tak jak moc baterii, albo całkowitej mocy czyszcząca w danym okresie czasu. Jednostką energii jest watogodzina, czyli moc jednego wata stosowana równomiernie przez jedną godzinę. W **podsumowanie energii**, jednostki są wyświetlane jako miliwatogodzinach **mW-h**.  
  
 ![Pojemność energii zasilania używane, Całkowita energia używane](../profiling/media/energyprof_capcitypowerused.png "ENERGYPROF_CapcityPowerUsed")  
  
 Na przykład w pełni naładowana bateria w tablecie zawiera pewną ilość zmagazynowanej energii. Gdy energia jest zużywana na potrzeby wykonywania zadań, takich jak komunikacja przez sieć, obliczanie wartości czy wyświetlanie grafiki, moc z baterii jest zużywana z różną szybkością. Dla dowolnego okresu mierzone jest także łączne zużycie mocy.  
  
## <a name="identify-scenarios-with-user-marks"></a>Identyfikowanie scenariuszy ze znacznikami użytkownika  
 Możesz dodać *znaczniki użytkownika* do profilowania dane, aby ułatwić określenie obszarów na linijce osi czasu.  
  
 ![Znaczniki użytkownika na osi czasu](../profiling/media/profilers_usermarktimeline.png "PROFILERS_UserMarkTimeline")  
  
 Znacznik jest wyświetlany na osi czasu w postaci pomarańczowego trójkąta w czasie wykonywania metody. Po umieszczeniu kursora myszy na znaczniku komunikat i czas są wyświetlane jako etykietka narzędzia. Jeśli co najmniej dwa znaczniki użytkownika znajdują się blisko siebie, są scalane, a dane etykietek narzędzia są łączone. Można powiększyć oś czasu, aby rozdzielić znaczniki.  
  
 **Dodaj znaczniki do języka C#, Visual Basic, kod w języku C++**  
  
 Aby dodać znacznik użytkownika do języka C#, najpierw utworzyć kod w języku C++, Visual Basic [Windows.Foundation.Diagnostics LoggingChannel](http://msdn.microsoft.com/library/windows/apps/windows.foundation.diagnostics.loggingchannel.aspx) obiektu. Następnie wstawianie wywołania do [LoggingChannel.LogMessage](http://msdn.microsoft.com/library/windows/apps/dn264210.aspx) metod w punktach swój kod, który ma zostać oznaczone. Użyj [LoggingLevel.Information](http://msdn.microsoft.com/library/windows/apps/windows.foundation.diagnostics.logginglevel.aspx) w wywołaniach.  
  
 Gdy jest wykonywana metoda, znacznik użytkownika jest dodawany do danych profilowania wraz z komunikatem.  
  
> [!NOTE]
>  -   Implementuje Windows.Foundation.Diagnostics LoggingChannel [Windows.Foundation.IClosable](/uwp/api/windows.foundation.iclosable) interfejsu (planowane jako [System.IDisposable](/dotnet/api/system.idisposable) w języku C# i VB). Aby uniknąć przeciek zasoby systemu operacyjnego, należy wywołać [LoggingChannel.Close](/uwp/api/Windows.Foundation.Diagnostics.LoggingChannel) ([Windows.Foundation.Diagnostics.LoggingChannel.Dispose](/uwp/api/Windows.Foundation.Diagnostics.LoggingChannel) w języku C# i VB) po zakończeniu z rejestrowaniem kanał.  
> -   Każdy otwarty kanał rejestrowania musi mieć unikatową nazwę. Próba utworzenia nowego kanału rejestrowania o takiej samej nazwie, jak nazwa aktualnie otwartego kanału, powoduje wyjątek.  
  
 Zobacz przykład zestawu SDK systemu Windows [próbki LoggingSession](http://code.msdn.microsoft.com/windowsapps/LoggingSession-Sample-ccd52336) przykłady.  
  
 **Dodaj znaczniki do kodu JavaScript**  
  
 Aby dodać znaczniki użytkownika, dodaj następujący kod w punktach w kodzie, które chcesz oznaczyć:  
  
```JavaScript  
if (performance && performance.mark) {  
    performance.mark(markDescription);  
}  
```  
  
 *markDescription* jest ciąg znaków zawierający komunikat wyświetlany w etykietce narzędzia znacznik użytkownika.  
  
## <a name="configure-your-environment-for-profiling"></a>Konfigurowanie środowiska do profilowania  
 Można uzyskać dobrą szacuje, należy do profilu aplikacji na urządzeniu zasilane małej jest są zasilane z baterii jego zużycie energii. Ponieważ program Visual Studio nie jest uruchamiane na większości tych urządzeń, należy podłączyć komputer programu Visual Studio do urządzenia za pomocą narzędzi Visual Studio remote tools. Aby podłączyć urządzenie zdalne, należy skonfigurować zarówno projekt programu Visual Studio, jak i urządzenie zdalne. Zobacz [aplikacji platformy uniwersalnej systemu Windows uruchom na komputerze zdalnym](../debugger/run-windows-store-apps-on-a-remote-machine.md) Aby uzyskać więcej informacji.  
  
> [!TIP]
>  -   Nie zaleca się energii profilowania w symulatorze platformy uniwersalnej systemu Windows lub na komputerze programu Visual Studio. Profilowanie na rzeczywistym urządzeniu umożliwia uzyskanie bardziej realistycznych danych.  
> -   Profiluj urządzenie docelowe zasilane z baterii.  
> -   Zamknij inne aplikacje, które mogą używać tych samych zasobów (sieci, procesora lub wyświetlacza).  
  
## <a name="collect-energy-profile-data-for-your-app"></a>Zbieranie danych profilu energetycznego aplikacji  
  
1.  Na **debugowania** menu, wybierz **Start diagnostycznych bez debugowania**.  
  
     ![Wybierz urządzenia i zużycie energii w Centrum diagnostyki](../profiling/media/energyprof_diagnosticshub.png "ENERGYPROF_DiagnosticsHub")  
  
2.  Wybierz **zużycie energii** , a następnie wybierz **Start**.  
  
    > [!NOTE]
    >  Po rozpoczęciu **zużycie energii** profilera, można napotkać **Kontrola konta użytkownika** okna żąda Twoje uprawnienia do uruchamiania *VsEtwCollector.exe*. Wybierz **tak**.  
  
3.  Zbadaj aplikację w celu zebrania danych.  
  
4.  Aby zatrzymać profilowanie, przełączyć się do programu Visual Studio (Alt + Tab), a następnie wybierz pozycję **zatrzymać zbieranie** na stronie Centrum diagnostyki.  
  
     ![Zatrzymaj zbieranie danych](../profiling/media/xamlprof_stopcollection.png "XAMLProf_StopCollection")  
  
     Program Visual Studio analizuje zebrane dane i wyświetla wyniki.  
  
## <a name="collect-energy-profile-data-for-an-installed-app"></a>Zbieranie danych profilu energetycznego zainstalowanej aplikacji  
 Narzędzie zużycia energii można uruchomić tylko na aplikacji platformy uniwersalnej systemu Windows, które są uruchamiane z rozwiązania Visual Studio lub są instalowane z Microsoft Store. Gdy rozwiązanie jest otwarty w programie Visual Studio, domyślny obiekt docelowy jest **projekt startowy**. Aby określić zainstalowaną aplikację jako obiekt docelowy:  
  
1.  Wybierz **zmiany docelowego** , a następnie wybierz **zainstalowanych aplikacji**.  
  
2.  Z **Wybierz zainstalowany pakiet aplikacji** wybierz element docelowy.  
  
3.  Wybierz **zużycie energii** na stronie Centrum diagnostyki.  
  
4.  Wybierz **Start** można rozpocząć profilowania.  
  
 Aby zatrzymać profilowanie, przełączyć się do programu Visual Studio (Alt + Tab), a następnie wybierz pozycję **zatrzymać zbieranie** na stronie Centrum diagnostyki.  
  
## <a name="analyze-energy-profile-data"></a>Analizowanie danych profilu energetycznego  
 Dane profilu energetycznego są wyświetlane w oknie dokumentu programu Visual Studio:  
  
 ![Strona raportu profilera energii](../profiling/media/energyprof_all.png "ENERGYPROF_All")  
  
|||  
|-|-|  
|![Krok 1](../profiling/media/procguid_1.png "ProcGuid_1")|Plik raportu nosi nazwę raportu*RRRRMMDD-hh: mm*.diagsession. Jeśli zechcesz zapisać raport, możesz zmienić jego nazwę.|  
|![Krok 2](../profiling/media/procguid_2.png "ProcGuid_2")|Na osi czasu są widoczne długość sesji profilowania, zdarzenia aktywacji cyklu życia aplikacji i znaczniki użytkownika.|  
|![Krok 3](../profiling/media/procguid_3.png "ProcGuid_3")|Raport można ograniczyć do części osi czasu, przeciągając niebieskie paski w celu wybrania regionu na osi czasu.|  
|![Krok 4](../profiling/media/procguid_4.png "ProcGuid_4")|**Zużycia energii** wykresu jest wykres wielowierszowego przedstawia zmiany w danych wyjściowych zasilania powodowany przez zasób urządzenia podczas sesji profilowania. Profiler Zużycie energii śledzi moc zużywaną przez procesor, działania sieciowe i wyświetlanie na ekranie.|  
|![Krok 5](../profiling/media/procguid_6.png "ProcGuid_6")|**Zasobów (włączone/wyłączone)** wykres zawiera szczegółowe informacje o sieci kosztów energii. **Sieci** pasek reprezentuje czas, który połączenie sieciowe jest otwarty. **Transferu danych** pasek podrzędnych jest czas, aby aplikacja była odbieranie i wysyłanie danych przez sieć.|  
|![Krok 6](../profiling/media/procguid_6a.png "ProcGuid_6a")|**Podsumowanie użycia energii** zawiera jaka całkowitej energii, którego użyto w wybranej osi czasu procesora CPU, działanie sieci i na ekranie.|  
  
 **Do analizowania danych profilu energii**  
  
 Znajdź obszar, w którym wzrosła moc zużywana przez zasoby. Powiąż ten obszar wzrostu z działaniem aplikacji. Następnie użyj pasków sterowania na osi czasu, aby powiększyć ten obszar. Jeśli są koncentruje się na użycie sieci, rozwiń **sieci** w węźle **zasobów (włączone/wyłączone)** wykres tak, aby porównać połączenie sieciowe jest otwarty, aby podczas odbierania lub przesyłania aplikacji w czasie dane za pośrednictwem połączenia. Skrócenie czasu niepotrzebnego otwarcia połączenia sieciowego to bardzo efektywny sposób optymalizacji.  
  
## <a name="optimize-energy-use"></a>Optymalizacja zużycia energii  
 Połączenia sieciowe generują koszty energii nie tylko podczas przesyłania danych, ale także podczas inicjowania, obsługi i wyłączania połączenia. Niektóre sieci obsługują połączenie przez pewien czas po zakończeniu wysyłania lub odbierania danych, aby umożliwić transmisję większej ilości danych za pośrednictwem jednego połączenia. Można użyć **zasobów (włączone/wyłączone)** okienko, aby zbadać sposób aplikacji współdziała z połączeniem.  
  
 ![Zasoby &#40;na&#47;poza&#41; okienko](../profiling/media/energyprof_resources.png "ENERGYPROF_Resources")  
  
 Jeśli **sieci** i **transferu danych** paski widoczne czy połączenie jest otwarte przez dłuższe okresy sporadycznie przesyłać szereg pakiety danych w małych, można partii danych do wysyłania w jednym transmisji skrócić czas, który jest otwarty w sieci, a w związku z tym ograniczenia kosztów energii.  
  
 ![Okienko Podsumowanie zużycia energii](../profiling/media/energyprof_summary.png "ENERGYPROF_Summary")  
  
 Koszty energii zużywanej przez wyświetlacz trudniej jest kontrolować. Większości ekranów potrzebuje więcej energii do wyświetlania jasnych kolorów niż do wyświetlania kolorów ciemniejszych, więc użycie ciemnego tła stanowi jedyny sposób zmniejszenia kosztów.  
  
## <a name="other-resources"></a>Inne zasoby  
  
-   **Stan połączenia i kosztów zarządzania** sekcje dla [C# / VB/C++ i XAML](http://msdn.microsoft.com/en-us/0ee0b706-8432-4d49-9801-306ed90764e1) i [JavaScript i HTML](http://msdn.microsoft.com/en-us/372afa6a-1c7c-4657-967d-03a77cd8e933) w Centrum deweloperów systemu Windows opisano interfejsów API systemu Windows, które zapewniają informacje łączność sieci używaną przez aplikację do minimalizuje to koszt ruchu sieciowego.  
  
     Symulator Visual Studio dla aplikacji platformy uniwersalnej systemu Windows umożliwia symulowanie właściwości połączenia danych informacji o sieci interfejsów API. Zobacz [uruchamianie aplikacji platformy UWP w symulatorze](../debugger/run-windows-store-apps-in-the-simulator.md)  
  
-   **Chronometrażu funkcji JavaScript** i **użycie procesora CPU** narzędzia może pomóc zmniejszyć obciążenie procesora CPU, gdy jest spowodowany przez funkcje nieefektywne. Zobacz [procesora analizowanie](../profiling/analyze-cpu-usage-in-a-windows-universal-app.md).

## <a name="see-also"></a>Zobacz także
 [Profilowanie w programie Visual Studio](../profiling/index.md)  
 [Przewodnik po funkcjach profilowania](../profiling/profiling-feature-tour.md)