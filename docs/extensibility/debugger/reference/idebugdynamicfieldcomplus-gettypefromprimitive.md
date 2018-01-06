---
title: IDebugDynamicFieldCOMPlus::GetTypeFromPrimitive | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugDynamicFieldCOMPlus::GetTypeFromPrimitive
- GetTypeFromPrimitive
ms.assetid: d7f51e2a-1b72-489c-b7b6-4af7b7e4d663
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: af8c9946d52115594618aac95eb7c752b4a1a3f8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdynamicfieldcomplusgettypefromprimitive"></a>IDebugDynamicFieldCOMPlus::GetTypeFromPrimitive
Pobiera typ danego jego typu podstawowego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetTypeFromPrimitive(  
   DWORD         dwCorElementType,  
   IDebugField** ppType  
);  
```  
  
```csharp  
int GetTypeFromPrimitive(  
   uint            dwCorElementType,  
   out IDebugField ppType  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwCorElementType`  
 [in] Wartość z [CorElementType — wyliczenie](/dotnet/framework/unmanaged-api/metadata/corelementtype-enumeration) reprezentujący typ pierwotny.  
  
 `ppType`  
 [out] Zwraca [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) reprezentujący typ.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)