---
title: Debugowanie kodu GPU | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: c7e77a5a-cb57-4b11-9187-ecc89acc8775
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eac4799bec68b275586512dcf0b55fffa7484a90
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="debugging-gpu-code"></a>Debugowanie kodu GPU
Można debugować kodu C++, który działa w jednostce przetwarzania graficznych (GPU). Obsługa w programie Visual Studio debugowania GPU obejmuje wykrywania wyścigu uruchamianie procesów i związanych z nimi i integracji w oknach debugowania.  
  
## <a name="supported-platforms"></a>Obsługiwane platformy  
 Debugowanie jest obsługiwane w [!INCLUDE[win7](../debugger/includes/win7_md.md)], [!INCLUDE[win8](../debugger/includes/win8_md.md)], [!INCLUDE[winsvr08_r2](../debugger/includes/winsvr08_r2_md.md)], i [!INCLUDE[winserver8](../debugger/includes/winserver8_md.md)]. Do debugowania w emulatorze oprogramowania [!INCLUDE[win8](../debugger/includes/win8_md.md)], lub [!INCLUDE[winserver8](../debugger/includes/winserver8_md.md)] jest wymagana. Do debugowania na sprzęcie, musisz zainstalować sterowników dla karty graficznej. Nie wszyscy dostawcy sprzętu implementuje wszystkie funkcje debugera. W dokumentacji dostawcy ograniczenia.  
  
> [!NOTE]
>  Niezależnych dostawców sprzętu, które mają być obsługiwane debugowania GPU w programie Visual Studio należy utworzyć własne sterowniki bibliotekę DLL, która implementuje interfejs VSD3DDebug i obiektów docelowych.  
  
## <a name="configuring-gpu-debugging"></a>Konfigurowanie debugowania GPU  
 Debuger nie może być dzielone w kodzie procesora CPU i kodu GPU podczas wykonywania tej samej aplikacji. Domyślnie debuger dzieli na kod procesora CPU. Debugowanie kodu GPU, użyj jednej z tych dwóch kroków:  
  
-   W **debugowania typu** listy na **standardowe** narzędzi wybierz **GPU tylko**.  
  
-   W **Eksploratora rozwiązań**, w menu skrótów projektu wybierz **właściwości**. W **strony właściwości** okno dialogowe, wybierz opcję **debugowanie**, a następnie wybierz **GPU tylko** w **typ debugera** listy.  
  
