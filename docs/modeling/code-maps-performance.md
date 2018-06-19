---
title: Mapy kodu są przetwarzane wolno
ms.date: 05/16/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 2dece1e63fffdba67678422ad9241babc63b7abd
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34267702"
---
# <a name="improve-performance-for-code-maps"></a>Poprawianie wydajności dla mapy kodu

Podczas generowania mapy po raz pierwszy, program Visual Studio indeksuje wszystkie zależności, które znajdzie. Ten proces może trochę potrwać, szczególnie w przypadku dużych rozwiązaniach, ale zwiększa wydajność nowsze. Zmiana kodu programu Visual Studio reindexes zaktualizowanego kodu. Aby zminimalizować czas poświęcony na mapie, aby zakończyć renderowania, należy wziąć pod uwagę poniższe sugestie:

- [Mapowanie tylko zależności, które są potrzebne.](#create-a-code-map-to-see-specific-dependencies)

- Aby wygenerować mapy dla całego rozwiązania, należy zawęzić zakres rozwiązania.

- Wyłącz automatyczne kompilacji dla rozwiązania, wybierając **pominięcia kompilacji** na pasku narzędzi mapy kodu.

- Wyłącz automatyczne dodawanie elementów nadrzędnych, wybierając **obejmują nadrzędnych** na pasku narzędzi mapy kodu.

   ![Przyciski pominięcia kompilacji i zawierać elementów nadrzędnych](../modeling/media/codemapsfilterskipbuildicons.png)

- Przeprowadź edycję pliku mapy kodu bezpośrednio do usuń węzły i łącza, które nie są potrzebne. Zmiana mapy nie wpływa na kod źródłowy. Zobacz [Dostosowanie map kodu przez edycję plików DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

Może zająć więcej czasu na tworzenie map lub Dodaj elementy do mapy z **Eksploratora rozwiązań** gdy element projektu **Kopiuj do katalogu wyjściowego** właściwość jest ustawiona na **zawsze Kopiuj**. Aby zwiększyć wydajność, należy zmienić tę właściwość, aby **Kopiuj, jeśli nowszy** lub `PreserveNewest`. Zobacz [kompilacji przyrostowej](../msbuild/incremental-builds.md).

Ukończono Mapa pokazuje zależności tylko w przypadku pomyślnie skompilowany kod. Jeśli występują błędy kompilacji dla niektórych składników, te błędy są wyświetlane na mapie. Upewnij się, że składnik faktycznie tworzy i ma zależności z przed wprowadzeniem architektury decyzje na podstawie na mapie.