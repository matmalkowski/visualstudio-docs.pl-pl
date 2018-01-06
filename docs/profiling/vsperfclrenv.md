---
title: VSPerfCLREnv | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- command-line tools, VSPerfCLREnv
- command line, tools
- performance tools, VSPerfCLREnv
- profiling tools,VSPerfCLREnv
- VSPerfCLREnv tool
ms.assetid: 4bc9dd6e-379c-4930-9bba-59a4faa93303
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a8f41fdf3a337fb2dea5ccca7131de34743c9096
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="vsperfclrenv"></a>VSPerfCLREnv
VSPerfCLREnv — narzędzie służy do ustawiania zmiennych środowiskowych, które są wymagane do profilu aplikacji .NET Framework. Używa następującej składni:  
  
```  
VsPerfCLREnv [/option]  
```  
  
 Możesz wybrać opcję zależy od tego, z trzech typów profilowania, należy użyć: próbkowania i instrumentacji, lub globalnego. Osobną opcją jest wymagany do dołączenia danych o interakcji między warstwy danych profilowania. W poniższych tabelach opisano składnię dla każdej opcji.  
  
> [!NOTE]
>  Po zakończeniu uruchom profilowanie, **VSPerfCLREnv** z **/ Wyłącz** lub **/globaloff** opcję, aby usunąć niezbędne do profilowania zmiennych środowiskowych. Aby uzyskać więcej informacji zobacz VSPerfCLREnv opcji, aby usunąć ustawienia środowiska pokazano poniżej.  
  
 **VSPerfCLREnv opcje dołączenia danych o interakcji między warstwy**  
  
