---
title: Style i szybkie akcje kodu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 03/10/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: 25bb9d99-aeff-4053-925d-2177f5e79574
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.openlocfilehash: d42bb9165748b7282aa42f062b545add62ad1c93
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="code-styles-and-quick-actions"></a>Style kodu i szybkie akcje
Można ustawić preferencje styl kodu dla projektów C# i Visual Basic, otwierając **Narzędzia > Opcje** okna, a następnie wybierając **Edytor tekstu > C# / podstawowe > Styl kodu > Ogólne**.  Opcje ustawione w tym oknie są stosowane do komputera lokalnego.  Każdy element na liście zostaną wyświetlone Podgląd preferencji, gdy zaznaczone, jak pokazano poniżej.

![Opcje stylu kodu](media/code-style-quick-actions-dialog.png)

Dla każdego elementu, można ustawić **preferencji** i **ważność** przy użyciu listy rozwijane w każdym wierszu.  Można ustawić ważność **Brak**, **sugestię**, **ostrzeżenie**, lub **błąd**, i Visual Studio będzie działać prawidłowo.  Jeśli chcesz użyć [szybkie akcje](quick-actions.md) przy użyciu tych stylów kodu do automatycznego ponownego pisania kodu do preferowanego stylu, upewnij się, że ustawienie ma wartość coś innego niż **Brak** więc ikoną żarówki ![Małych ikon żarówki](media/vs2015_lightbulbsmall.png "VS2017_LightBulbSmall") będą wyświetlane, gdy style innymi niż preferowane są używane.  Preferencje te można następnie może odnosić się ikoną żarówki klikając lub naciskając klawisz **Ctrl +.** gdy kursor znajduje się na odpowiedni wiersz kodu.

Kod ustawień stylu dla platformy .NET można także zarządzać za pomocą [EditorConfig](editorconfig-code-style-settings-reference.md) pliku.  W takim przypadku ustawienia wybrane w oknie Opcje będzie przełączanie awaryjne z plikiem EditorConfig biorąc pierwszeństwo.  Ten plik służy do wymuszania i skonfiguruj styl kodowania całe repozytorium lub zespołu.

## <a name="see-also"></a>Zobacz też
* [Szybkie akcje](quick-actions.md)