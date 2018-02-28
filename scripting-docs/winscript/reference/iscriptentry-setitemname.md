---
title: IScriptEntry::SetItemName | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IScriptEntry.SetItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetItemName
ms.assetid: 9551a7ec-38f8-466a-9722-09367763f380
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 483d3cdc1c8b8de9342003a99427fc2c727ad67f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptentrysetitemname"></a>IScriptEntry::SetItemName
Ustawia nazwę elementu, który identyfikuje `IScriptEntry` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `psz`  
 [in] Adres buforu, który zawiera nazwę elementu. Nazwa elementu jest używany przez hosta do zidentyfikowania wpisu.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_FAIL`|Metoda nie powiodła się.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać `IScriptEntry` obiekty, ta metoda zwraca `S_OK`.  
  
 Aby uzyskać `IScriptScriptlet` obiektów (wynikającymi z `IScriptEntry`), ta metoda zwraca `E_FAIL`. Aby uzyskać `IScriptScriptlet` obiekty, nazwa elementu jest ustawiana przez [IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md) i nie można zmienić.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IScriptEntry](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)