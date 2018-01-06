---
title: IEnumDebugCustomAttributes::Clone | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumCustomAttributes::Clone
helpviewer_keywords: IEnumDebugCustomAttributes::Clone
ms.assetid: e6825000-e195-42b4-b296-bfe1e533d79b
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7ecbd221c9d89c20c924dff16c42f6faa4849d8d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugcustomattributesclone"></a>IEnumDebugCustomAttributes::Clone
Tworzy moduł wyliczający, który zawiera takim samym stanie wyliczenie jako bieżący modułu wyliczającego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Clone (   
   IEnumCustomAttributes** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugCustomAttributes ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 ppEnum  
 [out] Zwraca kopię tego wyliczenia jako oddzielny obiekt.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Kopiuj wyliczenia ma takim samym stanie, co oryginalne w czasie, gdy ta metoda zostanie wywołana. Jednak kopiowania i oryginalny stan są oddzielone i można zmieniać pojedynczo.  
  
## <a name="see-also"></a>Zobacz też  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)