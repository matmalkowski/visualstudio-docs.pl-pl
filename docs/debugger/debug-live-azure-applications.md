---
title: "Debugowanie aplikacji ASP.NET Azure na żywo — Visual Studio | Dokumentacja firmy Microsoft"
ms.date: 11/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugger
ms.assetid: adb22512-4d4d-40e5-9564-1af421b7087e
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 71facc3515bf90d378b19242bb804ce825131b4e
ms.sourcegitcommit: 2c7f48ad6073a81fa927568793633f26cc1f0b15
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/17/2017
---
# <a name="debug-live-aspnet-azure-apps-using-the-snapshot-debugger"></a>Debugowania na żywo aplikacji ASP.NET Azure za pomocą debugera migawki

Debuger migawki wykonuje migawkę aplikacji w środowisku produkcyjnym, gdy wykonuje kod, który chcesz. Aby nakazać debugera do tworzenia migawki, należy ustawić snappoints i logpoints w kodzie. Debuger pozwala zobaczyć dokładnie co poszło źle, bez wpływu na ruch aplikacji produkcyjnej. Debuger migawki ułatwiają znacznie skrócić czas potrzebny na rozwiązać problemy występujące w środowisku produkcyjnym.

Snappoints i logpoints są podobne do punktów przerwania. W przeciwieństwie do punktów przerwania, snappoints nie wstrzymać aplikacja po trafieniu. Trwa przechwytywanie migawek na snappoint zazwyczaj, 10-20 w milisekundach. 

Kolekcja migawki jest dostępne dla następujących aplikacji sieci web uruchomionych w usłudze Azure App Service:

- Aplikacji platformy ASP.NET działających w środowisku .NET Framework 4.6.1 lub nowszej.
- Aplikacji platformy ASP.NET Core uruchomionych na .NET Core 2.0 lub nowszego systemu Windows.

Ponadto debugera migawki jest dostępna tylko dla programu Visual Studio Enterprise 2017 wersji 15.5 lub nowszej. 

## <a name="start-the-snapshot-debugger"></a>Uruchom debuger migawki

1. Zainstaluj [wersji zapoznawczej programu Visual Studio Enterprise 15,5 cala](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-preview-relnotes) lub nowszym. Jeśli aktualizacja z poprzedniej podglądu programu Visual Studio 2017, uruchom Instalatora programu Visual Studio i sprawdź składnika debugera migawki pracą programowanie ASP.NET i sieć web.

2. Otwórz projekt, który ma zostać debugowania migawki. 

    > [!IMPORTANT] 
    > W celu debugowania migawki, należy otworzyć **tę samą wersję programu kodu źródłowego** który jest opublikowany w usłudze Azure App Service. 

3. W Eksploratorze chmury (wybierz **Widok > Eksplorator chmury**), kliknij prawym przyciskiem myszy projekt jest wdrożony w usłudze Azure App Service i wybierz **dołączyć debuger migawki** można uruchomić debugera migawki.

   ![Uruchom debuger migawki](../debugger/media/snapshot-launch.png "Uruchom debuger migawki")

    Po raz pierwszy należy wybrać **dołączyć debuger migawki**, zostanie wyświetlony monit o Zainstaluj debugera migawki w usłudze Azure App Service. Ta instalacja wymaga ponownego uruchomienia usługi Azure App Service. 

   Program Visual Studio jest teraz migawki tryb debugowania.

   ![Tryb debugowania migawki](../debugger/media/snapshot-message.png "migawki tryb debugowania")

   **Modułów** okna pokazuje, kiedy wszystkie moduły zostały załadowane dla usługi Azure App Service (wybierz **Debug / Windows / modułów** otworzyć to okno).

   ![W oknie moduły](../debugger/media/snapshot-modules.png "Sprawdź okno modułów")

## <a name="set-a-snappoint"></a>Ustaw snappoint

1. W edytorze kodu kliknij odstępu po lewej stronie obok wiersza kodu, który chcesz ustawić snappoint. Upewnij się, że jest kod, który zostanie wykonany.

   ![Ustaw snappoint](../debugger/media/snapshot-set-snappoint.png "ustawić snappoint")

2. Kliknij przycisk **Rozpocznij zbieranie** włączyć snappoint.  

   ![Włącz snappoint](../debugger/media/snapshot-start-collection.png "włączyć snappoint")

    > [!TIP]
    > Nie można wykonać kroku podczas wyświetlania migawki, ale wiele snappoints można umieścić w kodzie wykonać wykonywania na różne wiersze kodu. Jeśli masz wiele snappoints w kodzie debugera migawki zapewnia, że odpowiednie migawki są z tej samej sesji użytkownika końcowego, nawet w przypadku wielu użytkowników naciśnięcie aplikacji.

## <a name="take-a-snapshot"></a>Utworzenie migawki

Po włączeniu snappoint będzie przechwytywać migawki, zawsze, gdy wiersz kodu rozmieszczenia snappoint jest wykonywana. Wykonanie tego może być spowodowane rzeczywistego żądania na serwerze. Aby wymusić snappoint Twojego trafienie, można także przejść do widoku przeglądarki witryny sieci web i wykonaj wymagane wszystkie akcje, które spowodować snappoint Twojego do trafiony.

## <a name="inspect-snapshot-data"></a>Sprawdź dane migawki

