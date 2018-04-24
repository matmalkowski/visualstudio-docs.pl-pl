---
title: Widok Kontencji zasobów - dane Kontencji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.resourcecontention
helpviewer_keywords:
- Resource Contentions view
ms.assetid: 14a7f774-211f-4ef8-af05-94d1c8f65d2f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e33a27d5f2b14effc9d8a90e903b34822d81edfb
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="resource-contentions-view---contention-data"></a>Widok Kontencji zasobów - dane Kontencji
Widok Kontencji zasobów zawiera dane kontencji zasobów, które zostały źródło zdarzenia rywalizacji. Zdarzenia rywalizacji występuje, gdy funkcja w wątku jest wymuszone czekać do uzyskiwania dostępu do zasobu, ponieważ funkcja w innym wątku uzyskał wyłączny dostęp do zasobu. Każdy zasób jest węzła głównego drzewa wywołań, który wyświetla ścieżki wykonywania funkcji, które spowodowały otrzymanie zdarzenia rywalizacji.  
  
## <a name="data-values"></a>Wartości danych  
  
### <a name="resource-values"></a>Wartości zasobów  
 Dane w wierszu zasobów wyświetla całkowity czas, który został zablokowany dostęp do zasobu w danych profilowania i łączna liczba zdarzeń rywalizacji, które wystąpiły z powodu konfliktu dostępu do tego zasobu. Włącznie i wyłącznego wartości zasobu zawsze są takie same.  
  
### <a name="function-values"></a>Wartości funkcji  
 Wartości funkcji są oparte na wystąpieniach funkcji, który wystąpił w ścieżce wykonywania reprezentowany w drzewie wywołań.  
  
-   Wyłączny wartości są oparte na zdarzenia, które wystąpiły podczas wykonywania instrukcji funkcji w jego treści funkcji. Zdarzenia, które wystąpiły w funkcjach, które zostały wywołane przez funkcję nie znajdują się w wartości wyłącznego.  
  
-   Wraz z wartościami granicznymi wartości są oparte na zdarzenia, które wystąpiły podczas wykonywania funkcji lub funkcja wywoływana przez funkcję.  
  
### <a name="percentage-values"></a>Wartości procentowe  
 Wartości procentowe są oparte na całkowity czas lub rywalizacji zdarzeń w danych profilowania. Jeśli raport lub widok przebiegu profilowania jest filtrowany, tylko czas blokowania i rywalizacji w to odfiltrowane dane są używane jako wartość całkowita.  
  
## <a name="navigating-the-resource-allocation-view"></a>Nawigowanie po Widok alokacji zasobów  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Nazwa**|Nazwa zasobu lub funkcji.|  
|**Wyłączny czasu blokowania**|— Dla zasobu łączny czas tej dostęp do zasobu został zablokowany i spowodował wątku oczekiwania.<br />— Dla funkcji, czasu, który wystąpień tych funkcji były zablokowany dostęp do zasobu nadrzędnego, gdy funkcja została uruchomiona kodu w treści funkcji. Czas blokowania w funkcje, które zostały wywołane przez funkcję nie jest włączony.|  
|**% Wyłącznego czasu blokowania**|— Dla zasobu, odsetek wszystkich czas blokowania w danych profilowania, która została zablokowana czasu tego zasobu<br />— Dla funkcji odsetek wszystkich czas blokowania w niej dane profilowania własny czas zablokowanych wystąpień tych funkcji.|  
|**Wyłączny rywalizacji**|— Dla zasobu całkowita liczba przypadków, które uzyskują dostęp do zasobu został zablokowany i spowodował wątku oczekiwania.<br />— Dla funkcji, ile razy te wystąpienia funkcji zostały zablokowany dostęp do zasobu nadrzędnego, gdy funkcja została uruchomiona kodu w treści funkcji. Blokowanie zdarzeń w funkcje, które zostały wywołane przez funkcję nie są uwzględniane.|  
|**% Wyłącznego rywalizacji**|— Dla zasobu, wartość procentowa wszystkie zdarzenia rywalizacji danych profilowania, które zostały zdarzenia rywalizacji w celu uzyskania dostępu do tego zasobu.<br />— Dla funkcji, wartość procentowa wszystkie zdarzenia rywalizacji danych profilowania, które zostały zdarzenia rywalizacji wyłącznego wystąpień tych funkcji dla zasobu nadrzędnego.|  
|**Całkowity czas blokowania**|— Dla zasobu łączny czas tej dostęp do zasobu został zablokowany i spowodował wątku oczekiwania.<br />— Dla funkcji godzinę, o której wystąpień tych funkcji lub wszystkie funkcje wywoływane przez wystąpienia został zablokowany dostęp do zasobu nadrzędnego, podczas gdy funkcja została uruchomiona kodu w treści funkcji.|  
|**Całkowity czas blokowania %**|— Dla zasobu, odsetek wszystkich czas blokowania w danych profilowania, która została zablokowana czasu tego zasobu<br />-Funkcja odsetek wszystkich czas blokowania w przebiegu, który profilowania zostało całkowity czas blokowania wystąpień tych funkcji.|  
|**Wraz z wartościami granicznymi rywalizacji**|— Dla zasobu całkowita liczba przypadków, które uzyskują dostęp do zasobu został zablokowany i spowodował wątku oczekiwania.<br />— Dla funkcji procent wszystkie zdarzenia rywalizacji w przebiegu, który profilowania były zdarzenia rywalizacji włącznie z tych wystąpień funkcji dla zasobu nadrzędnego.|  
|**% Rywalizacji włącznie**|— Dla zasobu procent wszystkie zdarzenia rywalizacji w przebiegu, który profilowania były zdarzenia rywalizacji w celu uzyskania dostępu do tego zasobu.<br />— Dla funkcji, ile razy te wystąpienia funkcji zostały zablokowany dostęp do zasobu nadrzędnego, gdy funkcja została uruchomiona kodu w treści funkcji. Blokowanie zdarzeń w funkcje, które zostały wywołane przez funkcję nie są uwzględniane.|  
|**poziom**|Długość tej funkcji w drzewie wywołań. Tylko w [VSPerfReport](../profiling/vsperfreport.md) raporty wiersza polecenia.|  
|**Numer wiersza — funkcja**|Numer wiersza początku tej funkcji w pliku źródłowym.|  
|**Nazwa modułu**|Nazwa modułu zawiera funkcję.|  
|**Ścieżka modułu**|Ścieżka moduł, który zawiera funkcję.|  
|**Identyfikator procesu**|Identyfikator procesu (PID) procesu, w którym funkcja została uruchomiona.|  
|**Nazwa procesu**|Nazwa procesu.|  
|**Plik źródłowy**|Plik źródłowy, który zawiera definicję dla tej funkcji.|