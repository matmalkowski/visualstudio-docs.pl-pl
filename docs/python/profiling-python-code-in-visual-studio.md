---
title: "Pomiaru wydajności kodu języka Python w programie Visual Studio | Dokumentacja firmy Microsoft"
description: "Jak używać profilera Visual Studio Aby sprawdzić wydajność Python code podczas usnig tłumaczy na podstawie języka CPython."
ms.custom: 
ms.date: 01/09/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: c946f9d0fea5192f75d2fd0a9865827b6027ef50
ms.sourcegitcommit: c0a2385a16cc4f47d2e1ff23d35c4da40f5605e0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="profiling-python-code"></a>Profilowanie kodu języka Python

Można profilu aplikacji Python, używając tłumaczy na podstawie języka CPython. (Zobacz [macierzy funkcji - profilowania](overview-of-python-tools-for-visual-studio.md#matrix-profiling) dostępności tej funkcji dla różnych wersji programu Visual Studio.)

Profilowanie jest uruchamiane za pośrednictwem **Analizuj > Uruchom profilowanie Python** polecenia menu, które umożliwia otwarcie okna dialogowego konfiguracji:

![Okno dialogowe konfiguracji profilowania](media/profiling-start.png)

Po wybraniu **OK**, profilera uruchamia i zostanie otwarty raport dotyczący wydajności za pomocą którego można sprawdzić, jak czas w aplikacji:

![Raport profilowania wydajności](media/profiling-results.png)

|   |   |
|---|---|
| ![Ikona aparatu film wideo](../install/media/video-icon.png "obejrzeć film wideo") | [Obejrzyj film (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Profiling-Python-s6FoC6LWE_1005918567) do pokazania Python profilowania (3 m 00s).|

> [!Note]
> Obecnie program Visual Studio obsługuje tylko na tym poziomie profilowania pełnej aplikacji, ale chcemy pewnością czekamy na Twoją opinię na przyszłe możliwości. Użyj [ **opinii produktu** przycisk](#feedback) u dołu tej strony.

## <a name="profiling-for-ironpython"></a>Profilowanie dla IronPython

IronPython nie jest na podstawie języka CPython interpreter, powyżej funkcję profilowania nie działa.

Zamiast tego należy użyć profilera Visual Studio .NET, uruchamiając `ipy.exe` bezpośrednio w aplikacji docelowej przy użyciu odpowiednie argumenty do uruchomienia skryptu uruchamiania. Obejmują `-X:Debug` w wierszu polecenia, aby upewnij się, że wszystkie Twoje Python kod może być debugowany i profilowaniu. Ten argument generuje raport dotyczący wydajności, tym czas IronPython środowiska uruchomieniowego i programowanie. Kod jest identyfikowany przy użyciu nazwy zniekształcone.

Alternatywnie IronPython ma kilka własnych wbudowanych profilowania, ale nie ma obecnie nie dobrej wizualizatora dla niego. Zobacz [profilera IronPython](http://blogs.msdn.com/b/curth/archive/2009/03/29/an-ironpython-profiler.aspx) (blogi MSDN) dla co jest dostępne.