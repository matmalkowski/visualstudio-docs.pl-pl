---
title: VSPerf | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5854e62-279e-4850-bfeb-0c6ef82f4805
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8bd2365752e31ce463610b75fee3884271841b3c
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2017
---
# <a name="vsperf"></a>VSPerf
Użyj **VsPerf** narzędzie wiersza polecenia do:  
  
1.  Profil aplikacji platformy uniwersalnej systemu Windows z wiersza polecenia programu Visual Studio nie jest zainstalowany na urządzeniu.  
  
2.  Profil aplikacji klasycznych systemu Windows 8 i aplikacji systemu Windows Server 2012 za pomocą metoda profilowania próbkowania.  
  
 Aby uzyskać więcej informacji o opcjach profilowania, zobacz [narzędzi wydajności w przypadku aplikacji systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
##  <a name="BKMK_In_this_topic"></a>W tym temacie  
 W tym temacie opisano opcje używane z `vsperf.exe` narzędzia wiersza polecenia. Temat zawiera następujące sekcje:  
  
 [Tylko aplikacje platformy uniwersalnej systemu Windows](#BKMK_windows_store_apps_only)  
  
 [Aplikacje systemu Windows 8 i tylko aplikacje systemu Windows Server 2012](#BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only)  
  
 [Wszystkie aplikacje](#BKMK_All_applications)  
  
##  <a name="BKMK_windows_store_apps_only"></a>Tylko aplikacje platformy uniwersalnej systemu Windows  
 Te opcje są stosowane tylko do aplikacji platformy uniwersalnej systemu Windows.  
  
|||  
|-|-|  
|**App: {AppName}**|Uruchamia profilera i czeka na określonej aplikacji, które mają zostać uruchomione z Start menu.<br /><br /> Uruchom `vsperf /listapps` wyświetlanie nazwy aplikacji i Pełna_nazwa_pakietu zainstalowane aplikacje.|  
|**/ pakietu: {Pełna_nazwa_pakietu}**|Uruchamia profilera i czeka na określonej aplikacji, które mają zostać uruchomione z Start menu.<br /><br /> Uruchom `vsperf /listapps` wyświetlanie nazwy aplikacji i Pełna_nazwa_pakietu zainstalowane aplikacje.|  
|**/js**|Wymagana dla profilowania aplikacji JavaScript.<br /><br /> Zbieranie danych wydajności z aplikacji JavaScript.<br /><br /> Używana tylko z przełącznika/Package lub / dołączyć.|  
|**/noclr**|Opcjonalny. Nie zbieraj danych CLR.<br /><br /> Używana tylko z przełącznika/Package lub / dołączyć.<br /><br /> Optymalizacja rozwiąże nie symbole zarządzane.|  
|**/listapps**|Lista zainstalowanych nazwy aplikacji i PackageFullNames.|  
  
##  <a name="BKMK_Windows_8_classic_applications_and_Windows_Server_2012_applications_only"></a>Aplikacje systemu Windows 8 i tylko aplikacje systemu Windows Server 2012  
 Te opcje nie działają w aplikacji platformy uniwersalnej systemu Windows.  
  
|||  
|-|-|  
|**/ uruchomić: {plik wykonywalny}**|Uruchamia i rozpocznie się profilowania określonego pliku wykonywalnego.|  
|**przełącznika/args: {ExecutableArguments}**|Określa argumenty wiersza polecenia do przekazania **/uruchamianie** docelowej.|  
|**/ Console**|Uruchamia **/uruchamianie** docelowego w nowym oknie polecenia.|  
  
##  <a name="BKMK_All_applications"></a>Wszystkie aplikacje  
 Te opcję stosowania do aplikacji systemu Windows 8 lub Windows Server 2012.  
  
|||  
|-|-|  
|**/ dołączyć: {PID &#124; Parametr} [, PID &#124; Parametr]...**|Zbiera dane z określonych procesów.<br /><br /> Użyj Menedżera zadań, aby wyświetlić identyfikator procesu (PID) i nazwy działających aplikacji procesu.|  
|**/ file:{ReportName}**|Opcjonalny. Określa plik wyjściowy (zastępuje istniejący plik).<br /><br /> Używana tylko z przełącznika/Package lub / dołączyć.|  
|**/ pause**|Wstrzymaj zbieranie danych.|  
|**/Resume**|Wznowienie zbierania danych.|  
|**/ stop**|Zatrzymaj zbieranie danych i zakończenie procesów docelowych.|  
|**/ detach**|Zatrzymaj zbieranie danych, ale pozwól procesów docelowych nadal działać.|  
|**/ status**|Pokaż stan profilera.|  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia wydajności w przypadku aplikacji systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)   
 [Profilowanie z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)