---
title: IDebugCoreServer3::QueryIsLocal | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer3::QueryIsLocal
helpviewer_keywords:
- IDebugCoreServer3::QueryIsLocal
ms.assetid: cca030de-f853-4ed7-b2fb-395f08a6b884
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4a899a1d37f1dc57f6aaac7bf1f5ec3823003f29
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31106029"
---
# <a name="idebugcoreserver3queryislocal"></a>IDebugCoreServer3::QueryIsLocal
Określa, czy serwer jest lokalny dla obiekt wywołujący.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT QueryIsLocal(  
   void  
);  
```  
  
```csharp  
int QueryIsLocal();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` aby wskazać serwer jest lokalny. Zwraca `S_FALSE` Jeśli serwer działa z wystąpienia msvsmon.exe, która zwykle jest używana do zdalnego debugowania.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)