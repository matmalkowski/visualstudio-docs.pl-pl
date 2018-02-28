---
title: IScriptEntry::GetSignature | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IScriptEntry.GetSignature
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetSignature
ms.assetid: 8cbf37ac-b14c-4e15-a613-06f34857da9b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 062f069bb6a19c24f26a6a0bc6a9f4de2292d88f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptentrygetsignature"></a>IScriptEntry::GetSignature
Zwraca typ informacji o `IScriptEntry` obiekt funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetSignature(  
   ITypeInfo          **ppti  
   ULONG              *piMethod  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppti`  
 [out] Wpisz informacje skojarzone z tym `IScriptEntry` obiekt funkcji.  
  
 `piMethod`  
 [out] Indeks metody w `ITypeInfo` obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Należy określić przy użyciu informacji o typie [IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md) lub [IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md). Informacje o typie może być również generowany przez wpis oparte na funkcji wewnętrznej reprezentacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IScriptEntry](../../winscript/reference/iscriptentry-interface.md)