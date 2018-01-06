---
title: IDebugCoreServer3::GetServerFriendlyName | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCoreServer3::GetServerFriendlyName
helpviewer_keywords: IDebugCoreServer3::GetServerFriendlyName
ms.assetid: 7035b904-b3d7-4d9b-98d9-65714b8a8b9f
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: cdcffa689dc9318c54969449a6548e3d9699defd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcoreserver3getserverfriendlyname"></a>IDebugCoreServer3::GetServerFriendlyName
Pobiera przyjazną nazwę dla serwera.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetServerFriendlyName(  
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetServerFriendlyName(  
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrName`  
 [out] Zwraca przyjazną nazwę dla serwera.  
  
> [!NOTE]
>  Element wywołujący jest odpowiedzialny za zwalnianie ciąg.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 W przypadku serwerów użytkownik uruchomił nazwa zwracane przez tę metodę jest pełna nazwa serwera. W przypadku serwerów uruchamiana automatycznie nazwa jest czy maszyny serwera jest uruchomiona.  
  
 Dla nazwy zorientowane na komputerze, należy wywołać [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)