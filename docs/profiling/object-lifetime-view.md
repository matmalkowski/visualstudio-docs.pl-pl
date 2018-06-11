---
title: Widok okresu istnienia obiektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.objectlifetime
helpviewer_keywords:
- lifetime, objects
- Objects Lifetime view
- profiling tools reports, Lifetime view
- performance reports, objects lifetime view
- profiling tools, Lifetime view
ms.assetid: d0501fdd-4b3a-4e74-b6ac-51d950a2e15b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 247c81d46ee8f5ae916a2a024620e4f4eb864194
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255622"
---
# <a name="object-lifetime-view"></a>Widok okresu istnienia obiektu
Widok okresu istnienia obiektu, jest dostępna, gdy **również zbieranie danych o okresie istnienia obiektu platformy .NET** jest zaznaczony na **sesji wydajności** strony właściwości.  
  
 Moduł zbierający elementy bezużyteczne programu [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] zarządza alokacji i wersji pamięci dla aplikacji. Aby zoptymalizować wydajność modułu zbierającego elementy bezużyteczne, sterty zarządzanej jest podzielony na trzy generacje: 0, 1 i 2. Moduł garbage collector środowiska uruchomieniowego przechowuje nowych obiektów generacji 0. Obiekty, które pozostają aktualne po kolekcje są awansowane i przechowywane w generacji 1 i 2.  
  
 Moduł zbierający elementy bezużyteczne zwraca pamięci przez dealokowanie całego generowania obiektów. Dla obiektów, które zostały utworzone przez aplikację profilowanych widok okresu istnienia obiektu Wyświetla liczbę i rozmiar obiektów i generowania, w którym są odzyskana.  
  
## <a name="general"></a>Ogólne  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Nazwa klasy**|Nazwa klasy przydzielonego typu.|  
|**Identyfikator procesu**|Identyfikator procesu przebiegu profilowania.|  
|**Nazwa procesu**|Nazwa procesu.|  
|**Nazwa modułu**|Nazwa modułu zawiera funkcję.|  
|**Ścieżka modułu**|Ścieżka moduł, który zawiera funkcję.|  
  
## <a name="instance-data"></a>Dane wystąpienia  
 Dane wystąpienia wskazuje liczbę obiektów tego typu, które zostały utworzone w procesie profilowania i generowania, w którym obiekty zostały alokację przez moduł garbage collector.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Wystąpienia**|Liczba przydziałów obiektów tego typu.|  
|**Całkowita liczba wystąpień %**|Wartość procentowa łącznej liczby przydziałów, które zostały wprowadzone w profilowania wykonywania.|  
|**Gł 0 wystąpień zebranych**|Liczba wystąpień tego typu, które zostały alokację podczas generowania 0 pamięci algorytm kolekcji.|  
|**Gł 1 wystąpień zebranych**|Liczba wystąpień tego typu, które zostały alokację podczas generowania 1 pamięci algorytm kolekcji.|  
|**Gł 2 wystąpienia zbierane**|Liczba wystąpień tego typu, które zostały alokację podczas generowania 2 pamięci algorytm kolekcji.|  
|**Wystąpienia aktywne na końcu**|Liczba wystąpień tego typu, które nie zostały deallocated aż do zakończenia profilowania uruchomienia.|  
  
## <a name="size-byte-data"></a>Dane rozmiar (bajty)  
 Rozmiar (bajty) danych wskazuje rozmiar obiektów tego typu, które zostały utworzone w procesie profilowania i ilość pamięci, która została odzyskana w każdej generacji, w którym zostały cofnięciu przydziału obiektów.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Łączna liczba przydzielonych bajtów**|Całkowita liczba bajtów dla wszystkich wystąpień tego typu.|  
|**Całkowita liczba bajtów %**|Procent całkowitej liczby przydzielonych bajtów w przebiegu profilowania przydzielonych dla wystąpień tego typu.|  
|**Gł 0 bajtów zebranych**|Rozmiar wystąpienia tego typu, które zostały alokację podczas generowania 0 pamięci algorytm kolekcji.|  
|**Gł 1 bajtów zebranych**|Rozmiar wystąpienia tego typu, które zostały alokację podczas generowania 1 pamięci algorytm kolekcji.|  
|**Gł 2 bajty zbierane**|Rozmiar wystąpienia tego typu, które zostały alokację podczas generowania 2 pamięci algorytm kolekcji.|  
  
## <a name="large-object-heap-data"></a>Dane sterty obiektów wielkich  
 Program przydzielania pamięci .NET zarządza bardzo dużych obiektów w lokalizacji, która różni się od standardowego sterty zarządzanej. Dane sterty dużego obiektu wskazuje liczbę i rozmiar obiektów tego typu, które były zarządzane w tej lokalizacji.  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Zebrane wystąpienia sterty obiektów wielkich**|Liczba wystąpień tego typu, który znajduje się w sterty dużego obiektu i które zostały zebrane w profilowania uruchomienia.|  
|**Zebrane bajty sterty obiektów wielkich**|Rozmiar w bajtach wystąpień tego typu, który znajduje się w sterty dużego obiektu i które zostały zebrane w przebiegu profilowania.|  
  
## <a name="see-also"></a>Zobacz także  
 [Widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md)