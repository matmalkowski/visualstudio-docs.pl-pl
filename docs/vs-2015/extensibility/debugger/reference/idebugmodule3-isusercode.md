---
title: IDebugModule3::IsUserCode | Dokumentacja firmy Microsoft
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
- IDebugModule3::IsUserCode
helpviewer_keywords:
- IDebugModule3::IsUserCode
ms.assetid: 77022946-bb8b-4114-aa81-614df6e54b13
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f6e633006cd41cfd88c85d8213498786c13fad9b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42678395"
---
# <a name="idebugmodule3isusercode"></a>IDebugModule3::IsUserCode
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugModule3::IsUserCode](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugmodule3-isusercode).  
  
Pobiera informacji na temat tego, czy moduł reprezentuje kod użytkownika, czy nie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT IsUserCode(  
   BOOL* pfUser  
);  
```  
  
```csharp  
int IsUserCode(  
   out int pfUser  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pfUser`  
 [out] Wartość różną od zera (`TRUE`) moduł reprezentuje kod użytkownika, wartość zero (`FALSE`) Jeśli nie jest.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)

