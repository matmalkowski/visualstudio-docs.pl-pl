---
title: Konfigurowanie sesji wydajności | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- common tasks, performance
- common tasks, profiling tools
- profiling tools, common tasks
- performance, gathering data
ms.assetid: e1c3ba41-ffca-4edf-9a7f-8a5a9244ef9b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5735c1c4cd1ec5521b9eea00bdc31ab53e67b325
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="configure-performance-sessions"></a>Konfigurowanie sesji wydajności
Za pomocą [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędziach profilowania mogą zbierać szeroką gamę dane wydajności dla wielu typów aplikacji. W tej sekcji przedstawiono sposób umożliwiają konfigurowanie narzędzi profilowania do zbierania danych interesującego Wizardand wydajności właściwości sesji wydajności i docelowy plik binarny. Profilowanie właściwości konfiguracji narzędzia mogą służyć do kontrolowania ilości danych są zbierane w przebiegu profilowania. Aby uzyskać więcej informacji, zobacz [kontroli zbierania danych](../profiling/controlling-data-collection.md).  
  
> [!NOTE]
>  W wielu przypadkach przy użyciu domyślnych właściwości Kreatora osiągów to efektywny sposób zbierania danych profilowania. Aby uzyskać więcej informacji, zobacz [przewodnik dla początkujących profilowanie wydajności](../profiling/beginners-guide-to-performance-profiling.md) i [wprowadzenie](../profiling/getting-started-with-performance-tools.md).  
  
## <a name="common-tasks"></a>Wspólne zadania
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Ustaw podstawowe opcje profilowania:** należy skonfigurować [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] do korzystania z serwera symboli firmy Microsoft. Będzie to upewnij się, że masz dostęp do symboli, takich jak nazwy funkcji i parametr, dla bieżącej wersji systemu Windows i innych aplikacji firmy Microsoft. Można również określić inne opcje ogólne, przed rozpoczęciem profilowania sesji, takie jak uprawnienia systemowe do narzędzi profilowania i nazw plików danych profilowania.|-   [Porady: odwołanie do systemu Windows — informacje o symbolach](../profiling/how-to-reference-windows-symbol-information.md)<br />-   [Porady: Serializuj informacje dotyczące symboli](../profiling/how-to-serialize-symbol-information.md)<br />-   [Porady: Ustawianie bieżącej sesji](../profiling/how-to-set-the-current-session.md)<br />-   [Porady: Ustawianie uprawnień](../profiling/how-to-set-permissions.md)<br />-   [Porady: Ustawianie opcji nazwy pliku danych wydajności](../profiling/how-to-set-performance-data-file-name-options.md)|  
|**Określ dane, które mają być zbierane:** procedur, które są używane do konfigurowania sesję profilowania zależą od typ aplikacji docelowej, który ma zostać profilu i typu danych wydajności, które mają być zbierane.|-   [Porady: Wybieranie metod kolekcji](../profiling/how-to-choose-collection-methods.md)<br />-   [Zbieranie statystyk wydajności za pomocą metody pobierania próbek](../profiling/collecting-performance-statistics-by-using-sampling.md)<br />-   [Zbieranie danych pamięci .NET alokacji i okresem istnienia](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Zbieranie szczegółowych danych o chronometrażu przy użyciu Instrumentacji](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)<br />-   [Porady: kodu JavaScript profilu na stronach sieci web](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Zbieranie danych współbieżności wątku i procesu](../profiling/collecting-thread-and-process-concurrency-data.md)<br />-   [Zbierać dodatkowe dane dotyczące wydajności](../profiling/collecting-additional-performance-data.md)|  
|**Ustawianie opcji konfiguracji zaawansowanej:** podczas profilu aplikacji .NET Framework, które ładują wielu wersji wspólnego języka środowiska wykonawczego języka wspólnego (CLR), można określić, którą wersję profilu. Jeśli masz wiele plików .exe w sesji wydajności, można ustawić kolejność uruchamiania plików binarnych.|-   [Porady: Określanie środowiska uruchomieniowego .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)<br />-   [Porady: Określanie plików binarnych do uruchomienia](../profiling/how-to-specify-the-binary-to-start.md)|  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Sterowanie zbieraniem danych](../profiling/controlling-data-collection.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Eksplorator wydajności](../profiling/performance-explorer.md)