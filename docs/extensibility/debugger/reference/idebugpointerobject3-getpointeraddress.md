---
title: IDebugPointerObject3::GetPointerAddress | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GetPointerAddress
- IDebugPointerObject3::GetPointerAddress
ms.assetid: 4cc5af04-9e70-420d-8230-ef3108df6d51
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7c761c9d74c88d8b3c3d6ee9a8c067aaa735e6db
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugpointerobject3getpointeraddress"></a>IDebugPointerObject3::GetPointerAddress
Pobiera adres wskaźnika.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetPointerAddress (  
   UINT64* puAddress  
);  
```  
  
```csharp  
int GetPointerAddress (  
   out ulong puAddress  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `puAddress`  
 [out] Zwraca adres wskaźnika.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)