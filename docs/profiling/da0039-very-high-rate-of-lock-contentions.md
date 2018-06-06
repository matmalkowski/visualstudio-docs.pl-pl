---
title: 'DA0039: Bardzo wysoka liczba rywalizacji blokad | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.39
- vs.performance.DA0039
- vs.performance.rules.DA0039
ms.assetid: 5a9fc57d-9097-413b-af0c-8726b1a57048
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 153b979dffed48dbce355faae7125f2bd338fd08
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34750444"
---
# <a name="da0039-very-high-rate-of-lock-contentions"></a>DA0039: Bardzo wysoka liczba rywalizacji blokad
|||  
|-|-|  
|Identyfikator reguły|DA0039|  
|Kategoria|Sposób użycia programu .NET framework|  
|Metod profilowania|Pobierania próbek<br /><br /> Oprzyrządowanie<br /><br /> Pamięci platformy .NET|  
|Komunikat|Występuje bardzo wysoka liczba rywalizacji o blokadę platformy .NET. Zbadaj przyczynę tych rywalizacji, uruchamiając profil współbieżność.|  
|Typ reguły|Ostrzeżenie|  
  
 Gdy profilu można za pomocą próbkowania, pamięci platformy .NET lub metody kontencji zasobów, należy zebrać co najmniej 25 próbek do wyzwolenia tej reguły.  
  
## <a name="cause"></a>Przyczyna  
 Dane wydajności systemu, które są zbierane z danych profilowania wskazuje zbyt wysoka liczba rywalizacji blokad, który wystąpił podczas wykonywania aplikacji. Należy rozważyć profilowanie ponownie, używając metoda profilowania współbieżności do odnalezienia przyczyny konfliktu.  
  
