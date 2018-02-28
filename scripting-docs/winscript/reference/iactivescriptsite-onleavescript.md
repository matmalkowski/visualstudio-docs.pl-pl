---
title: IActiveScriptSite::OnLeaveScript | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptSite.OnLeaveScript
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnLeaveScript
ms.assetid: 79af0e22-fbe3-4fae-8a5f-7af8b857678d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aba20c13dc5568165641c5c7b8e871e0b5e8f322
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsiteonleavescript"></a>IActiveScriptSite::OnLeaveScript
Informuje hosta, że aparat skryptów zwrócił wykonywanie kodu skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT OnLeaveScript(void);  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` w przypadku powodzenia.  
  
## <a name="remarks"></a>Uwagi  
 Aparat skryptów musi wywołać tę metodę przed zwróceniem sterowania do wywoływania aplikacji, która wprowadzona aparatu skryptów. Na przykład, jeśli skrypt wywołuje obiekt, który wyzwala zdarzenie obsługiwane przez aparat skryptów, aparat skryptów należy wywołać [IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md) metoda przed wykonaniem zdarzenia, a musi wywołać `IActiveScriptSite::OnLeaveScript`po wykonaniu zdarzenia przed zwróceniem do obiektu, który uruchomił zdarzenia. Mogą być zagnieżdżone wywołania tej metody. Każdego wywołania `IActiveScriptSite::OnEnterScript` wymaga odpowiedniego wywołania tej metody.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)