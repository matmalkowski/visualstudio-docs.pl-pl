---
title: "Porównywanie plików danych wydajności | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profiling tools, comparing profiling tools report files
- profiling tools reports, comparing
ms.assetid: e6fda144-f21d-4912-9d16-1b8d3555a210
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 734d0531cf1fbbbc2f7924cb1743cabf9e4a9578
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="comparing-performance-data-files"></a>Porównywanie plików danych wydajności
Funkcji porównywania plików danych narzędzi profilowania służy do wybierania dwa pliki raportu (. VSP notebooka. VSPS) pliki oraz Generowanie raportu, który przedstawia różnice, regresji wydajności i ulepszenia, które nastąpiły jednej sesji profilowania.  
  
 Raport porównania danych plików z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędziach profilowania porównuje wyniki analizy w jednym pliku danych profilowania, aby wyniki analizy linii bazowej w innym pliku danych. Oba pliki danych musi zostać wygenerowane za pomocą tej samej metody profilowania. Raport analizy porównania jest zapisany jako plik vsps.  
  
 Widok porównania raport przedstawia widok tabeli zmienione dane. Tabela przedstawia zmian lub zmiany z linii bazowej. Różnicowej jest obliczana przez określenie różnica między stara wartość, wartości bazowej i wartość wyniku z nowego analizy.  
  
 Porównywanie danych profilera może bazować na funkcje w kodzie, modułów w aplikacji, wiersze, wskaźników instrukcji (IP) i typy.  
  
 Profilowanie dane, które są dostępne dla porównania zawiera informacje, które jest wyświetlane w kolumnach. Definicje nazwy kolumn, zobacz [widoków raportu wydajności](../profiling/performance-report-views.md).  
  
 Próg można ustawić do zmniejszenia szumu i filtrowanie danych w widoku tabeli porównanie wierszy, które nie zostały zmienione o określoną wartość.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Porady: porównywanie plików danych wydajności](../profiling/how-to-compare-performance-data-files.md)