---
title: Menedżer pakietów dla R
description: Jak używać Menedżera pakietów języka R w Visual Studio, aby zainstalować i R Menedżera pakietów.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: 8086d28c9591195c90268b52a03325b8acc2e420
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="package-manager"></a>Menedżer pakietów

Narzędzia R Menedżera pakietów programu Visual Studio (RTVS) jest interfejs użytkownika do zarządzania pakietami R. Aby go otworzyć, wybierz **narzędzia R > Windows > pakiety** lub naciskając klawisz Ctrl + 7.

Menedżer pakietów zawiera trzy karty. Każdej karcie Wyświetla listę odpowiednich pakietów po lewej stronie i konkretne szczegółowe informacje dla wybranego pakietu po prawej stronie, takich jak wersja pakietu, opis, licencji, zainstaluj lokalizacji i linki do innych istotnych informacji. Pole wyszukiwania w prawym górnym rogu umożliwia filtrowanie listy.

> [!Tip]
> Termin w polu wyszukiwania obowiązuje jako Przełączanie kart.

- **Dostępne** umożliwia przeglądanie pakietów do zainstalowania. Jeśli pakiet jest już zainstalowany, **zainstalować** przycisk po prawej stronie zmienia się **Odinstaluj**.

    ![Karta pakiety dostępne w narzędziach R Menedżera pakietów programu Visual Studio](media/package-manager-available.png)

- **Zainstalowane** zawiera wszystkie zainstalowane i ładowane pakietów. Zielona kropka obok pakietu wskazuje, że jest załadowany do sesji R. Czerwony X ikonę na liście po lewej stronie lub **Odinstaluj** przycisku z prawej strony można odinstalować pakietu. Jeśli jest dostępna nowsza wersja zainstalowanego pakietu, niebieski Strzałka w prawo pakietu w górę wykonuje aktualizację.

    ![Zainstalowane pakiety kartę w narzędziach R Menedżera pakietów programu Visual Studio](media/package-manager-installed.png)

- **Załadowano** wyświetla tylko te pakiety, które są ładowane do sesji R, które są wyświetlane z zielonym kropką. Można również odinstalować i tutaj pakietów aktualizacji.

    ![Załadowano kartę pakietów w narzędziach R Menedżera pakietów programu Visual Studio](media/package-manager-loaded.png)

## <a name="package-locations"></a>Lokalizacje pakietów

Pakiety są instalowane w następujących lokalizacjach:

- Pakietami podstawowymi, które są dołączone do RTVS są zainstalowane w `C:\Program Files\Microsoft\R Client\R_SERVER\library`
- Instalowane są dodatkowe pakiety `%userprofile%\Documents\R\win-library\3.3`