## <a name="launching-and-attaching-to-applications"></a>Uruchamianie i dołączanie do aplikacji  
 Polecenia debugowania programu Visual Studio umożliwiają uruchamianie i zatrzymywanie debugowania GPU. Aby uzyskać więcej informacji, zobacz [nawigowanie po kodzie za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md). Można również dołączyć debuger procesora GPU do uruchomionego procesu, ale tylko wtedy, jeśli ten proces jest wykonywany kodu GPU. Aby uzyskać więcej informacji, zobacz [dołączyć do uruchamiania procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
## <a name="run-current-tile-to-cursor-and-run-to-cursor"></a>Uruchom bieżący Kafelek do kursora i uruchom do kursora  
 Podczas debugowania na procesorze GPU, masz dwie opcje uruchamiania w lokalizacji kursora. Polecenia obie te opcje są dostępne w menu skrótów w edytorze kodu.  
  
1.  **Uruchom do kursora** polecenie uruchamia aplikację, dopóki nie osiągnie lokalizacji kursora, a następnie dzieli. Nie oznacza to, czy bieżący wątek jest uruchomiony do kursora; zamiast oznacza to, że pierwszy wątku, który osiągnie punktu kursora wyzwala przerwy. Zobacz [nawigowanie po kodzie za pomocą debugera](../debugger/navigating-through-code-with-the-debugger.md)  
  
2.  **Uruchom bieżący Kafelek do kursora** polecenie uruchamia aplikację, aż zostanie wszystkie wątki na kafelku bieżący kursor, a następnie podziału.  
  
## <a name="debugging-windows"></a>Debugowanie systemu Windows  
 Przy użyciu określonych debugowania systemu windows, można zbadać, Flaga i Zablokuj wątki GPU. Aby uzyskać więcej informacji, zobacz:  
  
-   [Korzystanie z okna stosów równoległych](../debugger/using-the-parallel-stacks-window.md)  
  
-   [Korzystanie z okna zadań](../debugger/using-the-tasks-window.md)  
  
-   [Porady: Korzystanie z okna czujki równoległej](../debugger/how-to-use-the-parallel-watch-window.md)  
  
-   [Debugowanie wątków i procesów](../debugger/debug-threads-and-processes.md) (Lokalizacja debugowania narzędzi)  
  
-   [Porady: Korzystanie z okna wątków GPU](../debugger/how-to-use-the-gpu-threads-window.md)  
  
## <a name="data-synchronization-exceptions"></a>Wyjątki synchronizacji danych  
 Debuger można zidentyfikować kilka warunków synchronizacji danych podczas wykonywania. Gdy zostanie wykryty warunek, debuger wchodzi w stan przerwania. Dostępne są dwie opcje —**Podziel** lub **Kontynuuj**. Za pomocą **wyjątki** okno dialogowe, możesz określić, czy debuger wykrywa te warunki i warunki, które go będzie Przerwij dla. Aby uzyskać więcej informacji, zobacz [Zarządzanie wyjątkami za pomocą debugera](../debugger/managing-exceptions-with-the-debugger.md). Można również użyć **opcje** okno dialogowe, aby określić, że debuger ignorować wyjątki dane, które są zapisywane nie zmiany wartości danych. Aby uzyskać więcej informacji, zobacz [ogólne, debugowanie, opcje — Okno dialogowe](../debugger/general-debugging-options-dialog-box.md).  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
  
### <a name="specifying-an-accelerator"></a>Określanie klawiszy skrótów  
 Punkty przerwania w kodzie GPU są osiągane tylko, jeśli kod jest uruchomiony na [Accelerator::direct3d_ref —](/cpp/parallel/amp/reference/accelerator-class.md#accelerator__direct3d_ref_Data_Member) akceleratora (REF). Jeśli nie określisz akceleratora w kodzie, akceleratora REF jest automatycznie wybierany jako **typ akceleratora debugowania** we właściwościach projektu. Jeśli kod wybiera jawnie akceleratora, akceleratora REF nie będą używane podczas debugowania i punktów przerwania nie zostanie uruchomiona, chyba że ma sprzętu GPU obsługa debugowania. Użytkownik może rozwiązać ten problem przez pisania kodu, tak aby były używane podczas debugowania akceleratora REF. Aby uzyskać więcej informacji, zobacz właściwości projektu i [przy użyciu akceleratora i obiektów accelerator_view](/cpp/parallel/amp/using-accelerator-and-accelerator-view-objects) i [ustawienia projektu dla konfiguracji debugowania C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
### <a name="conditional-breakpoints"></a>Warunkowe punkty przerwania  
 Warunkowe punkty przerwania w kodzie GPU są obsługiwane, ale nie wszystkie wyrażenia nie można ocenić urządzenia. Jeśli na urządzeniu nie można obliczyć wyrażenia, jest obliczane w debugerze. Debuger prawdopodobnie może działać wolniej niż urządzenia.  
  
### <a name="error-there-is-a-configuration-issue-with-the-selected-debugging-accelerator-type"></a>Błąd: Brak problem konfiguracji wybranego typu akceleratora debugowania.  
 Ten błąd wystąpi, gdy występuje niespójność między ustawienia projektu i konfiguracji komputera, który debugowania na. Aby uzyskać więcej informacji, zobacz [ustawienia projektu dla konfiguracji debugowania C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
### <a name="error-the-debug-driver-for-the-selected-debugging-accelerator-type-is-not-installed-on-the-target-machine"></a>Błąd: Sterownik debugowania dla wybranego typu akceleratora debugowania nie jest zainstalowany na komputerze docelowym.  
 Ten błąd wystąpi w przypadku debugowania na komputerze zdalnym. Debuger nie może określić do czasu wykonywania, czy sterowniki są zainstalowane na komputerze zdalnym. Sterowniki staną się dostępne od producenta karty graficznej.  
  
### <a name="error-timeout-detection-and-recovery-tdr-must-be-disabled-at-the-remote-site"></a>Błąd: Limit czasu wykrywania i odzyskiwania (TDR) musi zostać wyłączone w lokacji zdalnej.  
 Istnieje możliwość obliczenia C++ AMP przekroczyć domyślny interwał czasu jest ustawiana przez proces odzyskiwania (TDR) i wykrywania limitu czasu systemu Windows. W takim przypadku obliczenia została anulowana, a dane zostaną utracone. Aby uzyskać więcej informacji, zobacz [obsługi TDR w C++ AMP](http://go.microsoft.com/fwlink/p/?LinkId=249154).  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Debugowanie aplikacji C++ AMP](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)   
 [Ustawienia projektu dla konfiguracji debugowania z C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Rozpoczynanie debugowania GPU w programie Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=255381)