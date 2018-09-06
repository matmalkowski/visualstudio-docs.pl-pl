---
title: Menedżer pakietów dla języka R
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
ms.openlocfilehash: 4063787711ae825cd587f72d735710444906d99b
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "35666517"
---
# <a name="package-manager"></a>Menedżer pakietów

R Tools for Visual Studio (RTVS) Menedżera pakietów jest interfejsem użytkownika do zarządzania pakietami języka R. Aby go otworzyć, wybierz **R Tools** > **Windows** > **pakietów** lub naciskając **Ctrl** + **7**.

Menedżer pakietów zawiera trzy karty. Każda karta zawiera listę odpowiednich pakietów po lewej stronie, i szczegółowe informacje dotyczące wybranego pakietu po prawej stronie, w tym wersja pakietu, opis i licencji, zainstaluj lokalizacji i łącza do innych istotnych informacji. Pole wyszukiwania w prawym górnym rogu umożliwia filtrowanie listy.

> [!Tip]
> Termin w polu wyszukiwania pozostaje, jak przełączać się między kartami.

- **Dostępne** pozwala przeglądać pakiety do zainstalowania. Jeśli pakiet jest już zainstalowany, **zainstalować** przycisk po prawej stronie zmienia się **Odinstaluj**.

    ![Dostępne pakiety karcie R Tools for Visual Studio Menedżera pakietów](media/package-manager-available.png)

- **Zainstalowane** pokazuje wszystkie zainstalowane i ładowane pakietów. Zieloną kropkę obok pakietu wskazuje, że jest załadowany do sesji języka R. Czerwona X ikonę na liście po lewej stronie lub **Odinstaluj** przycisk po prawej stronie można odinstalować pakiet. Jeśli dostępna jest nowsza wersja zainstalowanego pakietu, niebieski Strzałka w prawo pakietu w górę przeprowadza aktualizację.

    ![Zainstalowane pakiety kartę w R Tools for Visual Studio Menedżera pakietów](media/package-manager-installed.png)

- **Załadowano** wyświetla tylko te pakiety, które są ładowane do sesji języka R, które są wyświetlane z zieloną kropkę. Możesz również odinstalować i aktualizowanie pakietów w tym miejscu.

    ![Załadowano karcie pakiety R Tools for Visual Studio Menedżera pakietów](media/package-manager-loaded.png)

## <a name="package-locations"></a>Lokalizacje pakietów

Pakiety są instalowane w następujących lokalizacjach:

- Pakietami podstawowymi, które są dołączone RTVS są zainstalowane w *C:\Program Files\Microsoft\R Client\R_SERVER\library*
- Dodatkowe pakiety są instalowane na *%userprofile%\Documents\R\win-library\3.3*
