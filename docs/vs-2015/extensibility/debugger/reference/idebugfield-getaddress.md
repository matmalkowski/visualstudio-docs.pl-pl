---
title: IDebugField::GetAddress | Dokumentacja firmy Microsoft
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
- IDebugField::GetAddress
helpviewer_keywords:
- IDebugField::GetAddress method
ms.assetid: 6981bf03-66ef-4bf9-87ea-f6c9624486cb
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 560e3914a090b52cfa32c79fc8f0d85f2f1912ac
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42677245"
---
# <a name="idebugfieldgetaddress"></a>IDebugField::GetAddress
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugField::GetAddress](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugfield-getaddress).  
  
Ta metoda pobiera adres debugowania pola.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetAddress(   
   IDebugAddress** ppAddress  
);  
```  
  
```csharp  
int GetAddress(  
   out IDebugAddress ppAddress  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppAddress`  
 [out] Zwraca adres jako [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)

