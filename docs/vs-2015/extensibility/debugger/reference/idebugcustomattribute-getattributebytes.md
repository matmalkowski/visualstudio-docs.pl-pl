---
title: IDebugCustomAttribute::GetAttributeBytes | Dokumentacja firmy Microsoft
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
- IDebugCustomAttribute::GetAttributeBytes
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeBytes
ms.assetid: cf34583b-6530-4dcc-89f8-eb27e4e8d594
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 574deb12fd774d989f2868dd1300c6a641849015
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42677946"
---
# <a name="idebugcustomattributegetattributebytes"></a>IDebugCustomAttribute::GetAttributeBytes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugCustomAttribute::GetAttributeBytes](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcustomattribute-getattributebytes).  
  
Pobiera informacje o atrybutach jako obiekt blob bajtów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
 [out w] Tablica, która jest wypełniane bajtów atrybutu.  
  
 `pdwLen`  
 [out w] Określa maksymalną liczbę bajtów do zwrócenia w `ppBlob` tablicy i zwraca liczbę bajtów rzeczywiście zapisanych na tablicy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ustaw `ppBlob` parametr ma wartość null, aby zwrócić liczbę atrybutów dostępnych bajtów. Następnie przydzielić tablicy i przekażesz ten tablica w `ppBlob` parametru.  
  
 Bajty atrybut reprezentują dane pierwotne atrybutu niestandardowego.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)

