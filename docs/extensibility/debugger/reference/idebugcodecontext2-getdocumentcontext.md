---
title: IDebugCodeContext2::GetDocumentContext | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCodeContext2::GetDocumentContext
helpviewer_keywords: IDebugCodeContext2::GetDocumentContext
ms.assetid: d552cc92-963f-43c1-949f-ae6b63a427b8
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 335b8f7a2c92b299d62cda0f23c7d727cad653b5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcodecontext2getdocumentcontext"></a>IDebugCodeContext2::GetDocumentContext
Pobiera kontekst dokumentu umożliwiająca ten kontekst kodu. Kontekstu dokumentu reprezentuje pozycji w pliku źródłowym, która odnosi się do kodu źródłowego, który wygenerował tej instrukcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetDocumentContext(   
   IDebugDocumentContext2** ppSrcCxt  
);  
```  
  
```csharp  
int GetDocumentContext(   
   out IDebugDocumentContext2 ppSrcCxt  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppSrcCxt`  
 [out] Zwraca [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) obiekt, który odpowiada kontekst kodu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ogólnie rzecz biorąc kontekstu dokumentu można traktować jako pozycji w pliku źródłowym podczas kontekst kodu jest pozycji w strumieniu wykonywania instrukcji kodu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)