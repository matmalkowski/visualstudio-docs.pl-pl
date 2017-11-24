---
title: "Zarządzanie narzędziami zewnętrznymi | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/20/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.externaltools
helpviewer_keywords: external tools [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 65cd18ea74ced278d53841cb8204f7cc4d163dc3
ms.sourcegitcommit: eb954434c34b4df6fd2264266381b23ce9e6204a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2017
---
# <a name="manage-external-tools"></a>Zarządzanie narzędziami zewnętrznymi

Można wywołać narzędzia zewnętrznego w programie Visual Studio za pomocą **narzędzia** menu. Kilka domyślne narzędzia są dostępne z **narzędzia** menu, a menu można dostosować, dodając inne pliki wykonywalne własny.

## <a name="tools-available-on-the-visual-studio-tools-menu"></a>Narzędzia dostępne w menu programu Visual Studio Tools

**Narzędzia** menu zawiera kilka wbudowanych poleceń, takich jak:

* **Rozszerzenia i aktualizacje** dla [Zarządzanie rozszerzenia programu Visual Studio](finding-and-using-visual-studio-extensions.md)
* **Menedżer wstawek kodu...**  dla [organizowanie wstawki kodu](code-snippets.md#code-snippet-manager)
* **Ochrona cenią sobie wcześniejsze — Dotfuscator** uruchomienie [Dotfuscator Community Edition (CE)](dotfuscator/index.md) Jeśli jest [zainstalowany](dotfuscator/install.md)
* **Dostosuj...**  dla [Dostosowywanie menu i pasków narzędzi](how-to-customize-menus-and-toolbars-in-visual-studio.md)
* **Opcje...**  dla [ustawienie szereg różnych opcji dla programu Visual Studio IDE i inne narzędzia](reference/options-dialog-box-visual-studio.md)

## <a name="add-new-tools-to-the-tools-menu"></a>Dodawanie nowych narzędzi do menu Narzędzia

Możesz dodać zewnętrznego narzędzia na **narzędzia** menu.

1. Otwórz **zewnętrznych narzędzi** okno dialogowe, wybierając **narzędzia**, **zewnętrznych narzędzi...** .

1. Kliknij przycisk **Dodaj**, a następnie wypełnij informacje. Na przykład następujący wpis powoduje Eksploratora Windows, aby otworzyć znajduje się w katalogu pliku, który aktualnie otwarte w programie Visual Studio:

   * Nazwa:`Open File Location`

   * Polecenie:`explorer.exe`

   * Argumenty:`/root, "$(ItemDir)"`

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
|Nazwa pliku rozwiązania|$(Solutionfilename) —|Nazwa pliku bieżącego rozwiązania (dysk + ścieżka pliku nazwy).|

> [!NOTE]
> Pasek stanu IDE przedstawia zmienne bieżącego wiersza i bieżącej kolumny, aby wskazać, gdy punkt wstawiania znajduje się w edytorze kodu active. Zmienna tekst zwraca tekst lub wybrane w tej lokalizacji kodu.

## <a name="see-also"></a>Zobacz także

[Narzędzia kompilacji C/C++](/cpp/build/reference/c-cpp-build-tools)
