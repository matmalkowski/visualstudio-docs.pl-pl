---
title: Debugowanie aplikacji ASP.NET Azure na żywo
ms.description: Learn how to set snappoints and view snapshots with the Snapshot Debugger.
ms.custom: mvc
ms.date: 03/16/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
helpviewer_keywords:
- debugger
ms.assetid: adb22512-4d4d-40e5-9564-1af421b7087e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
- azure
ms.openlocfilehash: c576795a130b6e654310a9ad48381fdc6a23c0e2
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766327"
---
# <a name="debug-live-aspnet-azure-apps-using-the-snapshot-debugger"></a>Debugowania na żywo aplikacji ASP.NET Azure za pomocą debugera migawki

Debuger migawki wykonuje migawkę aplikacji w środowisku produkcyjnym, gdy wykonuje kod, który chcesz. Aby nakazać debugera do tworzenia migawki, należy ustawić snappoints i logpoints w kodzie. Debuger pozwala zobaczyć dokładnie co poszło źle, bez wpływu na ruch aplikacji produkcyjnej. Debuger migawki ułatwiają znacznie skrócić czas potrzebny na rozwiązać problemy występujące w środowisku produkcyjnym.

Snappoints i logpoints są podobne do punktów przerwania, jednak w przeciwieństwie do punktów przerwania, snappoints nie wstrzymać aplikacja po trafieniu. Trwa przechwytywanie migawek na snappoint zazwyczaj, 10-20 w milisekundach. 

W tym samouczku obejmują:

> [!div class="checklist"]
> * Uruchom debuger migawki
> * Ustaw snappoint i Wyświetl migawki
> * Ustaw logpoint

## <a name="prerequisites"></a>Wymagania wstępne

* Debuger migawki jest dostępna tylko dla programu Visual Studio Enterprise 2017 wersji 15.5 lub nowszym oraz **ASP.NET i sieć web development obciążenia**. Dla platformy ASP.NET Core może też być konieczne. **NET Core development** obciążenia zainstalowane.

    Jeśli to nie jest jeszcze zainstalowana, zainstaluj [Visual Studio Enterprise 2017 wersji 15,5 cala](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) lub nowszym. Aktualizowania z poprzedniej instalacji programu Visual Studio 2017, uruchom Instalatora programu Visual Studio i zaewidencjonuj składnika debugera migawki **ASP.NET i sieć web development obciążenia**.

* Plan usługi aplikacji Azure podstawowa lub nowszej.

* Kolekcja migawki jest dostępne dla następujących aplikacji sieci web uruchomionych w usłudze Azure App Service:

    * Aplikacji platformy ASP.NET działających w środowisku .NET Framework 4.6.1 lub nowszej.
    * Aplikacji platformy ASP.NET Core uruchomionych na .NET Core 2.0 lub nowszego systemu Windows.

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>Otwórz projekt i uruchomić debugera migawki

1. Otwórz projekt, który ma zostać debugowania migawki. 

    > [!IMPORTANT] 
    > Aby debugowania migawki, należy otworzyć **tę samą wersję programu kodu źródłowego** który jest opublikowany w usłudze Azure App Service. 

