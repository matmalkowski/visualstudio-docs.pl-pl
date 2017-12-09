---
title: Preferencje styl kodu programu Visual Studio | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 03/10/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.openlocfilehash: 24470f4fdb1a75d6ebd2743b2ade72e6195842b4
ms.sourcegitcommit: ebe9fb5eda724936f7a059d35d987c29dffdb50d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2017
---
# <a name="code-style-preferences"></a>Preferencje styl kodu

Można ustawić preferencje styl kodu dla projektów C# i Visual Basic, otwierając **opcje** okno dialogowe z **narzędzia** menu. Wybierz **Edytor tekstu**, **C#** lub **podstawowe**, **kodu stylu**, **ogólne**. Opcje ustawione w tym oknie są stosowane do komputera lokalnego. Każdy element na liście zostaną wyświetlone Podgląd preferencji, gdy zaznaczone, jak pokazano poniżej.

![Opcje stylu kodu](media/code-style-quick-actions-dialog.png)

Dla każdego elementu, można ustawić **preferencji** i **ważność** przy użyciu listy rozwijane w każdym wierszu. Można ustawić ważność **Brak**, **sugestię**, **ostrzeżenie**, lub **błąd**, i Visual Studio będzie działać prawidłowo. Jeśli chcesz użyć [szybkie akcje](quick-actions.md) przy użyciu tych stylów kodu do automatycznego ponownego pisania kodu do preferowanego stylu, upewnij się, że ustawienie ma wartość coś innego niż **Brak** więc ikoną żarówki ![Małych ikon żarówki](media/vs2015_lightbulbsmall.png "VS2017_LightBulbSmall") będą wyświetlane, gdy style innymi niż preferowane są używane. Preferencje te można następnie może odnosić się ikoną żarówki klikając lub naciskając klawisz **Ctrl +.** gdy kursor znajduje się na odpowiedni wiersz kodu.

Kod ustawień stylu dla platformy .NET można także zarządzać za pomocą [EditorConfig](../ide/editorconfig-code-style-settings-reference.md) pliku. W takim przypadku ustawienia w pliku EditorConfig pierwszeństwo opcje wybrane w **opcje** okno dialogowe. Plik EditorConfig służy do wymuszania i skonfiguruj styl kodowania całe repozytorium lub projektu.

## <a name="see-also"></a>Zobacz także

[Szybkie akcje](quick-actions.md)  
[Ustawienia EditorConfig Konwencji kodowania platformy .NET](../ide/editorconfig-code-style-settings-reference.md)