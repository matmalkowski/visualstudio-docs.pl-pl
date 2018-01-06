---
title: IDebugCanStopEvent2::GetDocumentContext | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCanStopEvent2::GetDocumentContext
helpviewer_keywords: IDebugCanStopEvent2::GetDocumentContext
ms.assetid: 936a6c4e-30c5-4c7e-9ad5-910cc605a4b5
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9d3f906c1dc1c019040f314204d3a4a423e1b8bf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcanstopevent2getdocumentcontext"></a>IDebugCanStopEvent2::GetDocumentContext
Pobiera kontekst dokumentu, który opisuje lokalizacja tego zdarzenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetDocumentContext (   
   IDebugDocumentContext2** ppDocCxt  
);  
```  
  
```csharp  
int GetDocumentContext (   
   out IDebugDocumentContext2 ppDocCxt  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppDocCxt`  
 [out] Zwraca [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) interfejs, który reprezentuje pozycji w pliku dokument źródłowy odpowiadającego do bieżącej lokalizacji kodu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ogólnie rzecz biorąc kontekstu dokumentu można traktować jako pozycji w pliku źródłowym.  
  
 Aby pobrać kontekst kodu, który jest zorientowany instrukcje kodu, należy wywołać [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)