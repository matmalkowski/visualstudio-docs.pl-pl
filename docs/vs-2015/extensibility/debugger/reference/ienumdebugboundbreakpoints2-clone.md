---
title: IEnumDebugBoundBreakpoints2::Clone | Dokumentacja firmy Microsoft
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
- IEnumDebugBoundBreakpoints2::Clone
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2::Clone
ms.assetid: c6ce01a2-7da3-46ec-9837-855042fa7244
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 959e86563ff77907cecde265ce8e9a5bc1c110df
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42682448"
---
# <a name="ienumdebugboundbreakpoints2clone"></a>IEnumDebugBoundBreakpoints2::Clone
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IEnumDebugBoundBreakpoints2::Clone](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ienumdebugboundbreakpoints2-clone).  
  
Zwraca kopię bieżącego wyliczenia jako oddzielny obiekt.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugBoundBreakpoints2** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugBoundBreakpoints2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppEnum`  
 [out] Zwraca kopię tego wyliczenia jako oddzielny obiekt.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Kopię wyliczenia ma ten sam stan, co oryginalny w czasie, którego ta metoda jest wywoływana. Jednak stany kopiowania i oryginalne są niezależne i można zmieniać indywidualnie.  
  
## <a name="see-also"></a>Zobacz też  
 [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)

