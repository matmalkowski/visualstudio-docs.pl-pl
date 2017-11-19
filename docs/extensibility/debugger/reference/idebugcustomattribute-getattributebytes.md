---
title: IDebugCustomAttribute::GetAttributeBytes | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCustomAttribute::GetAttributeBytes
helpviewer_keywords: IDebugCustomAttribute::GetAttributeBytes
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1258b2b7fdc1c91eaaa6265ce74a3891deda8ab0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcustomattributegetattributebytes"></a>IDebugCustomAttribute::GetAttributeBytes
Pobiera informacje o atrybutach jako obiekt blob bajtów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetAttributeBytes(   
   BYTE*  ppBlob,  
   DWORD* pdwLen  
);  
```  
  
```csharp  
int GetAttributeBytes(  
   ref byte[] ppBlob,   
   ref uint   pdwLen  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppBlob`  
 [w, out] Tablica jest wypełniane bajtów atrybutu.  
  
 `pdwLen`  
 [w, out] Określa maksymalną liczbę bajtów do zwrócenia w `ppBlob` tablicy i zwraca liczbę bajtów zapisana do tablicy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ustaw `ppBlob` parametr ma wartość null, aby zwrócić liczbę atrybutów liczby dostępnych bajtów. Następnie przydzielić tablicy i przekaż tablicy w przypadku `ppBlob` parametru.  
  
 Bajty atrybutu reprezentują nieprzetworzone dane atrybutu niestandardowego.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)