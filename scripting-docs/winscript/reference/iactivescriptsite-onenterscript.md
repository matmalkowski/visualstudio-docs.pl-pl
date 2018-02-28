---
title: IActiveScriptSite::OnEnterScript | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptSite.OnEnterScript
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnEnterScript
ms.assetid: 1ed9178c-fe80-41c4-b74d-23b85f9cddbf
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb4514770faaaad46c8590e6df03488e3d5bc679
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsiteonenterscript"></a>IActiveScriptSite::OnEnterScript
Informuje hosta, że aparat skryptów rozpoczął wykonywanie kodu skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT OnEnterScript(void);  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` w przypadku powodzenia.  
  
## <a name="remarks"></a>Uwagi  
 Aparat skryptów musi wywołać tej metody dla każdego wpisu i ponowny wpis do aparatu skryptów. Na przykład, jeśli skrypt wywołuje obiekt, który wyzwala zdarzenie obsługiwane przez aparat skryptów, aparat skryptów należy wywołać `IActiveScriptSite::OnEnterScript` przed wykonaniem zdarzenia i należy wywołać [IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md) Metoda po wykonaniu zdarzenia, ale przed zwróceniem do obiektu, który uruchomił zdarzenia. Mogą być zagnieżdżone wywołania tej metody. Co wywołanie tej metody wymaga odpowiedniego wywołania `IActiveScriptSite::OnLeaveScript`.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)