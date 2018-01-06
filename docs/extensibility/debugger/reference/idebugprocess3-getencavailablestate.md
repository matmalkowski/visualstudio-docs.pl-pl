---
title: IDebugProcess3::GetENCAvailableState | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess3::GetENCAvailableState
helpviewer_keywords: IDebugProcess3::GetENCAvailableState
ms.assetid: 98a5d527-8a72-476c-8e92-0bff3d97c195
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5d0fcac34457c12218ea8728af84e5f0a623edfe
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocess3getencavailablestate"></a>IDebugProcess3::GetENCAvailableState
Ta metoda pobiera bieżący stan Edytuj i Kontynuuj proces. Dostawcy niestandardowego numeru portu należy zawsze zwracają `E_NOTIMPL`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetENCAvailableState(  
   EncUnavailableReason* pReason  
);  
```  
  
```csharp  
int GetENCAvailableState(  
   EncUnavailableReason[] pReason  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pReason`  
 [out] Wartość z zakresu od [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) wyliczenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
> [!NOTE]
>  Dostawcy niestandardowego numeru portu należy zawsze zwracają `E_NOTIMPL`.  
  
## <a name="remarks"></a>Uwagi  
 Ten stan może mieć wpływ [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)   
 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)