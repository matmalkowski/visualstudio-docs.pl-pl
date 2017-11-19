---
title: IScriptNode::Alive | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptNode.Alive
apilocation: scrobj.dll
helpviewer_keywords: IScriptNode::Alive
ms.assetid: d2755c83-e9b9-4c0a-acb7-25b554fc9fe8
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0631690cbd961273175cf8dfbe35550980d4994d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptnodealive"></a>IScriptNode::Alive
Wskazuje, czy obiekt jest nadal aktywne.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Alive();  
```  
  
#### <a name="parameters"></a>Parametry  
 Metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Węzeł skryptu jest nadal aktywne.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli obiekt nie jest aktywne, składnik modelu COM. zwraca błąd z kierowania serwera proxy dla wywołania do tej metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IScriptNode](../../winscript/reference/iscriptnode-interface.md)