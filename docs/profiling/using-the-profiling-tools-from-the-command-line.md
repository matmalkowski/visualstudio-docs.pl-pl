---
title: "Narzędzia przy użyciu profilowania z wiersza polecenia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- command line, performance tools
- command-line tools, performance tools
- profiling tools,command line
- tools, command-line
- command line, tools
ms.assetid: 6593fa82-181e-4009-a0ed-02aa24c2c063
caps.latest.revision: "35"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cff5b3091213cb0c4c708ce016f486fc7262a2c4
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2017
---
# <a name="using-the-profiling-tools-from-the-command-line"></a>Korzystanie z narzędzi do profilowania z wiersza polecenia
Można użyć narzędzia wiersza polecenia z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] profilowania narzędzia do profilu aplikacji w wierszu polecenia i w celu zautomatyzowania profilowania za pomocą plików wsadowych i skryptów. Można również generować pliki raportu w wierszu polecenia. Lekkie autonomiczny profilera służy do zbierania danych na komputerach, które nie mają [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zainstalowane.  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagane znaczących zmian w sposobie profilera Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowe techniki kolekcji. Zobacz [narzędzi wydajności w przypadku aplikacji systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Typowe zadania  
  
|Zadanie|Zawartość pokrewna|  
|----------|---------------------|  
|**Ustaw lokalizację symboli:** Aby wyświetlić nazwy funkcji i parametrów, profilera musi mieć dostęp do plików symboli (.pdb) PROFILOWANEGO plików binarnych. Pliki te powinny obejmować pliki symboli dla systemu operacyjnego Microsoft i aplikacje, które chcesz wyświetlić w analizy. Upewnij się, że masz prawidłowe .pdb, pliki dla danych binarnych Microsoft umożliwia publicznego serwera Microsoft symbol server.|-   [Porady: Określanie lokalizacji plików symboli z wiersza polecenia](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md)|  
|**Profil aplikacji:** narzędzia wiersza polecenia i opcje używane do profilu aplikacji docelowej są zależne od typu aplikacji, metoda profilowania i określa, czy element docelowy jest aplikacją zarządzanym lub macierzystym.|-   [Przy użyciu metod profilowania z wiersza polecenia](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)<br />-   [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)<br />-   [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)<br />-   [Usługi profilowania](../profiling/command-line-profiling-of-services.md)|  
|**Tworzenie raportów XML i CSV:** profilowania w wierszu polecenia tworzy pliki danych, które mogą być wyświetlane w interfejsie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Można również generować plik .xml lub plik wartości rozdzielanych przecinkami (.csv) pliki danych za pomocą narzędzia wiersza polecenia VSPerfReport.|-   [Tworzenie raportów profilera z wiersza polecenia](../profiling/creating-profiler-reports-from-the-command-line.md)<br />-   [VSPerfReport](../profiling/vsperfreport.md)|  
|**Profilowanie kodu na komputerach bez programu Visual Studio:** autonomiczny profilera narzędziach profilowania służy do zbierania danych dla aplikacji na komputerach, które nie mają [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zainstalowane.|-   [Porady: Instalowanie autonomiczny profilera](../profiling/how-to-install-the-stand-alone-profiler.md)|  
  
## <a name="reference"></a>Tematy pomocy  
 [Wiersza polecenia narzędzi profilowania](../profiling/command-line-profiling-tools-reference.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Eksplorator wydajności](../profiling/performance-explorer.md)