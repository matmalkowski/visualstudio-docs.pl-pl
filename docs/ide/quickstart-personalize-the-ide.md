---
title: Ustaw motyw kolorów i czcionek w programie Visual Studio
ms.date: 11/20/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 326da0003e73c78a17df489473b49cf6d7b62380
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255418"
---
# <a name="quickstart-personalize-the-visual-studio-ide-and-editor"></a>Szybki Start: Personalizowanie środowiska IDE programu Visual Studio i edytora

W przypadku tego przewodnika Szybki Start 5 – 10 min możemy dostosować motywu kolorów w Visual Studio i kolory dwóch tekstu w **Edytor tekstu**.

Jeśli nie został już zainstalowany program Visual Studio, przejdź do [program Visual Studio pobiera](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) stronę, aby zainstalować ją bezpłatnie.

## <a name="set-the-color-theme"></a>Ustaw motywu kolorów

Nosi nazwę domyślny motyw kolorów dla programu Visual Studio 2017 **Blue**. Teraz Zmień, aby **ciemny**.

1. Na pasku menu wybierz **narzędzia** > **opcje**.

1. Na **środowiska** > **ogólne** Strona opcji, zmień **motywu kolorów** zaznaczenie, aby **ciemny**, a następnie wybierz pozycję **OK**.

   Motyw kolorów dla całego środowiska IDE jest zmieniana na **ciemny**.

   ![VS ciemnego motywu](media/quickstart-personalize-dark-theme.png)

> [!TIP]
> Można zainstalować dodatkowe kompozycje wstępnie zdefiniowanych przez zainstalowanie **Visual Studio kolor motywu edytora** z [programu Visual Studio marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor). Po zainstalowaniu tego narzędzia motywy kolorów dodatkowe są wyświetlane w **motywu kolorów** listy rozwijanej.

## <a name="change-text-color"></a>Zmiana koloru tekstu

Firma Microsoft będzie teraz dostosować niektóre kolory tekstu edytora. Po pierwsze umożliwia otwieranie pliku XML, aby wyświetlić domyślne kolory.

1. Na pasku menu wybierz **pliku** > **nowy** > **pliku**.

1. W **nowy plik** okna dialogowego, w obszarze **ogólne** kategorii, wybierz **pliku XML**, a następnie wybierz pozycję **Otwórz**.

1. Wklej następujący kod XML poniżej wiersza, który zawiera `<?xml version="1.0" encoding="utf-8"?>`.

   ```xml
   <Catalog>
     <Book id="bk101">
     <Author>Garghentini, Davide</Author>
     <Title>XML Developer's Guide</Title>
     <Genre>Computer</Genre>
     <Price>44.95</Price>
     <PublishDate>2000-10-01</PublishDate>
     <Description>
       An in-depth look at creating applications with XML.
     </Description>
   </Book>
   <Book id="bk102">
     <Author>Garcia, Debra</Author>
     <Title>Midnight Rain</Title>
     <Genre>Fantasy</Genre>
     <Price>5.95</Price>
     <PublishDate>2000-12-16</PublishDate>
     <Description>
       A former architect battles corporate zombies, an evil
       sorceress, and her own childhood to become queen of the world.
     </Description>
   </Book>
   </Catalog>
   ```

   Zwróć uwagę, że numery wierszy są kolor niebieski turkusowy i atrybutów XML są jasny kolor niebieski. Zamierzamy zmienić kolor tekstu dla tych elementów.

   ![Kolor czcionki pliku XML](media/quickstart-personalize-xml-file.png)

1. Aby otworzyć **opcje** oknie dialogowym wybierz **narzędzia** > **opcje** na pasku menu.

1. W obszarze **środowiska**, wybierz **czcionki i kolory** kategorii.

   Należy zauważyć, że tekst w polu **Pokaż ustawienia dla** mówi **Edytor tekstu**&mdash;jest to, co chcemy. Może rozszerzyć listy rozwijanej tylko w celu lista dużą ilością miejsca, w którym można dostosowywać czcionki i kolor tekstu.

1. Zmiana koloru tekstu numerów linii w **wyświetlania elementów** wybierz **numer wiersza**. W **pierwszego planu elementu** wybierz **oliwek**.

   ![Opcje — okno dialogowe, czcionki i kolory kategorii](media/quickstart-personalize-line-number-color.png)

   Niektóre języki mają własne określone ustawienia czcionek i kolorów. Jeśli jesteś deweloperem C++ i chcesz zmienić kolor używany dla funkcji, na przykład można wyszukać **funkcje języka C++** w **wyświetlania elementów** listy.

1. Przed zakończeniu poza okno dialogowe, umożliwia również zmianę koloru atrybutów XML. W **wyświetlania elementów** listy, przewiń w dół do **atrybutu XML** i zaznacz je. W **pierwszego planu elementu** wybierz **wapna**. Wybierz **OK** naszych opcji Zapisz i zamknij okno dialogowe.

   Numery wierszy są teraz oliwek kolorów i atrybutów XML jasny, limonowy zielony. Otwórz plik innego typu, takich jak plik kodu C++ lub C#, zobaczysz czy numery wierszy również są wyświetlane w kolorze oliwek.

   ![Plik XML z nowych kolorów czcionki](media/quickstart-personalize-xml-file-new-colors.png)

Firma Microsoft przedstawione kilka sposobów dostosowywanie kolorów w Visual Studio. Mamy nadzieję, że będzie zapoznanie się inne opcje dostosowywania w **opcje** okno dialogowe, aby rzeczywiście Visual Studio własne.

## <a name="see-also"></a>Zobacz także

- [Szybki Start: Pierwsze spojrzenie na środowiska IDE programu Visual Studio](../ide/quickstart-ide-orientation.md)
- [Szybki Start: Kodowania w edytorze](../ide/quickstart-editor.md)
- [Szybki Start: Projekty i rozwiązania](../ide/quickstart-projects-solutions.md)
- [Personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md)
- [Dopasowywanie edytora](../ide/customizing-the-editor.md)
- [Środowisko IDE programu Visual Studio — przegląd](../ide/visual-studio-ide.md)
