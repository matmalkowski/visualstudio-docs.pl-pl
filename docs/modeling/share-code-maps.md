---
title: Eksportowanie i Zapisz mapy kodu
ms.date: 05/16/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: abfe8d6160d023a99e9a49480baada9acb0c8243
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="share-code-maps"></a>Udostępnianie mapy kodu

Mapy kodu można zapisać jako część projektu programu Visual Studio, jak obraz lub jako plik XPS.

## <a name="share-a-code-map-with-other-visual-studio-users"></a>Udostępnij mapę kodu innych użytkowników programu Visual Studio

Użyj **pliku** menu, aby zapisać mapy.

—lub—

Aby zapisać mapy w ramach danego projektu, na pasku narzędzi mapy, wybierz **udziału** > **Przenieś \<CodeMapName > .dgml do**, a następnie wybierz projekt, w którym chcesz zapisać Mapa.

![Przenieś mapy do innego projektu](../modeling/media/codemapsmovemapmenu.png)

Visual Studio zapisuje mapy jako *.dgml* plików, które można udostępniać innym użytkownikom programu Visual Studio Enterprise i Visual Studio Professional.

> [!NOTE]
> Przed udostępnieniem mapy osób, które używają programu Visual Studio Professional, upewnij się, że wszystkie grupy rozwiń, Pokaż ukryte węzły i linki międzygrupowe i pobierać żadnych usuniętych węzłów, które mają być widoczne na mapie. W przeciwnym razie inni użytkownicy nie będą mogli zobaczyć tych elementów.
>
> Po zapisaniu mapy, który znajduje się w projekcie modelowania lub został skopiowany z projektem modelowania do innej lokalizacji, może wystąpić następujący błąd:
>
> "Nie można zapisać *fileName* poza katalogiem projektu. Elementy połączone nie są obsługiwane”.
>
> Program Visual Studio pokazuje błąd, ale mimo to tworzy zapisaną wersję. Aby uniknąć tego błędu, należy utworzyć mapy spoza projektu modelowania. Można następnie zapisać go w dowolnej lokalizacji. Skopiowanie pliku do innej lokalizacji w rozwiązaniu, a następnie próba zapisu zakończą się niepowodzeniem.

## <a name="export-a-code-map-as-an-image"></a>Eksportowanie jako obraz mapy kodu

Po wyeksportowaniu mapę kodu jako obraz, skopiuj go do innych aplikacji, takich jak Microsoft Word czy PowerPoint.

1. Na pasku narzędzi mapy kodu, wybierz **udziału** > **poczty E-mail jako obraz** lub **Kopiuj obraz**.

2. Wklej obraz do innej aplikacji.

## <a name="export-the-map-as-an-xps-file"></a>Eksportuj mapy jako plik XPS

Po wyeksportowaniu mapę kodu jako plik XPS, możesz to sprawdzić w XML lub XAML przeglądarki, takich jak program Internet Explorer.

1. Na pasku narzędzi mapy kodu, wybierz **udziału** > **poczty E-mail jako przenośne XPS** lub **zapisać przenośnych XPS**.

2. Przejdź do której chcesz zapisać plik.

3. Nazwa mapy kodu. Upewnij się, że **Zapisz jako typ** pole ma ustawioną wartość **plików XPS (\*XPS)**. Wybierz **zapisać**.

## <a name="see-also"></a>Zobacz także

- [Zależności mapy z mapy kodu](../modeling/map-dependencies-across-your-solutions.md)