> [!WARNING]
>  Informacje o profilowaniu interakcji między warstwami można zbierać w programach [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] i [!INCLUDE[vs_pro_current_short](../profiling/includes/vs_pro_current_short_md.md)], Jednak interakcja warstwowa profilowania danych jest możliwy tylko w [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] i [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  
  
 Profilowanie interakcji między warstwami zawiera dodatkowe informacje o zapytaniach ADO.NET w aplikacjach wielowarstwowych. Dane są zbierane tylko dla wywołań synchronicznych funkcji. Danych o interakcji między można dodać do dowolnego profilowania uruchomić przy użyciu dowolnej metody profilowania.  
  
 **InteractionOn** i **GlobalInteractionOn** opcji Włącz opcję zbierania danych o interakcji między warstwy. Opcja interakcji musi być ustawiona, po ustawienie zmiennej środowiskowej VSPerfCLREnv, który jest wymagany do profilu aplikacji.  
  
 Poniższy przykład zawiera warstwę danych o interakcji między w przebiegu profilowania, która używa metody pobierania próbek:  
  
```  
VSPerfCLREnv /SampleOn  
VSPerfCLREnv /InteractionOn  
VSPerfCmd /Start:Sample /Output:MyApp.exe.vsp /Launch:MyApp.exe  
```  
  
 Poniższy przykład zawiera warstwę danych o interakcji między do profilowania uruchomienia usługi systemu Windows:  
  
```  
VSPerfCLREnv /GlobalSampleOn  
VSPerfCLREnv /GlobalInteractionOn  
REM Restart the computer and start the service  
VSPerfCmd /Start:Sample /Output:MyService.exe.vsp   
VSPerfCmd /Attach:MyService.exe  
```  
  
 **Opcje VSPerfCLREnv przetworzyć profilowania Instrumentacji**  
  
 W poniższej tabeli opisano opcje VSPerfCLREnv do profilowania Instrumentacji:  
  
|Opcja|Opis|  
|------------|-----------------|  
|**TraceOn**|Włącza profilowanie, przy użyciu metody instrumentacji. Nie obsługuje alokacji pamięci profilowania lub zbieranie danych o okresie istnienia obiektu.|  
|**TraceGC**|Włącza profilowanie przydziału pamięci przy użyciu metody instrumentacji. Nie umożliwia zbieranie danych o okresie istnienia obiektu.|  
|**TraceGCLife**|Umożliwia przydzielanie pamięci profilowania i zbieranie danych o okresie istnienia obiektu przy użyciu metody instrumentacji.|  
  
 **Opcje VSPerfCLREnv profilowanie próbkowania procesu**  
  
 W poniższej tabeli opisano opcje VSPerfCLREnv profilowanie próbkowania:  
  
|Opcja|Opis|  
|------------|-----------------|  
|**SampleOn**|Włącza profilowanie, za pomocą metody pobierania próbek. Nie obsługuje alokacji pamięci profilowania lub zbieranie danych o okresie istnienia obiektu.|  
|**SampleGC**|Włącza profilowanie przydziału pamięci za pomocą metody pobierania próbek. Nie umożliwia zbieranie danych o okresie istnienia obiektu.|  
|**SampleGCLife**|Włącza profilowanie przydziału pamięci za pomocą metody pobierania próbek. Umożliwia również zbieranie danych o okresie istnienia obiektu.|  
|**SampleLineOff**|Wyłącza kolekcji .NET danych profilowania na poziomie wiersza.|  
  
 **VSPerfCLREnv opcje globalne profilowania**  
  
 Profilowanie zarządzanych usług takich jak i aplikacji sieci web ASP.NET, który jest uruchamiany przez system operacyjny, a nie jest uruchomiony przez użytkownika, należy użyć opcji dla globalne profilowania opcji VSPerfCLREnv. Poniższa tabela zawiera opis wersji globalnej VSPerfCLREnv opcji. Te opcje należy ustawić zmienne środowiskowe odpowiednie w rejestrze.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**GlobalTraceOn**|Włącza profilowanie globalne przy użyciu metody instrumentacji. Nie zbiera danych o okresie istnienia obiektu lub zdarzenia alokacji pamięci.|  
|**GlobalTraceGC**|Włącza profilowanie przydziału pamięci globalnej przy użyciu metody instrumentacji. Nie umożliwia zbieranie danych o okresie istnienia obiektu.|  
|**GlobalTraceGCLife**|Włącza profilowanie przydziału pamięci globalnej przy użyciu metody instrumentacji. Umożliwia również zbierania danych o okresie istnienia obiektu.|  
|**GlobalSampleOn**|Włącza profilowanie globalne przy użyciu metody próbkowania. Umożliwi zbieranie zdarzeń alokacji pamięci lub danych o okresie istnienia obiektu.|  
|**GlobalSampleGC**|Włącza profilowanie przydziału pamięci globalnej przy użyciu metody próbkowania. Nie umożliwia zbieranie danych o okresie istnienia obiektu.|  
|**GlobalSampleGCLife**|Włącza profilowanie przydziału pamięci globalnej przy użyciu metody próbkowania. Umożliwia również zbieranie danych o okresie istnienia obiektu.|  
  
 **VSPerfCLREnv opcji, aby usunąć ustawienia środowiska**  
  
 Po zakończeniu profilowania zarządzanej aplikacji służy jedną z następujących opcji do usuwania zmiennych środowiskowych, które zostały dodane przez VSPerfCLREnv. W poniższej tabeli opisano sposób usuwania obie zmienne środowiskowe globalnych i standardowe:  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Wyłączanie**|Usuwa zmiennych środowiskowych dla profilowania platformy .NET standard. Ta opcja nieglobalnej opcje VSPerfClrEnv były używane do ustawiania zmiennych środowiskowych profilera.|  
|**GlobalOff**|Usuwa zmiennych środowiskowych dla globalne profilowania .NET. Użyj tej opcji podczas uruchomienia aplikacji według systemu operacyjnego i nie profilera.|  
  
## <a name="remarks"></a>Uwagi  
 Te opcje nie są wymagane do profilowania zarządzaną aplikację, jeśli aplikacja zostanie uruchomiona przy użyciu Eksploratora wydajności w środowisku IDE. Eksplorator wydajności Ustawia wszystkie ustawienia wymagane środowisko dla Ciebie.  
  
 Jeśli poprawne środowisko nie została ustawiona podczas profilowania, ostrzeżenie jest raportowany w czasie analizy i zarządzanych funkcji, do której zostanie nie można poprawnie rozpoznać nazw.  
  
## <a name="see-also"></a>Zobacz też  
 [Profilowanie z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)