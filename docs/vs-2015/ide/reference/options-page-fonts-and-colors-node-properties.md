---
title: Strona opcji, czcionki i kolory — właściwości węzła | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Tools Options settings, Fonts and Colors node properties
- automation [Visual Studio], controlling Tools Options
ms.assetid: 8e1ab784-5f85-4e2b-8ef9-e5d59ca4dbcb
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 18524cb3b27a05763187b9d5567d127af39c25d3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42694043"
---
# <a name="options-page-fonts-and-colors-node-properties"></a>Strona opcji, czcionki i kolory — Właściwości węzła
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [Strona opcji, czcionki i kolory — właściwości węzła](https://docs.microsoft.com/visualstudio/ide/reference/options-page-fonts-and-colors-node-properties).  
  
  
Ten dokument zawiera opis właściwości czcionek i kolorów dla okna narzędzi, które jest zarejestrowana w celu są wyświetlane w obszarze **czcionki i kolory** w **środowiska** kategorii **opcje** okno dialogowe. Obejmuje to obsługę dynamiczny charakter grup z możliwością kolorowania elementów, które można zmienić w przypadku instalowania lub odinstalowywania pakietów VSPackage.  
  
 W poniższej sekcji pokazano przykład typu zarejestrowanych okna i właściwości, które są dostępne dla każdego okna.  
  
## <a name="text-editor-or-printer-or-dialogs-and-tool-windows"></a>Edytor tekstu lub drukarki lub oknami dialogowymi i narzędzie Windows  
 `DTE.Properties("FontsAndColors", "TextEditor")`  
  
 —lub—  
  
 `DTE.Properties("FontsAndColors", "Printer")`  
  
 —lub—  
  
 `DTE.Properties("FontsAndColors", "Dialogs and Tool Windows")`  
  
|Nazwa elementu właściwości|Wartość|Opis|  
|------------------------|-----------|-----------------|  
|fontFamily|Get/Set (ciąg)|Nazwa czcionki do użycia, takie jak "Courier New."|  
|FontCharacterSet|Get/Set (<xref:EnvDTE.vsFontCharSet>)|A <xref:EnvDTE.vsFontCharSet> określająca typ znaku skonfigurowany do używania takich jak hebrajski lub rosyjski.|  
|FontSize|Get/Set (krótki)|Rozmiar czcionki do użycia w punktach. Na przykład 10 lub 12.|  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolowanie ustawień opcji](http://msdn.microsoft.com/library/a09ed242-7494-4cde-bbd1-7a8ec617965d)   
 [Określanie nazw elementów właściwości na stronach opcji](http://msdn.microsoft.com/library/d450422d-47c7-4eeb-9f9f-3286264bc5aa)   
 [Strona opcji, środowisko — właściwości węzła](../../ide/reference/options-page-environment-node-properties.md)   
 [Strona opcji, edytor tekstu — Właściwości węzła](../../ide/reference/options-page-text-editor-node-properties.md)



