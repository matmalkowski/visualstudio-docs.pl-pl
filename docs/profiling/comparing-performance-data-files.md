---
title: Porównywanie plików danych wydajności | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, comparing profiling tools report files
- profiling tools reports, comparing
ms.assetid: e6fda144-f21d-4912-9d16-1b8d3555a210
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b56982cdef9c27beb4e5aeb82fa9d9741e87fbd7
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
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