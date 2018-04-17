---
title: IEEDataStorage::GetData | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2ddbc77950396df743b88ce3b6c1a94bbeaf8126
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
Pobiera określoną liczbę bajtów z obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetData(  
   ULONG  dataSize,  
   ULONG* sizeGotten,  
   BYTE*  data  
);  
```  
  
```csharp  
int GetData(  
   uint     dataSize,  
   out uint sizeGotten,  
   byte[]   data  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dataSize`  
 [in] Liczba bajtów do pobrania ( `data` tablicy musi posiadać co najmniej następującej liczbie bajtów).  
  
 `sizeGotten`  
 [out] Zwraca liczbę bajtów faktycznie pobrany.  
  
 `data`  
 [w, out] Tablica wypełnia się żądanych danych.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Zalecane użycie tej metody jest do pobrania wszystkich bajtów danych do lokalnej tablicy, ponieważ nie można pominąć bajtów w procesie pobierania. W tym przypadku parametr `dataSize` powinien mieć wartość zwracana przez [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)