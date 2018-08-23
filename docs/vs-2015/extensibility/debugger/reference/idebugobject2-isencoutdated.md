---
title: IDebugObject2::IsEncOutdated | Dokumentacja firmy Microsoft
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
- IDebugObject2::IsEncOutdated
helpviewer_keywords:
- IDebugObject2::IsEncOutdated method
ms.assetid: d3a8c02d-895b-478c-9957-d663130f308e
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 829da5ec42d19a0c938a87dbc51bf10d92d21e55
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42678255"
---
# <a name="idebugobject2isencoutdated"></a>IDebugObject2::IsEncOutdated
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugObject2::IsEncOutdated](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugobject2-isencoutdated).  
  
Ta metoda określa, czy stan Edytuj i Kontynuuj tego obiektu lub kontenera nadrzędnego jest nieaktualna. Ewaluator wyrażeń niestandardowych nie implementuje tę metodę i zawsze zwraca `E_NOTIMPL`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT IsEncOutdated(  
   BOOL* pfEncOutdated  
);  
```  
  
```csharp  
int IsEncOutdated(  
   out int pfEncOutdated  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pfEncOutdated`  
 [out] Wartość różną od zera (`TRUE`) Jeśli stan Edytuj i Kontynuuj jest nieaktualna, zero (`FALSE`) Jeśli nie jest.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
> [!NOTE]
>  Ewaluator wyrażeń niestandardowych zawsze powinna zwrócić `E_NOTIMPL`.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)

