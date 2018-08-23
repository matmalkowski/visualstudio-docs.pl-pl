---
title: IEnumDebugFrameInfo2::GetCount | Dokumentacja firmy Microsoft
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
- IEnumDebugFrameInfo2::GetCount
helpviewer_keywords:
- IEnumDebugFrameInfo2::GetCount
ms.assetid: d02a08e3-f34f-461e-8195-5157e154c481
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0fb2d31b74b73f59586be359e62d5ab176b8c9f5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681461"
---
# <a name="ienumdebugframeinfo2getcount"></a>IEnumDebugFrameInfo2::GetCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IEnumDebugFrameInfo2::GetCount](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ienumdebugframeinfo2-getcount).  
  
Zwraca liczbę elementów w wyliczeniu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetCount(  
   ULONG* pcelt  
);  
```  
  
```csharp  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pcelt`  
 [out] Zwraca liczbę elementów w wyliczeniu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda nie jest częścią zwyczajowego interfejs wyliczanie modelu COM, który określa, że tylko `Next`, `Clone`, `Skip`, i `Reset` metod, które muszą zostać zaimplementowane.  
  
## <a name="see-also"></a>Zobacz też  
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)

