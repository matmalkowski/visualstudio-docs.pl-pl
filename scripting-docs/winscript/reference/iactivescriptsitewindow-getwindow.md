---
title: IActiveScriptSiteWindow::GetWindow | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteWindow.GetWindow
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteWindow_GetWindow
ms.assetid: 6284e38c-9dfb-4d69-903d-f243f78c0331
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b3257ac5632a2f3d713b6329a9a1eeebc4415851
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793570"
---
# <a name="iactivescriptsitewindowgetwindow"></a>IActiveScriptSiteWindow::GetWindow
Pobiera dojścia do okna, które mogą działać jako właściciel okno podręczne wyświetlające musi aparatu skryptów.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetWindow(  
    HWND *phwnd  // address of variable for window handle  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `phwnd`  
 [out] Adres zmiennej, która odbiera uchwytu okna.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` w przypadku powodzenia lub `E_FAIL` Jeśli wystąpił błąd.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest podobna do `IOleWindow::GetWindow` metody.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)