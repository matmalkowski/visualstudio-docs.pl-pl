---
title: IDebugPortSupplierDescription2::GetDescription | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugPortSupplierDescription2::GetDescription
ms.assetid: bff5f536-1cd1-4313-8856-db7b05818305
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d281ae3b069eb3644e57b82581cc3f5b51a7b0c2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugportsupplierdescription2getdescription"></a>IDebugPortSupplierDescription2::GetDescription
Pobiera opis metadanych i Opis portu dostawcy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetDescription(  
   PORT_SUPPLIER_DESCRIPTION_FLAGS *pdwFlags,  
   BSTR *pbstrText  
);  
```  
  
```csharp  
public int GetDescription(  
   out enum_PORT_SUPPLIER_DESCRIPTION_FLAGS pdwFlags,  
   out string pbstrText  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdwFlags`  
 [out] Metadane flagi opisu.  
  
 `pbstrText`  
 [out] Opis dostawcy portu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md)