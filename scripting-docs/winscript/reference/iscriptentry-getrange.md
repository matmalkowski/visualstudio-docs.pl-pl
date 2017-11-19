---
title: IScriptEntry::GetRange | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptEntry.GetRange
apilocation: scrobj.dll
helpviewer_keywords: IScriptEntry::GetRange
ms.assetid: 3ac18f0a-b470-4f4d-b8f5-2da3fdef74f1
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ae0ee34298e03fdd2e9c6bc841d9fbe90967e8f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptentrygetrange"></a>IScriptEntry::GetRange
Zwraca długość hasła i pozycji początkowej.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetRange(  
   ULONG              *pichMin  
   ULONG              *pcch  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pichMin`  
 [out] Aby uzyskać `IScriptEntry` obiektów, które określają blok skryptu, zwraca wartość 0.  
  
 Aby uzyskać `IScriptEntry` obiektów, które określają obiektem funkcji zwraca pozycję początkową funkcji w bieżącym bloku skryptu.  
  
 Aby uzyskać `IScriptScriptlet` obiektów, zwraca wartość 0.  
  
 `pcch`  
 [out] Aby uzyskać `IScriptEntry` obiektów, które określają blok skryptu, zwraca długość tekstu.  
  
 Aby uzyskać `IScriptEntry` obiektów, które określają obiektem funkcji zwraca długość definicji funkcji.  
  
 Aby uzyskać `IScriptScriptlet` obiektów, zwraca długość wpisu.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IScriptEntry](../../winscript/reference/iscriptentry-interface.md)