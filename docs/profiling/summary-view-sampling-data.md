---
title: "Widok podsumowania - dane próbkowania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sampling profiling method, Summary view
- Summary view
ms.assetid: 79056873-2985-40be-9112-cdbc26a65156
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c78ba45fda91650b5b7deb37ce9fd5dabbee6fb3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="summary-view---sampling-data"></a>Widok podsumowania - dane próbkowania
Widok podsumowania Wyświetla informacje o wydajności najdroższych funkcje w przebiegu profilowania. Aby uzyskać więcej informacji, łącznie z opisem łącza powiadomień i listy raport, zobacz [widoku podsumowania](../profiling/summary-view.md).  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagane znaczących zmian w sposobie profilera Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowe techniki kolekcji. Zobacz [narzędzi wydajności w przypadku aplikacji systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="timeline-graph"></a>Oś czasu wykresu  
 Oś czasu wykresu w widoku Podsumowanie zawiera procent użycia procesora (CPU) PROFILOWANEGO aplikacji wraz z upływem czasu, który wystąpił profilowania. Oś czasu wykresu umożliwia filtrowanie widoku w wybranym okresie. Aby uzyskać więcej informacji, zobacz [porady: Filtr widoków raportu z podsumowania osi czasu](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## <a name="hot-path"></a>Aktywnej ścieżki  
 **Aktywnej ścieżki** jest wyświetlana ścieżka wykonywania, w której większość przykłady zostały zebrane. Możesz kliknąć funkcji, aby wyświetlić widok szczegółów funkcji dla funkcji. Aby wyświetlić inne widoki dotyczące funkcji, kliknij prawym przyciskiem myszy funkcji, a następnie kliknij przycisk Widok z listy.  
  
 **Aktywnej ścieżki** obejmuje następujące dane dla każdej funkcji:  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Nazwa**|Nazwa funkcji.|  
|**% Próbek włącznie**|Procent wszystkich próbek, które wystąpiły podczas wykonywania tej funkcji i funkcji wywoływanych przez tę funkcję.|  
|**% Wyłącznych próbek**|Procent wszystkich próbek, które wystąpiły, gdy funkcja została uruchomiona kodu w treści funkcji. Przykłady zbierane w funkcjach wywoływanych przez tę funkcję, nie są uwzględniane.|  
  
## <a name="functions-doing-most-individual-work"></a>Funkcje wykonujące najwięcej indywidualnej pracy  
 **Funkcje wykonywania najwięcej indywidualnej pracy** lista zawiera funkcje, które mają najwięcej wyłącznych próbek w przebiegu profilowania. Wyłączny próbki jest przypisany do funkcji, jeśli funkcja jest wykonywana własnego kodu w momencie próbki został zebrany. Wyłączny próbki nie jest przypisany do funkcji, jeśli funkcja powoduje wywołanie innej funkcji, gdy próbki został zebrany. Duża liczba próbek wyłącznych wskazuje, czy znaczących czasu w samej funkcji.  
  
 Możesz kliknąć funkcji, aby wyświetlić widok szczegółów funkcji dla funkcji. Wyświetlanie innych widoków dla funkcji prawym przyciskiem myszy funkcji, a następnie kliknij przycisk Widok z listy.  
  
 **Funkcje wykonywania najwięcej indywidualnej pracy** obejmuje następujące dane dla każdej funkcji:  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**Nazwa**|Nazwa funkcji.|  
|**% Wyłącznych próbek**|Procent wszystkich próbek w przebiegu profilowania, które zostały zebrane, gdy funkcja została uruchomiona kod w jego treści funkcji. Wartość procentowa wyklucza przykłady, które zostały zebrane podczas wykonywania zostały funkcje, które wywołuje tej funkcji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Widok podsumowania](../profiling/summary-view-dotnet-memory-data.md)   
 [Widok podsumowania](../profiling/summary-view-instrumentation-data.md)