---
title: IScriptEntry::SetSignature | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetSignature
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetSignature
ms.assetid: 8513587d-9df2-4621-afe7-56eacbb5e688
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9ff480f8e5c3192a7e2b355d39825cc3a084370
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794956"
---
# <a name="iscriptentrysetsignature"></a>IScriptEntry::SetSignature
Ustawia typ informacji o `IScriptEntry` obiekt funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetSignature(  
   ITypeInfo          *pti  
   ULONG              iMethod  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pti`  
 [in] Informacje o typie.  
  
 `iMethod`  
 [in] Indeks metody w `ITypeInfo` obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Należy określić przy użyciu informacji o typie `IScriptEntry::SetSignature` lub [IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md). Informacje o typie może być również generowany przez wpis oparte na funkcji wewnętrznej reprezentacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IScriptEntry](../../winscript/reference/iscriptentry-interface.md)