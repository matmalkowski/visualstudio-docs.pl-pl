---
title: IDebugArrayField::GetNumberOfElements | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugArrayField::GetNumberOfElements
helpviewer_keywords:
- IDebugArrayField::GetNumberOfElements method
ms.assetid: a1961ef3-d69d-4022-b8c9-b9cfb9811345
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2dff7f7aa8f32fe89b6d2568b570390e89fd75d8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugarrayfieldgetnumberofelements"></a>IDebugArrayField::GetNumberOfElements
Pobiera liczbę elementów w tablicy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetNumberOfElements(   
   DWORD* pdwNumElements  
);  
```  
  
```csharp  
int GetNumberOfElements(  
   out uint pdwNumElements  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdwNumElements`  
 [out] Zwraca liczbę elementów w tablicy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Wartość zwracana jest liczba elementów w tablicy, niezależnie od liczby wymiarów.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)