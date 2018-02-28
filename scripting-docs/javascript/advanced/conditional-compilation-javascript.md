---
title: Kompilacja warunkowa (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ConditionalComp_JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- conditional compilation, overview
- conditional compilation
ms.assetid: a843de4e-3aae-43cd-ad64-477dd00814a2
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6d6a5987b21afcab8c62a609dfba33f963d544de
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="conditional-compilation-javascript"></a>Kompilacja warunkowa (JavaScript)
Kompilacja warunkowa zezwala na korzystanie z nowych [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] — funkcje językowe bez ograniczania zgodności z poprzednimi wersjami, które nie obsługują funkcji.  
  
> [!WARNING]
>  Kompilacja warunkowa jest obsługiwana we wszystkich wersjach programu Internet Explorer wcześniejszych niż Internet Explorer 11. Uruchamianie w trybie standardów programu Internet Explorer 11 oraz w [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplikacje, kompilacja warunkowa nie jest obsługiwane.  
  
## <a name="statements"></a>Instrukcje  
 Kompilacja warunkowa jest aktywowany przy użyciu `@cc_on` instrukcji lub przy użyciu `@if` lub `@set` instrukcji. Niektóre typowe zastosowania kompilacja warunkowa obejmują korzystać z nowych funkcji w [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], obsługę debugowania w skrypcie osadzanie i śledzenie realizacji kodu.  
  
 Zawsze umieszczaj kod kompilacji warunkowej w komentarzach, tak aby hosty (jak Netscape Navigator), które nie obsługują kompilacji warunkowej, ignorowały go. Oto przykład.  
  
```JavaScript  
/*@cc_on @*/  
/*@if (@_jscript_version >= 4)  
    alert("JavaScript version 4 or better");  
    @else @*/  
    alert("Conditional compilation not supported by this scripting engine.");  
/*@end @*/  
```  
  
 W tym przykładzie użyto ograniczników do komentarzy specjalne, które są używane tylko wtedy, gdy kompilacja warunkowa jest aktywowany przez `@cc_on` instrukcji. Aparaty skryptów, które nie obsługują kompilacji warunkowej, znajdują jedynie komunikat informujący o tym, że kompilacja warunkowa nie jest obsługiwana.