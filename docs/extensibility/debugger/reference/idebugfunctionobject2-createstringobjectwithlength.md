---
title: IDebugFunctionObject2::CreateStringObjectWithLength | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CreateStringObjectWithLength
- IDebugFunctionObject2::CreateStringObjectWithLength
ms.assetid: 1f43ec66-1615-4a4c-8b9d-e933f549f96d
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 78b5f21a2b2f018c4eb35007cdfd2aa4f67b5ebf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugfunctionobject2createstringobjectwithlength"></a>IDebugFunctionObject2::CreateStringObjectWithLength
Tworzy obiekt ciągu zawierający określonej długości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateStringObjectWithLength (  
   LPCOLESTR      pcstrString,  
   UINT           uiLength,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int CreateStringObjectWithLength (  
   string           pcstrString,  
   uint             uiLength,  
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pcstrString`  
 [in] Wartość ciągu z obiektem ciągu.  
  
 `uiLength`  
 [in] Długość ciągu w bajtach.  
  
 `ppObject`  
 [out] Zwraca [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) obiekt, który reprezentuje ciąg nowo utworzony obiekt.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)