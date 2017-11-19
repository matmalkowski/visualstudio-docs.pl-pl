---
title: IScriptEntry::SetText | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IScriptEntry.SetText
apilocation: scrobj.dll
helpviewer_keywords: ISetEntry::SetText
ms.assetid: 4605481b-7707-43d1-ab78-a9207d0cf6fe
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 62f1d113dc23dca85db02bf23b2c79551108f3b6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptentrysettext"></a>IScriptEntry::SetText
Ustawia tekst, który odpowiada `IScriptEntry` bloku skryptu lub kodu źródłowego, który jest zawarty w `IScriptScriptlet` obsługi zdarzeń.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetText(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `psz`  
 [in] Tekst `IScriptEntry` bloku skryptu lub kod źródłowy `IScriptScriptlet` obsługi zdarzeń.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IScriptEntry](../../winscript/reference/iscriptentry-interface.md)