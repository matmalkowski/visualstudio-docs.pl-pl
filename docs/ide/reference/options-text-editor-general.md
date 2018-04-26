---
title: Opcje, edytor tekstów, ogólne
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.TOOLSOPTIONSPAGES.TEXT_EDITOR.SQL_SERVER_TOOLS.GENERAL
- VS.ToolsOptionsPages.Text_Editor.All_Languages.General
- VS.ToolsOptionsPages.Text_Editor.RDL_Expression.General
- VS.ToolsOptionsPages.Text_Editor.SQL.General
- vs.toolsoptionspages.text_editor
- VS.ToolsOptionsPages.Text_Editor.XML.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL80.General
- VS.ToolsOptionsPages.Text_Editor.CSS
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.General
- VS.ToolsOptionsPages.Text_Editor.SQL_Script.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.General
- VS.ToolsOptionsPages.Text_Editor.All_Languages
- VS.ToolsOptionsPages.Text_Editor.T-SQL7.General
- VS.ToolsOptionsPages.Text_Editor.Basic.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL.General
- VS.ToolsOptionsPages.Text_Editor.F#.Tabs
- VS.ToolsOptionsPages.Text_Editor.F#
- VS.ToolsOptionsPages.Text_Editor.PL/SQL.General
- VS.ToolsOptionsPages.Text_Editor.C/C++.General
- VS.ToolsOptionsPages.Text_Editor.Plain_Text
- VS.ToolsOptionsPages.Text_Editor.HTML
- VS.ToolsOptionsPages.Text_Editor.XAML.General
- VS.ToolsOptionsPages.Text_Editor
- VS.ToolsOptionsPages.Text_Editor.F#.General
- VS.ToolsOptionsPages.Text_Editor.XOML.General
- VS.ToolsOptionsPages.Text_Editor.SQL
- vs.toolsoptionspages.text_editor.c/c++
- VS.ToolsOptionsPages.Text_Editor.SQL_Script
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.General
- VS.ToolsOptionsPages.Text_Editor.General
- VS.ToolsOptionsPages.Text_Editor.CSharp
- VS.ToolsOptionsPages.Text_Editor.Python
- VS.ToolsOptionsPages.Text_Editor.R
helpviewer_keywords:
- Text Editor Options dialog box
- Code Editor
- Text Editor [Visual Studio]
- editors, global settings
ms.assetid: 4ac21e48-3243-4141-9058-7eaf12b3cde7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 72a2abbfe1e410763822c44367a183d1d9ab8ab6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="options-text-editor-general"></a>Opcje, edytor tekstów, ogólne

To okno dialogowe umożliwia zmianę ustawienia globalne dla edytora kodu i tekstu Visual Studio. Aby wyświetlić to okno dialogowe, zaznacz **opcje** na **narzędzia** menu, rozwiń węzeł **Edytor tekstu** folder, a następnie wybierz **ogólne**.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="settings"></a>Ustawienia

### <a name="drag-and-drop-text-editing"></a>Przeciągnij i upuść edycji tekstu

Po wybraniu umożliwia przenoszenie tekstu, wybierając ją i przeciągając myszą do innej lokalizacji w ramach bieżącego dokumentu lub otwartego dokumentu.

### <a name="automatic-delimiter-highlighting"></a>Automatyczne wyróżnianie ogranicznika

Po wybraniu znaki ogranicznik, oddzielające parametry lub pary wartości elementu, a także pasujących nawiasów klamrowych, są wyróżnione.

### <a name="track-changes"></a>Śledzenie zmian

Po wybraniu edytora kodu pionowym wierszem żółty pojawia się w margines zaznaczania, aby oznaczyć kod, który zmienił się od czasu ostatniego został zapisany plik. Po zapisaniu zmian pionowych linii stają się zielony.

### <a name="auto-detect-utf-8-encoding-without-signature"></a>Autowykrywanie kodowania bez podpisu UTF-8

Domyślnie Edytor wykrywa kodowania, wyszukując znaczniki kolejności bajtów lub tagi zestawu znaków. Jeśli nie zostanie znaleziony w bieżącym dokumencie, edytora kodu próbuje Autowykrywanie kodowania UTF-8 przez zeskanowanie sekwencji bajtów. Aby wyłączyć automatyczne wykrywanie kodowania, usuń zaznaczenie tej opcji.

## <a name="display"></a>Monitor

### <a name="selection-margin"></a>Margines zaznaczania

Po wybraniu Wyświetla pionowego marginesu wzdłuż lewej krawędzi obszaru tekstu w edytorze. Możesz kliknąć ten margines, aby zaznaczyć cały wiersz tekstu, lub kliknij i przeciągnij, aby wybrać kolejnych wierszy tekstu.

|Margines zaznaczania na|Margines zaznaczania wyłączone|
|-------------------------|--------------------------|
|![HTMLpageSelectionMarginOn — zrzut ekranu](../../ide/reference/media/vxselmaron.gif "vxSelmaron")|![HTMLpageSelectionMarginOff — zrzut ekranu](../../ide/reference/media/vxselmaroff.gif "vxSelmaroff")|

### <a name="indicator-margin"></a>Margines wskaźnika

Po wybraniu Wyświetla pionowego marginesu poza lewą krawędzią obszaru tekstu w edytorze. Po kliknięciu tego marginesie są wyświetlane ikonę i etykietkę narzędzia, które są powiązane z tekstu. Na przykład punkt przerwania lub zadanie skróty listy są wyświetlane w margines wskaźnika. Wskaźnik marginesu informacji nie do drukowania.

### <a name="vertical-scroll-bar"></a>Pionowy pasek przewijania

Po wybraniu Wyświetla pionowy pasek przewijania, dzięki czemu można przewiń w górę i w dół do widoku elementy, które wykraczają poza obszar wyświetlania edytora. Jeśli pionowe paski przewijania nie są dostępne, można użyć Page Up, Page Down i klucze kursora do przewijania.

### <a name="horizontal-scroll-bar"></a>Poziomy pasek przewijania

Po wybraniu Wyświetla poziomy pasek przewijania, dzięki czemu można przewiń z bok Wyświetl elementy, które wykraczają poza obszar wyświetlania edytora. Jeśli poziomych pasków przewijania są niedostępne, można klawiszy strzałek przewijania.

### <a name="highlight-current-line"></a>Podświetlenie bieżącej linii

Po wybraniu Wyświetla szare pole w pobliżu wiersza kodu, w którym znajduje się kursor.

## <a name="see-also"></a>Zobacz także

- [Opcje, Edytor tekstu, wszystkie języki](../../ide/reference/options-text-editor-all-languages.md)
- [Opcje, Edytor tekstu, wszystkie języki, karty](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [Opcje, Edytor tekstu, rozszerzenie pliku](../../ide/reference/options-text-editor-file-extension.md)
- [Identyfikowanie i dostosowywanie skrótów klawiaturowych](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)
- [Dostosowywanie edytora](../../ide/customizing-the-editor.md)
- [Korzystanie z funkcji IntelliSense](../../ide/using-intellisense.md)