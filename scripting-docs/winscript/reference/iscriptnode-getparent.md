---
title: IScriptNode::GetParent | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptNode.GetParent
apilocation: scrobj.dll
helpviewer_keywords: IScriptNode::GetParent
ms.assetid: 0fb813f6-ab94-46b2-b0cf-ef5d1cd38ae4
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1da2f68de40a66b98b97ab7c7eb1d63748f1e07a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptnodegetparent"></a>IScriptNode::GetParent
Zwraca `IScriptNode` obiekt, który jest elementem nadrzędnym obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetParent(  
   IScriptNode       **ppsnParent  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppsnParent`  
 [out] Adres zmiennej, która otrzymuje wskaźnik `IScriptNode` interfejsu wystąpienie nadrzędne.  
  
 Jeśli klasa implementuje `IScriptEntry` lub `IScriptScriptlet`, `IScriptNode` obiekt jest zwracany.  
  
 Jeśli klasa implementuje `IScriptNode` (reprezentujący stronę sieci Web), zostanie zwrócona wartość NULL.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IScriptNode](../../winscript/reference/iscriptnode-interface.md)