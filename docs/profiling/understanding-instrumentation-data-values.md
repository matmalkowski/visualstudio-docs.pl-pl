---
title: "Zapoznanie z wartościami danych Instrumentacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Profiling Tools,instrumentation
- instrumentation profiling method
ms.assetid: 2cf94cf9-c317-4a52-bf00-670f1262165e
caps.latest.revision: "29"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7f0fc8530e45831132f3ec3f357ff0113fa4abe
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="understanding-instrumentation-data-values"></a>Zapoznanie z wartościami danych instrumentacji
*Instrumentacji* profilowania metody [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rejestruje szczegółowe informacje o chronometrażu dla wywołania funkcji, wierszy i instrukcje w profilowanych aplikacji  
  
 **Wymagania**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Metoda Instrumentacji injects kod na początku i końcu funkcji docelowego w profilowanych danych binarnych, a przed i po każdym wywołaniu przez te funkcje do innych funkcji. Wprowadzony kod rejestruje następujące czynności:  
  
-   Interwał między to zdarzenie kolekcji i poprzedni.  
  
-   Określa, czy system operacyjny wykonał operację w interwale. Na przykład system operacyjny może odczytu lub zapisu na dysku, albo Przełącz między wątek docelowy i inny wątek w innym procesie.  
  
 **Wymagania**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Dla każdego interwału analizy profilera rekonstruuje stos wywołań, która znajdowała się na końcu zakresu. Stos wywołań jest lista funkcji, które są aktywne na procesora w punkcie w czasie. Tylko jednej funkcji (funkcja bieżącej) jest wykonywanie kodu; inne funkcje są łańcuch wywołań funkcji, które zakończyły się wywołanie funkcji bieżącego (stosu wywołań).  
  
 Dla każdej funkcji w stosie wywołań podczas interwał została zarejestrowana, analizy profilera dodaje interwał do co najmniej jednej z czterech danych wartości dla funkcji. Analiza dodaje interwał do wartości danych dla funkcji, na podstawie dwóch kryteriów:  
  
-   Określa, czy interwał wystąpił w kodzie funkcji lub w *funkcji podrzędnych* (funkcja została wywołana przez funkcję).  
  
-   Określa, czy wystąpiło zdarzenie systemu operacyjnego w interwale.  
  
 Wartości danych dla interwału zakresu funkcję lub dane są nazywane *upłynął włącznie*, *upłynął wyłącznego*, *aplikacji włącznie*, i  *Aplikacja na wyłączność*:  
  
-   Wartość danych, który upłynął włącznie mają zostać dodane interwały wszystkich funkcji.  
  
-   Jeśli interwał wystąpił w kodzie funkcji, a nie w funkcji podrzędnych, interwał jest dodawany do wartość danych, który upłynął wyłącznego funkcji.  
  
-   Jeśli zdarzenia systemu operacyjnego nie zostało przeprowadzone w danym okresie, interwał jest dodawany do aplikacji z wartościami granicznymi wartości danych.  
  
-   Jeśli zdarzenia systemu operacyjnego nie zostało przeprowadzone w zakresie, a interwał podczas bezpośrednie wykonywanie kodu funkcji (czyli go nie wystąpił w funkcji podrzędnego), interwał jest dodawana do aplikacji wyłącznego wartości danych.  
  
 Narzędzia profilowania raporty agregacji łączne wartości funkcji w sesji profilowania i procesy, wątki i pliki binarne sesji.  
  
## <a name="elapsed-inclusive-values"></a>Czas wartości włącznie  
 Łączny czas, który został podczas wykonywania funkcji i jej funkcji podrzędnych.  
  
 Czas wartości z wartościami granicznymi obejmują interwałów, które zostały poświęconego bezpośrednie wykonywanie kodu funkcji i interwałów, które zostały podczas wykonywania funkcji podrzędnych funkcji docelowej. Interwały funkcji i jej funkcji podrzędnych, które obejmują oczekujące dla systemu operacyjnego znajdują się również w wartości, który upłynął włącznie.  
  
## <a name="elapsed-exclusive-values"></a>Czas wartości wyłączności  
 Czas, jaki był poświęcony na wykonywanie funkcji, z wyłączeniem czas przeznaczony na funkcje podrzędne.  
  
 Czas wyłącznego wartości to interwałów, które zostały poświęconego bezpośrednie wykonywanie kodu funkcji, niezależnie od tego, czy wystąpiło zdarzenie systemu operacyjnego w interwale. Wszystkich interwałów w funkcji podrzędne, które zostały wywołane przez funkcję docelowych nie znajdują się w wartości, który upłynął wyłącznego.  
  
## <a name="application-inclusive-values"></a>Wartości z wartościami granicznymi aplikacji  
 Czas, jaki był poświęcony na wykonywanie funkcji i jej funkcji podrzędnych, z wyłączeniem czas przeznaczony na zdarzenia systemu operacyjnego.  
  
 Wartości z wartościami granicznymi aplikacji nie zawierają interwałów, które zawierają zdarzenia systemu operacyjnego. Wartości z wartościami granicznymi aplikacji obejmują wszystkich interwałów, które zostały podczas wykonywania funkcji, niezależnie od tego, czy interwał był poświęcony na bezpośrednie wykonywanie kodu funkcji lub był poświęcony w funkcjach podrzędnych funkcji docelowej.  
  
## <a name="application-exclusive-values"></a>Wartości wyłącznego aplikacji  
 Czas, jaki był poświęcony na wykonywanie funkcji, z wyłączeniem czas przeznaczony na funkcje podrzędne i czas przeznaczony na zdarzenia systemu operacyjnego.  
  
 Nie dołączaj wyłącznego wartości aplikacji, interwałów, które zawierają zdarzenia systemu operacyjnego lub interwałów, które zostały podczas wykonywania funkcji, które zostały wywołane przez funkcję. Wartości wyłącznego aplikacji obejmują tylko tych interwałów, które zostały poświęconego bezpośrednie wykonywanie kodu funkcji i nie zawiera zdarzeń systemu operacyjnego.  
  
## <a name="elapsed-inclusive-percent"></a>Czas procent włącznie  
 Procent upłynął włącznie wartości sum sesji profilowania będące upłynął włącznie wartości funkcji modułu, wątku lub procesu.  
  
 100 * funkcji, jaki upłynął włącznie / sesji, który upłynął włącznie  
  
## <a name="elapsed-exclusive-percent"></a>Czas procent wyłączności  
 Procent upłynął włącznie wartości sum sesji profilowania będące upłynął wyłącznego wartości funkcji modułu, wątku lub procesu.  
  
 100 * funkcji wzajemnie dotychczasowy / sesji, który upłynął włącznie  
  
## <a name="application-inclusive-percent"></a>Procent włącznie aplikacji  
 Procent całkowitej aplikacji włącznie wartości sesja profilowania będące aplikacji włącznie wartości funkcji modułu, wątku lub procesu.  
  
 100 * funkcji aplikacji włącznie / sesji aplikacji włącznie  
  
## <a name="application-exclusive-percent"></a>Procent wyłącznego aplikacji  
 Procent aplikacji włącznie wartości sum sesji profilowania będące aplikacji wyłącznego interwałów funkcji modułu, wątku lub procesu.  
  
 100 * funkcji aplikacji na wyłączność / sesji aplikacji włącznie  
  
## <a name="see-also"></a>Zobacz też  
 [Analizowanie wydajności narzędzi danych](../profiling/analyzing-performance-tools-data.md)   
 [Porady: Wybieranie metod kolekcji](../profiling/how-to-choose-collection-methods.md)