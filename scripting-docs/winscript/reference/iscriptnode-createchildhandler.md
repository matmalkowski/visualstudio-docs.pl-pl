---
title: IScriptNode::CreateChildHandler | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.CreateChildHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::CreateChildHandler
ms.assetid: 4ce5eb10-1a3f-43b0-a4b7-599a397ed3a2
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff2ba40d1570e23f0256bd34ca8aff0f8d77ce5c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24795022"
---
# <a name="iscriptnodecreatechildhandler"></a>IScriptNode::CreateChildHandler
Dodaje skryptlet jako wystąpienie podrzędne `IScriptNode`.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CreateChildHandler(  
   LPCOLESTR          pszDefaultName,  
   LPCOLESTR          *prgpszNames,  
   ULONG              cpszNames,  
   LPCOLESTR          pszEvent,  
   LPCOLESTR          pszDelimiter,  
   ITypeInfo*         ptiSignature,  
   ULONG              iMethodSignature,  
   ULONG              isn,  
   DWORD              dwCookie,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszDefaultName`  
 [in] Adres domyślną nazwę do skojarzenia z skryptlet.  
  
 `prgpszNames`  
 [w size_is (`cpszNames`)] identyfikatorów w pełni kwalifikowaną nazwę hosta.  
  
 `cpszNames`  
 [in] Liczba identyfikatorów w `prgpszNames` parametru.  
  
 `pszEvent`  
 [in] Adres buforu, który identyfikuje skojarzone z skryptlet Nazwa zdarzenia.  
  
 `pszDelimiter`  
 [in] Adres ogranicznik zakończenia elementu skryptu bloku. Do analizy, hosta zwykle wykorzystuje ogranicznik (na przykład dwa pojedynczy cudzysłów), aby wykryć koniec bloku skryptu.  
  
 Ogranicznik, który umożliwia przetwarzanie wstępne za pomocą skryptu tworzenia aparatu. Na przykład aparat może zastąpić znak pojedynczego cudzysłowu dwa znaki pojedynczego cudzysłowu do użycia jako ogranicznik. Aparat Określa, jak ogranicznik, który jest używany.  
  
 Wartość NULL, jeśli nie ogranicznik służy do identyfikowania koniec bloku skryptu.  
  
 `ptiSignature`  
 [in] Informacje o typie dla obiekt funkcji.  
  
 `iMethodSignature`  
 [in] Indeks tej funkcji w `ITypeInfo``ptiSignature` parametru.  
  
 `isn`  
 [in] Indeks elementu podrzędnego w obiekcie nadrzędnym.  
  
 `dwCookie`  
 [in] Wartość zdefiniowanym przez aplikację, która jest używana do skojarzenia wpis z obiektu hosta.  
  
 `ppse`  
 [out] Adres zmiennej, która otrzymuje wskaźnik `IScriptEntry` interfejsu wystąpienia podrzędnych.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Skryptlet Określa program obsługi zdarzeń. Ta metoda tworzy skryptletu, jeśli jest ona wywoływana przez `IScriptNode` obiekt reprezentujący stronę sieci Web. Ta metoda nie powiedzie się, gdy została wywołana przez inne interfejsy.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IScriptNode](../../winscript/reference/iscriptnode-interface.md)   
 [Interfejs IScriptEntry](../../winscript/reference/iscriptentry-interface.md)