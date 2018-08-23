---
title: Analizowanie kodowanych testów interfejsu użytkownika, przy użyciu dzienników testu kodowanego interfejsu użytkownika | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7e795873-1d4b-4a13-a52a-a411d87fb759
caps.latest.revision: 15
ms.author: gewarren
manager: douge
ms.openlocfilehash: 8da6f37e36dd249c6b458b31870259f30a00f883
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681845"
---
# <a name="analyzing-coded-ui-tests-using-coded-ui-test-logs"></a>Analiza dzienników zakodowanych testów interfejsu użytkownika
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [analizowanie kodowanych testów przy użyciu kodowanego interfejsu użytkownika dzienników testów interfejsu użytkownika](https://docs.microsoft.com/visualstudio/test/analyzing-coded-ui-tests-using-coded-ui-test-logs).  
  
Kodowane filtr dzienników testu interfejsu użytkownika i rekord, który uruchamia ważne informacje dotyczące Twojego kodowanego testu interfejsu użytkownika.  
  
 **Wymagania**  
  
-   Visual Studio Enterprise  
  
## <a name="why-should-i-do-this"></a>Dlaczego należy to zrobić?  
 Dzienniki są prezentowane w formacie, który umożliwia szybkie debugowanie problemów.  
  
## <a name="how-do-i-do-this"></a>Jak to zrobić?  
  
### <a name="step-1-enable-logging"></a>Krok 1: Włączanie rejestrowania  
 Zależnie od scenariusza należy użyć jednej z następujących metod Aby włączyć dziennik.  
  
-   Docelowa wersja .NET Framework 4 z pliku App.config, nie jest obecne w projekcie testowym  
  
    -   Otwórz **QTAgent32_40.exe.config** pliku.  
  
         Domyślnie ten plik znajduje się w  **\<drvie >: \Program Files (x86) \Microsoft Visual Studio 12.0\Common7\IDE**.  
  
         Na poziom dziennika, który ma, należy zmodyfikować wartość EqtTraceLevel.  
  
         Zapisz plik.  
  
-   Docelowa wersja .NET Framework 4.5 w pliku App.config, nie jest obecne w projekcie testowym  
  
    -   Otwórz **QTAgent32.exe.config** pliku.  
  
         Domyślnie ten plik znajduje się w  **\<drvie >: \Program Files (x86) \Microsoft Visual Studio 12.0\Common7\IDE**.  
  
         Zmień wartość EqtTraceLevel na poziom dziennika, który ma.  
  
         Zapisz plik.  
  
-   Plik App.config w projekcie testowym  
  
    -   Otwórz plik App.config w projekcie.  
  
         Dodaj następujący kod w węźle Konfiguracja:  
  
         `<system.diagnostics>     <switches>       <add name="EqtTraceLevel" value="4" />     </switches>  </system.diagnostics>`  
  
-   Włączanie rejestrowania z sam kod testu  
  
    -   <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.LoggerOverrideState%2A> = HtmlLoggerState.AllActionSnapshot;  
  
### <a name="step-2-run-your-coded-ui-test-and-view-the-log"></a>Krok 2: Uruchamianie kodowanego testu interfejsu użytkownika i Wyświetl dziennik  
 Po uruchomieniu kodowanego testu interfejsu użytkownika ze zmianami do **QTAgent32.exe.config** pliku w miejscu, zostanie wyświetlony w wynikach Eksploratora testów znajduje się link danych wyjściowych. Pliki dziennika są tworzone, nie tylko w przypadku, gdy test zakończy się niepowodzeniem, ale także w przypadku udanych testów, gdy poziom śledzenia jest ustawiona na "pełne."  
  
1.  Na **testu** menu, wybierz **Windows** , a następnie wybierz **Eksplorator testów**.  
  
2.  Na **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.  
  
3.  W Eksploratorze testów wybierz kodowanego testu interfejsu użytkownika, aby uruchomić, otwórz jego menu skrótów, a następnie wybierz **Uruchom wybrane testy**.  
  
     Uruchomisz testy automatyczne i wskazują one powodzeniem lub niepowodzeniem.  
  
    > [!TIP]
    >  Aby wyświetlić Eksplorator testu z **Test menu**, wskaż polecenie **Windows** , a następnie wybierz **Eksplorator testów**.  
  
4.  Wybierz **dane wyjściowe** łącze w wynikach Eksploratora testów.  
  
     ![Link danych wyjściowych w Eksploratorze testów](../test/media/cuit-htmlactionlog1.png "CUIT_HTMLActionLog1")  
  
     Spowoduje to wyświetlenie danych wyjściowych testu, który będzie zawierać łącze do dziennika akcji.  
  
     ![Wyniki i łącza danych wyjściowych z kodowanego testu interfejsu użytkownika](../test/media/cuit-htmlactionlog2.png "CUIT_HTMLActionLog2")  
  
5.  Wybierz łącze UITestActionLog.html.  
  
     Dziennik jest wyświetlany w przeglądarce sieci web.  
  
     ![Kodowanego testu interfejsu użytkownika pliku dziennika](../test/media/cuit-htmlactionlog3.png "CUIT_HTMLActionLog3")  
  
## <a name="q--a"></a>Pytania i odpowiedzi  
  
### <a name="q-what-happened-to-the-enablehtmllogger-key"></a>P: co się stało z kluczem EnableHtmlLogger?  
 W poprzednich wersjach programu Visual Studio wystąpiły dwa więcej ustawień konfiguracji włączania Html rejestratora kodowanego testu interfejsu użytkownika:  
  
```  
  
<add key="EnableHtmlLogger" value="true"/>  
  
<add key="EnableSnapshotInfo" value="true"/>  
  
```  
  
 Oba te ustawienia są przestarzałe od Visual Studio 2012. EqtTraceLevel to jedyne ustawienie, które są wymagane do zmodyfikowania, aby umożliwić HtmlLogger.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)   
 [Porady: Uruchamianie testów z programu Microsoft Visual Studio](http://msdn.microsoft.com/library/1a1207a9-2a33-4a1e-a1e3-ddf0181b1046)



