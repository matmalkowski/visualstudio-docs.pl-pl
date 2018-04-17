---
title: Preferencje styl kodu programu Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/10/2017
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload:
- multiple
ms.openlocfilehash: 4898a2e4a55f5c11179ae5a00e46c87a44519a7b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="code-style-preferences"></a>Preferencje styl kodu

Można ustawić preferencje styl kodu dla projektów C# i Visual Basic, otwierając **opcje** okno dialogowe z **narzędzia** menu. Wybierz **Edytor tekstu** > **C#** lub **podstawowe** > **kodu stylu**  >   **Ogólne**. Opcje ustawione w tym oknie są stosowane do komputera lokalnego. Każdy element na liście zostaną wyświetlone Podgląd preferencji, gdy zaznaczone, jak pokazano poniżej.

![Opcje stylu kodu](media/code-style-quick-actions-dialog.png)

Dla każdego elementu, można ustawić **preferencji** i **ważność** wartości przy użyciu listy rozwijane w każdym wierszu. Można ustawić ważność **Brak**, **sugestię**, **ostrzeżenie**, lub **błąd**. Jeśli chcesz włączyć [szybkie akcje](../ide/quick-actions.md) stylu kodu, upewnij się, że **ważność** mają ustawioną wartość coś innego niż **Brak**. Szybkie akcje ikoną żarówki ![małych ikon żarówki](media/vs2015_lightbulbsmall.png) będą wyświetlane, gdy jest używany styl innymi niż preferowane i konieczne jest wybranie opcji na liście Szybkie akcje do automatycznego ponownego pisania kodu do preferowanego stylu.

Kod ustawień stylu dla platformy .NET można także zarządzać za pomocą [EditorConfig](../ide/editorconfig-code-style-settings-reference.md) pliku. W takim przypadku ustawienia w pliku EditorConfig pierwszeństwo opcje wybrane w **opcje** okno dialogowe. Plik EditorConfig służy do wymuszania i skonfiguruj styl kodowania całe repozytorium lub projektu.

### <a name="see-also"></a>Zobacz także

[Szybkie akcje](../ide/quick-actions.md)  
[Ustawienia EditorConfig Konwencji kodowania platformy .NET](../ide/editorconfig-code-style-settings-reference.md)