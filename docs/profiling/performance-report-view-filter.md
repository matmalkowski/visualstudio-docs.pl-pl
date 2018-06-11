---
title: Filtr widoku raportów wydajności | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, Profiler Report view filter
- Profiler Report View filter, profiling tools
ms.assetid: 35f89d86-4683-4db1-aa0c-ae0ce65fa524
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 17fc42eab94d98ceb636e53e3ed6efd39a08f920
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35254273"
---
# <a name="performance-report-view-filter"></a>Filtr widoku raportów wydajności
**Filtr widoku raportów profilera** okna znajduje się w górnej części **raport wydajności** okna. Jeśli nie widzisz, kliknij przycisk **Pokaż filtru** przycisku.  
  
 Można zmodyfikować każdej klauzuli filtru, aby uściślić wyniki. Następujące kolumny są dostępne w Konstruktorze filtru.  
  
|Element filtru|Opis|  
|-----------------|-----------------|  
|I/lub|Wybierz **i** Jeśli klauzulę i dalej klauzula musi być true na zgodny wynik. Wybierz **lub** Jeśli klauzulę lub klauzuli dalej może być true na zgodny wynik.|  
|Pole|Wybierz pole do użycia w klauzuli filtru na liście pola danych, które są dostępne w bieżącym pliku raportu.|  
|Operator|Wybierz operator, który określa relację między pola i wartości.<br /><br /> = Równa się<br /><br /> <> Nie równa się<br /><br /> < Mniej niż<br /><br /> > Większa niż<br /><br /> < = mniejsza niż lub równe<br /><br /> > = większe lub równe|  
|Wartość|Wybierz lub wprowadź wartość do wyszukania. Niektóre pola listy dostępnych wartości dla pola.|  
  
 Dopóki uważasz, że filtr zapewni najlepsze wyniki, możesz dodać klauzul filtru. Kliknij przycisk **wykonania filtru** Aby zastosować filtr do pliku danych.  
  
 Z **znaczniki** widoku raportu, można wygenerować filtru klauzule ograniczające danych w widoku raportu do danych zbieranych pomiędzy dwoma znakami. Wybierz te znaczniki, które mają być rozpoczęcia i zakończenia raportu danych, następnie kliknij prawym przyciskiem myszy i wybierz opcję **Dodaj filtr na znaki** lub **Dodaj filtr na sygnatury czasowe**. Obu filtrów ograniczenie danych w bieżącym pliku danych do tego samego zakresu; **Dodaj filtr na znaki** może odnosić się do innych plików Vsp.  
  
 Do zapisania filtru, kliknij przycisk **wyeksportować filtru** na **raport wydajności** narzędzi, a następnie określ lokalizację i nazwę pliku. *vspf* pliku. Aby załadować uprzednio zapisanego filtru, kliknij przycisk **Filtr importu** i zlokalizuj plik zapisany filtr. Filtr plików można również filtrować pliki danych na komputerach autonomicznych narzędzi profilowania zainstalowane. Aby uzyskać więcej informacji, zobacz [VSPerfReport](../profiling/vsperfreport.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Analizowanie danych narzędzi wydajności](../profiling/analyzing-performance-tools-data.md)   
 [VSPerfReport](../profiling/vsperfreport.md)