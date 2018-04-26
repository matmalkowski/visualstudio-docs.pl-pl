---
title: 'Porady: Ustawianie opcji ułatwień dostępu IDE'
description: Dowiedz się, jak ustawić opcje ułatwień dostępu w programie Visual Studio, aby ułatwić jego zintegrowane środowisko programistyczne (IDE) ułatwia dla każdego, w tym dla osób, które mają słabym wzrokiem do odczytu i dla osób o ograniczonej sprawności ruchowej do zapisu.
ms.date: 08/22/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: ddc96c4c-0600-46c1-8267-7dce4c44ad24
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f977c30f1f4d6db7ce165de8483c8fd1977922d8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-set-ide-accessibility-options"></a>Porady: Ustawianie opcji ułatwień dostępu IDE

> [!TIP]
> Aby dowiedzieć się więcej o najnowszych aktualizacji ułatwień dostępu, zobacz [ulepszenia ułatwień dostępu w programie Visual Studio 2017 wersji 15 ustęp 3](https://blogs.msdn.microsoft.com/visualstudio/2017/08/14/accessibility-improvements-in-visual-studio-2017-version-15-3/) wpis w blogu.

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zawiera funkcje, które ułatwiają dla osób, które mają słabym wzrokiem do odczytu i osób o ograniczonej sprawności ruchowej, aby zapisać. Te funkcje obejmują, zmienianie rozmiaru i koloru tekstu w edytorach, zmiana rozmiaru tekstu i przyciski na paski narzędzi i autouzupełniania metod i parametrów, kilka.

 Ponadto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] obsługuje układów klawiatury Dvoraka, które najczęściej wpisane znaki dostęp. Można również dostosować dostępnych z klawiszy skrótów domyślne [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Aby uzyskać więcej informacji, zobacz [zidentyfikowanie i dostosowywanie skrótów klawiaturowych](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="editors-dialogs-and-tool-windows"></a>Edytory, okna dialogowe i okna narzędzi

 Domyślnie, okna dialogowe i okien narzędzi w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] używać tego samego rozmiaru czcionki i kolory jako systemu operacyjnego. Ustawienia kolorów dla ramki IDE, okna dialogowe, pasków narzędzi i okien narzędzi są oparte schemat kolorów: jasny lub ciemny. Można zmienić bieżącego motywu kolorów w [ogólne, środowisko, opcje — Okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md).

 Można także wyświetlić wyskakujących okienek w widok kodu edytora. Okna te można monit z dostępnych elementów członkowskich w bieżący obiekt i parametrów do wykonania instrukcji lub funkcji. Okna te mogą być przydatne, jeśli masz problemy z pisaniem. Jednak zakłócają fokusu w edytorze kodu, który może być problemów w przypadku niektórych użytkowników. Można wyłączyć te okna, otwierając okno dialogowe Opcje i wyczyszczenie **automatyczna lista członków** i **informacje o parametrach** w **Edytor tekstu**, **wszystkie Języki**, **ogólne** strony **opcje** okno dialogowe.

 Możesz zmienić kolejność w zintegrowane środowisko programistyczne (IDE) z własnymi sposobu pracy systemu windows. Można dock, float, Ukryj lub ukrywać każdego okna narzędzia.

 Aby uzyskać więcej informacji na temat zmiany układów okien, zobacz [dostosowywanie układów okien](../../ide/customizing-window-layouts-in-visual-studio.md).

### <a name="changing-the-size-of-text"></a>Zmiana rozmiaru tekstu

 Można zmienić ustawienia dla okien narzędzi tekstowych, takich jak **polecenia** okna, **Immediate** okno i **dane wyjściowe** okna w **czcionek i Kolory** okienku **środowiska** opcje w **narzędzia** okno dialogowe. Gdy **[wszystkie okna narzędzi tekstu]** wybrano **Pokaż ustawienia dla** listy rozwijanej domyślne ustawienie jest określone jako **domyślne** w **pierwszego planu elementu**  i **tła elementu** list rozwijanych. Możesz również zmienić ustawienia do wyświetlania tekstu w edytorze.

##### <a name="to-change-the-size-of-text-in-text-based-tool-windows-and-editors"></a>Aby zmienić rozmiar tekstu w okna narzędzi tekstowych i Redaktorzy

1.  Z **narzędzia** menu, wybierz **opcje**.

2.  Wybierz **czcionki i kolory** na **środowiska** folderu.

3.  Wybierz opcję na **Pokaż ustawienia dla** menu rozwijanego.

     Aby zmienić rozmiar czcionki tekstu w edytorze, wybierz **Edytor tekstu**.

     Aby zmienić rozmiar czcionki tekstu w okna narzędzi tekstowych, wybierz **[wszystkie okna narzędzi tekstu]**.

     Aby zmienić rozmiar czcionki tekstu etykietki narzędzia w edytorze, wybierz **Tooltip edytor**.

     Aby zmienić rozmiar czcionki tekstu w wyskakujące okienka uzupełniania instrukcji, wybierz **uzupełniania**.

4.  Z **wyświetlania elementów**, wybierz pozycję **zwykły tekst**.

5.  W **czcionki**, wybierz nowy typ czcionki.

6.  W **rozmiar**, wybierz nowy rozmiar czcionki.

    > [!NOTE]
    >  Aby zresetować rozmiar okna narzędzi tekstowych i edytory, wybierz **Użyj ustawień domyślnych**.

7.  Wybierz **OK**.

### <a name="change-the-colors-that-are-used-in-the-ide"></a>Zmienianie kolorów, które są używane w środowisku IDE

 Można również zmienić kolory domyślne tekstu, wskaźniki margines biały znak i elementy kodu w edytorze.

> [!NOTE]
> Aby użyć dużego kontrastu kolorów dla wszystkich aplikacji systemu windows w systemie operacyjnym, naciśnij klawisz lewej **ALT +** lewej **SHIFT + PRINT SCREEN**. Jeśli [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jest otworzyć, zamknij i otwórz ponownie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] do pełnego wdrożenia duży kontrast kolorów.


##### <a name="to-change-the-color-of-items-in-the-editor"></a>Aby zmienić kolor elementów w edytorze

1.  Z **narzędzia** menu, wybierz **opcje**.

2.  W **środowiska** folderu, wybierz **czcionki i kolory**.

3.  W **Pokaż ustawienia dla**, wybierz **Edytor tekstu**.

4.  Z **wyświetlania elementów**, wybierz element, którego ekran, musisz zmienić, takich jak **zwykły tekst**, **wskaźnik marginesu**, **widoczne biały znak**, **Nazwa atrybutu HTML**, lub **atrybutu XML**.

5.  Wybierz ustawienia następujące opcje wyświetlania: **pierwszego planu elementu**, **tła elementu**, i **Bold**.

6.  Wybierz **OK**.

## <a name="toolbars"></a>Paski narzędzi

 Aby poprawić użyteczność narzędzi i ułatwień dostępu, można dodać tekstu do przycisków paska narzędzi.

#### <a name="to-assign-text-to-toolbar-buttons"></a>Aby przypisać tekst do przycisków paska narzędzi

1.  Z **narzędzia** menu, wybierz **Dostosuj**.

2.  W **Dostosuj** okno dialogowe, wybierz opcję **polecenia** kartę.

3.  Wybierz **narzędzi** , a następnie wybierz nazwę narzędzi, która zawiera chcesz wyświetlić tekst dla przycisku.

4.  Na liście wybierz polecenie, które chcesz zmienić.

5.  Wybierz **Modyfikuj zaznaczenie**.

6.  Wybierz **obraz i tekst**.

#### <a name="to-modify-the-displayed-text-in-a-button"></a>Aby zmodyfikować wyświetlanego tekstu w przycisku

1.  Wybierz ponownie **Modyfikuj zaznaczenie**.

2.  Sąsiadujące w **nazwa**, Wstaw Podaj nowy podpis dla przycisku.

## <a name="see-also"></a>Zobacz także

* [Funkcje ułatwień dostępu programu Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)
* [Zasoby do projektowania dostępnych aplikacji](../../ide/reference/resources-for-designing-accessible-applications.md)
