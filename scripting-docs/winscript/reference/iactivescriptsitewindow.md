---
title: IActiveScriptSiteWindow | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteWindow interface
ms.assetid: 96d5c493-2c0b-47e2-848b-4a8dacdcd65c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3043a3c36b2f1ebdf439f22b1de19dd559e50cfa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitewindow"></a>IActiveScriptSiteWindow
Ten interfejs jest implementowany przez hosty, które obsługuje interfejs użytkownika dla tego samego obiektu jako [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) . Hosty, które nie obsługują interfejsu użytkownika, takich jak serwery, nie może implementować `IActiveScriptSiteWindow` interfejsu. Aparat skryptów uzyskuje dostęp do tego interfejsu, wywołując `QueryInterface` z `IActiveScriptSite`.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptSiteWindow::GetWindow](../../winscript/reference/iactivescriptsitewindow-getwindow.md)|Pobiera uchwyt okna, które mogą działać jako właściciel okno podręczne wyświetlające musi aparatu skryptów.|  
|[IActiveScriptSiteWindow::EnableModeless](../../winscript/reference/iactivescriptsitewindow-enablemodeless.md)|Powoduje, że host włączyć lub wyłączyć jego okno główne, a także Niemodalne okna dialogowe.|  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy aktywnego skryptu](../../winscript/reference/active-script-interfaces.md)