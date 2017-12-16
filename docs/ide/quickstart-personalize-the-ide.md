---
title: "Ustaw motyw kolorów i czcionek w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/20/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a08bcc91159182043b68391bc869243909d6df8b
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2017
---
# <a name="quickstart-personalize-the-visual-studio-ide-and-editor"></a>Szybki Start: personalizowanie środowiska IDE programu Visual Studio i edytora

W przypadku tego przewodnika Szybki Start 5 – 10 min możemy dostosować motywu kolorów programu Visual Studio i dwa kolory tekstu w edytorze tekstu.

## <a name="set-the-color-theme"></a>Ustaw motywu kolorów

Nosi nazwę domyślny motyw kolorów dla programu Visual Studio 2017 **Blue**. Teraz Zmień, aby **ciemny**.

1. Na pasku menu wybierz **narzędzia**, **opcje**.

1. Na **środowiska**, **ogólne** Strona opcji, zmień **motywu kolorów** zaznaczenie, aby **ciemny**, a następnie wybierz pozycję **OK** .

   Motyw kolorów dla całego środowiska IDE jest zmieniana na **ciemny**.

   ![VS ciemnego motywu](media/quickstart-personalize-dark-theme.png)

> [!TIP]
> Można zainstalować dodatkowe kompozycje wstępnie zdefiniowanych przez zainstalowanie **Visual Studio kolor motywu edytora** z [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.VisualStudio2017ColorThemeEditor). Po zainstalowaniu tego narzędzia motywy kolorów dodatkowe są wyświetlane na liście rozwijanej kolor motywu.

## <a name="change-text-color"></a>Zmiana koloru tekstu

Firma Microsoft będzie teraz dostosować niektóre kolory tekstu edytora. Po pierwsze umożliwia otwieranie pliku XML, aby wyświetlić domyślne kolory.

1. Na pasku menu wybierz **pliku**, **nowy**, **pliku...** .

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

   Zwróć uwagę, że numery wierszy są kolor niebieski turkusowy i atrybutów xml są jasny kolor niebieski. Zamierzamy zmienić kolor tekstu dla tych elementów.

   ![Kolor czcionki pliku XML](media/quickstart-personalize-xml-file.png)

1. Aby otworzyć **opcje** okno dialogowe, na pasku menu wybierz **narzędzia**, **opcje**.

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

[Szybki Start: Pierwsze spojrzenie na środowiska IDE programu Visual Studio](../ide/quickstart-ide-orientation.md)  
[Szybki Start: kodowania w edytorze](../ide/quickstart-editor.md)  
[Szybki Start: projekty i rozwiązania](../ide/quickstart-projects-solutions.md)  
[Personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md)  
[Dostosowywanie edytora](../ide/customizing-the-editor.md)  
[Środowisko IDE programu Visual Studio — przegląd](../ide/visual-studio-ide.md)