1. W Eksploratorze chmury (**Widok > Eksplorator chmury**), kliknij prawym przyciskiem myszy projekt jest wdrożony w usłudze Azure App Service i wybierz **dołączyć debuger migawki**.

   ![Uruchom debuger migawki](../debugger/media/snapshot-launch.png)

    Po raz pierwszy należy wybrać **dołączyć debuger migawki**, zostanie wyświetlony monit, aby zainstalować rozszerzenie lokacji debugera migawki w usłudze Azure App Service. Ta instalacja wymaga ponownego uruchomienia usługi Azure App Service. 

   Program Visual Studio jest teraz migawki tryb debugowania.

    > [!NOTE]
    > Rozszerzenia usługi Application Insights witryny obsługuje również debugowania migawki. Jeśli wystąpią komunikat o błędzie "w lokacji rozszerzenie nieaktualne", zobacz [Rozwiązywanie problemów z porady i znane problemy dotyczące debugowania migawki](../debugger/debug-live-azure-apps-troubleshooting.md) uaktualniania szczegóły.

   ![Tryb debugowania migawki](../debugger/media/snapshot-message.png)

   **Modułów** okna pokazuje, kiedy wszystkie moduły zostały załadowane dla usługi Azure App Service (wybierz **Debug / Windows / modułów** otworzyć to okno).

   ![Sprawdź okno modułów](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>Ustaw snappoint

1. W edytorze kodu kliknij odstępu po lewej stronie obok wiersza kodu, który chcesz ustawić snappoint. Upewnij się, że jest kod, który zostanie wykonany.

   ![Ustaw snappoint](../debugger/media/snapshot-set-snappoint.png)

2. Kliknij przycisk **Rozpocznij zbieranie** włączyć snappoint.  

   ![Włącz snappoint](../debugger/media/snapshot-start-collection.png)

    > [!TIP]
    > Nie można wykonać kroku podczas wyświetlania migawki, ale wiele snappoints można umieścić w kodzie wykonać wykonywania na różne wiersze kodu. Jeśli masz wiele snappoints w kodzie debugera migawki zapewniają odpowiedniego migawek z tej samej sesji użytkownika końcowego. Debuger migawki dzieje się tak nawet w przypadku wielu użytkowników naciśnięcie aplikacji.

## <a name="take-a-snapshot"></a>Utworzenie migawki

Po włączeniu snappoint będzie przechwytywać migawki, zawsze, gdy wiersz kodu rozmieszczenia snappoint wykonuje. Wykonanie tego może być spowodowane rzeczywistego żądania na serwerze. Aby wymusić snappoint Twojego trafień, przejdź do widoku przeglądarki witryny sieci web i podjąć działania wymagane które spowodować snappoint Twojego do trafiony.

## <a name="inspect-snapshot-data"></a>Sprawdź dane migawki

1. Po wybraniu snappoint, migawka zostanie wyświetlony w oknie narzędzia diagnostyczne. Aby otworzyć to okno, wybierz polecenie **Debug / Windows / Pokaż narzędzia diagnostyczne**.

   ![Otwórz snappoint](../debugger/media/snapshot-diagsession-window.png)

1. Kliknij dwukrotnie snappoint, aby otworzyć migawki w edytorze kodu.

   ![Sprawdź dane migawki](../debugger/media/snapshot-inspect-data.png)

   W tym widoku można umieść kursor nad zmienne do wyświetlania etykietek danych, użyj **zmiennych lokalnych**, **obserwowanie**, i **stos wywołań** systemu windows, a także obliczać wyrażeń.

    Sama witryna sieci Web jest nadal aktywne i nie ma wpływu na użytkowników końcowych. Tylko jedna migawka jest przechwytywany na snappoint domyślnie: po przechwyceniu migawki snappoint zostanie wyłączony. Chcesz przechwytywać kolejną migawkę na snappoint, można włączyć snappoint ponownie, klikając **kolekcji aktualizacji**.

Możesz również dodać więcej snappoints do aplikacji i włączyć je z **kolekcji aktualizacji** przycisku.

**Potrzebujesz pomocy?** Zobacz [Rozwiązywanie problemów i znane problemy](../debugger/debug-live-azure-apps-troubleshooting.md) i [często zadawane pytania dotyczące debugowania migawki](../debugger/debug-live-azure-apps-faq.md) stron.

## <a name="set-a-conditional-snappoint"></a>Ustaw snappoint warunkowe

Jeśli trudno odtworzyć określonego stanu w aplikacji, należy wziąć pod uwagę czy użycie warunkowego snappoint może pomóc. Warunkowe snappoints uniknąć wykonywania migawki, dopóki aplikacja przechodzi żądany stan, na przykład jeśli zmienna zawiera konkretną wartość, które chcesz sprawdzić. Można ustawić warunki za pomocą wyrażeń, filtry lub liczbą trafień.

#### <a name="to-create-a-conditional-snappoint"></a>Aby utworzyć snappoint warunkowe

1. Kliknij prawym przyciskiem myszy ikonę snappoint (piłka pusty) i wybierz polecenie **ustawienia**.

   ![Wybierz ustawienia](../debugger/media/snapshot-snappoint-settings.png)

1. W oknie Ustawienia snappoint wpisz wyrażenie.

   ![Wpisz wyrażenie](../debugger/media/snapshot-snappoint-conditions.png)

   Na powyższej ilustracji tylko migawki dla snappoint podczas `visitor.FirstName == "Dan"`.

## <a name="set-a-logpoint"></a>Ustaw logpoint

Oprócz wykonywania migawki po wybraniu snappoint, można również skonfigurować snappoint do rejestrowania wiadomości (czyli tworzenie logpoint). Możesz ustawić logpoints bez konieczności ponownego wdrażania aplikacji. Logpoints są wykonywane w praktycznie i spowodować nie wpływu i efekty uboczne w uruchomionej aplikacji.

#### <a name="to-create-a-logpoint"></a>Aby utworzyć logpoint

1. Kliknij prawym przyciskiem myszy ikonę snappoint (sześciokąt niebieski) i wybierz polecenie **ustawienia**.

1. W oknie Ustawienia snappoint wybierz **akcje**.

    ![Utwórz logpoint](../debugger/media/snapshot-logpoint.png)

1. W polu komunikat można wprowadzić nowy komunikat dziennika, które mają być rejestrowane. Zmienne w wiadomości dziennika można również ocenić, umieszczając je wewnątrz nawiasów klamrowych.

    Jeśli wybierzesz **Wyślij do okna wyjściowego**, gdy zostaje trafiony logpoint komunikat jest wyświetlany w oknie narzędzia diagnostyczne.

    ![Logpoint danych w oknie diagsession](../debugger/media/snapshot-logpoint-output.png)

    Jeśli wybierzesz **wysyłane do dziennika aplikacji**, po wybraniu logpoint, pojawi się komunikat z dowolnego miejsca można wyświetlić komunikaty z `System.Diagnostics.Trace` (lub `ILogger` w .NET Core), takich jak [App Insights](/azure/application-insights/app-insights-asp-net-trace-logs).

## <a name="next-steps"></a>Następne kroki

W tym samouczku kiedy znasz już jak używać debugera migawki. Warto przeczytać więcej informacji na temat tej funkcji.

> [!div class="nextstepaction"]
> [Debugowanie migawek — często zadawane pytania](../debugger/debug-live-azure-apps-faq.md)
