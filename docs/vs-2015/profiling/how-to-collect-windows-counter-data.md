---
title: 'Porady: zbieranie danych licznika Windows | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.property.syscounter
- vs.performance.property.wincounter
helpviewer_keywords:
- windows counters
- performance tools, using windows counters
- profiling tools, using windows counters
ms.assetid: db4fbac2-bea5-4558-aa8b-160fcccf4b33
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7f0ace1d920cdd4f2c503c608a1695b04c1251f2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680720"
---
# <a name="how-to-collect-windows-counter-data"></a>Porady: zbieranie danych liczników systemu Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: zbieranie danych licznika Windows](https://docs.microsoft.com/visualstudio/profiling/how-to-collect-windows-counter-data).  
  
Liczniki Windows są liczniki wydajności systemu, które mogą być zbierane podczas profilowania w ustalonych odstępach czasu. W widoku znaczniki raportu narzędzi profilowania z wiersza jest oznaczona etykietą **AutoMark** dla każdego interwału zbierania. Wiersz zawiera kolumny, które opisują wartości licznika wydajności, w tym odstępach czasu. Aby ograniczyć analizę do okresu czasu między dwoma określonymi znacznikami, zaznacz znaki, kliknij prawym przyciskiem myszy, a następnie wybierz **Filtruj wg** ->  **znaczniki** z menu skrótów.  
  
 **Wymagania**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagają znaczących zmian w taki sposób, programu Visual Studio profiler zbiera dane na tych platformach. Aplikacje Windows Store również wymagają nowych technik zbierania. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
### <a name="to-collect-windows-counter-data"></a>Aby zebrać dane Windows  
  
1.  W Eksploratorze wydajności, kliknij prawym przyciskiem myszy sesję, dla której chcesz skonfigurować liczniki Windows, a następnie wybierz pozycję **właściwości**.  
  
2.  W **stron właściwości**, kliknij przycisk **liczniki Windows**.  
  
3.  Wybierz **zbierania liczników Windows** pole wyboru.  
  
4.  W **interwał zbierania (MS)** tekstu wpisz przedział czasu.  
  
5.  Wybierz kategorię z **kategorii licznika** listy rozwijanej.  
  
6.  Wybierz domyślne wystąpienie z **wystąpienia** listy rozwijanej.  
  
7.  Wybierz liczniki, które chcesz użyć podczas profilowania aplikacji.  
  
8.  Kliknij przycisk **zastosowania.**  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [Właściwości sesji wydajności](../profiling/performance-session-properties.md)   
 [CPU i liczniki Windows](../profiling/cpu-and-windows-counters.md)



