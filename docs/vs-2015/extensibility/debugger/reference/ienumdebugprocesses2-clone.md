---
title: IEnumDebugProcesses2::Clone | Dokumentacja firmy Microsoft
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
- IEnumDebugProcesses2::Clone
helpviewer_keywords:
- IEnumDebugProcesses2::Clone
ms.assetid: 3d4196d3-5a80-4f76-b8b2-f72e80c8d406
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 24fd1780c785b40c9894cf1d10a856c84a8e0800
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42686792"
---
# <a name="ienumdebugprocesses2clone"></a>IEnumDebugProcesses2::Clone
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IEnumDebugProcesses2::Clone](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ienumdebugprocesses2-clone).  
  
Zwraca kopię bieżącego wyliczenia jako oddzielny obiekt.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugProcesses2** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugProcesses2 ppEnum  
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
 [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)

