---
title: "Porady: zbieranie danych wydajności dla witryny sieci Web | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vsperf.url.url
- vsperf.chooseurl
- vs.performance.wizard.asppage
- vsperf.url.ok
- vsperf.url.cancel
helpviewer_keywords:
- Profiling Tools,profiling ASP.NET
- web sites, performance profiling
- ASP.NET, performance profilng
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: db9cefe31201a3b67ba176a56fed58bbe155bcf0
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2018
---
# <a name="how-to-collect-performance-data-for-a-web-site"></a>Porady: zbieranie danych wydajności dla witryny sieci Web

Można użyć **kreatora osiągów** do gromadzenia danych wydajności [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web. Można profilu aplikacji sieci Web, która jest otwarta w programie Visual Studio, lub można profilu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] witryny sieci Web, który znajduje się na komputerze lokalnym i nie jest otwarty w programie Visual Studio IDE.

> [!NOTE]
> **Kreatora osiągów** umożliwia dodanie danych interakcji (TIP) i/lub JScript danych wydajności zebranych danych profilowania. Opcja Porada zbiera dane z procesów po stronie serwera. Profilowanie JScript zbiera dane ze skryptów, które są uruchomione na lokalnym lub zdalnym witryny sieci Web. W większości przypadków należy wybrać tylko jedną z opcji.

 W zależności od ustawienia uprawnień dostępu użytkownika, które administrator ma zostać udostępnione użytkownik może lub może nie mieć uprawnień do utworzenia sesji profilera na komputerze, który jest hostem procesu ASP.NET. Poniższe przykłady przedstawiają możliwe różnice między użytkowników:

- Niektórzy użytkownicy mogą uzyskiwać dostęp do zaawansowanych funkcji profilowania, gdy Administrator ustawił sterownik i uruchomienie usługi.

- Użytkownicy domeny mogą uzyskiwać dostęp do przykładowej tylko profilowania.

- W przypadku niektórych użytkowników może uniemożliwić dostęp do profilowania do innych użytkowników.

 Aby uzyskać więcej informacji, zobacz [profilowanie i bezpieczeństwo systemu Windows Vista](../profiling/profiling-and-windows-vista-security.md) i opcje administratora w [VSPerfCmd](../profiling/vsperfcmd.md).

## <a name="to-profile-a-web-site-project"></a>Profilowanie projekt witryny sieci Web

1. Otwórz [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] projektu sieci Web w programie Visual Studio.

2. Na **Analizuj** menu, wybierz **wydajności profilera**, wybierz pozycję **Eksplorator wydajności**, a następnie wybierz **Start**.

3. Na pierwszej stronie kreatora wybierz metodę profilowania, a następnie kliknij przycisk **dalej**. Aby uzyskać więcej informacji na temat metod profilowania, zobacz [metoda zbierania danych wydajności opis](../profiling/understanding-performance-collection-methods.md). Należy pamiętać, że metoda profilowania narzędzia concurrency visualizer nie jest dostępna dla aplikacji sieci web.

4. W **aplikacji, które chcesz docelowe dla profilowania?** listy rozwijanej, upewnij się, że bieżący projekt jest wybrany, a następnie kliknij przycisk **dalej**.

5. Na trzeciej stronie kreatora możesz dodać warstwy interakcji profilowania (TIP), dane z JavaScript w lub strony sieci Web.

    - Aby zebrać interakcja warstwowa, wybierz **Włącz profilowanie interakcji między warstwami** pole wyboru.

    - Aby zbierać dane z poziomu języka JavaScript, uruchomione na stronach sieci Web, wybierz **JavaScript profilu** pole wyboru.

6. Kliknij przycisk **Dalej**.

7. Na czwartej stronie kreatora, kliknij przycisk **Zakończ**.

8. Sesja wydajności jest tworzona dla [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji i witrynę sieci Web jest uruchomiony w przeglądarce. Wykonuje funkcje, które chcesz profilu, a następnie zamknij przeglądarkę.

     Profiler generuje plik danych i wyświetla widok podsumowania danych w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] głównego okna.

## <a name="to-profile-a-web-site-without-opening-a-project-in-visual-studio"></a>Profilowanie witryny sieci Web bez konieczności otwierania projektu w programie Visual Studio

1. Otwórz program Visual Studio.

2. Na **Analizuj** menu, wybierz **wydajności profilera**, wybierz pozycję **Eksplorator wydajności**, a następnie wybierz **Start**.

3. Na pierwszej stronie kreatora wybierz metodę profilowania, a następnie kliknij przycisk **dalej**. Aby uzyskać więcej informacji, zobacz [metoda zbierania danych wydajności opis](../profiling/understanding-performance-collection-methods.md).

4. Na drugiej stronie kreatora wybierz **profilu aplikacji ASP.NET lub JavaScript** , a następnie kliknij przycisk **dalej**.

5. W **jakim adresem URL lub ścieżką będzie działała aplikacja sieci web** na trzeciej stronie kreatora, wprowadź adres URL do strony głównej aplikacji, a następnie kliknij przycisk **dalej**.

    - Witryny sieci Web opartej na serwerze (IIS), wpisz adres URL takich jak **http://localhost/MySite/default.aspx**. Powoduje to [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji na komputerze lokalnym w katalogu głównym aplikacji, witryna do profilowania i default.aspx strony w tej witrynie ma zostać uruchomiony w programie Internet Explorer, aby rozpocząć sesję.

    - Dla witryny sieci Web opartą na plikach, wpisz ścieżkę, np. plik / / /**c:\WebSites\MySite\default.aspx**. Powoduje to [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji znajdujących się na stronę http://localhost:nnnn/MySite/default.aspx ma zostać uruchomiony w programie Internet Explorer, aby rozpocząć sesję i c:\webSites\MySite do profilowania.

    - Dla zewnętrznych witryn, które mają zostać zebrane dane JavaScript na wpisz adres URL, na przykład http://www.contoso.com.

     Aby uzyskać więcej informacji, Wyświetl strony właściwości dla [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] docelowy plik binarny.

6. Na trzeciej stronie kreatora możesz dodać warstwy interakcji profilowania (TIP), dane z JavaScript w lub strony sieci Web.

    - Aby zebrać interakcja warstwowa, wybierz **Włącz profilowanie interakcji między warstwami** pole wyboru.

    - Aby zbierać dane z poziomu języka JavaScript, uruchomione na stronach sieci Web, wybierz **JavaScript profilu** pole wyboru.

7. Kliknij przycisk **Dalej**.

8. Na czwartej stronie kreatora, kliknij przycisk **Zakończ**.

9. Zostanie utworzona sesja wydajności dla aplikacji ASP.NET, a witryna sieci Web jest uruchamiana w przeglądarce. Wykonuje funkcje, które chcesz profilu, a następnie zamknij przeglądarkę.

     Profiler generuje plik danych i wyświetla widok podsumowania danych w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] głównego okna.

## <a name="see-also"></a>Zobacz także

[Omówienia](../profiling/overviews-performance-tools.md)  
[Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)  
[Zapoznanie z wartościami danych Instrumentacji](../profiling/understanding-instrumentation-data-values.md)  
[Opis pobierania wartości danych](../profiling/understanding-sampling-data-values.md)
