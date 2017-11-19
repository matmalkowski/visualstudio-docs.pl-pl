---
title: "Profilowanie szybkie witryny sieci Web za pomocą VSPerfASPNETCmd | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- proflilng tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
ms.assetid: 9a9d62a6-549a-45ac-a948-76eb98586ac5
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a1f2bc5acb69aa49fb37713942edb4e018039e8a
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2017
---
# <a name="rapid-web-site-profiling-with-vsperfaspnetcmd"></a>Szybkie profilowanie witryny sieci Web za pomocą VSPerfASPNETCmd
**VSPerfASPNETCmd** narzędzie wiersza polecenia umożliwia łatwe profilu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web. W porównaniu z [VSPerfCmd](../profiling/vsperfcmd.md) narzędzia wiersza polecenia, opcje zostały zredukowane nie zmiennych środowiskowych, które muszą być ustawione i ponowne uruchomienie komputera nie jest wymagane. Przy użyciu **VSPerfASPNETCmd** jest to preferowana metoda profilowania z Autonomiczny profiler. Aby uzyskać więcej informacji, zobacz [porady: Instalowanie autonomiczny profilera](../profiling/how-to-install-the-stand-alone-profiler.md).  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagane znaczących zmian w sposobie profilera Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowe techniki kolekcji. Zobacz [narzędzi wydajności w przypadku aplikacji systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 W niektórych scenariuszach, takich jak zbieranie danych współbieżności lub wstrzymywanie i wznawianie profilowania, za pomocą **VSPerfCmd** jest to preferowana metoda profilowania.  
  
> [!NOTE]
>  Narzędzia wiersza polecenia narzędzi profilowania znajdują się w podkatalogu narzędzia \Team Tools\Performance [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] katalogu instalacyjnego. Na komputerach 64-bitowe narzędzie VSPerfASPNETCmd znajduje się w katalogu narzędzia \Team Tools\Performance 32-bitowych. Za pomocą narzędzi wiersza polecenia profilera, możesz dodać ścieżkę narzędzia do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać go do samo polecenie. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
## <a name="profiling-an-aspnet-application"></a>Profilowanie aplikacji ASP.NET  
 Do profilu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web, wpisz jedno z poleceń opisane w poniższych sekcjach. Witryna sieci Web jest uruchamiana i uruchamia profilera do zbierania danych. Wykonywanie aplikacji, a następnie zamknij przeglądarkę. Aby zatrzymać profilowanie, naciśnij klawisz Enter w oknie wiersza polecenia.  
  
> [!NOTE]
>  Domyślnie wiersza polecenia nie może zwracać po **vsperfaspnetcmd** polecenia. Można użyć **/nowait** opcję, aby wymusić wiersza polecenia do zwrócenia. Zobacz [przy użyciu opcji/nowait](#UsingNoWait).  
  
## <a name="to-collect-application-statistics-by-using-the-sampling-method"></a>W celu zbierania statystyk aplikacji przy użyciu metody pobierania próbek  
 Próbkowanie to domyślne metody profilowania **VSPerfASPNETCmd** narzędzia i nie muszą być określone w wierszu polecenia. Następujący wiersz polecenia służy do zbierania statystyk aplikacji z określonej aplikacji sieci Web:  
  
 **vsperfaspnetcmd***podanym adresem URL*   
  
## <a name="to-collect-detailed-timing-data-by-using-the-instrumentation-method"></a>Do zbierania danych o chronometrażu przy użyciu metody Instrumentacji  
 Użyj następującego polecenia do zbierania danych o chronometrażu z dynamicznie skompilowanej [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web:  
  
 **polecenie vsperfaspnetcmd/trace***podanym adresem URL*   
  
 Jeśli chcesz profilu plików dll statycznie skompilowanej aplikacji sieci Web musi Instrumentacja plików za pomocą [VSInstr](../profiling/vsinstr.md) narzędzia wiersza polecenia. Polecenie vsperfaspnetcmd/trace obejmuje dane z instrumentowanych plików.  
  
## <a name="to-collect-net-memory-data"></a>Zbieranie danych pamięci .NET  
 **/Memory** opcję zbiera dane dotyczące alokacji obiektów w pamięci .NET i może zbierać dane dotyczące okresu istnienia tych obiektów. Zbieranie danych alokacji jest to domyślny tryb **/Memory** danych opcję i nie muszą być określone w wierszu polecenia.  
  
 **vsperfaspnetcmd /memory** *podanym adresem URL*  
  
 Użyj **okres istnienia** parametru dodatkowo do zebrania danych o okresie istnienia obiektu danych alokacji:  
  
 **vsperfaspnetcmd /memory:lifetime** *podanym adresem URL*  
  
 Można również użyć **/Trace** możliwość uwzględnienia szczegółowych informacji z danych pamięci .NET:  
  
 **vsperfaspnetcmd /memory**[**: okres istnienia**]   **/śledzenia**`websiteUrl`  
  
## <a name="to-collect-tier-interaction-data"></a>Do zbierania danych o interakcji między warstwy  
  
> [!WARNING]
>  Interakcja warstwowa profilowania danych (TIP) mogą zostać pobrane za pomocą [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], lub [!INCLUDE[vs_pro_current_short](../profiling/includes/vs_pro_current_short_md.md)]. Jednak interakcja warstwowa profilowania danych jest możliwy tylko w [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)] i [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  
>   
>  Aby zbierać dane Porada w systemie Windows 8 lub Windows Server 2012, należy użyć Instrumentacja (**/trace**) opcja.  
  
 Do zbierania danych o interakcji między warstwy z dane próbkowania:  
  
 **polecenie vsperfaspnetcmd/TIP**`websiteUrl`  
  
 Do zbierania danych o interakcji między warstwy danych Instrumentacji:  
  
 **/ vsperfaspnetcmd/trace TIP** *podanym adresem URL*  
  
 Do zbierania danych o interakcji między warstwy z danych pamięci .NET:  
  
 **vsperfaspnetcmd /memory**[**: okres istnienia**] **/tip***podanym adresem URL*  
  
##  <a name="UsingNoWait"></a>Przy użyciu opcji/nowait  
 Domyślnie wiersza polecenia nie może zwracać po **vsperfaspnetcmd** polecenia. Następująca opcja składni służy do wymuszenia Zwróć w wierszu polecenia. W oknie wiersza polecenia można wykonywać innych operacji. Aby zakończyć profilowania, należy użyć **/shutdown** opcji w oddzielnej **vsperfaspnetcmd** polecenia.  
  
 Aby rozpocząć profilowanie:  
  
 **vsperfaspnetcmd** [*opcje*] **/nowait***podanym adresem URL*  
  
 Aby zakończyć profilowania:  
  
 **polecenie vsperfaspnetcmd/shutdown** *podanym adresem URL*  
  
## <a name="additional-options"></a>Dodatkowe opcje  
 Można dodać żadnego z następujących opcji do polecenia wymienione wcześniej w tej sekcji, z wyjątkiem **polecenie vsperfaspnetcmd/shutdown** polecenia.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/ Output:**`VspFile`|Domyślnie profilowania plik danych (Vsp) jest tworzony w bieżącym katalogu z nazwą pliku **PerformanceReport.vsp**. Aby określić inną lokalizację i nazwę pliku, należy użyć opcji/Output.|  
|**/ PackSymbols: wyłączanie**|Domyślnie VsPerfASPNETCmd osadza symboli (funkcja i nazwy parametrów itp.) w pliku Vsp. Osadzanie symbole wprowadzić plik danych profilowania bardzo duże. Jeśli mają dostęp do .pdb, pliki, które zawierają symbole podczas analizowania danych, użyj /packsymbols: wyłącz opcję, aby wyłączyć osadzanie symboli.|
