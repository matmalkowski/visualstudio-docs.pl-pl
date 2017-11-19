---
title: "Strona opcji, czcionki i kolory — właściwości węzła | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tools Options settings, Fonts and Colors node properties
- automation [Visual Studio], controlling Tools Options
ms.assetid: 8e1ab784-5f85-4e2b-8ef9-e5d59ca4dbcb
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0c2618dbaad3fcae95219e2b6a8a1f9b3d87bf09
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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
 [Kontrolowanie opcji ustawienia](http://msdn.microsoft.com/Library/a09ed242-7494-4cde-bbd1-7a8ec617965d)   
 [Określanie nazwy właściwości elementów na stronach opcje](http://msdn.microsoft.com/Library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)   
 [Strona opcji, środowisko — właściwości węzła](../../ide/reference/options-page-environment-node-properties.md)   
 [Strona opcji, Edytor tekstu — właściwości węzła](../../ide/reference/options-page-text-editor-node-properties.md)