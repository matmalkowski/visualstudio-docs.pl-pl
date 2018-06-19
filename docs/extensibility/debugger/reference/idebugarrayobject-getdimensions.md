---
title: IDebugArrayObject::GetDimensions | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugArrayObject::GetDimensions
helpviewer_keywords:
- IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5a20073a19f785d30b0fcd0a7f126919371e722c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31098963"
---
# <a name="idebugarrayobjectgetdimensions"></a>IDebugArrayObject::GetDimensions
Pobiera wymiarów tablicy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetDimensions(   
   DWORD dwCount,  
   DWORD dwDimensions[]  
);  
```  
  
```csharp  
int GetDimensions(  
   [In] uint    dwCount,   
   [Out] uint[] dwDimensions  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwCount`  
 [in] Liczba wymiarów do pobrania.  
  
 `dwDimensions`  
 [w, out] Tablica jest wypełniane rozmiary każdego wymiaru. `dwCount` Określa maksymalny rozmiar `dwDimensions` tablicy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Wielowymiarowe tablice mogą mieć różne rozmiary, dla każdego wymiaru. Przykładowo, podana tablicą trójwymiarową `myarray[3][2][6]`, ta metoda zwróci 3, 2 i 6 w `dwDimensions` parametru w podanej kolejności.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)