---
title: IDebugProperty2::GetSize | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty2::GetSize
helpviewer_keywords: IDebugProperty2::GetSize
ms.assetid: 0deb8ec5-d6fb-4622-bb14-0c46b9459cc6
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0c027c396172299612f52aef5f2d4c99a6ea5ac1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugproperty2getsize"></a>IDebugProperty2::GetSize
Pobiera rozmiar w bajtach wartości właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetSize (   
   DWORD* pdwSize  
);  
```  
  
```csharp  
int GetSize (   
   out uint pdwSize  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdwSize`  
 [out] Zwraca rozmiar w bajtach wartości właściwości.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Zwraca `S_GETSIZE_NO_SIZE` Jeśli rozmiar nie ma właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)