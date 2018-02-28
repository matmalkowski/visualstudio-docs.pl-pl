---
title: IScriptNode::Delete | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IScriptNode.Delete
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::Delete
ms.assetid: 6765ff80-a9a8-40a3-a669-7fcc284c87af
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1d1404d90cc1edd882505e463938a2c1a5e8aea8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptnodedelete"></a>IScriptNode::Delete
Usuwa obiekt poziomu tego drzewa.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Delete();  
```  
  
#### <a name="parameters"></a>Parametry  
 Metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Po `Delete` metoda jest wywoływana, [IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md) — metoda powinny wskazywać, w tym węźle skryptu nie jest aktywny.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IScriptNode](../../winscript/reference/iscriptnode-interface.md)