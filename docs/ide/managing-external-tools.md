---
title: Zarządzanie narzędziami zewnętrznymi
ms.date: 11/20/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.externaltools
helpviewer_keywords:
- external tools [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eeeee2e6e7ae5d043124faaa79bc6bad7c527702
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="manage-external-tools"></a>Zarządzanie narzędziami zewnętrznymi

Można wywołać narzędzia zewnętrznego w programie Visual Studio za pomocą **narzędzia** menu. Kilka domyślne narzędzia są dostępne z **narzędzia** menu, a menu można dostosować, dodając inne pliki wykonywalne własny.

## <a name="tools-available-on-the-tools-menu"></a>Narzędzia dostępne w menu Narzędzia

**Narzędzia** menu zawiera kilka wbudowanych poleceń, takich jak:

* **Rozszerzenia i aktualizacje** do [Zarządzanie rozszerzeń programu Visual Studio](finding-and-using-visual-studio-extensions.md)
* **Menedżer wstawek kodu** do [organizowanie wstawki kodu](code-snippets.md)
* **Ochrona cenią sobie wcześniejsze — Dotfuscator** można uruchomić [Dotfuscator Community Edition (CE)](dotfuscator/index.md) przypadku [zainstalowany](dotfuscator/install.md)
* **Dostosuj** do [Dostosowywanie menu i pasków narzędzi](how-to-customize-menus-and-toolbars-in-visual-studio.md)
* **Opcje** do [ustawić szereg różnych opcji dla programu Visual Studio IDE i inne narzędzia](reference/options-dialog-box-visual-studio.md)

## <a name="add-new-tools-to-the-tools-menu"></a>Dodawanie nowych narzędzi do menu Narzędzia

Możesz dodać zewnętrznego narzędzia na **narzędzia** menu.

1. Otwórz **zewnętrznych narzędzi** okno dialogowe, wybierając **narzędzia** > **zewnętrznych narzędzi**.

1. Kliknij przycisk **Dodaj**, a następnie wypełnij informacje. Na przykład następujący wpis powoduje **Eksploratora Windows** można otworzyć w katalogu pliku aktualnie zainstalowana jest otwarty w programie Visual Studio:

   * Nazwa: `Open File Location`

   * polecenie: `explorer.exe`

   * Argumenty: `/root, "$(ItemDir)"`

   ![Okno dialogowe narzędzia zewnętrzne](media/external-tools-dialog.png)

Poniżej znajduje się pełna lista argumentów, które mogą być używane podczas definiowania zewnętrznego narzędzia:

|Nazwa|Argument|Opis|
|----------|--------------|-----------------|
|Ścieżka elementu|$(ItemPath)|Pełnej nazwy pliku bieżącego pliku (dysk + ścieżka pliku nazwy).|
|Element katalogu|$(ItemDir)|Katalog bieżącego pliku (dysk + ścieżki).|
|Nazwa pliku elementu|$(ItemFilename)|Nazwa pliku bieżącego pliku (nazwa pliku).|
|Rozszerzenia elementu|$(ItemExt)|Rozszerzenie nazwy pliku bieżącego pliku.|
|Bieżący wiersz|$(CurLine)|Bieżącej pozycji kursora w oknie kodu.|
|Bieżącej kolumny|$(CurCol)|Bieżąca kolumna pozycja kursora w oknie kodu.|
|Tekst|$(CurText)|Zaznaczonego tekstu.|
|Ścieżka docelowa|$(Targetpath) —|Pełnej nazwy pliku elementu, który ma zostać utworzony (dysk + ścieżka pliku nazwy).|
|Katalog docelowy|$(Targetdir) —|Katalog elementu, który ma zostać utworzony.|
|Nazwa obiektu docelowego|$(TargetName)|Nazwa pliku elementu, który ma zostać utworzony.|
|Rozszerzenie docelowego|$(TargetExt)|Rozszerzenie nazwy pliku elementu, który ma zostać utworzony.|
|Katalog danych binarnych|$(BinDir)|Lokalizacji końcowej pliku binarnego budowanego (zdefiniowany jako dysk + ścieżki).|
|Katalog projektu|$(ProjDir)|Katalog bieżącego projektu (dysk + ścieżki).|
|Nazwa pliku projektu|$(ProjFileName)|Nazwa pliku bieżącego projektu (dysk + ścieżka pliku nazwy).|
|Katalog rozwiązań|$(SolutionDir)|Katalog bieżącego rozwiązania (dysk + ścieżki).|
|Nazwa pliku rozwiązania|$(SolutionFileName)|Nazwa pliku bieżącego rozwiązania (dysk + ścieżka pliku nazwy).|

> [!NOTE]
> Wyświetla pasek stanu IDE **bieżącego wiersza** i **bieżącej kolumny** zmienne, aby wskazać, gdy punkt wstawiania znajduje się w aktywne **edytora kodu**. **Tekst** zmiennej zwraca tekst lub wybrane w tej lokalizacji kodu.

## <a name="see-also"></a>Zobacz także

- [Narzędzia kompilacji C/C++](/cpp/build/reference/c-cpp-build-tools)
