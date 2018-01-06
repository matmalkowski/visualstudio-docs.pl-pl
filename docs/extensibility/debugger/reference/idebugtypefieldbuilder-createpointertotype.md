---
title: IDebugTypeFieldBuilder::CreatePointerToType | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CreatePointerToType
- IDebugTypeFieldBuilder::CreatePointerToType
ms.assetid: 73966e8a-b643-43e0-9b4e-0aa4b402ebbe
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a3db59124a8691fc68ac88ab065bf0a2e6c66b93
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugtypefieldbuildercreatepointertotype"></a>IDebugTypeFieldBuilder::CreatePointerToType
Tworzy wskaźnik do określonego typu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreatePointerToType(  
   IDebugField*  pTypeField,  
   IDebugField** pPtrToTypeField  
);  
```  
  
```csharp  
int CreatePointerToType(  
   IDebugField     pTypeField,  
   out IDebugField pPtrToTypeField  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pTypeField`  
 [in] Typ, aby wskazywał. Jest reprezentowana przez [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfejsu.  
  
 `pPtrToTypeField`  
 [out] Zwraca wskaźnik reprezentowana przez nowy **IDebugField** obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)