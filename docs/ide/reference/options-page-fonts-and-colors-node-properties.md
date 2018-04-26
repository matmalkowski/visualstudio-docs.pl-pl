---
title: Strona opcji, czcionki i kolory — Właściwości węzła
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Tools Options settings, Fonts and Colors node properties
- automation [Visual Studio], controlling Tools Options
ms.assetid: 8e1ab784-5f85-4e2b-8ef9-e5d59ca4dbcb
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5cf39d9a01794e34a50d81489214bb006e4c6448
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="options-page-fonts-and-colors-node-properties"></a>Strona opcji, czcionki i kolory — Właściwości węzła
Ten dokument zawiera opis właściwości czcionek i kolorów dla okna narzędzia, która jest zarejestrowana są wyświetlane w obszarze **czcionki i kolory** w **środowiska** kategorii **opcje** okno dialogowe. W ten sposób realizowany dynamiczny charakter grup colorable elementów, które można zmienić, jeśli pakiety VSPackage są zainstalowane lub odinstalowane.

 Poniższej sekcji przedstawiono przykład typu zarejestrowanych okna i właściwości, które są dostępne dla każdego okna.

## <a name="text-editor-or-printer-or-dialogs-and-tool-windows"></a>Edytor tekstu lub drukarki lub okien dialogowych i okien narzędzi
 `DTE.Properties("FontsAndColors", "TextEditor")`

 —lub—

 `DTE.Properties("FontsAndColors", "Printer")`

 —lub—

 `DTE.Properties("FontsAndColors", "Dialogs and Tool Windows")`

|Nazwa elementu właściwości|Wartość|Opis|
|------------------------|-----------|-----------------|
|FontFamily|Pobierz/Ustaw (ciąg)|Nazwa czcionki do użycia, takie jak "Courier New."|
|FontCharacterSet|Pobierz/Ustaw (<xref:EnvDTE.vsFontCharSet>)|A <xref:EnvDTE.vsFontCharSet> określająca typ zestaw znaków używany, takich jak hebrajski lub rosyjski.|
|FontSize|Pobierz/Ustaw (Short)|Rozmiar czcionki do użycia w punktach. Na przykład, 10 lub 12.|

## <a name="see-also"></a>Zobacz też

- [Kontrolowanie opcji ustawienia](http://msdn.microsoft.com/Library/a09ed242-7494-4cde-bbd1-7a8ec617965d)
- [Określanie nazwy właściwości elementów na stronach opcje](http://msdn.microsoft.com/Library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)
- [Strona opcji, środowisko — Właściwości węzła](../../ide/reference/options-page-environment-node-properties.md)
- [Strona opcji, edytor tekstu — Właściwości węzła](../../ide/reference/options-page-text-editor-node-properties.md)