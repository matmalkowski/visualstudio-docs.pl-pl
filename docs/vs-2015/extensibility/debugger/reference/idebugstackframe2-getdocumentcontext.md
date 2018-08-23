---
title: IDebugStackFrame2::GetDocumentContext | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugStackFrame2::GetDocumentContext
helpviewer_keywords:
- IDebugStackFrame2::GetDocumentContext
ms.assetid: 69e81439-1238-4f18-9028-6fd1c1ba5e4a
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d017b16042fdba5855a10b6477e857bb949b11d3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42679690"
---
# <a name="idebugstackframe2getdocumentcontext"></a>IDebugStackFrame2::GetDocumentContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugStackFrame2::GetDocumentContext](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugstackframe2-getdocumentcontext).  
  
Pobiera kontekst dokumentu dla tej ramki stosu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetDocumentContext (   
   IDebugDocumentContext2** ppCxt  
);  
```  
  
```csharp  
int GetDocumentContext (   
   out IDebugDocumentContext2 ppCxt  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppCxt`  
 [out] Zwraca [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) obiekt, który reprezentuje bieżącą pozycję w dokumencie źródłowym.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest szybsza niż wywoływania [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) metody, a następnie wywołując [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) metody na kontekst kodu. Jednak nie ma żadnej gwarancji, każdy silnik debugowania (DE) będzie zaimplementować tę metodę.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)

