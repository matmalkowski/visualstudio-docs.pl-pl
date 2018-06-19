---
title: Okno Eksploratora wydajności | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performanceexplorer
- vs.performance.explorer
helpviewer_keywords:
- performance tools, Performance Explorer
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f27d1436aaeb0ec75876edf9119dff93f7539483
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
ms.locfileid: "31582114"
---
# <a name="performance-explorer-window"></a>Okno Eksploratora wydajności

**Eksplorator wydajności** okna w środowisku IDE programu Visual Studio pozwala skonfigurować i uruchomić sesji wydajności przy użyciu programu Visual Studio Profiling Tools.

## <a name="performance-explorer-toolbar"></a>Pasek narzędzi Eksploratora wydajności

Poniższe opcje są dostępne na **Eksplorator wydajności** narzędzi:

- **Uruchom Kreatora wydajności** -wyświetla Kreatora wydajności w celu dodania nowej sesji wydajności do okna Eksplorator wydajności.

- **Nowa sesja wydajności** -dodaje sesji wydajności puste okno Eksploratora wydajności.

- **Uruchom** — **uruchamianie** polecenia listy przycisków umożliwia uruchamianie aplikacji docelowej, która natychmiast włączono profilowanie (**uruchamianie o profilowania**) lub wstrzymane (profilowania **Uruchom z profilowania wstrzymana**).

- **Metoda** — Określa, czy próbki jest używana metoda profilowania sesji lub Instrumentacji.

- **Zatrzymaj** -natychmiast kończy pracę w aplikacji docelowej i profilera.

- **Attach/Detach** -Wyświetla **Dołącz Profiler do procesu** okno dialogowe, aby wybrać uruchomionego procesu, do którego ma zostać dołączony profilera.

## <a name="performance-explorer-window"></a>Okno Eksploratora wydajności

**Eksplorator wydajności** okna zawiera formant drzewa, który zawiera pliki binarne i pliki danych raportu z co najmniej jednej sesji wydajności.

- **Nazwa sesji** -katalog główny na drzewie zawiera nazwę sesji. Kliknij prawym przyciskiem myszy Nazwa sesji, aby ustawić właściwości sesji, czy też chcesz rozpocząć aplikacji docelowej i profilera.

- **Obiekty docelowe** -Wyświetla nazwy plików binarnych, które mają być profilowane w sesji. Kliknij prawym przyciskiem myszy **celów** do dodawania lub usuwania pliku binarnego, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projekt lub witrynę sieci Web. Kliknij prawym przyciskiem myszy nazwę docelowej, można ustawić właściwości dla poszczególnych pliku binarnego.

- **Raporty** -Wyświetla nazwy plików danych profilera, które są generowane dla tej sesji. Kliknij prawym przyciskiem myszy **raporty** Dodawanie istniejącego raportu lub do porównywania dwóch plików danych profilera. Kliknij prawym przyciskiem myszy nazwę raportu, aby otworzyć, usuń lub Eksportuj plik danych profilera.

## <a name="see-also"></a>Zobacz także

[Omówienia](../profiling/overviews-performance-tools.md)  
[Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)  
[Kontrolowanie zbierania danych](../profiling/controlling-data-collection.md)