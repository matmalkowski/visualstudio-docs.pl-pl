---
title: IDebugPortPicker::SetSite | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugPortPicker::SetSite
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a307c2b387905706d229d7811f490f109f14c78f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugportpickersetsite"></a>IDebugPortPicker::SetSite
Ustawia dostawcę usługi.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetSite(  
   IServiceProvider * pSP  
);  
```  
  
```csharp  
public int SetSite(  
   IServiceProvider pSP  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pSP`  
 [in] Odwołanie do interfejsu dostawcy usług.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zostanie wywołana przed wszystkie inne metody są wywoływane.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)