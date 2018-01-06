---
title: "Pomiaru wydajności kodu języka Python w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 07/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload: python
ms.openlocfilehash: 525ff73c70b092ca97a9c53759ffa93d55d12c88
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="profiling-python-code"></a>Profilowanie kodu języka Python

Program Visual Studio obsługuje profilowania aplikacji Python, używając tłumaczy na podstawie języka CPython.

Profilowanie jest uruchamiane za pośrednictwem **Analizuj > Uruchom profilowanie Python** polecenia menu, które umożliwia otwarcie okna dialogowego konfiguracji:

![Okno dialogowe konfiguracji profilowania](media/profiling-start.png)

Po wybraniu **OK**, profilera uruchamia i zostanie otwarty raport dotyczący wydajności za pomocą którego można sprawdzić, jak czas w aplikacji:

![Raport profilowania wydajności](media/profiling-results.png)

Wideo dla pokaz, [profilowania Python](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=hb46k6LWE_405918567) (Microsoft Virtual Academy, 3m00s).

> [!VIDEO https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Testing-Python-hb46k6LWE_405918567]


## <a name="profiling-for-ironpython"></a>Profilowanie dla IronPython

IronPython nie jest na podstawie języka CPython interpreter, powyżej funkcję profilowania nie działa.

Zamiast tego należy użyć profilera Visual Studio .NET, uruchamiając `ipy.exe` bezpośrednio w aplikacji docelowej przy użyciu odpowiednie argumenty do uruchomienia skryptu uruchamiania. Obejmują `-X:Debug` w wierszu polecenia, aby wymusić możliwością debugowania i możliwego kodu języka Python. Ten argument generuje raport dotyczący wydajności, tym czas IronPython środowiska uruchomieniowego i programowanie. Kod jest identyfikowany przy użyciu nazwy zniekształcone.

Alternatywnie IronPython ma kilka własnych wbudowanych profilowania, ale nie ma obecnie nie dobrej wizualizatora dla niego. Zobacz [profilera IronPython](http://blogs.msdn.com/b/curth/archive/2009/03/29/an-ironpython-profiler.aspx) (blogi MSDN) dla co jest dostępne.