1. Po wybraniu snappoint, migawka zostanie wyświetlony w oknie narzędzia diagnostyczne. Wybierz **Debug / Windows / Pokaż narzędzia diagnostyczne** do otwarcia tego okna.

   ![Otwórz snappoint](../debugger/media/snapshot-diagsession-window.png "Otwórz snappoint")

1. Kliknij dwukrotnie snappoint, aby otworzyć migawki w edytorze kodu.

   ![Sprawdź dane migawki](../debugger/media/snapshot-inspect-data.png "sprawdzać dane migawki")

   W tym widoku można umieść kursor nad zmienne do wyświetlania etykietek danych, użyj **zmiennych lokalnych**, **obserwowanie**, i **stos wywołań** systemu windows, a także obliczać wyrażeń.

    Samej strony jest nadal aktywne i nie wpływ na użytkowników końcowych. Tylko jedna migawka jest przechwytywany na snappoint domyślnie: po przechwyceniu migawki snappoint zostanie wyłączony. Chcesz przechwytywać kolejną migawkę na snappoint, można włączyć snappoint ponownie, klikając **kolekcji aktualizacji**.

Możesz również dodać więcej snappoints do aplikacji i włączyć je z **kolekcji aktualizacji** przycisku.

**Potrzebujesz pomocy?** Zobacz [Rozwiązywanie problemów i znane problemy](../debugger/debug-live-azure-apps-troubleshooting.md) i [często zadawane pytania dotyczące debugowania migawki](../debugger/debug-live-azure-apps-faq.md) stron.

## <a name="set-a-conditional-snappoint"></a>Ustaw snappoint warunkowe

Jeśli trudno odtworzyć określonego stanu w aplikacji, należy wziąć pod uwagę czy użycie warunkowego snappoint może pomóc. Warunkowe snappoints umożliwia uniknąć wykonywania migawki, dopóki aplikacja przechodzi do stanu żądaną, takie jak kiedy zmienna ma wartość określonego interesuje Cię. Można ustawić warunki za pomocą wyrażeń, filtry lub liczbą trafień.

#### <a name="to-create-a-conditional-snappoint"></a>Aby utworzyć snappoint warunkowe

1. Kliknij prawym przyciskiem myszy ikonę snappoint (piłka pusty) i wybierz polecenie **ustawienia**.

   ![Wybierz ustawienia](../debugger/media/snapshot-snappoint-settings.png "wybierz ustawienia")

1. W oknie Ustawienia snappoint wpisz wyrażenie.

   ![Wpisz wyrażenie](../debugger/media/snapshot-snappoint-conditions.png "wpisz wyrażenie")

   Na powyższej ilustracji tylko migawki dla snappoint podczas `visitor.FirstName == "Dan"`.

## <a name="set-a-logpoint"></a>Ustaw logpoint

Oprócz wykonywania migawki po wybraniu snappoint, można również skonfigurować snappoint do rejestrowania wiadomości (czyli tworzenie logpoint). Możesz ustawić logpoints bez konieczności ponownego wdrażania aplikacji. Logpoints są wykonywane w praktycznie i spowodować nie wpływu i efekty uboczne w uruchomionej aplikacji.

#### <a name="to-create-a-logpoint"></a>Aby utworzyć logpoint

1. Kliknij prawym przyciskiem myszy ikonę snappoint (sześciokąt niebieski) i wybierz polecenie **ustawienia**.

1. W oknie Ustawienia snappoint wybierz **akcje**.

    ![Utwórz logpoint](../debugger/media/snapshot-logpoint.png "utworzyć logpoint")

1. W polu komunikat można wprowadzić nowy komunikat dziennika, które mają być rejestrowane. Zmienne w wiadomości dziennika można również ocenić, umieszczając je wewnątrz nawiasów klamrowych.

    Jeśli wybierzesz **Wyślij do okna wyjściowego**, gdy zostaje trafiony logpoint komunikat jest wyświetlany w oknie narzędzia diagnostyczne.

    ![Logpoint danych w oknie .diagsession](../debugger/media/snapshot-logpoint-output.png "Logpoint danych w oknie .diagsession")

    Jeśli wybierzesz **wysyłane do dziennika aplikacji**, po wybraniu logpoint, pojawi się komunikat z dowolnego miejsca można wyświetlić komunikaty z `System.Diagnostics.Trace` (lub `ILogger` w .NET Core), takich jak [App Insights](/azure/application-insights/app-insights-asp-net-trace-logs).

## <a name="next-steps"></a>Następne kroki

- Aby dowiedzieć się, jak sprawdzić zmienne podczas wyświetlania migawek, zobacz [samouczek funkcji Debbuger](../debugger/debugger-feature-tour.md).
- Widok [często zadawane pytania dotyczące debugowania migawki](../debugger/debug-live-azure-apps-faq.md).
- Widok [Rozwiązywanie problemów z porady i znane problemy dotyczące debugowania migawki](../debugger/debug-live-azure-apps-troubleshooting.md).
- Jeśli chcesz wyświetlić migawki w usłudze Application Insights, gdy aplikacja trafi wyjątek, możesz to zrobić. Aby uzyskać więcej informacji, zobacz [debugowania migawek na wyjątki w aplikacjach .NET](/azure/application-insights/app-insights-snapshot-debugger). Usługi Application Insights obsługuje aplikacje platformy Service Fabric oprócz usługi Azure App Service.
