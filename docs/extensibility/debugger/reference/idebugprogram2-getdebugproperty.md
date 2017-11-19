---
title: IDebugProgram2::GetDebugProperty | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::GetDebugProperty
helpviewer_keywords: IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 86328e07b8cd2cf8c72de5713b347512f4a354c8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogram2getdebugproperty"></a>IDebugProgram2::GetDebugProperty
Pobiera właściwości tego programu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetDebugProperty(   
   IDebugProperty2** ppProperty  
);  
```  
  
```csharp  
int GetDebugProperty(   
   out IDebugProperty2 ppProperty  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppProperty`  
 [out] Zwraca [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) obiekt, który reprezentuje właściwości programu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Właściwości zwracane przez tę metodę są specyficzne dla programu. Jeśli program musi zwracać więcej niż jedną właściwość, a następnie [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) obiektu zwróconego przez tę metodę jest kontenerem dodatkowe właściwości i wywoływania [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) zwraca — metoda Lista wszystkich właściwości.  
  
 Program może narazić dowolną liczbę i rodzaj dodatkowe właściwości, które można opisać za pośrednictwem `IDebugProperty2` interfejsu. IDE może wyświetlić właściwości dodatkowy program za pomocą interfejsu użytkownika przeglądarki właściwości ogólnych.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)