---
title: Profilowanie szybkie witryny sieci Web za pomocą VSPerfASPNETCmd | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- proflilng tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9c30aebca3fc57912ac1a9bfc6fb16379dda24ed
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815561"
---
# <a name="rapid-web-site-profiling-with-vsperfaspnetcmd"></a>Szybkie profilowanie za pomocą VSPerfASPNETCmd witryny sieci web

**VSPerfASPNETCmd** narzędzia wiersza polecenia umożliwia łatwe profilu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci web. W porównaniu z [VSPerfCmd](../profiling/vsperfcmd.md) narzędzia wiersza polecenia, opcje zostały zredukowane nie zmiennych środowiskowych, które muszą być ustawione i ponowne uruchomienie komputera nie jest wymagane. Przy użyciu **VSPerfASPNETCmd** jest to preferowana metoda profilowania z Autonomiczny profiler. Aby uzyskać więcej informacji, zobacz [porady: Instalowanie autonomiczny profilera](../profiling/how-to-install-the-stand-alone-profiler.md).

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagane znaczących zmian w sposobie profilera Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowe techniki kolekcji. Zobacz [narzędzi wydajności w przypadku aplikacji systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

 W niektórych scenariuszach, takich jak zbieranie danych współbieżności lub wstrzymywanie i wznawianie profilowania, za pomocą **VSPerfCmd** jest to preferowana metoda profilowania.

> [!NOTE]
> Narzędzia wiersza polecenia narzędzi profilowania znajdują się w *\Team Tools\Performance narzędzia* podkatalogu w katalogu instalacji programu Visual Studio. Na komputerach 64-bitowych, należy użyć narzędzia VSPerfASPNETCmd znajduje się w 32-bitowych *\Team Tools\Performance narzędzia* katalogu. Za pomocą narzędzi wiersza polecenia profilera, możesz dodać ścieżkę narzędzia do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać go do samo polecenie. Aby uzyskać więcej informacji, zobacz [Określ ścieżkę do narzędzia wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

## <a name="profile-an-aspnet-application"></a>Profiluj aplikację ASP.NET

Do profilu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci web, wpisz jedno z poleceń opisane w poniższych sekcjach. Witryna sieci Web jest uruchamiana i uruchamia profilera do zbierania danych. Wykonywanie aplikacji, a następnie zamknij przeglądarkę. Aby zatrzymać profilowanie, naciśnij klawisz **Enter** klucza w oknie wiersza polecenia.

> [!NOTE]
> Domyślnie wiersza polecenia nie może zwracać po **vsperfaspnetcmd** polecenia. Można użyć **/nowait** opcję, aby wymusić wiersza polecenia do zwrócenia. Zobacz [użyj opcji/nowait](#UsingNoWait).

## <a name="to-collect-application-statistics-by-using-the-sampling-method"></a>W celu zbierania statystyk aplikacji przy użyciu metody pobierania próbek
 Próbkowanie to domyślne metody profilowania **VSPerfASPNETCmd** narzędzia i nie muszą być określone w wierszu polecenia. Następujący wiersz polecenia służy do zbierania statystyk aplikacji z określonej aplikacji sieci web:

 **vsperfaspnetcmd***podanym adresem URL*

## <a name="to-collect-detailed-timing-data-by-using-the-instrumentation-method"></a>Do zbierania danych o chronometrażu przy użyciu metody Instrumentacji

Użyj następującego polecenia do zbierania danych o chronometrażu z dynamicznie skompilowanej [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci web:

**polecenie vsperfaspnetcmd/trace***podanym adresem URL*

Jeśli chcesz statycznie profilu skompilowany. *dll* plików w aplikacji sieci web musi Instrumentacja plików za pomocą [VSInstr](../profiling/vsinstr.md) narzędzia wiersza polecenia. Polecenie vsperfaspnetcmd/trace obejmuje dane z instrumentowanych plików.

## <a name="to-collect-net-memory-data"></a>Zbieranie danych pamięci .NET

**/Memory** opcję zbiera dane dotyczące alokacji obiektów w pamięci .NET i może zbierać dane dotyczące okresu istnienia tych obiektów. Zbieranie danych alokacji jest to domyślny tryb **/Memory** danych opcję i nie muszą być określone w wierszu polecenia.

 **vsperfaspnetcmd /memory** *podanym adresem URL*

 Użyj **okres istnienia** parametru dodatkowo do zebrania danych o okresie istnienia obiektu danych alokacji:

 **vsperfaspnetcmd /memory:lifetime** *podanym adresem URL*

 Można również użyć **/Trace** możliwość uwzględnienia szczegółowych informacji z danych pamięci .NET:

 **vsperfaspnetcmd /memory**[**: okres istnienia**]   **/śledzenia**`websiteUrl`

## <a name="to-collect-tier-interaction-data"></a>Do zbierania danych o interakcji między warstwy

> [!WARNING]
> Interakcja warstwowa profilowania danych (TIP) mogą być zbierane przy użyciu dowolnej wersji programu Visual Studio. Jednak dane profilowania interakcji warstwy można wyświetlić tylko w programie Visual Studio Enterprise.
>
> Aby zbierać dane Porada w systemie Windows 8 lub Windows Server 2012, należy użyć Instrumentacja (**/trace**) opcja.

Do zbierania danych o interakcji między warstwy z dane próbkowania:

**polecenie vsperfaspnetcmd/TIP** `websiteUrl`

Do zbierania danych o interakcji między warstwy danych Instrumentacji:

**/ vsperfaspnetcmd/trace TIP** *podanym adresem URL*

Do zbierania danych o interakcji między warstwy z danych pamięci .NET:

**vsperfaspnetcmd /memory**[**: okres istnienia**] *  */tip *** podanym adresem URL*

## <a name="UsingNoWait"></a> Przy użyciu opcji/nowait

Domyślnie wiersza polecenia nie może zwracać po **vsperfaspnetcmd** polecenia. Następująca opcja składni służy do wymuszenia Zwróć w wierszu polecenia. W oknie wiersza polecenia można wykonywać innych operacji. Aby zakończyć profilowania, należy użyć **/shutdown** opcji w oddzielnej **vsperfaspnetcmd** polecenia.

Aby rozpocząć profilowanie:

**vsperfaspnetcmd** [*opcje*] *  */nowait *** podanym adresem URL*

Aby zakończyć profilowania:

**polecenie vsperfaspnetcmd/shutdown** *podanym adresem URL*

## <a name="additional-options"></a>Dodatkowe opcje

Można dodać żadnego z następujących opcji do polecenia wymienione wcześniej w tej sekcji, z wyjątkiem **polecenie vsperfaspnetcmd/shutdown** polecenia.

|Opcja|Opis|
|------------|-----------------|
|**/ Output:** `VspFile`|Domyślnie dane profilowania (. *Vsp*) plik jest tworzony w bieżącym katalogu z nazwą pliku **PerformanceReport.vsp**. Aby określić inną lokalizację i nazwę pliku, należy użyć opcji/Output.|
|**/ PackSymbols: wyłączanie**|Domyślnie VsPerfASPNETCmd osadza w symboli (nazwy funkcji i parametru i itd.). *vsp* pliku. Osadzanie symbole wprowadzić plik danych profilowania bardzo duże. Jeśli masz dostęp do. *pdb* pliki, które zawierają symbole podczas analizowania danych, użyj /packsymbols: wyłącz opcję, aby wyłączyć osadzanie symboli.|
