---
title: IActiveScriptSiteWindow::EnableModeless | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteWindow.EnableModeless
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteWindow_EnableModeless
ms.assetid: 83fe4f62-8e97-4f03-bc6f-d90aa888657d
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7099fe7d13a1cb3231e67049104722af9373d7a8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793582"
---
# <a name="iactivescriptsitewindowenablemodeless"></a>IActiveScriptSiteWindow::EnableModeless
Powoduje, że host włączyć lub wyłączyć jego okno główne, a także Niemodalne okna dialogowe.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnableModeless(  
    BOOL fEnable  // enable flag  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fEnable`  
 [in] Flaga, jeśli `TRUE`, włącza okno główne i Niemodalne okna dialogowe lub, jeśli `FALSE`, wyłącza je.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` w przypadku powodzenia lub `E_FAIL` Jeśli wystąpił błąd.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest taki sam jak `IOleInPlaceFrame::EnableModeless` metody.  
  
 Mogą być zagnieżdżone wywołania tej metody.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)