---
title: IDebugArrayObject::GetRank | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugArrayObject::GetRank
helpviewer_keywords: IDebugArrayObject::GetRank method
ms.assetid: 9948551a-e334-4ff6-979c-08dab633b9b6
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b3ef04279c4a9e34313c7d449714cb0a519d5652
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugarrayobjectgetrank"></a>IDebugArrayObject::GetRank
Pobiera rangą tablicy, czyli liczby wymiarów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetRank(   
   DWORD* pdwRank  
);  
```  
  
```csharp  
int GetRank(  
   out uint pdwRank  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdwRank`  
 [out] Zwraca rangę.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Użyj [GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md) metodę, aby pobrać rozmiar każdego wymiaru tablicy obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)