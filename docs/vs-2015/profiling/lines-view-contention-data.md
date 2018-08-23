---
title: Widok linii - dane Kontencji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Lines view
ms.assetid: 859b02d2-eddf-4ad3-95de-0df67ee2ab03
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 09149f44e80155a13986d42d2b3279e5c39c8884
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42679213"
---
# <a name="lines-view---contention-data"></a>Widok linii — dane rywalizacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [widok linii - dane Kontencji](https://docs.microsoft.com/visualstudio/profiling/lines-view-contention-data).  
  
Widok wierszy danych rywalizacji o zasoby wyświetla dane o wydajności dla instrukcji, które były wykonywane w chwili przykłady zostały zebrane podczas uruchomienia profilowania. W pliku źródłowym instrukcji może obejmować więcej niż jeden wiersz w pliku źródłowym, a jeden wiersz może zawierać więcej niż jedną instrukcję.  
  
 Instrukcja jest identyfikowany przez następujące dane:  
  
-   Plik źródłowy, który zawiera deklarację funkcji.  
  
-   Funkcja, która zawiera instrukcję.  
  
-   Wiersza źródłowego, w którym rozpoczyna się wykonywanie instrukcji.  
  
-   Znak w wierszu źródłowym, w którym rozpoczyna się wykonywanie instrukcji.  
  
-   Wiersza źródłowego, w którym kończy się instrukcji.  
  
-   Znak w wierszu źródłowym, w którym kończy się instrukcji.  
  
 Kolumna Nazwa wiersza zawiera wzorzec sortowalnej łączenia danych identyfikator.  
  
 W poniższej tabeli opisano kolumny raportu widok wierszy.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Wyłączny czas blokowania**|Ilość czasu, w którym ta instrukcja został zablokowany wykonywanie kodu w instrukcji z powodu zdarzenia rywalizacji o zasoby. Czas blokowania w funkcje, które wywołały instrukcja nie jest włączony.|  
|**% Własnego czasu blokowania**|Procent wszystkich czas blokowania w procesie, który był wyłączny czas blokowania instrukcji.|  
|**Rywalizacje wyłączne**|Liczba prób niniejszych zablokowano wykonywanie kodu w instrukcji z powodu zdarzenia rywalizacji o zasoby. Zdarzenia rywalizacji w funkcje, które wywołały wykonywanie instrukcji nie są uwzględniane.|  
|**% Rywalizacji wyłącznych**|Procent wszystkich zdarzeń rywalizacji o zasoby w procesie, które były rywalizacji wyłącznych instrukcji.|  
|**Adres funkcji**|Adres funkcji, która zawiera tej instrukcji.|  
|**Nazwa funkcji**|W pełni kwalifikowana nazwa funkcji, która zawiera tej instrukcji.|  
|**Całkowity czas blokowania**|Czas blokowania w tej instrukcji i funkcji o nazwie w instrukcji.|  
|**% Całkowitego czasu blokowania**|Procent wszystkich czas blokowania w procesie, który był całkowity czas blokowania instrukcji.|  
|**Rywalizacje włączne**|Ile razy zostały zablokowane tej instrukcji i funkcji, które zostały wywołane w zestawieniu z wykonywania.|  
|**% Rywalizacji włącznych**|Procent wszystkich zdarzeń rywalizacji o zasoby w procesie, które były rywalizacji włącznych instrukcji.|  
|**Nazwa wiersza**|Identyfikator wygenerowany przez program profilujący wiersza. Identyfikator używa następującej składni:`SourceFile`**; [**  `LineNumberStart` **,**`CharacterStart`**] ->; [** `LineNumberEnd`**,**`CharacterEnd`**]**|  
|**Numer wiersza funkcji**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Nazwa modułu**|Nazwa modułu, który zawiera instrukcję.|  
|**Ścieżka modułu**|Ścieżka modułu, który zawiera instrukcję.|  
|**Identyfikator procesu**|Identyfikator procesu (PID) dla PROFILOWANEGO procesu.|  
|**Nazwa procesu**|Nazwa procesu.|  
|**Początkowy znak w źródle**|Przesunięcie początkowy znak w wierszu pliku źródłowego, w którym rozpoczyna się tej instrukcji.|  
|**Końcowy znak w źródle**|Przesunięcie początkowy znak w wiersza pliku źródłowego, w którym kończy się w tej instrukcji.|  
|**Plik źródłowy**|Nazwa pliku źródłowego, który zawiera deklarację funkcji.|  
|**Początkowy wiersz w źródle**|Numer wiersza w pliku źródłowym, w którym rozpoczyna się wykonywanie instrukcji.|  
|**Końcowy wiersz w źródle**|Numer wiersza w pliku źródłowym, w którym kończy się instrukcji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Dostosowywanie kolumn widoku raportu](../profiling/how-to-customize-report-view-columns.md)   
 [Widok linii](../profiling/lines-view.md)   
 [Widok linii - próbkowanie](../profiling/lines-view-dotnet-memory-sampling-data.md)   
 [Widok linii](../profiling/lines-view-sampling-data.md)



