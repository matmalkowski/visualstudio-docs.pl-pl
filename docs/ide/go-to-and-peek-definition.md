---
title: Wyświetlanie definicji typu w programie Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/10/2018
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code editor, view definition
- go to definition
- peek definition
- type definition [Visual Studio]
- member definition [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 61428294fc9c4afa32a50b4776f03ce1e98b83b9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="view-type-and-member-definitions"></a>Wyświetlanie definicji typu i element członkowski

Deweloperzy muszą często wyświetlić definicje kodu źródłowego dla typów lub elementów członkowskich klasy, których używają w swoich kodu. W programie Visual Studio **przejdź do definicji** i **definicji wglądu** funkcje umożliwiają łatwe wyświetlanie definicji typu lub elementu członkowskiego. Jeśli kod źródłowy jest niedostępny, zamiast niego wyświetlony metadanych.

## <a name="go-to-definition"></a>Przejdź do definicji

**Przejdź do definicji** funkcji przechodzi do źródła typu lub elementu członkowskiego i otwiera wynik na nowej karcie. Jeśli jesteś użytkownikiem klawiatury, umieść kursor tekstu gdzieś wewnątrz nazwy symbolu i naciśnij klawisz **F12**. Jeśli jesteś użytkownikiem myszy albo wybierz **przejdź do definicji** z menu kontekstowego lub użyj **klawisz Ctrl** funkcji opisanych w poniższej sekcji.

### <a name="ctrl-click-go-to-definition"></a>Klawisz CTRL, przejdź do definicji

W programie Visual Studio 2017 wersji 15.4, jest prostsze dla użytkowników myszy szybkiego dostępu **przejdź do definicji**. Symbole stają się aktywne po naciśnięciu **Ctrl** i zatrzymaj wskaźnik myszy typu lub elementu członkowskiego. Aby szybko przejść do definicji symbolu, naciśnij klawisz **Ctrl** klucza, a następnie kliknij go. To bardzo proste!

![Przejdź do definicji animacji kliknięcia myszą](../ide/media/click_gotodef.gif)

Można zmienić klucz modyfikujący na kliknięcie myszą **przejdź do definicji** , przechodząc do **narzędzia** > **opcje** > **Edytor tekstu**   >  **Ogólne**i wybierając jedną **Alt** lub **klawisze Ctrl + Alt** z **klawisz modyfikujący użyj**listy rozwijanej. Można również wyłączyć kliknięcia myszą **przejdź do definicji** usuwając zaznaczenie pola wyboru **Włącz myszy kliknij, aby wykonać przejdź do definicji** wyboru.

![Włączanie kliknięcia myszą przejdź do definicji](../ide/media/editor_options_mouse_click_gotodef.png)

## <a name="peek-definition"></a>Definicji wglądu

**Definicji wglądu** funkcji umożliwia podgląd definicję typu bez opuszczania bieżącej lokalizacji w edytorze. Jeśli jesteś użytkownikiem klawiatury, umieść kursor tekstu gdzieś wewnątrz nazwy typu lub elementu członkowskiego i naciśnij klawisz **Alt + F12**. Jeśli jesteś użytkownikiem mysz, możesz wybrać **definicji wglądu** z menu kontekstowego. W Visual Studio 2017 wersji 15,4 i nowszych ma w nowy sposób wglądu w widoku definicji za pomocą myszy. Po pierwsze, przejdź do **narzędzia** > **opcje** > **Edytor tekstu** > **ogólne**. Wybierz opcję **Otwórz definicję w widoku peek** i kliknij przycisk **OK** zamknąć **opcje** okno dialogowe.

![Ustawienie opcji definicji wglądu kliknięcia myszą](../ide/media/editor_options_peek_view.png)

Naciśnij klawisz **Ctrl** (lub innego klawisz modyfikujący został wybrany w **opcje**) i kliknij polecenie typu lub elementu członkowskiego.

![Podgląd animacji definicji](../ide/media/peek_definition.gif)

Jeśli wgląd inną definicję w oknie podręcznym, zostanie uruchomiona ścieżką nawigacją, której można nawigować przy użyciu okręgi i strzałki wyświetlane powyżej menu podręcznego.

Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie i edytowanie kodu za pomocą definicji wglądu (Alt + F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).

## <a name="view-metadata-as-source-code-c"></a>Wyświetlanie metadanych jako kodu źródłowego (C#)

Podczas wyświetlania definicji typów C# lub elementów członkowskich, których kod źródłowy jest niedostępny, zamiast tego jest wyświetlany ich metadanych. Deklaracje typów i członków, ale nie ich implementacji jest widoczny.

Po uruchomieniu **przejdź do definicji** lub **definicji wglądu** polecenia dla elementu, którego kod źródłowy jest niedostępny, dokument z kartami zawiera widok metadanych tego elementu wyświetlana jako kodu źródłowego zostanie wyświetlony w edytorze kodu. Nazwa typu, a następnie **[z metadanych]**, zostanie wyświetlony na karcie dokumentu.

Na przykład, jeśli uruchomisz **przejdź do definicji** polecenia dla <xref:System.Console>, metadane <xref:System.Console> zostanie wyświetlony w edytorze kodu jako kodu źródłowego C#. Kod przypomina jego deklaracji, ale implementacja nie są wyświetlane.

![Metadane jako źródło](../ide/media/metadatasource.png "MetadataSource")

> [!NOTE]
> Podczas próby uruchomienia **przejdź do definicji** lub **definicji wglądu** polecenia dla typów albo elementów członkowskich, które są oznaczone jako wewnętrzne programu Visual Studio nie wyświetla metadane jako kod źródłowy, niezależnie od tego, czy zestaw odwołujący się jest znajomym, czy nie.

### <a name="view-decompiled-source-definitions-instead-of-metadata-c"></a>Wyświetlanie definicji źródła decompiled zamiast metadanych (C#)

Nowy w programie Visual Studio 2017 wersji 15,6, można ustawić opcję, aby wyświetlić kod źródłowy decompiled podczas wyświetlania definicji typu C# lub element członkowski, którego kod źródłowy jest niedostępny. Aby włączyć tę funkcję, należy wybrać **narzędzia** > **opcje** na pasku menu. Następnie rozwiń **Edytor tekstu** > **C#** > **zaawansowane**i wybierz **umożliwiają nawigowanie do źródeł decompiled**.

![Wyświetlanie definicji decompiled](media/go-to-definition-decompiled-sources.png)

> [!NOTE]
> Visual Studio rekonstruuje przy użyciu dekompilacji ILSpy treści metody. Po raz pierwszy uzyskać dostęp do tej funkcji, należy zaakceptować zrzeczenia dotyczące oprogramowania, licencjonowania i prawach autorskich i znak towarowy prawa.

## <a name="see-also"></a>Zobacz także

[Nawigowanie po kodzie](../ide/navigating-code.md)

[Porady: wyświetlanie i edytowanie kodu za pomocą definicji wglądu (Alt + F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)
