---
title: IDebugObject::IsEqual | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugObject::IsEqual
helpviewer_keywords: IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2af7ef11a142442b97dbb5d6a4d0545bf118da39
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
Porównuje obiekt z tym obiektem.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT IsEqual(   
   IDebugObject* pObject,  
   BOOL*         pfIsEqual  
);  
```  
  
```csharp  
int IsEqual(  
   IDebugObject pObject,  
   out int      pfIsEqual  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pObject`  
 [in] [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) obiekt reprezentujący obiekt do porównania.  
  
 `pfIsEqual`  
 [out] Zwraca wartość inną niż zero (`TRUE`) Jeśli wartości obiekty są równe; w przeciwnym razie, zwraca zero (`FALSE`).  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Zazwyczaj tej metody można porównać wartości reprezentowane przez adresy `pObject` parametr i to [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) obiekt; Jeśli adresy są takie same, a następnie obiekty mogą być uważane za takie same.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)