---
title: IDebugProgramPublisher2::SetDebuggerPresent | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramPublisher2::SetDebuggerPresent
helpviewer_keywords: IDebugProgramPublisher2::SetDebuggerPresent
ms.assetid: c88c3ff4-3632-4199-b5de-83c6d21bcf75
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 61ad9f9fe19de17d1dc21c4f9f9be24ffce2900a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogrampublisher2setdebuggerpresent"></a>IDebugProgramPublisher2::SetDebuggerPresent
Określa, że wydawca programu czy debugera jest obecna i uruchomiona.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetDebuggerPresent(  
   BOOL fDebuggerPresent  
);  
```  
  
```csharp  
int SetDebuggerPresent(  
   int fDebuggerPresent  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fDebuggerPresent`  
 [in] Niezerowa (`TRUE`) Jeśli jest obecny debuger, zero (`FALSE`) Jeśli nie jest.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Obecności lub braku debugera jest widoczny w dane zwrócone w wyniku [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) metody: wartości zwracanej jest ustawiona lub usunięte przez poprzednie wywołanie `SetDebuggerPresent` metody.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)