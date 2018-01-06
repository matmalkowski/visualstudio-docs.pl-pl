---
title: 'Porady: Wybieranie metod kolekcji | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance tools, choosing collection method
- profiling tools, choosing collection method
- performance collection methods
ms.assetid: c87cfd3a-0fc7-49ae-9c05-d8480891cc63
caps.latest.revision: "34"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ff646066c4e29c46c7ad3c24322d368fa54da9eb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-choose-collection-methods"></a>Porady: wybieranie metod kolekcji
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Narzędzi profilowania obsługuje trzy metody zbieranie danych o wydajności: pobierania próbek, Instrumentacja i współbieżności. Metoda próbkowanie lub instrumentację umożliwia również zbieranie danych pamięci .NET alokacji i okresem istnienia.  
  
 **Wymagania**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Można użyć sesję wydajności **metody** właściwości w celu określenia najbardziej odpowiedniej metody kolekcji dla aplikacji. Można ustawić metod gromadzenia danych z Kreatora osiągów, Eksplorator wydajności lub strony właściwości sesji wydajności. Jeśli używasz narzędzia wiersza polecenia, zobacz [profilowania z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md) Aby uzyskać więcej informacji.  
  
## <a name="performance-wizard"></a>Kreator Wydajności  
  
#### <a name="to-select-a-collection-method-using-the-performance-wizard"></a>Aby wybrać metodę kolekcji za pomocą Kreatora osiągów  
  
-   Na pierwszej stronie kreatora wybierz jedną z następujących opcji:  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Próbkowanie Procesora**|Zbieranie statystyk aplikacji, które są przydatne do początkowej analizy i analizować problemy wykorzystanie procesora CPU.|  
|**Instrumentacji**|Zbiera dane chronometrażu, które są przydatne do ukierunkowanej analizy i analizowania problemów z wydajnością wejścia/wyjścia.|  
|**Alokacja pamięci platformy .NET**|Zbiera [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] danych alokacji pamięci przy użyciu metoda profilowania próbkowania.|  
|**Współbieżność**|Zbiera dane kontencji zasobów liczbowych.|  
  
## <a name="performance-explorer"></a>Eksplorator wydajności  
  
#### <a name="to-select-a-collection-method-using-performance-explorer"></a>Aby wybrać metodę kolekcji za pomocą Eksploratora wydajności  
  
1.  Na **Eksplorator wydajności** narzędzi, kliknij strzałkę obok pozycji **metody** listy rozwijanej.  
  
2.  Kliknij preferowaną metodę kolekcji.  
  
## <a name="performance-session-property-pages"></a>Strony właściwości sesji wydajności  
  
#### <a name="to-select-the-sampling-or-instrumentation-method-using-performance-session-properties"></a>Aby wybrać metodę próbkowanie lub instrumentację, przy użyciu właściwości sesji wydajności  
  
1.  W **Eksplorator wydajności**, wybierz sesję wydajności.  
  
     Nazwa pliku sesji wydajności ma rozszerzenie .psess.  
  
2.  Kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij przycisk **właściwości**.  
  
3.  W **strony właściwości**, kliknij przycisk **ogólne**.  
  
4.  Kliknij preferowaną metodę kolekcji.  
  
    -   Aby uzyskać informacje o opcjach, które są dostępne, gdy są zbierane dane z próbkowania, zobacz [zbieranie statystyk wydajności za pomocą próbkowania](../profiling/collecting-performance-statistics-by-using-sampling.md)  
  
    -   Aby uzyskać informacje o opcjach, które są dostępne, gdy są zbierane dane z próbkowania, zobacz [zbieranie szczegółowych danych o chronometrażu przy użyciu Instrumentacji](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md).  
  
#### <a name="to-select-net-memory-data-collection-by-using-performance-session-properties"></a>Aby wybrać kolekcję danych pamięci .NET przy użyciu właściwości sesji wydajności  
  
1.  W **Eksplorator wydajności**, wybierz sesję wydajności.  
  
     Nazwa pliku sesji wydajności ma rozszerzenie .psess.  
  
2.  Kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij przycisk **właściwości**.  
  
3.  W **strony właściwości**, kliknij przycisk **ogólne**.  
  
4.  Kliknij przycisk **próbkowania** lub **Instrumentacji**.  
  
5.  Kliknij przycisk **.NET zbierać informacje dotyczące alokacji obiektów** do zbierania rozmiaru i liczby [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] obiekt alokacji.  
  
6.  (Opcjonalnie) Kliknij przycisk **również zbierać informacje dotyczące okresu istnienia obiektu platformy .NET** do zebrania informacji o pamięci generacji kolekcji, w których pamięci obiektu została odzyskana.  
  
     Aby uzyskać informacje o innych opcjach dostępnych podczas zbierania danych pamięci .NET, zobacz [zbieranie alokacji pamięci .NET i okres istnienia obiektu](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md).  
  
#### <a name="to-select-concurrency-data-collection-by-using-performance-session-properties"></a>Aby wybrać zbierania danych współbieżności przy użyciu właściwości sesji wydajności  
  
1.  W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij przycisk **właściwości**.  
  
2.  W **strony właściwości**, kliknij przycisk **ogólne**.  
  
3.  Kliknij przycisk **współbieżności**.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [Opis pobierania wartości danych](../profiling/understanding-sampling-data-values.md)   
 [Właściwości sesji wydajności](../profiling/performance-session-properties.md)