---
title: 'IScriptNode:: CreateChildEntry | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IScriptNode. CreateChildEntry
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::CreateChildEntry
ms.assetid: b9682505-4457-40e9-8691-235843637506
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8fcc010efe8fcf30a8f467dd94befff54bc5fac5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptnode-createchildentry"></a>IScriptNode:: CreateChildEntry
Dodaje wystąpienie podrzędne `IScriptEntry`.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CreateChildEntry(  
   ULONG              isn,  
   DWORD              dwCookie,  
   LPCOLESTR          pszDelimiter,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `isn`  
 [in] Indeks elementu podrzędnego w obiekcie nadrzędnym.  
  
 `dwCookie`  
 [in] Zdefiniowane przez aplikację wartości używanego do kojarzenia zapisie podrzędnych z obiektu hosta.  
  
 `pszDelimiter`  
 [in] Adres ogranicznik zakończenia elementu skryptu bloku. Do analizy, hosta zwykle wykorzystuje ogranicznik (na przykład dwa pojedynczy cudzysłów), aby wykryć koniec bloku skryptu.  
  
 Ogranicznik, który umożliwia skryptu tworzenia aparatu, aby zapewnić przetwarzania wstępnego. Na przykład aparat może zastąpić znak pojedynczego cudzysłowu dwa znaki pojedynczego cudzysłowu do użycia jako ogranicznik. Aparat Określa, jak ogranicznik, który jest używany.  
  
 Wartość NULL, jeśli ogranicznik nie oznacza koniec bloku skryptu.  
  
 `ppse`  
 [out] Adres zmiennej, która otrzymuje wskaźnik `IScriptEntry` interfejsu wystąpienia podrzędnych.  
  
 Aby uzyskać `IScriptNode` obiektów, które reprezentują strony sieci Web, ten parametr zwraca `IScriptEntry` wystąpienia, która określa Blok skryptu.  
  
 Aby uzyskać `IScriptEntry` obiektów, które reprezentują blok skryptu, ten parametr zwraca `IScriptEntry` wystąpienia, który określa obiekt funkcji.  
  
 Aby uzyskać `IScriptEntry` obiektu obiektów, które reprezentują funkcji, ta metoda zakończy się niepowodzeniem.  
  
 Aby uzyskać `IScriptScriptlet` obiekty, ta metoda zakończy się niepowodzeniem.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 `IScriptNode` Interfejsu reprezentuje strony sieci Web i jej elementów. `IScriptEntry` Interfejsu (która jest pochodną `IScriptNode`) reprezentuje blok skryptu albo obiektem funkcji. `IScriptScriptlet` Interfejsu (która jest pochodną `IScriptEntry`) reprezentuje program obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IScriptNode](../../winscript/reference/iscriptnode-interface.md)   
 [Interfejs IScriptEntry](../../winscript/reference/iscriptentry-interface.md)