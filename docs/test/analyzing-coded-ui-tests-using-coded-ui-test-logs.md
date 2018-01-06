---
title: "Analizowanie kodowanych testów interfejsu użytkownika przy użyciu dzienników testu kodowanego interfejsu użytkownika | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e795873-1d4b-4a13-a52a-a411d87fb759
caps.latest.revision: "13"
ms.author: douge
manager: douge
ms.workload: multiple
ms.openlocfilehash: af89bbfadfa992fad4b2ba114ffb006e4b0f818a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="analyzing-coded-ui-tests-using-coded-ui-test-logs"></a>Analiza dzienników zakodowanych testów interfejsu użytkownika
Zakodowanych filtru dzienników testu interfejsu użytkownika i rekord, który uruchamia ważne informacje o kodowanego testu interfejsu użytkownika.  
  
 **Wymagania**  
  
-   Visual Studio Enterprise  
  
## <a name="why-should-i-do-this"></a>Dlaczego należy to zrobić?  
 Dzienniki są przedstawione w formacie, który umożliwia szybkie debugowanie problemów.  
  
## <a name="how-do-i-do-this"></a>Jak to zrobić?  
  
### <a name="step-1-enable-logging"></a>Krok 1: Włączanie rejestrowania  
 W zależności od scenariusza użyj jednej z następujących metod Aby włączyć dziennik.  
  
-   Docelowa wersja programu .NET Framework 4 nie istnieje w projekcie testowym pliku App.config  
  
    -   Otwórz **QTAgent32_40.exe.config** pliku.  
  
         Domyślnie ten plik znajduje się w  **\<drvie >: \Program pliki (x86) \Microsoft Visual Studio 12.0\Common7\IDE**.  
  
         Zmień wartość dla EqtTraceLevel na poziom dziennika, który ma.  
  
         Zapisz plik.  
  
-   Docelowa wersja programu .NET Framework 4.5 nie istnieje w projekcie testowym pliku App.config  
  
    -   Otwórz **QTAgent32.exe.config** pliku.  
  
         Domyślnie ten plik znajduje się w  **\<drvie >: \Program pliki (x86) \Microsoft Visual Studio 12.0\Common7\IDE**.  
  
         Zmień wartość EqtTraceLevel na poziom dziennika, który ma.  
  
         Zapisz plik.  
  
-   Istnieje w projekcie testowym pliku App.config  
  
    -   Otwórz plik App.config w projekcie.  
  
         Dodaj następujący kod w węźle Konfiguracja:  
  
         `<system.diagnostics>     <switches>       <add name="EqtTraceLevel" value="4" />     </switches>  </system.diagnostics>`  
  
-   Włącz rejestrowanie z kodu testu  
  
    -   <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.LoggerOverrideState%2A>= HtmlLoggerState.AllActionSnapshot;  
  
### <a name="step-2-run-your-coded-ui-test-and-view-the-log"></a>Krok 2: Uruchamianie kodowanego testu interfejsu użytkownika i sprawdź dzienniki  
 Po uruchomieniu kodowanego testu interfejsu użytkownika ze zmianami do **QTAgent32.exe.config** pliku w miejscu, zobaczysz, ma łącza dane wyjściowe w wynikach testów Explorer. Pliki dziennika są produkowane nie tylko w przypadku, gdy test zakończy się niepowodzeniem, ale także dla testów powiodło się, gdy poziom śledzenia jest ustawiona na "pełne."  
  
1.  Na **testu** menu, wybierz **Windows** , a następnie wybierz **Eksploratora testów**.  
  
2.  Na **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.  
  
3.  W Eksploratorze testów, wybierz kodowanego testu interfejsu użytkownika, które chcesz uruchomić, otwórz menu skrótów, a następnie wybierz **Uruchom testy wybierz**.  
  
     Testy automatyczne zostaną uruchomione i wskazują one przekazany lub niepowodzenie.  
  
    > [!TIP]
    >  Aby wyświetlić narzędzia Eksplorator testów z **Test menu**, wskaż polecenie **Windows** , a następnie wybierz **Eksploratora testów**.  
  
4.  Wybierz **dane wyjściowe** łącze w wynikach narzędzia Eksplorator testów.  
  
     ![Połącz dane wyjściowe w Eksploratorze testów](../test/media/cuit_htmlactionlog1.png "CUIT_HTMLActionLog1")  
  
     Zostaną wyświetlone dane wyjściowe dla testu, który zawiera łącze do dziennika akcji.  
  
     ![Wyniki i łącza dane wyjściowe z kodowanego testu interfejsu użytkownika](../test/media/cuit_htmlactionlog2.png "CUIT_HTMLActionLog2")  
  
5.  Wybierz łącze UITestActionLog.html.  
  
     Dziennik jest wyświetlany w przeglądarce sieci web.  
  
     ![Plik dziennika testu kodowanego interfejsu użytkownika](../test/media/cuit_htmlactionlog3.png "CUIT_HTMLActionLog3")  
  
## <a name="q--a"></a>Pytania i odpowiedzi  
  
### <a name="q-what-happened-to-the-enablehtmllogger-key"></a>Pytanie: co się stało klucza EnableHtmlLogger?  
 W poprzednich wersjach programu Visual Studio wystąpiły dwa ustawienia konfiguracji więcej umożliwiających rejestratora Html w kodowanego testu interfejsu użytkownika:  
  
```  
  
<add key="EnableHtmlLogger" value="true"/>  
  
<add key="EnableSnapshotInfo" value="true"/>  
  
```  
  
 Oba te ustawienia są przestarzałe od programu Visual Studio 2012. EqtTraceLevel jest tylko ustawienie, które muszą zostać zmodyfikowane w celu włączenia HtmlLogger.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)   
 [Porady: Uruchamianie testów za pomocą programu Microsoft Visual Studio](http://msdn.microsoft.com/Library/1a1207a9-2a33-4a1e-a1e3-ddf0181b1046)
