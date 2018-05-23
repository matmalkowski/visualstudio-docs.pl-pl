---
title: Narzędzia przy użyciu profilowania z wiersza polecenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- command line, performance tools
- command-line tools, performance tools
- profiling tools,command line
- tools, command-line
- command line, tools
ms.assetid: 6593fa82-181e-4009-a0ed-02aa24c2c063
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 74b00a65dac65bc9b0f5f6b7a4084c1a0999f0e2
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
---
# <a name="use-the-profiling-tools-from-the-command-line"></a>Użyj narzędzi profilowania z wiersza polecenia
Można użyć narzędzia wiersza polecenia z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] profilowania narzędzia do profilu aplikacji w wierszu polecenia i w celu zautomatyzowania profilowania za pomocą plików wsadowych i skryptów. Można również generować pliki raportu w wierszu polecenia. Lekkie autonomiczny profilera służy do zbierania danych na komputerach, które nie mają [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zainstalowane.  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagane znaczących zmian w sposobie profilera Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowe techniki kolekcji. Zobacz [narzędzi wydajności w przypadku aplikacji systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Wspólne zadania  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Ustaw lokalizację symboli:** Aby wyświetlić nazwy funkcji i parametrów, profilera musi mieć dostęp do plików symboli (.pdb) PROFILOWANEGO plików binarnych. Pliki te powinny obejmować pliki symboli dla systemu operacyjnego Microsoft i aplikacje, które chcesz wyświetlić w analizy. Upewnij się, że masz prawidłowe .pdb, pliki dla danych binarnych Microsoft umożliwia publicznego serwera Microsoft symbol server.|-   [Porady: Określanie lokalizacji plików symboli z wiersza polecenia](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md)|  
|**Profil aplikacji:** narzędzia wiersza polecenia i opcje używane do profilu aplikacji docelowej są zależne od typu aplikacji, metoda profilowania i określa, czy element docelowy jest aplikacją zarządzanym lub macierzystym.|-   [Użyj metod profilowania z wiersza polecenia](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)<br />-   [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)<br />-   [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)<br />-   [Usługi profilowania](../profiling/command-line-profiling-of-services.md)|  
|**Tworzenie raportów XML i CSV:** profilowania w wierszu polecenia tworzy pliki danych, które mogą być wyświetlane w interfejsie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Można również generować plik .xml lub plik wartości rozdzielanych przecinkami (.csv) pliki danych za pomocą narzędzia wiersza polecenia VSPerfReport.|-   [Tworzenie raportów profilera z wiersza polecenia](../profiling/creating-profiler-reports-from-the-command-line.md)<br />-   [VSPerfReport](../profiling/vsperfreport.md)|  
|**Profilowanie kodu na komputerach bez programu Visual Studio:** autonomiczny profilera narzędziach profilowania służy do zbierania danych dla aplikacji na komputerach, które nie mają [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zainstalowane.|-   [Porady: Instalowanie autonomiczny profilera](../profiling/how-to-install-the-stand-alone-profiler.md)|  
  
## <a name="reference"></a>Tematy pomocy  
 [Informacje dotyczące wiersza polecenia narzędzi profilowania](../profiling/command-line-profiling-tools-reference.md)  
  
## <a name="see-also"></a>Zobacz także  
 [Eksplorator wydajności](../profiling/performance-explorer.md)