## <a name="rule-description"></a>Opis reguły  
 Blokady są używane do ochrony krytycznych fragmentów kodu, który musi zostać wykonane szeregowe przez jeden wątek na czas w aplikacji wielowątkowych. Microsoft .NET CLR czasu wykonywania (języka wspólnego CLR) zapewnia zbiór pełnej synchronizacji i blokowanie elementów podstawowych. Na przykład w języku C# obsługuje instrukcji "lock" (SyncLock w języku Visual Basic). Zarządzanej aplikacji można wywołać metody Monitor.Enter i Monitor.Exit w system.Threading — przestrzeń nazw nabywanie i zwolnić blokady bezpośrednio. .NET Framework obsługuje dodatkowe synchronizacji i blokowanie elementów podstawowych, w tym klas, które obsługują muteksy ReaderWriterLocks i semaforów. Aby uzyskać więcej informacji, zobacz [podstawowych Omówienie synchronizacji](http://go.microsoft.com/fwlink/?LinkId=177867) w przewodniku programistów platformy .NET Framework w witrynie MSDN. Klasy .NET Framework są nałożone usługi synchronizacji niższego poziomu wbudowane w system operacyjny Windows. Obejmują one obiekty sekcja krytyczna wiele różnych oczekiwania i zdarzenie sygnalizujące funkcji. Aby uzyskać więcej informacji, zobacz [synchronizacji](http://go.microsoft.com/fwlink/?LinkId=177869) sekcji Win32 i COM Programowanie w bibliotece MSDN.  
  
 Zarówno .NET Framework klas i obiektów macierzystych systemu Windows, które są używane do synchronizacji i blokowanie są lokalizacji pamięci współużytkowanej, które należy zmienić przy użyciu operacje blokowane. Blokowanej operacji użyj specyficzne dla sprzętu instrukcje, które działają w lokalizacji pamięci współużytkowanej zmianę ich stanu przy użyciu operacji niepodzielnych. Niepodzielne operacje dotrą do wszystkich procesorów na maszynie. Blokad i elementów WaitHandle są obiektami .NET, które automatycznie używają operacje blokowane, jeśli są one skonfigurować lub zresetować. Mogą występować inne pamięci współużytkowanej struktury danych w aplikacji, która wymaga również użycia operacje blokowane w celu zaktualizowania w sposób wątkowo. Aby uzyskać więcej informacji, zobacz [operacji Blokowanej](http://go.microsoft.com/fwlink/?LinkId=177870) w sekcji .NET Framework w bibliotece MSDN.  
  
 Synchronizacji i blokowanie to mechanizmy służące do zapewnienia poprawnie wykonać wielowątkowości aplikacji. Każdy wątek aplikacji wielowątkowych jest jednostką niezależne wykonywania z harmonogramem niezależnie przez system operacyjny. Rywalizacji blokad występuje, gdy wątek, który próby uzyskania blokady jest opóźnione, ponieważ inny wątek jest blokadą.  
  
 Blokady są często zagnieżdżone. Zagnieżdżanie występuje, gdy wątek wykonywania sekcja krytyczna wykonuje funkcję, która następnie wymaga kolejną blokadę. Niektóre ilość zagnieżdżenia blokady jest nieuniknione. Krytyczne sekcji może wywołać metody .NET Framework korzystający blokad, aby upewnić się, że jest bezpieczne wątkowo. Wywołania z niektórych sekcja krytyczna w aplikacji do metody Framework, która również blokuje przy użyciu dojścia do różnych blokady powoduje, że blokad zagnieździć. Zagnieżdżone warunki blokowania może prowadzić do problemów z wydajnością, które są bardzo trudne do unravel i napraw.  
  
 Ta zasada generowane, gdy pomiarów podczas przebiegu profilowania wskazywać jest zbyt dużej ilości rywalizacji blokad. Rywalizacji blokad opóźnienie wykonywania wątków, które oczekują na blokadę. Należy zbadać nawet stosunkowo małej ilości rywalizacji blokad w testach jednostkowych lub w testach obciążenia uruchomione na sprzęcie końcowy dolnej.  
  
> [!NOTE]
>  Gdy liczba rywalizacji blokad zgłoszone w danych profilowania jest istotne, ale nie nadmiernego [DA0038: wysoka liczba rywalizacji blokad](../profiling/da0038-high-rate-of-lock-contentions.md) komunikat z informacjami uruchamiane, a ten komunikat ostrzegawczy.  
  
## <a name="how-to-investigate-a-warning"></a>Jak badać ostrzeżenie  
 Kliknij dwukrotnie komunikat, aby przejść do [znaczniki](../profiling/marks-view.md) widoku danych profilowania.  Znajdź **.NET CLR LocksAndThreads\Contention szybkość / sekundę** kolumny. Określa, czy określone fazy wykonywania programu rywalizacji blokad w przypadku większych niż inne faz.  
  
 Ta zasada uruchamia się tylko wtedy, gdy nie jest używana metoda profilowania współbieżności. Metoda profilowania współbieżności jest najlepszym narzędziem służące do diagnozowania problemów z wydajnością związane z rywalizacji blokad w aplikacji. Zbieraj dane, aby zrozumieć zachowania blokującego aplikacji profilowania współbieżności. Dotyczy to również opis blokad, które są mocno utrzymywał, jak długo wątku czasu wykonywania jest opóźnione oczekiwania na utrzymywał blokad i jakie kod jest powiązana. Współbieżność profile zbiera dane na wszystkich zablokować rywalizacji, w tym zachowania blokującego natywnego urządzeń systemu Windows, klas .NET Framework i innych bibliotek innych firm aplikacji odwołań. Aby uzyskać informacje dotyczące profilowania współbieżności z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE, zobacz [zbierania danych współbieżności wątku i procesu](../profiling/collecting-thread-and-process-concurrency-data.md). Linki do informacji dotyczących współbieżności profilowania z wiersza polecenia dla **zbieranie danych działania rywalizacji i wątku zasobów przy użyciu metody współbieżności** sekcji [Użyj metod profilowania z Wiersz polecenia](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md).