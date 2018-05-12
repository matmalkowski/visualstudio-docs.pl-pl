---
title: Preferencje styl kodu programu Visual Studio
ms.date: 03/10/2017
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 6dd046fa8a01cde7abdc33484da3ff8227eda966
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/11/2018
---
# <a name="code-style-preferences"></a>Preferencje styl kodu

Można ustawić preferencje styl kodu dla projektów C# i Visual Basic, otwierając **opcje** okno dialogowe z **narzędzia** menu. Wybierz **Edytor tekstu** > **C#** lub **podstawowe** > **kodu stylu**  >   **Ogólne**. Opcje ustawione w tym oknie są stosowane do komputera lokalnego.

Każdy element na liście Podgląd preferencji, w przypadku wybrania:

![Opcje stylu kodu](media/code-style-quick-actions-dialog.png)

## <a name="preference-and-severity"></a>Preferencji i ważność

Dla każdego elementu, można ustawić **preferencji** i **ważność** wartości przy użyciu listy rozwijane w każdym wierszu. Można ustawić ważność **Brak**, **sugestię**, **ostrzeżenie**, lub **błąd**. Jeśli chcesz włączyć [szybkie akcje](../ide/quick-actions.md) stylu kodu, upewnij się, że **ważność** mają ustawioną wartość coś innego niż **Brak**. Szybkie akcje ikoną żarówki ![małych ikon żarówki](media/vs2015_lightbulbsmall.png) apspear, gdy jest używany styl innymi niż preferowane i konieczne jest wybranie opcji na liście Szybkie akcje do automatycznego ponownego pisania kodu do preferowanego stylu.

## <a name="editorconfig-files"></a>Pliki EditorConfig

Kod ustawień stylu dla platformy .NET można także zarządzać za pomocą [EditorConfig](../ide/editorconfig-code-style-settings-reference.md) pliku. Ustawienia w pliku EditorConfig mają pierwszeństwo przed opcje wybrane w **opcje** okno dialogowe. Plik EditorConfig służy do wymuszania i skonfiguruj styl kodowania całe repozytorium lub projektu.

## <a name="see-also"></a>Zobacz także

- [Szybkie akcje](../ide/quick-actions.md)
- [Ustawienia EditorConfig Konwencji kodowania platformy .NET](../ide/editorconfig-code-style-settings-reference.md)