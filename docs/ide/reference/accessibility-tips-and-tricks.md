---
title: "I porady dotyczące ułatwień dostępu dla programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 09/15/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: accessibility [Visual Studio]
ms.assetid: 6b491d88-f79e-4686-8841-857624bdcfda
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4cfc07cb77e1db595d1b381b1097dcfcba0abdab
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="accessibility-tips-and-tricks-for-visual-studio"></a>I porady dotyczące ułatwień dostępu dla programu Visual Studio
> [!TIP]
> Aby dowiedzieć się więcej o najnowszych aktualizacji ułatwień dostępu, zobacz [ulepszenia ułatwień dostępu w programie Visual Studio 2017 wersji 15 ustęp 3](https://blogs.msdn.microsoft.com/visualstudio/2017/08/14/accessibility-improvements-in-visual-studio-2017-version-15-3/) wpis w blogu.

Visual Studio ma wbudowanych funkcji ułatwień dostępu są zgodne z czytników ekranu i innych technologii pomocniczych. W tym temacie wymieniono typowe kombinacje klawiszy skrótu można używać do wykonywania zadań za pomocą klawiatury tylko i zawiera informacje dotyczące używania motywów dużego kontrastu do poprawy widoczności. Również przedstawia sposób użycia adnotacje do ujawniania przydatne informacje na temat kodu i jak ustawić dźwięku wskaźniki kompilacji i przerwania zdarzenia.

## <a name="save-your-ide-settings"></a>Zapisz ustawienia IDE  
 Zapisywanie układu okna, schemat mapowania klawiatury i inne preferencje można dostosować środowiska IDE. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  

## <a name="modify-your-ide-for-high-contrast-viewing"></a>Modyfikowanie środowiskiem IDE w celu wyświetlenia dużego kontrastu
Dla niektórych pracowników niektóre kolory są trudne do Zobacz. Jeśli mają więcej kontrastu jako kod można, ale nie chcesz używać Typowe motywy "Duży kontrast", firma Microsoft oferuje teraz motywu "Niebieski (dodatkowy kontrastu)".

  ![Porównanie motywu niebieski i motyw niebieski kontrastu dodatkowe](media/blue-extra-contrast-theme.png "widocznej różnicy między motywu niebieski i motyw niebieski dodatkowe kontrast")

## <a name="use-annotations-to-reveal-useful-information-about-your-code"></a>Umożliwia ujawnienie przydatnych informacji o kodzie adnotacji

Edytor programu Visual Studio zawiera wiele tekst "skojarzenia" umożliwiające wiedzieć o cechy i funkcje w punktach określonego wiersza kodu, takie jak lightbulbs, błąd i ostrzeżenie "zygzaki" zakładki i tak dalej. Możesz użyć polecenia "Pokaż linii adnotacji" Ustaw ułatwiają odnajdywanie, a następnie przejdź między tymi skojarzenia.

  ![Użyj zestawu poleceń Pokaż linii adnotacji](media/show-line-annotations-command-set.png "przedstawiono sposób ustawiania zestawu poleceń Pokaż linii adnotacji")

## <a name="access-toolbars-by-using-shortcut-key-combinations"></a>Paski narzędzi dostępu przy użyciu kombinacji klawiszy skrótów
Środowiska IDE programu Visual Studio ma paski narzędzi, jak wiele okien narzędzi. Następujące kombinacje klawiszy skrótu pomóc uzyskiwać do nich dostęp.

|Funkcja|Opis|Kombinacja klawiszy|  
|-------------|-----------------|---------------------|  
|Paski narzędzi IDE|Kliknij pierwszy przycisk na standardowym pasku narzędzi.|**ALT**, **CTRL** + **KARTĘ**|  
|Paski narzędzi okna narzędzi|Przenieś fokus na paskach narzędzi w oknie narzędzia. <br> <br> **Uwaga:** działa to w przypadku większości okien narzędzi, ale tylko wtedy, gdy fokus w oknie narzędzia. Ponadto musisz wybrać klawisz SHIFT przed klawisza ALT. W niektórych okien narzędzi, takich jak Team Explorer musi przytrzymaj klawisz SHIFT, na chwilę przed wybraniem klawisza ALT.|**SHIFT** + **ALT**|
|Paski narzędzi|Przejdź do pierwszego elementu w pasku narzędzi dalej (po aktywowaniu paska narzędzi).|**CTRL** + **KARTĘ**|

### <a name="other-useful-shortcut-key-combinations"></a>Kombinacje klawiszy skrótów przydatne  
Oto niektóre inne przydatne kombinacje klawiszy skrótu.

|Funkcja|Opis|Kombinacja klawiszy|  
|-------------|-----------------|---------------------|  
|IDE|Przełącz duży kontrast, włączać i wyłączać. <br> <br> **Uwaga:** skrót standardowych systemu Windows|**ALT + Left SHIFT + PRINT SCREEN w lewo**|  
|Okno dialogowe|Wybierz lub wyczyść pole wyboru opcji w oknie dialogowym. <br> <br> **Uwaga:** skrót standardowych systemu Windows|**SPACJA**|  
|Menu kontekstowe|Otwórz menu kontekstowe (kliknij prawym przyciskiem myszy). <br> <br> **Uwaga:** skrót standardowych systemu Windows|**SHIFT** + **F10**|
|Menu|Szybki dostęp do elementu menu przy użyciu jego klawiszy skrótów. Wybierz **ALT** klucza następuje podkreślone litery w menu, aby uaktywnić to polecenie. Na przykład, aby wyświetlić okno dialogowe Otwórz projekt w programie Visual Studio, możesz wybrać **ALT** + **F** + **O**  +  **P**.  <br><br> **Uwaga:** skrót standardowych systemu Windows|**ALT** + **[list]**|
|Okno przybornika|Przenoszenie między kartami przybornika.|**CTRL** + **UPARROW**<br /><br /> and<br /><br /> **CTRL** + **DOWNARROW**|  
|Okno przybornika|Dodaj formant z przybornika do formularza lub projektanta.|**WPROWADŹ**|  
|Klawiatura, środowisko, opcje — Okno dialogowe|Usuń kombinację klawiszy w **klawiszy skrótów** opcji.|**BACKSPACE**|  

> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.  


## <a name="use-the-sound-applet-to-set-build-and-breakpoint-cues"></a>Użyj apletu dźwięku, aby ustawić wskaźników kompilacji i punktu przerwania
Aplet dźwięku w systemie Windows umożliwia przypisać dźwięk do zdarzenia programu Visual Studio. W szczególności można przypisać dźwięki do następujących programów:

 * Trafienie punktu przerwania
 * Kompilacja anulowana
 * Budowanie nie powiodło się
 * Powodzenie kompilacji

Poniżej przedstawiono sposób.

1. W **wyszukiwania** pole na komputerze z systemem Windows 10, typ **Zmień dźwięki systemu**.

  ![Pole wyszukiwania w systemie Windows 10](media/type-here-to-search.png "polu Dźwięki typu do wyszukiwania na komputerze z systemem Windows 10")

  (Alternatywnie, jeśli włączono funkcję Cortana, powiedz "Witaj Cortana", a następnie powiedz "Zmień dźwięki systemu".)

2. Kliknij dwukrotnie **Zmień dźwięki systemu**.

  ![Wyniki wyszukiwania w systemie Windows 10](media/change-system-sounds.png "kliknij dwukrotnie pozycję Zmień dźwięki systemu w wynikach wyszukiwania")

3. W **dźwięk** okno dialogowe, kliknij przycisk **dźwięki** kartę. <br><br>
 Następnie w **zdarzenia programu**, przewiń do **programu Microsoft Visual Studio**i wybierz dźwięki, które chcesz zastosować do zdarzenia, które można wybrać.

  ![Dźwięki kartę dźwiękową apletu w systemie Windows 10](media/sound-applet.png "kliknij dwukrotnie pozycję Zmień dźwięki systemu w wynikach wyszukiwania")

4. Kliknij przycisk **OK**.



## <a name="see-also"></a>Zobacz także  
* [Ułatwienia dostępu w Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)
  * [Instrukcje: Dostosowywanie menu i pasków narzędzi w programie Visual Studio](../../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
* [Personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
* [Ułatwienia dostępu firmy Microsoft](https://www.microsoft.com/Accessibility)
