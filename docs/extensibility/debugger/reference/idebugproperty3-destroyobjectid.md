---
title: IDebugProperty3::DestroyObjectID | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty3::DestroyObjectID
helpviewer_keywords:
- IDebugProperty3::DestroyObjectID
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0db5ef80a1734aedb819c109aa4c27c40224886e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
Niszczy Unikatowy identyfikator skojarzony z tą właściwością wskazujący, że obiekt wywołujący nie jest już dba do identyfikowania tej właściwości jednoznacznie ze wszystkich innych właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT DestroyObjectID(  
   void  
);  
```  
  
```csharp  
int DestroyObjectID();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli aparat debugowania nie musi obsługiwać unikatowych identyfikatorów dla właściwości (ponieważ jest on już śledzi je jednoznacznie wewnętrznie), a następnie po prostu może zwrócić `E_NOTIMPL` dla tej metody.  
  
 Unikatowe identyfikatory są tworzone w wyniku wywołania [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) metody, gdy obiekt wywołujący chce upewnij się, że ta właściwość jest unikatowo identyfikowana wśród innych właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)