---
title: IDebugArrayObject::GetDimensions | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugArrayObject::GetDimensions
helpviewer_keywords: IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d516032e458bcc0f85c73c75a9147ff53fc0fff2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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
 [w, out] Tablica jest wypełniane rozmiary każdego wymiaru. `dwCount`Określa maksymalny rozmiar `dwDimensions` tablicy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Wielowymiarowe tablice mogą mieć różne rozmiary, dla każdego wymiaru. Przykładowo, podana tablicą trójwymiarową `myarray[3][2][6]`, ta metoda zwróci 3, 2 i 6 w `dwDimensions` parametru w podanej kolejności.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)