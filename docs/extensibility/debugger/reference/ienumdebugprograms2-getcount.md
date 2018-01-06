---
title: IEnumDebugPrograms2::GetCount | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugPrograms2::GetCount
helpviewer_keywords: IEnumDebugPrograms2::GetCount
ms.assetid: 84832982-fa68-4090-a5b7-b233817876b7
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c74e14ee32d58a638cc4c60f98aca1ca26e4c075
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugprograms2getcount"></a>IEnumDebugPrograms2::GetCount
Zwraca liczbę elementów w wyliczeniu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetCount(  
   ULONG* pcelt  
);  
```  
  
```csharp  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pcelt`  
 [out] Zwraca liczbę elementów w wyliczeniu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda nie jest częścią zwyczajowe interfejsu wyliczenie COM, który określa tylko `Next`, `Clone`, `Skip`, i `Reset` metody muszą zostać wdrożone.  
  
## <a name="see-also"></a>Zobacz też  
 [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)