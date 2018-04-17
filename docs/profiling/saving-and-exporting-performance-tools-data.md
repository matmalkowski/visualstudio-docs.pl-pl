---
title: Zapisywanie i eksportowanie wydajności narzędzi danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, saving and exporting reports
ms.assetid: 2e9b28fe-3ed2-4e1d-b9cb-0a5e384380b0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: da2f15eee4e5fab64e0847f8e6d964c03b954833
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="saving-and-exporting-performance-tools-data"></a>Zapisywanie i eksportowanie wydajności narzędzi danych
W tym temacie opisano sposób zapisania i wyeksportowane pliki danych wydajności.  
  
##  <a name="BKMK_Save_Profiler_Data_Files_As_Analyzed_Report_Files"></a> Porady: zapisywanie plików danych wydajności jako pliki raportu analizy  
 Możesz zapisać filtrowane lub niefiltrowane widoki profilowania pliki danych (Vsp) jako pliki raportu analizy (vsps). Plik raportu analizy mogą być wyświetlane w oknie widoku raportu i jest znacznie mniejszy niż oryginalny plik Vsp. Nie można jednak zastosować filtr do danych pliku vsps. W Eksploratorze wydajności można utworzyć pliku raportu analizy, bez konieczności otwierania pliku w zintegrowane środowisko programistyczne (IDE), lub można otwierać i plik Vsp filtru i następnie zapisz wyniki.  
  
#### <a name="to-save-an-analyzed-performance-report-from-the-performance-explorer"></a>Aby zapisać raport analizy wydajności z Eksploratora wydajności  
  
1.  W obszarze **raporty**, kliknij prawym przyciskiem myszy plik danych profilowania, który chcesz przeanalizować, a następnie kliknij przycisk **zapisać przeanalizowane**.  
  
2.  W **zapisania analizy danych** okna dialogowego wprowadź określ katalog, a następnie wpisz nazwę pliku.  
  
3.  Kliknij przycisk **zapisać.**  
  
#### <a name="to-save-an-analyzed-performance-report-from-the-report-view-window"></a>Aby zapisać raport analizy wydajności z okna widoku raportu  
  
1.  Otwórz plik danych (Vsp) profilowania w oknie widoku raportu.  
  
2.  (Opcjonalnie) Zastosuj filtr do danych. Aby uzyskać więcej informacji, zobacz [filtr widoku raportów wydajności](../profiling/performance-report-view-filter.md).  
  
3.  Kliknij przycisk **zapisać przeanalizowane** na pasku narzędzi okna widoku raportu.  
  
4.  W **zapisania analizy danych** okna dialogowego wprowadź określ katalog, a następnie wpisz nazwę pliku.  
  
5.  Kliknij przycisk **zapisać.**  
  
## <a name="how-to-export-profiling-tools-reports-to-an-xml-or-csv-file"></a>Porady: narzędzi profilowania eksportowania raportów. XML lub. Plik CSV  
 Co najmniej jeden widok raportu można eksportować z pliku Vsp lub vsps pliku danych profilowania jako albo rozdzielonych przecinkami lub plik XML. Można filtrować dane w oknie widoku raportu, przed eksportowania lub wyeksportować widoków raportu w pliku danych z **Eksplorator wydajności** okna.  
  
> [!NOTE]
>  Można również skopiuj i wklej zaznaczone wiersze z okna wyświetlania raportu jako wartości rozdzielane tabulatorami.  
  
#### <a name="to-export-performance-reports-from-the-performance-explorer-window"></a>Raporty wydajności można eksportować z okno Eksploratora wydajności  
  
1.  W **Eksplorator wydajności**, wybierz raport, a następnie kliknij prawym przyciskiem myszy i wybierz **wyeksportować**.  
  
     **Eksportowanie raportu** zostanie wyświetlone okno dialogowe.  
  
2.  Wybierz widoki raportu, który chcesz wyeksportować.  
  
3.  W obszarze **prefiksu raport o**, określ prefiks, które chcesz dodać do nazwy raportu.  
  
4.  W obszarze **lokalizację dla eksportowanego raportu**, określ katalog.  
  
5.  W obszarze **format raportu eksportować**, wybierz (rozdzielany przecinkami) (\*CSV\), lub danych XML (\*.xml\).  
  
6.  Kliknij przycisk **wyeksportować**.  
  
     Każdy widok raport jest zapisywany do osobnego pliku o nazwie \<prefiks > _\<nazwy widoku raportu >.\< CSV&#124;xml >  
  
#### <a name="to-export-performance-reports-from-the-report-view-window"></a>Raporty wydajności można eksportować z okno widoku raportu  
  
1.  Otwórz plik Vsp w oknie widoku raportu.  
  
2.  (Opcjonalnie) Zastosuj filtr do danych. Aby uzyskać więcej informacji, zobacz [filtr widoku raportów wydajności](../profiling/performance-report-view-filter.md).  
  
3.  Kliknij przycisk **Eksportowanie raportu** na pasku narzędzi okna widoku raportu.  
  
4.  Wybierz widoki raportu, który chcesz wyeksportować.  
  
5.  W obszarze **prefiksu raport o**, określ prefiks, które chcesz dodać do nazwy raportu.  
  
6.  W obszarze **lokalizację dla eksportowanego raportu**, określ katalog.  
  
7.  W obszarze **format raportu eksportować**, wybierz (rozdzielany przecinkami) (\*CSV), lub danych XML (\*.xml).  
  
8.  Kliknij przycisk **wyeksportować**.  
  
     Każdy widok raport jest zapisywany do osobnego pliku o nazwie \<prefiks > _\<nazwy widoku raportu >.\< CSV&#124;xml >  
  
## <a name="see-also"></a>Zobacz też  
 [Eksplorator wydajności](../profiling/performance-explorer.md)   
 [Analizowanie wydajności narzędzi danych](../profiling/analyzing-performance-tools-data.md)   
 [Porównywanie plików danych wydajności](../profiling/comparing-performance-data-files.md)   
 [VSPerfReport](../profiling/vsperfreport.md)
