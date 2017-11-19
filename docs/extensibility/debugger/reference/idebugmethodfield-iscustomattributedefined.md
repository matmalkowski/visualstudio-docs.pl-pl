---
title: IDebugMethodField::IsCustomAttributeDefined | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugMethodField::IsCustomAttributeDefined
helpviewer_keywords: IDebugMethodField::IsCustomAttributeDefined method
ms.assetid: 1b5d95a8-cc87-4acb-9e6a-3928f3632b7c
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5bf6d2dbc915638005f377826c5504b2f6bdf859
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmethodfieldiscustomattributedefined"></a>IDebugMethodField::IsCustomAttributeDefined
Określa, czy została zdefiniowana określonego atrybutu niestandardowego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT IsCustomAttributeDefined(   
   LPCOLESTR pszCustomAttributeName  
);  
```  
  
```csharp  
int IsCustomAttributeDefined(  
   [In] string pszCustomAttributeName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszCustomAttributeName`  
 [in] Ciąg zawierający nazwę atrybutu niestandardowego można znaleźć.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK Jeśli atrybut niestandardowy jest zdefiniowany dla tej metody, w przeciwnym razie wartości S_FALSE.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)