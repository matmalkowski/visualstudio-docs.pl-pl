---
title: 'Przygotowanie debugowania: Typy projektów Visual C++ | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- project templates, debugging
- Visual C++ projects, debugging
- debug builds, project settings
- debugging [C++]
ms.assetid: 912b4ba2-7719-43d5-b087-db33e3f9329a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 64d49d799c0ec0b3845a262c248d2438572ecd5d
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="debugging-preparation-visual-c-project-types"></a>Przygotowanie debugowania: Typy projektów Visual C++
W tej sekcji opisano sposób debugowania typów podstawowych projektów utworzonych przez [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] szablony projektu.  
  
 Należy pamiętać, że tych typów projektów, które utworzyć biblioteki DLL jako ich dane wyjściowe zostały zgrupowane jako [debugowanie projektów DLL](../debugger/debugging-dll-projects.md) z powodu wspólne funkcje mają.  
  
##  <a name="BKMK_In_this_topic"></a> W tym temacie  
 [Zalecane ustawienia właściwości](#BKMK_Recommended_Property_Settings)  
  
 [Projekty Win32](#BKMK_Win32_Projects)  
  
-   [Debugowanie aplikacji C lub C++ Win32](#BKMK_To_debug_a_C_or_C___Win32_application)  
  
-   [Aby ręcznie ustawić konfiguracji debugowania](#BKMK_To_manually_set_a_Debug_configuration)  
  
 [Aplikacje Windows Forms (.NET)](#BKMK_Windows_Forms_Applications___NET_)  
  
##  <a name="BKMK_Recommended_Property_Settings"></a> Zalecane ustawienia właściwości  
 Taki sam sposób dla wszystkich niezarządzanych scenariuszach debugowania można ustawić niektórych właściwości. Poniższe tabele Wyświetl zalecane ustawienia właściwości. Ustawienia niewymienione w tym może się różnić między typami inny projekt niezarządzane. Aby uzyskać więcej informacji, zobacz [ustawienia projektu dla konfiguracji debugowania języka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)  
  
### <a name="configuration-properties-124-cc-124-optimization-node"></a>Właściwości konfiguracji &#124; C/C++ &#124; węzła optymalizacji  
  
|Nazwa właściwości|Ustawienie|  
|-------------------|-------------|  
|**Optymalizacja**|Ustaw **wyłączone (/ 0 d).** Kod zoptymalizowany jest trudniej debugowania, ponieważ nie odpowiadają wygenerowanego instrukcje bezpośrednio w kodzie źródłowym. Jeśli program zawiera usterkę, która jest wyświetlana tylko w zoptymalizowanym kodzie, możesz włączyć to ustawienie, ale należy pamiętać, że kodem przedstawionym w **dezasemblacji** okna jest generowany na podstawie zoptymalizowane źródła, które mogą być niezgodne elementy wyświetlane w źródle systemu Windows. Inne funkcje, takie jak wykonywanie krok po kroku, może nie działać zgodnie z oczekiwaniami.|  
  
### <a name="configuration-properties-124-linker-124-debugging-node"></a>Właściwości konfiguracji &#124; konsolidatora &#124; węzła debugowania  
  
|Nazwa właściwości|Ustawienie|  
|-------------------|-------------|  
|**Generuj informacje debugowania**|Zawsze należy ustawić tę opcję, **tak (/ DEBUG)** do tworzenia, debugowania symbole i pliki wymagane do debugowania. Gdy aplikacja przechodzi do środowiska produkcyjnego, można ustawić na wyłączone.|  
  
 [W tym temacie](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Win32_Projects"></a> Projekty Win32  
 Win32 — aplikacje są napisane w języka C lub C++ tradycyjnych programów systemu Windows. Debugowanie tego typu aplikacji w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jest prosta.  
  
 Win32 — aplikacje obejmują aplikacje MFC i ATL projektów. Użyj interfejsów API systemu Windows i może używać MFC lub ATL, ale nie należy używać środowisko uruchomieniowe języka wspólnego (CLR). One jednak wywołać kodu zarządzanego, która używa środowiska CLR.  
  
 W poniższej procedurze wyjaśniono sposób debugowania projektu Win32 z poziomu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Innym sposobem debugowania aplikacji Win32 jest uruchomienie aplikacji poza [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i Dołącz do niej. Aby uzyskać więcej informacji, zobacz [dołączyć do uruchamiania procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
###  <a name="BKMK_To_debug_a_C_or_C___Win32_application"></a> Debugowanie aplikacji C lub C++ Win32  
  
1.  Otwórz projekt w programie Visual Studio.  
  
2.  Na **debugowania** menu, wybierz **Start**.  
  
3.  Debugowanie za pomocą techniki opisane w [podstawy debugera](../debugger/debugger-basics.md).  
  
###  <a name="BKMK_To_manually_set_a_Debug_configuration"></a> Aby ręcznie ustawić konfiguracji debugowania  
  
1.  Na **widoku** menu, kliknij przycisk **strony właściwości**.  
  
2.  Kliknij przycisk **właściwości konfiguracji** węzeł, aby go otworzyć, jeśli nie jest jeszcze  
  
3.  Wybierz **ogólne**i ustaw wartość **dane wyjściowe** wiersz do **debugowania**.  
  
4.  Otwórz **C/C++** , a następnie wybierz węzeł **ogólne**.  
  
     W **debugowania** wiersza, określ typ debugowania informacji ma zostać wygenerowane przez kompilator. Można wybrać wartości to **bazy danych programu (/Zi)** lub **bazy danych programu dla Edytuj i Kontynuuj (/ZI)**.  
  
5.  Wybierz **optymalizacji**, a następnie w **optymalizacji** wierszu, wybierz opcję **wyłączone (/ 0d)** z listy rozwijanej.  
  
     Kod zoptymalizowany jest trudniej debugowania, ponieważ nie odpowiadają wygenerowanego instrukcje bezpośrednio w kodzie źródłowym. Jeśli okaże się, że program zawiera usterkę, która jest wyświetlana tylko w zoptymalizowanym kodzie, możesz włączyć to ustawienie, ale należy pamiętać, że kod wyświetlany w oknie dezasemblacji jest generowany na podstawie zoptymalizowane źródła, które może nie odpowiadać widać w systemu windows źródła. Funkcje, takie jak wykonywanie krok po kroku są prawdopodobnie Pokaż punktów przerwania i wykonywania punktu niepoprawnie.  
  
6.  Otwórz **konsolidatora** , a następnie wybierz węzeł **debugowanie**. W pierwszym **Generuj** wierszu, wybierz opcję **tak (/ DEBUG)** z listy rozwijanej. Zawsze nadawaj temu podczas debugowania.  
  
 Aby uzyskać więcej informacji, zobacz[ustawienia projektu dla konfiguracji debugowania C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
 [W tym temacie](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
##  <a name="BKMK_Windows_Forms_Applications___NET_"></a> Aplikacje Windows Forms (.NET)  
 **Aplikacji formularzy systemu Windows (.NET)** szablon tworzy [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] aplikacji formularzy systemu Windows. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie projektu aplikacji Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
 Debugowanie tego typu aplikacji w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] przebiega podobnie jak w zarządzanych aplikacjach formularzy systemu Windows.  
  
 Podczas tworzenia projektu formularzy systemu Windows przy użyciu szablonu projektu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automatycznie tworzy wymagane ustawienia konfiguracji Debug i Release. Jeśli to konieczne, możesz zmienić te ustawienia w  **\<Nazwa projektu > strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [konfiguracji Debug i Release](../debugger/how-to-set-debug-and-release-configurations.md).  
  
 Aby uzyskać więcej informacji, zobacz [ustawienia projektu dla konfiguracji debugowania C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
 Innym sposobem debugowania aplikacji formularzy systemu Windows jest uruchomienie aplikacji poza [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i Dołącz do niej. Aby uzyskać więcej informacji, zobacz [dołączanie do uruchamiania programu lub wielu programów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 [W tym temacie](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe informacje o debugerze](../debugger/debugger-basics.md)   
 [Ustawienia projektu dla konfiguracji debugowania z C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Dołączanie do uruchomiony Program lub wielu programów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Konfiguracje debugowania i wydania](../debugger/how-to-set-debug-and-release-configurations.md)   
 [Porady: Tworzenie projektu aplikacji systemu Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)