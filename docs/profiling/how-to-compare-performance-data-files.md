---
title: "Porady: porównywanie plików danych wydajności | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vsperf.choosediffbinaries
helpviewer_keywords:
- profiling tools, how to compare profiler result files
- profiler result files, how to compare
ms.assetid: 1905b45d-c6b3-43c8-87b1-1aee734f37f9
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 09e16202fb1b35a48925297e35840a60b65f0488
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-compare-performance-data-files"></a>Porady: porównywanie plików danych wydajności
Możesz porównać wyniki dwa pliki danych innego profilera (Vsp lub vsps), tworzenie raportu porównania ("Diff") lub widoku. Porównanie przedstawia różnice, regresji wydajności i ulepszenia, które nastąpiły jednej sesji profilowania.  
  
 Diff raport będzie zawierał tabeli widoku danych. Tabela przedstawia zmian lub zmiany z linii bazowej. To jest obliczana przez określenie różnica między stara wartość, wartości bazowej i wartość wyniku z nowego analizy.  
  
 Porównywanie danych profilera może bazować na funkcje w kodzie, modułów w aplikacji, wiersze, wskaźników instrukcji (IP) i typy.  
  
 Próg można ustawić do zmniejszenia szumu i filtrowanie danych w widoku tabeli wiersze, które nie zostały zmienione o określoną wartość.  
  
### <a name="to-create-comparison-file-view-for-a-project-in-performance-explorer"></a>Aby utworzyć widok porównania pliku projektu w Eksploratorze wydajności  
  
1.  W **Eksplorator wydajności**w obszarze **raporty**, wybierz plik Vsp lub vsps raportu, który ma być używany jako wartości odniesienia do porównania.  
  
2.  Wybierz plik Vsp lub vsps pliki raportów, które chcesz porównać.  
  
3.  Kliknij prawym przyciskiem myszy jeden z wybranych plików, a następnie kliknij przycisk **porównania raporty**.  
  
### <a name="to-compare-values"></a>Aby porównać wartości  
  
1.  Wybierz **raportu porównawczego** karty w oknie widoku raportu.  
  
2.  W **tabeli** listy rozwijanej wybierz funkcji lub moduły do porównania.  
  
3.  W **kolumny** listy rozwijanej wybierz wartość do porównania.  
  
4.  (opcjonalnie) Wpisz wartość **próg**.  
  
5.  Kliknij przycisk **zastosować**.  
  
### <a name="to-compare-report-files"></a>Porównywanie plików raportów  
  
1.  Na **Analizuj** menu, wybierz opcję **raporty porównanie wydajności**.  
  
2.  W **wybierz pliki analizy do porównania** okna, Przeglądaj i wybierz **pliku bazowego** analizy pliku (pliku Vsp lub vsps) i **pliku do porównania** (Vsp lub vsps).  
  
3.  Kliknij przycisk **OK**.