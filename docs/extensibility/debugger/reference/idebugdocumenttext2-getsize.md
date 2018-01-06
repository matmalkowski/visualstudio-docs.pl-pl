---
title: IDebugDocumentText2::GetSize | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDocumentText2::GetSize
helpviewer_keywords: IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 117d557ad2ee5d7fe3490644162d1995e86c1873
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdocumenttext2getsize"></a>IDebugDocumentText2::GetSize
Pobiera rozmiar tekstu, w tym miejscu w dokumencie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetSize(   
   ULONG* pcNumLines,  
   ULONG* pcNumChars  
);  
```  
  
```csharp  
int GetSize(   
   ref uint pcNumLines,  
   ref uint pcNumChars  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pcNumLines`  
 [out] Zwraca liczbę wierszy tekstu.  
  
 `pcNumChars`  
 [out] Zwraca liczbę znaków tekstu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 [Tylko C++] Jeśli konkretną wartość nie jest wymagana, należy przekazać wartość NULL dla parametru.  
  
 [C# tylko] Oba parametry muszą być określone.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)