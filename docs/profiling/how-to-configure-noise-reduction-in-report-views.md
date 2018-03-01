---
title: 'Porady: Konfigurowanie redukcji szumu w widoku raportu | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.noisereduction.dialog
helpviewer_keywords:
- profiling tools, trimming
- profiling tools, report noise reduction
- profiling tools, folding
ms.assetid: b07e0375-bb73-47e3-8d1d-b9b492fb16c9
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c0648336f4ba6be42de7253c27703fe544fb58d7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-noise-reduction-in-report-views"></a>Porady: konfigurowanie redukcji szumu w widoku raportu
Raporty wydajności można skonfigurować dla redukcji szumu poprzez ograniczenie ilości danych, które są prezentowane w widoku drzewa wywołań i Widok alokacji. Za pomocą redukcji szumu, problemy z wydajnością są lepiej widoczne. Jest to przydatne podczas analizowania wydajności raportów.  
  
 Opcje konfiguracji redukcji szumu obejmują następujące ustawienia:  
  
-   **Przycinanie** podczas analizowania raportu widoku zostaną pominięte funkcje, które wchodzą w ustawieniach wartość i wartość progową, które zostały skonfigurowane, zgodnie z opisem w poniższej procedurze przycinania. Przycinanie jest domyślnie włączone.  
  
-   **Składanie** po włączeniu składania, funkcje na ścieżce zgodne z ustawieniami, które skonfigurowano zostaną scalone, zgodnie z opisem w procedurze składania poniżej. Domyślnie składania jest domyślnie włączona.  
  
### <a name="to-configure-trimming-for-a-performance-report"></a>Aby skonfigurować przycinanie dla raportu dotyczącego wydajności  
  
1.  Gdy widok drzewa wywołań lub Widok alokacji jest wyświetlany w wygenerowanym raporcie na **Developer** menu, kliknij przycisk **profilera** , a następnie kliknij przycisk **opcje redukcji szumu**.  
  
     **Redukcji szumu** zostanie wyświetlone okno dialogowe.  
  
2.  Aby umożliwić przycinanie, wykonaj następujące kroki:  
  
    1.  Wybierz **umożliwić przycinanie**. To jest ustawienie domyślne.  
  
        > [!NOTE]
        >  Jeśli włączono redukcję szumów pasek informacyjny będą wyświetlane w raporcie. Aby uzyskać więcej informacji, zobacz [widok drzewa wywołań](../profiling/call-tree-view.md) i [Widok alokacji](../profiling/dotnet-memory-allocations-view.md).  
  
    2.  Skonfiguruj ustawienie wartości przy użyciu **wartość** listy rozwijanej i wybierając odpowiednie ustawienie.  
  
    3.  Skonfiguruj ustawienia żądaną wartość progową, wpisując wartość procentową w **próg** pola tekstowego.  
  
    4.  Aby włączyć ostrzeżenie redukcji szumu w generowanym raporcie, zaznacz **wyświetlane ostrzeżenia, gdy redukcja szumów jest włączona**. To jest ustawienie domyślne.  
  
3.  Aby wyłączyć przycinanie wyczyść **umożliwić przycinanie**.  
  
4.  Kliknij przycisk **OK**.  
  
### <a name="to-configure-folding-for-a-performance-report"></a>Aby skonfigurować składania dla raportu dotyczącego wydajności  
  
1.  Na **Developer** menu, kliknij przycisk **profilera** , a następnie kliknij przycisk **opcje redukcji szumu**.  
  
     **Redukcji szumu** zostanie wyświetlone okno dialogowe.  
  
2.  Aby włączyć składania, wykonaj następujące kroki:  
  
    1.  Wybierz **włączyć składania**. To jest ustawienie domyślne.  
  
        > [!NOTE]
        >  Jeśli włączono redukcję szumów pasek informacyjny będą wyświetlane w raporcie. Aby uzyskać więcej informacji, zobacz [widok drzewa wywołań](../profiling/call-tree-view.md) i [Widok alokacji](../profiling/dotnet-memory-allocations-view.md).  
  
    2.  Skonfiguruj ustawienie wartości przy użyciu **wartość** listy rozwijanej i wybierając odpowiednie ustawienie.  
  
    3.  Skonfiguruj ustawienia żądaną wartość progową, wpisując wartość procentową w **próg** pola tekstowego.  
  
    4.  Aby włączyć ostrzeżenie redukcji szumu w generowanym raporcie, zaznacz **wyświetlane ostrzeżenia, gdy redukcja szumów jest włączona**. To jest ustawienie domyślne.  
  
3.  Aby wyłączyć składania, wyczyść **włączyć składania**.  
  
4.  Kliknij przycisk **OK**.  
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowywanie wydajności widoków raportów narzędzi](../profiling/customizing-performance-tools-report-views.md)   
 [Porady: wykluczanie lub uwzględnianie krótkich funkcji z Instrumentacji](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)   
 [Widok drzewa wywołań](../profiling/call-tree-view.md)   
 [Widok alokacji](../profiling/dotnet-memory-allocations-view.md)