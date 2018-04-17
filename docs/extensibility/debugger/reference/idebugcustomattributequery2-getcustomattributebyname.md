---
title: IDebugCustomAttributeQuery2::GetCustomAttributeByName | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b61cb7304f6fed3e2f3da55b94450c58bfc53334
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
Uzyskuje bajtów atrybutów niestandardowych, które otrzymuje nazwę atrybutu niestandardowego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetCustomAttributeByName(   
   LPCOLESTR pszCustomAttributeName,  
   BYTE*     ppBlob,  
   DWORD*    pdwLen  
);  
```  
  
```csharp  
int GetCustomAttributeByName(  
   [In] string        pszCustomAttributeName,   
   [In, Out] byte[]   ppBlob,   
   [In, Out] ref uint pdwLen  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszCustomAttributeName`  
 [in] Ciąg zawierający nazwę atrybutu niestandardowego do wyszukania.  
  
 `ppBlob`  
 [w, out] Tablica jest wypełniane bajtów atrybutu niestandardowego.  
  
 `pdwLen`  
 [w, out] Określa maksymalną liczbę bajtów do zwrócenia w `ppBlob` tablicy i zwraca liczbę bajtów zapisana do tablicy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK lub zwraca wartości S_FALSE, jeśli atrybut niestandardowy nie istnieje. W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ustaw `ppBlob` parametr ma wartość null, aby zwrócić liczbę atrybutów liczby dostępnych bajtów. Następnie przydzielić tablicy i przekaż tablicy w przypadku `ppBlob` parametru.  
  
 Bajty atrybutu reprezentują nieprzetworzone dane atrybutu niestandardowego.  
  
 Jeśli `ppBlob` i `pdwLen` parametry są ustawione na wartość null, ta metoda może być używany do ustalenia, czy atrybut niestandardowy jedynie istnieje. Alternatywą łatwiej jest jednak wywołać [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)