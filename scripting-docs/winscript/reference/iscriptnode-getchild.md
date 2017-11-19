---
title: IScriptNode::GetChild | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptNode.GetChild
apilocation: scrobj.dll
helpviewer_keywords: IScriptNode::GetChild
ms.assetid: 8cb3f8b0-958b-40bb-a91a-49a788661861
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d127b1b8a8db0c6d272e50d33b523fbe182a9e21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptnodegetchild"></a>IScriptNode::GetChild
Zwraca podrzędny, który znajduje się pod określonym indeksem w węźle.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetChild(  
   ULONG              isn,  
   IScriptNode        **ppsn  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `isn`  
 [in] Indeks elementu podrzędnego w obiekcie nadrzędnym.  
  
 `ppsn`  
 [out] Adres zmiennej, która otrzymuje wskaźnik `IScriptNode` interfejsu wystąpienia podrzędnych.  
  
 Aby uzyskać `IScriptNode` obiektów, które reprezentują strony sieci Web, ten parametr zwraca obiekt, który zawiera blok skryptu.  
  
 Aby uzyskać `IScriptEntry` obiektów, które określają blok skryptu, ten parametr zwraca obiekt, który określa funkcję.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Dla `IScriptEntry` obiektów, które określają obiektem funkcji oraz `IScriptScriptlet` obiekty, ta metoda nie powiedzie się, ponieważ nie ma żadnych wpisów podrzędnych.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IScriptNode](../../winscript/reference/iscriptnode-interface.md)