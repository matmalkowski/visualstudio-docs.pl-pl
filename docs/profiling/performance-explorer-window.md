---
title: "Okno Eksploratora wydajności | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performanceexplorer
- vs.performance.explorer
helpviewer_keywords: performance tools, Performance Explorer
ms.assetid: cb6a6efc-93a5-49a2-8d03-6969b5f3b6d7
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6fc3be33c332d643e5feb48f4a3733395c2a608
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="performance-explorer-window"></a>Okno Eksploratora wydajności
**Eksplorator wydajności** okna w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zintegrowane środowisko programistyczne (IDE) pozwala skonfigurować i uruchomić sesji wydajności przy użyciu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędziach profilowania.  
  
 **Wymagania**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
## <a name="performance-explorer-toolbar"></a>Pasek narzędzi Eksploratora wydajności  
 Poniższe opcje są dostępne na **Eksplorator wydajności** narzędzi:  
  
-   **Uruchom Kreatora wydajności** -wyświetla Kreatora wydajności w celu dodania nowej sesji wydajności do okna Eksplorator wydajności.  
  
-   **Nowa sesja wydajności** -dodaje sesji wydajności puste okno Eksploratora wydajności.  
  
-   **Uruchom** — **Uruchom** polecenia listy przycisków umożliwia uruchamianie aplikacji docelowej, która natychmiast włączono profilowanie (**uruchamianie o profilowania**) lub profilowania (wstrzymane **Wstrzymana uruchamiania o profilowania**).  
  
-   **Metoda** — Określa, czy próbki jest używana metoda profilowania sesji lub Instrumentacji.  
  
-   **Zatrzymaj** -natychmiast kończy pracę w aplikacji docelowej i profilera.  
  
-   **Attach/Detach** -Wyświetla **Dołącz Profiler do procesu** okno dialogowe, aby wybrać uruchomionego procesu, do którego ma zostać dołączony profilera.  
  
## <a name="performance-explorer-window"></a>Okno Eksploratora wydajności  
 **Eksplorator wydajności** okna zawiera formant drzewa, który zawiera pliki binarne i pliki danych raportu z co najmniej jednej sesji wydajności.  
  
-   **Nazwa sesji** -katalog główny na drzewie zawiera nazwę sesji. Kliknij prawym przyciskiem myszy Nazwa sesji, aby ustawić właściwości sesji, czy też chcesz rozpocząć aplikacji docelowej i profilera.  
  
-   **Obiekty docelowe** -Wyświetla nazwy plików binarnych, które mają być profilowane w sesji. Kliknij prawym przyciskiem myszy **celów** do dodawania lub usuwania pliku binarnego, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projekt lub witrynę sieci Web. Kliknij prawym przyciskiem myszy nazwę docelowej, można ustawić właściwości dla poszczególnych pliku binarnego.  
  
-   **Raporty** -Wyświetla nazwy plików danych profilera, które są generowane dla tej sesji. Kliknij prawym przyciskiem myszy **raporty** Dodawanie istniejącego raportu lub do porównywania dwóch plików danych profilera. Kliknij prawym przyciskiem myszy nazwę raportu, aby otworzyć, usuń lub Eksportuj plik danych profilera.  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie](../profiling/overviews-performance-tools.md)   
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [Kontrolowanie zbierania danych](../profiling/controlling-data-collection.md)