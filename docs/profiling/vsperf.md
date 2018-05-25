---
title: VSPerf | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: b5854e62-279e-4850-bfeb-0c6ef82f4805
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fcac1e902ccc1fcc5432a231c5f34629422815fd
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2018
---
# <a name="vsperf"></a>VSPerf
Użyj **VsPerf** narzędzie wiersza polecenia do:  
  
1.  Profil aplikacji platformy uniwersalnej systemu Windows z wiersza polecenia programu Visual Studio nie jest zainstalowany na urządzeniu.  
  
2.  Profil aplikacji klasycznych systemu Windows 8 i aplikacji systemu Windows Server 2012 za pomocą metoda profilowania próbkowania.  
  
 Aby uzyskać więcej informacji o opcjach profilowania, zobacz [narzędzi wydajności w przypadku aplikacji systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="uwp-apps-only"></a>Tylko aplikacje platformy uniwersalnej systemu Windows  
 Te opcje są stosowane tylko do aplikacji platformy uniwersalnej systemu Windows.  
  
|||  
|-|-|  
|**App: {AppName}**|Uruchamia profilera i czeka na określonej aplikacji, które mają zostać uruchomione z Start menu.<br /><br /> Uruchom `vsperf /listapps` wyświetlanie nazwy aplikacji i Pełna_nazwa_pakietu zainstalowane aplikacje.|  
|**/ pakietu: {Pełna_nazwa_pakietu}**|Uruchamia profilera i czeka na określonej aplikacji, które mają zostać uruchomione z Start menu.<br /><br /> Uruchom `vsperf /listapps` wyświetlanie nazwy aplikacji i Pełna_nazwa_pakietu zainstalowane aplikacje.|  
|**/js**|Wymagana dla profilowania aplikacji JavaScript.<br /><br /> Zbieranie danych wydajności z aplikacji JavaScript.<br /><br /> Używana tylko z przełącznika/Package lub / dołączyć.|  
|**/noclr**|Opcjonalna. Nie zbieraj danych CLR.<br /><br /> Używana tylko z przełącznika/Package lub / dołączyć.<br /><br /> Optymalizacja rozwiąże nie symbole zarządzane.|  
|**/listapps**|Lista zainstalowanych nazwy aplikacji i PackageFullNames.|  
  
## <a name="windows-8-desktop-applications-and-windows-server-2012-applications-only"></a>Aplikacje systemu Windows 8 i tylko aplikacje systemu Windows Server 2012  
 Te opcje nie działają w aplikacji platformy uniwersalnej systemu Windows.  
  
|||  
|-|-|  
|**/ uruchomić: {plik wykonywalny}**|Uruchamia i rozpocznie się profilowania określonego pliku wykonywalnego.|  
|**przełącznika/args: {ExecutableArguments}**|Określa argumenty wiersza polecenia do przekazania **/uruchamianie** docelowej.|  
|**/ Console**|Uruchamia **/uruchamianie** docelowego w nowym oknie polecenia.|  
  
## <a name="all-applications"></a>Wszystkie aplikacje  
 Te opcję stosowania do aplikacji systemu Windows 8 lub Windows Server 2012.  
  
|||  
|-|-|  
|**/ dołączyć: {PID&#124;ProcessName} [, PID&#124;ProcessName]...**|Zbiera dane z określonych procesów.<br /><br /> Użyj Menedżera zadań, aby wyświetlić identyfikator procesu (PID) i nazwy działających aplikacji procesu.|  
|**/ file:{ReportName}**|Opcjonalna. Określa plik wyjściowy (zastępuje istniejący plik).<br /><br /> Używana tylko z przełącznika/Package lub / dołączyć.|  
|**/ pause**|Wstrzymaj zbieranie danych.|  
|**/Resume**|Wznowienie zbierania danych.|  
|**/ stop**|Zatrzymaj zbieranie danych i zakończenie procesów docelowych.|  
|**/ detach**|Zatrzymaj zbieranie danych, ale pozwól procesów docelowych nadal działać.|  
|**/ status**|Pokaż stan profilera.|  
  
## <a name="see-also"></a>Zobacz także  
 [Narzędzia wydajności w przypadku aplikacji systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)   
 [Profilowanie z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)